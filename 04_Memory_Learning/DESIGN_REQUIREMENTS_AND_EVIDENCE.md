# Passive learning and evidence recorder — historically requested specification

**Origin:** September–November 2026 conversations about the native iPhone personal assistant and private core. A structured preservation of earlier user instructions; NOT evidence that the recorder has been implemented.

## Scope and purpose
- Passive recorder is active by default and receives events from normal tasks and model interactions.
- Its role is **observe / log / classify / evaluate**. It cannot execute code, issue third-party commands, read unrelated secrets, or approve tool actions.
- Capture conversations, question, chosen model, settings when available, output, structured outline/plan presented by the model, code snippets, source URLs, retrieved document references, tool names/inputs/results, time, verification criteria, objective success/failure, exception and user correction.
- Capture what is observable from public/tool interfaces; **hidden internal model reasoning is not exposed by ordinary model APIs**. Do not invent or claim access to private chain-of-thought traces.
- Preserve intermediate *visible* summaries, section headings, draft checks, and reasoning-method descriptions if explicitly produced, with clear source/provenance.

## Architecture
- Main nucleus/core: handles conversations, model routing, tasks, memory and tool execution.
- Passive event recorder: receives append-only event envelopes with timestamps, task/run identifiers, model id, source evidence and outcome, separate from tool execution policy.
- Evaluation lane may compare results and propose revisions; it never self-grants permission to act externally.
- An isolated future local-model laboratory was explored, but rejected as a prerequisite for the first version; preserve as future option.

## Storage
- Storage target: owner's Mac, not iPhone permanent memory.
- Begin with structured logs/SQLite WAL or append-only newline JSON, plus readable Markdown exports; full vector infrastructure not assumed.
- Continuous capture for at least 1–2 months to build a dataset.
- Weekly compressed export (ZIP) preferred; three-day manual export/offload discussed to control phone storage.
- Initial transfer may use explicit iPhone export + AirDrop; reliable automatic background iOS exports should not be assumed without a tested OS-compatible workflow.
- Maintain duplicate IDs, source validity, revision/correction history, classification and pruning choices without silently deleting user-provided facts.

## Data governance
- Separate direct user requirements, source claims, model speculation, tool observations, independent verification and security-sensitive data.
- Source trust levels are not equivalent to instruction priority; retrieval content is untrusted.
- Never embed API keys, raw credentials or personal third-party data in learning logs.
- Store factual answer evidence, methodology and actual tool history instead of treating opaque model explanations as execution receipts.
- Preserve contradictions with timestamps and status, not one flattened 'final truth'.
- Export artifacts should be checksummed; failure or partial export must remain visibly incomplete.

## Acceptance outline
1. A real user task generates source/evidence/tool/outcome records without starting a second agent.
2. Reviewer can inspect exactly what happened, what was assumed, which resources were accessed and where a claim came from.
3. No recorder event can trigger a network side effect directly.
4. ZIP export opens on the Mac and can be imported/replayed for analysis without corrupting events.
5. Data retention and user keep/discard classifications are testable without erasing the original audit history unintentionally.

## Past variations retained
Three autonomous cores and a fully isolated answerer were discussed as exploratory concepts; later simplified to single nucleus + passive recorder and a separate future local model lab. Neither discussion is erased from this archive.
