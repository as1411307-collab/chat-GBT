# LANGFLOW: detailed extraction and requirement relevance
- Number of entries in this source snapshot: **186**
- Categories: **18**
- What this source actually provides: A visual authoring and flow-running product. Bundles are providers, not 80 individually proven installed plugins. Legacy components are separated. Human-in-the-loop has checkpoint behavior in current documentation, but it is not a full external policy engine.
- Scope: all listed items are retained, including low-priority, historical, and third-party ones. No new test run was conducted.
- See `filtered_high_relevance.md` for the useful shortlist and `catalog.csv` for spreadsheet-style search.

## المكونات الأساسية / المدخلات والمخرجات (3)  [3]
### R-0123: [Chat Input](https://docs.langflow.org/concepts-components)
- Original description: إدخال رسائل المستخدم
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 17: UI, dynamic pages and interaction
- Why it may matter: Compose this node with other visual nodes for UI, dynamic pages and interaction; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-013, U-014, U-015, U-016, U-017, U-018, U-019, U-020.

### R-0124: [Chat Output](https://docs.langflow.org/concepts-components)
- Original description: عرض رسائل الناتج
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 17: UI, dynamic pages and interaction
- Why it may matter: Compose this node with other visual nodes for UI, dynamic pages and interaction; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-013, U-014, U-015, U-016, U-017, U-018, U-019, U-020.

### R-0125: [Webhook](https://docs.langflow.org/concepts-components)
- Original description: استقبال طلبات من خدمات خارجية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 09: Tools, skills and MCP connections, 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Tools, skills and MCP connections, Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-076, U-077.

