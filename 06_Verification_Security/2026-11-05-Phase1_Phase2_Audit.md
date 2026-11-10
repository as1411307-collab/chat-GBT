# Joint Phase 1 + Phase 2 Audit (2026-11-05)

## Scope and evidence

This report audits the *actual* Phase 1 package, not an assumed future implementation. Baseline: `private_core_phase1_subtraction_reviewed.zip` (5 project files). Its 14 existing tests passed locally. Additional adversarial checks demonstrated: (a) `NaN` and `1e999` task values caused HTTP 500; (b) Arabic word forms differed in FTS5 matching; (c) the same owner API key could create and approve a task; (d) memory had no delete endpoint. The minimally amended Phase 1 package now passes **17/17** tests. The tests do not prove a production deployment is safe.

**Phase 2 has not been implemented, invoked, or tested against live model providers.** Everything about Phase 2 here is an implementation boundary and acceptance plan, not a claim of working AI integration.

## Decision: subtract before adding

Keep:
- One FastAPI process on a single private machine; SQLite + WAL + FTS5; no separate vector DB.
- A knowledge table with an external-content FTS5 index and matching update/delete triggers.
- One versioned memory history table; conflict detection; explicit owner deletion.
- A task intent ledger, but ONLY for future external side-effect workflows, never as the LLM transport protocol.
- The existing encrypted offline backup and restore, within its small-DB/RAM limits.

Exclude from the first model integration:
- LangChain/LangGraph/agent swarms, autonomous tool executors, message brokers, Redis, PostgreSQL, pgvector, Chroma, new storage services, model-controlled SQL or network access.
- Auto-switching among vendors when the failure mode, privacy tradeoff, or cost is unknown.
- Hosted conversation storage as the source of truth for personal memory.
- Any automatic promotion of model output to verified long-term memory.

Do not physically drop existing tables on user databases. No destructive auto-migration.

## Actual Phase 1 defects and minimal repairs

1. **Non-finite JSON values** in `tasks.data` reached `json.dumps(..., allow_nan=False)`, causing unhandled ValueError / HTTP 500. Fixed: input rejected with HTTP 422, no task row created.
2. **Memory could be written indefinitely but not erased through the API.** Fixed: owner-authenticated `DELETE /api/v1/memory/{key}` removes all versions in the active history table and older `memory_current` duplicate rows where that legacy table exists. It does NOT erase old backups, WAL/free-list remnants, model-provider copies, or forensic disk residues.
3. **Single shared owner key can submit and approve.** Proven by the local probe, but deliberately not 'solved' with a new auth stack: Phase 2 must NEVER pass this key to a model or vendor. Before exposing the server to iPhone/network clients, separate client authorization and approval authority appropriately (outside this local Phase 1 scope).
4. **FTS is lexical, not natural-language RAG.** `"الموافقات"` matched, `"والموافقات"` did not; a full question also returned no match because the query uses AND. Do not claim semantic retrieval. Prefer a small, tested keyword normalization or two-pass keyword search within the existing FTS5 layer before introducing embeddings. Any changes require Arabic recall/precision tests first.
5. **Knowledge sources are user-supplied labels**, not proof of publication or authenticity. Future answers must cite returned document IDs and describe origins as unverified unless independently established. An edited document has no immutable content version; if verifiable snapshots become necessary, derive a hash from selected context at retrieval time before adding another table.
6. **No bounded evidence packet exists yet** because there is no model connector. A 20-document lookup could return up to ~400k characters of content; Stage 2 must limit excerpts before sending external traffic. Do not pipe the whole knowledge search response into a provider request.
7. **This is not a deployed authentication/security design.** The current API key is for localhost and must not be embedded in a public iOS app. SQLite data at rest is not encrypted. Encrypted backups alone do not protect a compromised host.

## Minimal Phase 2 contract (design only)

