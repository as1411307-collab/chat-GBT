# Archive — ChatGPT research, app and agent system (Sep–Nov 2026)

This branch is **separate from** `main` and separate from the `kimi` repository. It stores accessible ChatGPT-side research, technical analyses, requirements and files for native iPhone assistant app and private agent system.

## Time window
2026-09-10 — 2026-11-10. Older references may be preserved when later conversations incorporated them.

## Categories

- `01_Requirements_History/`: historical instructions, decisions and contradictory alternatives **without silent deletion**.
- `02_iOS_App_Xcode/`: SwiftUI / iOS, UI, security, TestFlight and development.
- `03_Architecture_Core/`: client–core boundaries, server, approvals, execution.
- `04_Memory_Learning/`: append-only recorder, knowledge, local memory and learning.
- `05_Repository_Research/`: GitHub studies and catalogs.
- `06_Verification_Security/`: real-code audits, threat reviews, test evidence.
- `07_Tools_Skills_Integrations/`: agents, skills, MCP, n8n and external systems.
- `08_Implementation_Artifacts/`: code and technical deliverables.
- `09_Incoming_Source_Reports/`: submitted reports and original source material, including other models' work, **clearly labeled as incoming**.
- `10_Raw_Indexes/`: Git inventories, trees, branches, raw lists.
- `11_Asset_Register/`: binary files and archives that may require another upload route.
- `12_Claims_Status/`: verified vs source-claimed vs unresolved evidence.

## Provenance rules
1. Preserve originals and historical alternatives; **classification is not endorsement**.
2. Distinguish user requirements, ChatGPT-origin outputs, uploaded outside-model reports, external repository facts and inferences.
3. Never label an item tested because an identical count or a test file exists.
4. Do not post personal unrelated files or credentials; source files blocked for secrets will be identified in the manifest.
5. This archive is **incremental**. The manifest lists what was actually imported and what remains accessible only via ChatGPT Library. Do not claim complete prior-conversation coverage unless all underlying source records have been verified.
6. Namespaces remain separate: `as1411307-collab/kimi` is never modified by this branch's updates.

## Historical decisions (see details)
- Native iPhone app (SwiftUI/Xcode, Arabic RTL) with control/review UI.
- Private server-side core owns task execution and memory; no provider keys or agent execution in iOS client.
- Sensitive external actions need explicit owner approval and verifiable receipts.
- Append-only learning recorder captures evidence, sources, tool use, evaluations (not inaccessible private model chain-of-thought), periodic export to Mac.
- Multiple architectures and abandoned prototypes remain part of the historical record, not endorsed implementations.
- Verify real execution end to end; remove needless complexity before expanding scope.

See `01_Requirements_History/CHRONOLOGY.md` and `12_Claims_Status/VERIFICATION_POLICY.md`.
