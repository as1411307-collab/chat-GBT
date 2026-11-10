# Evidence/claim status

Definitions:
- **SOURCE-CLAIMED:** Stated in uploaded report or upstream docs, not independently re-run.
- **CODE-INSPECTED:** Relevant implementation read from the exact upstream Git commit; not necessarily executed.
- **TEST-FILE-SEEN:** Test exists; no claim that it passed in this session.
- **REPORTED-PASS:** Source states it passed; original log not independently validated.
- **RUN-VERIFIED:** A test or end-to-end path was executed with recorded environment, command and result.
- **UNRESOLVED:** Missing evidence or conflicting statements.

Examples found in four-repository reviews:
- Ollama web search source calls `https://ollama.com/api/web_search`: CODE-INSPECTED; does **not** establish offline search.
- Ollama speech routes validate formats/capabilities: CODE-INSPECTED; test file seen; no local speech model benchmark here.
- Langflow refresh-token implementation at commit `60999cc9a7350e44dde3ef641baae864e10861f0` checks token type and active user. Older skipped tests contradicted the current implementation: CODE-INSPECTED.
- Awesome LLM Apps local_chatgpt_memory.py trusts user-supplied user_id with no authentication in that example: CODE-INSPECTED; unsafe multi-user example.
- Open Design has connector-specific rate limits (10 calls/minute and 60 per run) in connector service at `07a86b1041531bfa0bec1006d9c0993985fee560`: CODE-INSPECTED; not proof of global API rate limiting.
- User-provided independent audit records 21/21 redaction and 13/13 SSRF acceptance probes: REPORTED-PASS unless underlying execution logs are available.

All research materials keep their original claims; this page does not overwrite those originals.