Transport: ONE authenticated `/api/v1/ask` endpoint inside the existing FastAPI service. Implementation should use an explicit, fixed allow-list of model aliases and provider endpoints. One provider is sufficient for the first live smoke test; the same adapter signature can support a second provider without changing the database.

Logical request: `question`, `model_alias`, `include_private_context=false` by default, plus a bounded context selection policy. The owner must consciously allow cloud-bound private context; model output cannot change that permission.

Flow:
1. Authenticate the OWNER/CLIENT to the Core (the model itself receives no core credentials).
2. Choose a permitted model alias and cap input/output and active calls.
3. If approved by the owner, retrieve a bounded number of knowledge excerpts and attach stable local IDs; treat every excerpt as untrusted text. Do not convert source text into system instructions.
4. Send the minimum necessary context over an outbound connection to an allowed provider endpoint, with keys stored only on the server; apply a short timeout.
5. Parse the provider response as untrusted result DATA. Validate model identity, response format and completion status; return the answer plus source IDs, actual provider alias, and any reported usage.
6. Do not perform any tool invocation, memory write, task approval or remote action based only on text returned by the model.

OpenAI Responses API: set `store=false` as a privacy preference where compatible, while recognizing that this alone does not promise zero retention; check provider-specific data controls. Anthropic Messages API is stateless by design. Both should be wrapped behind a very small adapter, not a framework.

Timeout rule: a network timeout does NOT prove the provider did not process or charge the request. Report an explicit unknown/timeout status; no automatic retry or silent fallback across vendors.

## The task ledger must stay out of ordinary inference

`/api/v1/tasks`, `approve` and `cancel` currently record intent/authorization only. `READY` specifically means approved but **not executed**. Avoid reusing this state machine for a text generation call. If later external actions are added, that is a separate verified execution path with request hashes and distinct approval authority. Do not claim 'executed' until an actual tool result is verified.

## Phase 2 security acceptance tests (not yet run)

A. Without owner-approved external sharing, mock provider captures **zero** knowledge/memory text.
B. With sharing approved, mock provider sees only approved short excerpts, with local document IDs and hard context bounds.
C. A retrieved document containing malicious commands cannot trigger owner approval, database writes, shell use, or HTTP calls; model tools are disabled.
D. A model response that asks to store memory is treated as text, not a write operation.
E. Provider key and Core owner key never appear in model input/output, returned error text, or normal logs.
F. Timeout/unavailable/rate-limit are reflected as errors; no false success, unbounded loop, or automatic vendor fallback.
G. Switching an explicitly selected provider does not modify knowledge or memory and does not change the meaning of source citations.
H. Model outputs, provider usage, and whether any private context left the Core are correctly reported, and cannot claim that tools were executed.
I. Existing Phase 1 tests keep passing unchanged after the adapter is added.

## Deployment gate

Phase 1 after these small repairs is suitable as a locally testable single-owner foundation, NOT an internet-exposed production server. Before remote iPhone access: device authentication, TLS/private tunnel, secrets rotation, host disk encryption, restored backup rehearsal, and network-level exposure checks must be scoped and tested. They are operational deployment gates, not reasons to install another agent framework today.

## Source verification

- SQLite external-content FTS5 & triggers: https://www.sqlite.org/fts5.html
- SQLite WAL restrictions: https://www.sqlite.org/wal.html
- OpenAI Responses API, `store=false`: https://developers.openai.com/api/docs/guides/migrate-to-responses
- OpenAI API data retention: https://developers.openai.com/api/docs/guides/your-data
- Anthropic Messages API (stateless): https://platform.claude.com/docs/en/build-with-claude/working-with-messages
- OWASP prompt injection limits and least privilege: https://genai.owasp.org/glossary/prompt-injection/

Evidence quality: official vendor/security documentation supports the API and database claims. Community discussions about personal RAG setups are anecdotal and do not justify more services before testing a failure of the present FTS5-based approach.