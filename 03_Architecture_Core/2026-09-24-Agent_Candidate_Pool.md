# Ahmed Agent v2 — Master Candidate Pool
**تاريخ التجميع:** 24 سبتمبر 2026  
**الحالة:** RAW / UNFILTERED — لا اختيار، لا ترتيب أفضلية، لا اعتماد معماري بعد.  
**الهدف:** حفظ كل الأنظمة والأدوات والمفاهيم التي ظهرت في نقاشات Ahmed Agent حتى الآن، ثم نقارنها لاحقًا ونختار منها قبل Architecture Freeze.

> قاعدة هذه الوثيقة: وجود الاسم هنا لا يعني اعتماده. هذه قائمة تجميع فقط.

---

## 1) Orchestration / Agent Frameworks / Workflow Engines
- LangGraph
- Dify
- n8n
- CrewAI
- Relevance AI
- Gumloop
- Lindy
- Flowise
- OpenAI Agents SDK
- Make
- Prefect
- Temporal
- DBOS
- Restate
- Hatchet
- Inngest
- Trigger.dev
- Buildy
- Replit Agent
- LangChain / LangGraph ecosystem
- Pydantic / structured contracts
- MCP-compatible agent runtimes

## 2) Decision / Routing / Planning / Control
- Jev — TypeSafe AI
- Model Router
- Agent Router
- Tool Router
- Runtime Router
- FastPlanner
- Control Plane
- Model Manager
- Tool Registry
- Tool Gateway
- Capability Registry
- Adapter Layer
- Budget Governor
- Token Budget
- Cost Gate
- Permission Gate
- Approval Gate
- HITL Gate
- Task Contract
- Dependency Graph
- Dynamic Execution Graph
- Final Synthesis
- Verifier / Judge
- Critic / Reviewer
- Contradiction Detector
- Evaluator
- Escalation policy
- Retry policy
- Stop / Pause / Resume controls

## 3) Model Access / Model Providers / Model Abstraction
- OpenRouter
- LiteLLM
- OpenAI models / GPT
- Anthropic / Claude
- Google / Gemini
- Qwen
- Hugging Face
- Replicate
- Multi-provider fallback
- Provider-independent adapters
- Model selection by quality / cost / latency
- Smart Routing
- Load balancing
- Fallback routing
- Model telemetry
- Provider telemetry
- **اسم ظهر في نقاش سابق ويحتاج تحقق قبل أي اعتماد:** “GPT-6 Astra”

## 4) Model Families / Specialized Model Types
- LLM
- VLM
- SLM
- LAM
- MoE
- LCM
- MLM
- SAM
- Vision models
- Speech models
- Image generation models
- Video generation models
- Embedding models
- Reranking models

## 5) Search / Web Research / Deep Research
- Tavily
- Firecrawl
- Exa
- Parallel Search
- Needle
- Waldo
- Sider Scholar
- Powerset Research
- SearchProvider abstraction
- PageFetcher abstraction
- Web Search
- Deep Research
- Scientific / Technical Research
- Market / Opportunity Research
- Verification Research
- Query Planning
- Search decomposition
- Source discovery
- Crawling
- Scraping
- Extraction
- Source ranking
- Evidence mapping
- Gap analysis
- Contradiction detection
- Citation generation
- Freshness checks

## 6) Specialized Research / Data Sources Mentioned
- DirectCase Legal Research
- Midpage Legal Research
- CourtListener
- Quartr
- GSC Wizard
- Serpstat
- Adthena
- Mixpanel Headless
- Coupler.io
- Windsor.ai
- Common Room
- LinkedIn
- Indeed
- JobsPipe
- ClinicalTrials.gov
- openFDA
- Healthcare Public Data
- Soracom Knowledge

## 7) RAG / Knowledge / Retrieval
- RAG
- GraphRAG
- Vector Store
- Knowledge Graph
- Embeddings
- Chunking
- Parsing / ingestion
- Metadata filtering
- Hybrid retrieval
- Reranking
- Indexing
- Index Scaling
- Source of Truth
- Knowledge freshness
- Retrieval citations
- Evidence Core
- Vettara / الاسم السابق كما ورد ويحتاج تحقق من الاسم الدقيق
- Supabase Vector / pgvector-style option
- PostgreSQL-backed knowledge storage