## المكونات الأساسية / المعالجة (5)  [5]
### R-0126: [Data Operations](https://docs.langflow.org/concepts-components)
- Original description: عمليات البيانات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0127: [Dynamic Create Data](https://docs.langflow.org/concepts-components)
- Original description: إنشاء بيانات ديناميكيًا
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0128: [Parser](https://docs.langflow.org/concepts-components)
- Original description: تحليل وتنسيق المحتوى
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Compose this node with other visual nodes for Files, PDF, websites, repositories and structured data; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0129: [Split Text](https://docs.langflow.org/concepts-components)
- Original description: تجزئة النصوص
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0130: [Type Convert](https://docs.langflow.org/concepts-components)
- Original description: تحويل أنواع البيانات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

## المكونات الأساسية / مصادر البيانات (4)  [4]
### R-0131: [API Request](https://docs.langflow.org/concepts-components)
- Original description: استدعاء REST API
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 09: Tools, skills and MCP connections
- Why it may matter: Compose this node with other visual nodes for Tools, skills and MCP connections; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-076, U-077, U-078, U-079, U-080, U-081, U-082, U-083.

### R-0132: [Mock Data](https://docs.langflow.org/concepts-components)
- Original description: توليد بيانات تجريبية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0133: [URL](https://docs.langflow.org/concepts-components)
- Original description: قراءة روابط
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0134: [Web Search](https://docs.langflow.org/concepts-components)
- Original description: البحث عبر الويب
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Compose this node with other visual nodes for Deep research, source checks and evidence; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

## المكونات الأساسية / الملفات والمعرفة (5)  [5]
### R-0135: [File System](https://docs.langflow.org/concepts-components)
- Original description: قراءة وإدارة ملفات ضمن الصلاحيات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Compose this node with other visual nodes for Files, PDF, websites, repositories and structured data; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0136: [Knowledge Base](https://docs.langflow.org/concepts-components)
- Original description: قواعد المعرفة
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 03: RAG, document retrieval and hybrid search, 04: Memory, knowledge history and conflicts
- Why it may matter: Compose this node with other visual nodes for RAG, document retrieval and hybrid search, Memory, knowledge history and conflicts; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0137: [Memory Base](https://docs.langflow.org/concepts-components)
- Original description: ذاكرة أساسية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 04: Memory, knowledge history and conflicts, 21: Storage, export, backup and migration
- Why it may matter: Compose this node with other visual nodes for Memory, knowledge history and conflicts, Storage, export, backup and migration; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0138: [Read File](https://docs.langflow.org/concepts-components)
- Original description: تحميل وقراءة الملفات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Compose this node with other visual nodes for Files, PDF, websites, repositories and structured data; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0139: [Write File](https://docs.langflow.org/concepts-components)
- Original description: كتابة الملفات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data, 28: Writing, journalism, education and content creation
- Why it may matter: Compose this node with other visual nodes for Files, PDF, websites, repositories and structured data, Writing, journalism, education and content creation; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

## المكونات الأساسية / التحكم في المسار (5)  [5]
### R-0140: [If-Else](https://docs.langflow.org/concepts-components)
- Original description: الشروط والتفرعات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0141: [Human Input](https://docs.langflow.org/concepts-components)
- Original description: إدخال بشري أثناء المسار
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 08: Human approval, intervention and checkpoints, 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Human approval, intervention and checkpoints, Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-086, U-087.

### R-0142: [Loop](https://docs.langflow.org/concepts-components)
- Original description: التكرار
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067.

### R-0143: [Notify and Listen](https://docs.langflow.org/concepts-components)
- Original description: تنبيه وانتظار حدث
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 08: Human approval, intervention and checkpoints
- Why it may matter: Compose this node with other visual nodes for Human approval, intervention and checkpoints; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-086, U-087, U-088, U-089, U-090, U-091, U-092, U-093.

### R-0144: [Run Flow](https://docs.langflow.org/concepts-components)
- Original description: تشغيل مسار آخر
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 06: Orchestration, routing and multiple agents, 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Orchestration, routing and multiple agents, Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-108, U-109.

## المكونات الأساسية / عمليات النماذج (7)  [7]
### R-0145: [Batch Run](https://docs.langflow.org/concepts-components)
- Original description: تشغيل دفعات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 10: Workflow visual builder and controllable flows, 18: Schedules, monitoring and always-on operation, 20: Performance, token cost and context optimization
- Why it may matter: Compose this node with other visual nodes for Workflow visual builder and controllable flows, Schedules, monitoring and always-on operation, Performance, token cost and context optimization; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-050, U-051, U-052, U-053, U-054, U-055, U-056, U-057.

### R-0146: [Guardrails](https://docs.langflow.org/concepts-components)
- Original description: فحص ضوابط المدخلات/المخرجات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 07: Security, prompt injection and risk boundaries
- Why it may matter: Compose this node with other visual nodes for Security, prompt injection and risk boundaries; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-086, U-087, U-088, U-089, U-090, U-091, U-092, U-093.

### R-0147: [Policies (Beta)](https://docs.langflow.org/concepts-components)
- Original description: سياسات تحكم؛ ميزة تجريبية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 07: Security, prompt injection and risk boundaries
- Why it may matter: Compose this node with other visual nodes for Security, prompt injection and risk boundaries; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-086, U-087, U-088, U-089, U-090, U-091, U-092, U-093.

### R-0148: [LLM Selector](https://docs.langflow.org/concepts-components)
- Original description: اختيار النموذج
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 12: Model selection and multi-provider comparison
- Why it may matter: Compose this node with other visual nodes for Model selection and multi-provider comparison; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-068, U-069, U-070, U-071, U-072, U-073, U-074, U-075.

### R-0149: [Smart Router](https://docs.langflow.org/concepts-components)
- Original description: توجيه ذكي
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 06: Orchestration, routing and multiple agents, 12: Model selection and multi-provider comparison
- Why it may matter: Compose this node with other visual nodes for Orchestration, routing and multiple agents, Model selection and multi-provider comparison; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-068, U-069, U-070, U-071, U-072, U-073, U-074, U-075.

### R-0150: [Smart Transform](https://docs.langflow.org/concepts-components)
- Original description: تحويل البيانات بالنموذج
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0151: [Structured Output](https://docs.langflow.org/concepts-components)
- Original description: إخراج منظّم
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

## المكونات الأساسية / النماذج والوكلاء (7)  [7]
### R-0152: [Language Model](https://docs.langflow.org/concepts-components)
- Original description: تشغيل نموذج لغوي
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0153: [Prompt Template](https://docs.langflow.org/concepts-components)
- Original description: قالب التعليمات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0154: [Agents](https://docs.langflow.org/concepts-components)
- Original description: إنشاء وكيل بأدوات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 01: General-purpose personal assistant and agents
- Why it may matter: Compose this node with other visual nodes for General-purpose personal assistant and agents; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0155: [A2A Agent](https://docs.langflow.org/concepts-components)
- Original description: التواصل بين الوكلاء
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 06: Orchestration, routing and multiple agents
- Why it may matter: Compose this node with other visual nodes for Orchestration, routing and multiple agents; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-108, U-109, U-110, U-111, U-112, U-113, U-114, U-115.

### R-0156: [MCP Tools](https://docs.langflow.org/concepts-components)
- Original description: أدوات MCP
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 09: Tools, skills and MCP connections
- Why it may matter: Compose this node with other visual nodes for Tools, skills and MCP connections; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-076, U-077, U-078, U-079, U-080, U-081, U-082, U-083.

### R-0157: [Embedding Model](https://docs.langflow.org/concepts-components)
- Original description: تمثيلات متجهية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 03: RAG, document retrieval and hybrid search
- Why it may matter: Compose this node with other visual nodes for RAG, document retrieval and hybrid search; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0158: [Message History](https://docs.langflow.org/concepts-components)
- Original description: سجل الرسائل
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 04: Memory, knowledge history and conflicts, 19: Tracing, lineage and trustworthy run records
- Why it may matter: Compose this node with other visual nodes for Memory, knowledge history and conflicts, Tracing, lineage and trustworthy run records; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-086, U-087.

## المكونات الأساسية / الأدوات العامة (4)  [4]
### R-0159: [Calculator](https://docs.langflow.org/concepts-components)
- Original description: الحسابات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0160: [Current Date](https://docs.langflow.org/concepts-components)
- Original description: قراءة التاريخ
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0161: [Python Interpreter](https://docs.langflow.org/concepts-components)
- Original description: تشغيل Python وفق إعدادات النظام
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0162: [SQL Database](https://docs.langflow.org/concepts-components)
- Original description: العمل مع قواعد SQL
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 21: Storage, export, backup and migration
- Why it may matter: Compose this node with other visual nodes for Storage, export, backup and migration; any safety or authority beyond the flow needs separate controls.
- Recorded status: `direct_candidate`. Relevant directly to one or more historical requirements; assess adoption as a separate decision.
- Example associated requirement IDs: U-144, U-145, U-146, U-147, U-148, U-149, U-150, U-151.

## حزم التكاملات Bundles (80)  [80]
### R-0163: [Agentics](https://docs.langflow.org/bundles-agentics)
- Original description: مكوّنات Agentics قديمة وغير متوافقة مع Langflow الحديث؛ لا تعمل في الإصدار 1.13 **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0164: [AI/ML API](https://docs.langflow.org/bundles-aiml)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to AI/ML API; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0165: [Amazon](https://docs.langflow.org/bundles-amazon)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Amazon; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0166: [Anthropic](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Anthropic; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0167: [Apify](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Apify; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0168: [arXiv](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Potential connection to arXiv; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0169: [AssemblyAI](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 13: Voice, transcription, audio and spoken assistants
- Why it may matter: Potential connection to AssemblyAI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-040, U-041, U-042, U-043, U-044, U-045, U-046, U-047.

### R-0170: [Azure](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 22: Private server, cloud, API and deployment
- Why it may matter: Potential connection to Azure; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0171: [Baidu](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Baidu; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0172: [Bing](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Bing; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0173: [Cassandra](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Cassandra; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0174: [Cleanlab](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Cleanlab; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0175: [Code Agents](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 01: General-purpose personal assistant and agents, 16: Autonomous coding and software engineering
- Why it may matter: Potential connection to Code Agents; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0176: [ClickHouse](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to ClickHouse; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0177: [Cloudflare](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Cloudflare; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0178: [Cohere](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Cohere; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0179: [CometAPI](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to CometAPI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0180: [Composio](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Composio; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0181: [IBM Confluent](https://docs.langflow.org/bundles-confluent)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to IBM Confluent; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0182: [Couchbase](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Couchbase; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0183: [CUGA](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to CUGA; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0184: [DataStax](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to DataStax; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0185: [DeepSeek](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to DeepSeek; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0186: [Docling](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Docling; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0187: [DuckDuckGo](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to DuckDuckGo; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0188: [Elastic](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Elastic; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0189: [EmpirioLabs AI](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to EmpirioLabs AI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0190: [Exa](https://docs.langflow.org/bundles-exa)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Exa; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0191: [FAISS](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to FAISS; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0192: [Figranium](https://docs.langflow.org/bundles-figranium)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Figranium; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0193: [File Processing](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Potential connection to File Processing; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0194: [Firecrawl](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Firecrawl; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0195: [Glean](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Glean; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0196: [Google components](https://docs.langflow.org/bundles-google)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Google components; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0197: [Groq](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Groq; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0198: [Hugging Face](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Hugging Face; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0199: [IBM](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to IBM; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0200: [Icosa Computing](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Icosa Computing; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0201: [LangChain](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to LangChain; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0202: [LiteLLM](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 12: Model selection and multi-provider comparison, 20: Performance, token cost and context optimization
- Why it may matter: Potential connection to LiteLLM; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-068, U-069, U-070, U-071, U-072, U-073, U-074, U-075.

### R-0203: [LM Studio](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to LM Studio; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0204: [MariTalk](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to MariTalk; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0205: [Mem0](https://docs.langflow.org/bundles-mem0)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Mem0; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0206: [Microsoft 365 components](https://docs.langflow.org/bundles-microsoft)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Microsoft 365 components; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0207: [Milvus](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Milvus; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0208: [MistralAI](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to MistralAI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0209: [MongoDB](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to MongoDB; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0210: [MrScraper](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 02: Deep research, source checks and evidence, 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Potential connection to MrScraper; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0211: [NextPlaid](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to NextPlaid; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0212: [Notion](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Potential connection to Notion; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0213: [Novita](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Novita; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0214: [NVIDIA](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to NVIDIA; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0215: [Ollama](https://docs.langflow.org/bundles-ollama)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 11: Local models and independence
- Why it may matter: Potential connection to Ollama; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0216: [OpenAI](https://docs.langflow.org/bundles-openai)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to OpenAI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0217: [OpenAI Compatible](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to OpenAI Compatible; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0218: [OpenRouter](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 06: Orchestration, routing and multiple agents, 12: Model selection and multi-provider comparison
- Why it may matter: Potential connection to OpenRouter; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-068, U-069, U-070, U-071, U-072, U-073, U-074, U-075.

### R-0219: [Oracle](https://docs.langflow.org/bundles-oracle)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Oracle; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0220: [OrcaRouter](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 06: Orchestration, routing and multiple agents, 12: Model selection and multi-provider comparison
- Why it may matter: Potential connection to OrcaRouter; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-068, U-069, U-070, U-071, U-072, U-073, U-074, U-075.

### R-0221: [Paddle](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Paddle; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0222: [Perplexity](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Perplexity; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0223: [pgvector](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 03: RAG, document retrieval and hybrid search
- Why it may matter: Potential connection to pgvector; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0224: [Pinecone](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Pinecone; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0225: [Plivo](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Plivo; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0226: [Qdrant](https://docs.langflow.org/bundles-qdrant)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 03: RAG, document retrieval and hybrid search
- Why it may matter: Potential connection to Qdrant; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0227: [Redis](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Redis; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0228: [SambaNova](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to SambaNova; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0229: [SearchApi](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Potential connection to SearchApi; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0230: [Serper](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Serper; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0231: [Serping API](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Serping API; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0232: [Serply](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Serply; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0233: [Slack](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: 23: Messaging, email and personal productivity
- Why it may matter: Potential connection to Slack; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: U-040, U-041, U-042, U-043, U-044, U-045, U-046, U-047.

### R-0234: [Supabase](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Supabase; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0235: [Upstash](https://docs.langflow.org/bundles-upstash)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Upstash; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0236: [Valkey](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Valkey; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0237: [Vectara](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Vectara; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0238: [Vertex AI](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Vertex AI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0239: [vLLM](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to vLLM; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0240: [Weaviate](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Weaviate; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0241: [Wikipedia](https://docs.langflow.org/components-bundle-components)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to Wikipedia; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0242: [xAI](https://docs.langflow.org/bundles-xai)
- Original description: حزمة تكامل؛ تختلف المكوّنات الداخلية حسب النسخة والتثبيت
- Usage type: Optional provider package with separate connectors or nodes
- Historical requirements connection: Unclassified reference
- Why it may matter: Potential connection to xAI; opening the bundle lists individual supported nodes and credentials.
- Recorded status: `bundle_provider_not_single_component`. Provider bundle; internal nodes, supported versions and required keys vary.
- Example associated requirement IDs: No direct U-ID assigned.

## المنصة والنشر والتطوير (10)  [10]
### R-0243: [Langflow editor](https://docs.langflow.org/)
- Original description: محرّر مرئي لبناء المسارات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067.

### R-0244: [Playground](https://docs.langflow.org/concepts-playground)
- Original description: تجربة المسارات والرسائل
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0245: [Langflow API](https://docs.langflow.org/api-reference-api-examples)
- Original description: تشغيل التدفقات عبر API
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 10: Workflow visual builder and controllable flows
- Why it may matter: Compose this node with other visual nodes for Workflow visual builder and controllable flows; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067.

### R-0246: [MCP server support](https://docs.langflow.org/mcp-server)
- Original description: إتاحة مسارات أو أدوات عبر MCP
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 09: Tools, skills and MCP connections, 22: Private server, cloud, API and deployment
- Why it may matter: Compose this node with other visual nodes for Tools, skills and MCP connections, Private server, cloud, API and deployment; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0247: [LFX runtime](https://docs.langflow.org/lfx)
- Original description: حزمة تشغيل وتطوير مكوّنات Langflow
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 11: Local models and independence
- Why it may matter: Compose this node with other visual nodes for Local models and independence; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

### R-0248: [Custom Python components](https://docs.langflow.org/components-custom-components)
- Original description: تطوير مكوّنات مخصّصة
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0249: [Extensions](https://docs.langflow.org/components-extensions)
- Original description: امتدادات لواجهة/تشغيل Langflow
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0250: [Legacy components](https://docs.langflow.org/legacy-core-components)
- Original description: أدوات قديمة قد تُزال أو تُستبدل
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 32: History of deferred, changed and withdrawn alternatives
- Why it may matter: Compose this node with other visual nodes for History of deferred, changed and withdrawn alternatives; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0251: [Templates](https://docs.langflow.org/templates)
- Original description: قوالب وتدفقات البداية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0252: [Docker deployment](https://docs.langflow.org/deployment-docker)
- Original description: تشغيل في حاوية
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 22: Private server, cloud, API and deployment
- Why it may matter: Compose this node with other visual nodes for Private server, cloud, API and deployment; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-001, U-002, U-003, U-004, U-005, U-006, U-007, U-008.

## مكوّنات قديمة (Legacy) / مدخلات ومخرجات قديمة (2)  [2]
### R-0253: [Text Input](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0254: [Text Output](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

## مكوّنات قديمة (Legacy) / تحميل بيانات قديم (3)  [3]
### R-0255: [Directory](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0256: [Load CSV](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0257: [Load JSON](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

## مكوّنات قديمة (Legacy) / معرفة قديمة (2)  [2]
### R-0258: [Knowledge Base (legacy)](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 03: RAG, document retrieval and hybrid search, 04: Memory, knowledge history and conflicts, 32: History of deferred, changed and withdrawn alternatives
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0259: [Knowledge Ingestion](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 03: RAG, document retrieval and hybrid search, 04: Memory, knowledge history and conflicts
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

## مكوّنات قديمة (Legacy) / مساعدات قديمة (4)  [4]
### R-0260: [Message Store](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0261: [Create List](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0262: [ID Generator](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0263: [Output Parser](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 15: Files, PDF, websites, repositories and structured data
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

## مكوّنات قديمة (Legacy) / منطق قديم (4)  [4]
### R-0264: [Condition](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0265: [Pass](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0266: [Flow As Tool](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 09: Tools, skills and MCP connections, 10: Workflow visual builder and controllable flows
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-076, U-077.

### R-0267: [Sub Flow](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 10: Workflow visual builder and controllable flows
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067.

## مكوّنات قديمة (Legacy) / معالجة قديمة (19)  [19]
### R-0268: [Alter Metadata](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0269: [Combine Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0270: [Combine Text](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0271: [Create Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0272: [JSON Operations](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0273: [Table Operations](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0274: [Text Operations](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0275: [Data to DataFrame](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0276: [Data to Message](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0277: [Extract Key](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0278: [Filter Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0279: [Filter Values](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0280: [JSON Cleaner](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0281: [Message to Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0282: [Parse DataFrame](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0283: [Parse JSON](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0284: [Regex Extractor](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0285: [Select Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0286: [Update Data](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

## مكوّنات قديمة (Legacy) / أدوات قديمة (10)  [10]
### R-0287: [Calculator Tool](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 09: Tools, skills and MCP connections
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-076, U-077, U-078, U-079, U-080, U-081, U-082, U-083.

### R-0288: [Python Code Structured](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 16: Autonomous coding and software engineering
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-013, U-014, U-015, U-016, U-017, U-018, U-019, U-020.

### R-0289: [Python REPL](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0290: [Search API](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0291: [SearXNG Search](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0292: [Serp Search API](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0293: [Tavily Search API](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 02: Deep research, source checks and evidence
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: U-119, U-120, U-121, U-122, U-123, U-124, U-125, U-126.

### R-0294: [Wikidata API](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0295: [Wikipedia API](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: Unclassified reference
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0296: [Yahoo! Finance](https://docs.langflow.org/legacy-core-components)
- Original description: قد يكون مخفيًا أو مُزالًا؛ لا يُنصح به في مسار جديد **[قديم / غير مدعوم]**
- Usage type: Historical reference only
- Historical requirements connection: 24: Finance, investing, markets and trading explorations
- Why it may matter: Retain only for ideas and migration/historical comparison; do not use as the current default.
- Recorded status: `legacy_or_deprecated`. Older, legacy, retired or incompatibility-marked item: retain in history and do not default to deploying.
- Example associated requirement IDs: No direct U-ID assigned.

## أوامر LFX التطويرية (12)  [12]
### R-0297: [lfx serve](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0298: [lfx run](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0299: [lfx-mcp](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 09: Tools, skills and MCP connections
- Why it may matter: Compose this node with other visual nodes for Tools, skills and MCP connections; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-076, U-077, U-078, U-079, U-080, U-081, U-082, U-083.

### R-0300: [lfx init](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0301: [lfx login](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 19: Tracing, lineage and trustworthy run records
- Why it may matter: Compose this node with other visual nodes for Tracing, lineage and trustworthy run records; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-062, U-063, U-064, U-065, U-066, U-067, U-086, U-087.

### R-0302: [lfx create](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0303: [lfx validate](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0304: [lfx requirements](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 17: UI, dynamic pages and interaction
- Why it may matter: Compose this node with other visual nodes for UI, dynamic pages and interaction; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-013, U-014, U-015, U-016, U-017, U-018, U-019, U-020.

### R-0305: [lfx status](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0306: [lfx push](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0307: [lfx pull](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: Unclassified reference
- Why it may matter: Compose this node with other visual nodes for General reference; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: No direct U-ID assigned.

### R-0308: [lfx export](https://docs.langflow.org/lfx)
- Original description: من أوامر أدوات Langflow/LFX؛ راجع التوثيق الحالي للصيغة والمتطلبات
- Usage type: Visual node / platform feature / integration documentation
- Historical requirements connection: 21: Storage, export, backup and migration
- Why it may matter: Compose this node with other visual nodes for Storage, export, backup and migration; any safety or authority beyond the flow needs separate controls.
- Recorded status: `reference_candidate`. Useful reference or possible supporting component; no automatic commitment to install.
- Example associated requirement IDs: U-144, U-145, U-146, U-147, U-148, U-149, U-150, U-151.
