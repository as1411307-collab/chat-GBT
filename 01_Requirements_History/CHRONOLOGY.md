# Chronology of application + private agent system (conversation-derived)

> This timeline is **historical context**, not a declaration that all proposed solutions were implemented or that all options are still approved.

| Period | Earlier request / development | Status |
|---|---|---|
| 2026-09-23 | General-purpose agent: memory, comprehension, web, files and tools; privacy concerns. | User requirements |
| 2026-09-26 | Discussion of Hermes desktop runtime, iPhone app as client, platform builders and API bridge. | Options considered |
| 2026-09-30 | Base44 CRM/"AHMED" UI; preserve existing CRM, mobile-first missions, agents, approvals, chat. | Historical prototype |
| 2026-10-01 | Expo / React Native / EAS starting path for iPhone testing. | Historical choice, later superseded |
| 2026-10-21–25 | Cinematic interface/Unreal/ready-made asset, connectors, agents, voice; later cinematic priority lowered. | Historical alternatives |
| 2026-11-01–04 | Expo SDK 57 repository audits, Hermes bridge, Secure Enclave approvals, run state and execution/receipt gaps. | Historical design/debugging |
| 2026-11-05 | User rejected earlier repository and requested a clean start; simplification and re-auditing. | New starting point |
| 2026-11-06 | Selected "architecture two" with single core + passive learning recorder, Mac storage and optional weekly ZIP exports. | Selected direction, subject to later changes |
| 2026-11-06–08 | Scoped to native SwiftUI, Arabic RTL, thin iOS client, protected Core API, owner approvals, memory and evidence. | User requirements |
| 2026-11-08–09 | Collected iPhone research corpus, previous requirements and code/design previews; multiple ZIP/Markdown versions. | Document corpus, not production proof |
| 2026-11-09–10 | Four-repository catalog: Open Design, Awesome LLM Apps, Langflow and Ollama; reports, Git inventories and security review. | Research and code inspection |
| 2026-11-10 | Requested separate repositories/branches for work from different models. | Archive task |

## Current architectural direction as recorded in discussion

- **Interface:** native iPhone app with Chat, Spaces and Activity; source code in Xcode and the owner's Apple Developer account. Live execution only when verified by the core, otherwise DEMO/Offline.
- **Core:** private server (Mac or VPS considered), orchestration, task state, data store, tool execution and approvals.
- **Storage:** SQLite WAL/FTS5 as lightweight initial option; vectors or Postgres deferred unless demonstrated necessary.
- **Learning recorder:** passive append-only event/evidence capture and periodic export to Mac; it has no tool execution authority.
- **Approval security:** signed/verified approvals for sensitive actions, fail-closed external IO, source/tool receipts; Secure Enclave P-256 discussed.
- **Security:** limit prompt injection, memory/RAG/tool poisoning, secret access, exposed endpoints, unauthorized tool use and false success reports.
- **Integrations:** add connector-backed services selectively, not a swarm of autonomous agents.
- **Do not erase:** early alternatives, code, drafts, corrections and conflicting instructions; label status and provenance.

## Important caveats

Historical conversations include proposals that conflict across dates (e.g. Expo/SwiftUI, multiple cores/single core, cinematic UI/plain control UI, cloud/Mac runtime). Archive all with dates. Do not resolve conflicts silently.