## 8) Memory
- Short-term memory
- Long-term memory
- Episodic memory
- Semantic memory
- Working memory
- Selective Memory Gate
- Memory importance scoring
- Memory update / overwrite policy
- Forgetting / decay policy
- Retrieval by relevance
- Basic Memory Cloud
- Memco Shared Memory
- Session State
- Operational Project State
- Persistent context
- “احفظ فقط ما يحتمل أن نحتاجه مستقبلًا”

## 9) Connectors / Actions / Tool Access
- Composio
- MCP
- n8n integrations
- Make integrations
- Gmail
- Google Calendar
- Google Drive
- Google Docs
- Google Sheets
- Google Slides
- GitHub
- GitHub Actions
- Slack
- Notion
- Airtable
- Dropbox
- Supabase
- CRM connectors
- APIs
- Webhooks
- Browser / Computer Use
- Code execution / Code-as-Action sandbox
- File tools
- MY_FILES scope
- WEB scope
- WhatsApp integration candidate where a suitable supported connector exists
- Sina Connect
- Neura Relay MCP
- ToolMatch
- Context7
- API Documentation Checker

## 10) Media / Voice / Multimodal
- ElevenLabs
- Whisper
- Kokoro
- Replicate
- Higgsfield
- Runway
- HeyGen
- Image generation
- Video generation
- Speech-to-Text
- Text-to-Speech
- Voice cloning / voice localization
- Image understanding
- Video understanding
- Multimodal Perception & Communication Plane
- Media Team / Media Path

## 11) Execution / Reliability / Long-running Work
- Async Agent Jobs
- Queues
- Workers
- Worker leases
- Orphan detection
- Checkpoints
- Recovery
- Retry
- Resume
- Durable execution
- Persistence
- State machine
- Idempotency
- Deduplication
- Scheduling
- Background jobs
- Long-running tasks
- Human approval checkpoints
- Prefect
- Temporal
- DBOS
- Restate
- Hatchet
- Inngest
- Trigger.dev

## 12) Observability / Quality / Evaluation
- LangSmith
- Tracing & Evals
- OpenTelemetry
- Logs
- Metrics
- Alerts
- Regression tests
- Evaluation harness
- Semantic quality evaluation
- Provider/model telemetry
- Audit trail
- Provenance
- Evidence verification
- Independent reviewer
- QA Gate
- Source-status inspection
- Architecture fingerprinting

## 13) Caching / Performance / Cost
- Prompt Cache
- Semantic Cache
- Token Budget
- Tool Budget
- Model Budget
- Request quotas
- Rate limits
- Cost optimization
- Model fallback
- Edge Inference
- Serverless GPU
- Index Scaling
- Parallel execution
- Smart routing by latency / cost / quality

## 14) Security / Permissions / Governance
- Permissions
- Scopes
- MY_FILES / WEB isolation
- Human-in-the-loop approvals
- Approval gates
- Secrets management
- Sandbox
- Tenant isolation
- Workspace isolation
- Read-only vs write permissions
- Tool allowlist / denylist
- Cost limits
- Audit chain
- Cedar
- Clerk
- Policy engine
- Owner token
- Provider independence
- Controlled autonomy
- Sovereignty / no provider lock-in

## 15) Data / Storage
- PostgreSQL
- Drizzle
- Supabase
- MotherDuck
- Object Storage
- Vector Store
- File Storage
- Audit Storage
- State Storage
- Memory Storage
- Archive
- Backups
- Retention / cleanup
- Versioning

## 16) UI / App / Product Layer
- Lovable
- Replit
- Vercel
- Buildy
- SwiftUI Expert
- Product Design
- Canva
- Xmind
- Presentations Craft
- Visualize
- Dashboard
- Mission Control
- Live workflow map
- Tasks
- Files
- Archive
- Plan / Steps
- Progress
- Blockage indicator
- Stop point indicator
- Settings
- Workspaces
- Chat UI
- API
- Notifications

## 17) Multi-Agent / Team Patterns
- Multi-Agent
- Supervisor
- Specialist Agents
- Researcher
- Executor
- Planner / Organizer
- Independent Reviewer
- Economic / Investment Team
- Research Team
- Personal Team
- Media Team
- Technical Team
- Delegation
- Agent handoffs
- Parallel work
- Crew / Workforce
- Shared capability layer
- Frozen Path Policy
- Dynamic Tool Selection

## 18) Candidate Paths / Operating Profiles
- Quick Path
- Research Path
- Deep Research Path
- Scientific / Technical Research Path
- Economic / Investment Path
- Market / Opportunity Path
- Verification Path
- Personal Path
- Media Path
- Technical Path
- Files / Knowledge Path
- Code Path
- Tasks / Execution Path
- Reviewer Path

## 19) Hosting / Runtime / Infrastructure
- Replit
- VPS
- Vercel
- Self-hosting
- Cloud hosting
- Edge inference
- Serverless GPU
- Local AI / ASUS NUC concept
- Python 3.13
- Starlette
- Uvicorn
- MCP Python SDK
- Express / TypeScript — legacy / earlier stack
- Expo / Metro — legacy / earlier direction
- GitHub as source of truth
- GitHub Actions

## 20) Future Platform / Business Layer
- Multi-workspace
- Multi-tenant
- Workspace-specific memory
- Workspace-specific permissions
- Customer-specific teams
- Billing
- Usage metering
- Admin console
- Customer configuration
- Tenant isolation
- Business templates
- Sell / deploy configured systems to other companies
- Embedded agent platform
- White-label possibility

## 21) Earlier / Peripheral Candidates That Appeared in Project Discussions
هذه الأسماء ظهرت سابقًا في سياق الأدوات أو التكاملات أو البحث أو التوسع، لكنها ليست بالضرورة Core architecture candidates:
- Spaceship
- Sina Connect
- OpenAI Ads Conversions
- AI Vibe Prospecting
- ClearBounce
- Code Tytor: Python
- Agent Calendars
- Portable Mind Maps
- Agent Community
- GetMeDesign
- Sweet Analytics
- A4B CMMS
- Prompt Perfect
- Werify
- agent.spot
- ArmorCodex
- DocRunic
- Formester
- Lawve AI
- idealista
- AppDeploy
- Scandit SDK
- PR Readiness Check
- RiverScript
- IHate.ai Humanizer
- ChatGPT Ads Manager
- Data Analytics
- Documents
- PDF
- Presentations
- Spreadsheets
- Google Drive / Docs / Sheets / Slides
- Dropbox
- Notion
- Airtable

## 22) Core Architectural Concepts to Preserve for Comparison
- Executive Brain / Main Orchestrator
- Intent Recognition
- Complexity Classification
- Planner
- Budget Governor
- Permission / Policy Layer
- Selective Memory
- Shared Research Capability
- Shared Tool Capability
- Shared Model Pool
- Specialist Teams
- Verification / Judge
- HITL
- Audit / Provenance
- Persistence
- Recovery
- Provider Independence
- Adapter-first integrations
- Workspace separation
- Build-vs-Buy comparison before coding
- Architecture Freeze after research
- New tools/videos enter as candidates first, not immediate design changes

---

## 23) Explicitly NOT FINAL YET
لا يوجد في هذه الوثيقة حتى الآن:
- اختيار نهائي لـ LangGraph أو Dify أو n8n أو CrewAI أو غيرها.
- اختيار نهائي لمزود البحث.
- اختيار نهائي لمزود الذاكرة.
- اختيار نهائي للـRAG / GraphRAG stack.
- اختيار نهائي لمزود النماذج.
- اختيار نهائي للاستضافة.
- قرار Build / Buy لأي طبقة.
- ترتيب أولوية أو Score.

المرحلة التالية لاحقًا:
**Compare → Score → Cost → Fit → Lock Architecture → Build**