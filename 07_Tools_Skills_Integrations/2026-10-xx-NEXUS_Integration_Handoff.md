# NEXUS ONE — حزمة التكاملات التنفيذية
إعداد المنسق لأحمد وCodex — 21 أكتوبر 2026 (الإمارات).
هذه حزمة ربط معدّة، وليست شهادة تشغيل للخدمات. تصحح توجيهات البناء المكرر السابقة. لا تستبدل عمل الفرع المحلي الأحدث.

## 1. القرار التنفيذي
المسار: العالم الجاهز + Architect الحالي → NEXUS Gateway الحالي → محوّل Hermes الحالي → Hermes → أدواته الأصلية وMCP.
نحتفظ بـHTTP Runs الذي بُني فعلاً؛ لا نغيّر إلى ACP/TUI لمجرد أن الوثائق تعرضهما. نستخدم client MCP داخل Hermes بدل توسيع client موازٍ في Gateway. وظيفة Gateway الهوية والسياسات والميزانية وربط الأحداث والموافقات بالعالم.
لا يُنقل التنفيذ إلى Hermes قبل إثبات أن الأدوات الفعلية والموديل يمران بحدود السياسة المطلوبة؛ observer أو prompt ليس إنفاذًا.

## 2. المكونات المحددة وقرار الاستخدام
| المكوّن | القرار | موضع الربط | المتطلب المتبقي |
|---|---|---|---|
| المحرك | NousResearch/hermes-agent v0.22.2 حسب pin المستودع | محوّل nexus/hermes.ts القائم | تحقق النسخة المحلية وتشغيل معزول |
| مزود النموذج | مزود واحد مهيأ في Hermes؛ لا نفرض اشتراكًا جديدًا | إعداد Hermes الأصلي | اعتماد مزود فعلي واختيار موديل متاح؛ الاشتراك في تطبيق ليس دليل API |
| البحث | الاحتفاظ باستدعاء Tavily الموجود | nexus/integrations.ts | مفتاح وتسعير واختبار من مهمة كاملة؛ لا استدعاءين متنافسين لنفس البحث |
| MCP | عميل Hermes الأصلي | إعداد Hermes | tools allowlist + مصادقة + موافقة قبل الأثر + اختبار النقل |
| خدمات الحسابات | Composio Sessions عبر MCP عند الحاجة | حساب مستخدم ثابت وجلسة محفوظة | حساب Composio وربط الحساب المختار؛ ليس شرط أول مهمة |
| الأتمتة | n8n الرسمي عبر MCP، اختياري | URL من instance ينتهي /mcp-server/http | إصدار n8n متوافق، OAuth، اختيار workflows |
| البريد | read-only عبر موصل واحد مختار | MCP/Composio بعد ربط الحساب | OAuth بأقل صلاحية قراءة وقائمة أدوات موجبة؛ لا send/modify/delete |
| النموذج المحلي | Ollama اختياري | مزود Hermes القائم | خدمة وموديل على نفس الجهاز/وجهة معتمدة؛ inventory ليس inference |
| الذاكرة | Hermes لذاكرة المحرك؛ الاحتفاظ بذاكرة التطبيق الحالية لنطاقها | IDs/session mapping | لا إنشاء مخزن ذاكرة ثالث أو مزامنة ثنائية غير لازمة |
| المعرفة | فهرس المعرفة الحالي والاستشهادات | nexus/knowledge.ts | lexical معلن؛ embeddings فقط لحاجة مثبتة |
| الملفات | validator/readFile الحاليان | workspace محدد | لا خادم filesystem إضافي واسع دون حاجة |
| الوكلاء | تفويض Hermes الأصلي | المحوّل والأحداث | إثبات تكليف ونتيجة ورفض وتوقف؛ لا orchestrator آخر |
| التحكم | Architect/React Flow الحالي | Gateway | الواجهة تعكس القدرات المؤكدة؛ لا إعادة shell |
| العالم | أصل UE جاهز قابل للتحرير | worldBridge/director الموجودان | أصل معتمد وجهاز UE/GPU؛ لم يُشتر أو يُشغّل |
| البث | Pixel Streaming الخاص بـUnreal عند تشغيل الأصل | جلسة عرض مصادقة | GPU/build وشبكة؛ لا بنية بث جديدة الآن |
| الصوت | غير مفعل حاليًا | يحدد بعد تشغيل مسار المهمة | اختيار خدمة مباشر وفق الحاجة؛ TTS وحده ليس محادثة صوتية ثنائية |

## 3. pin وحدود التوافق
تقرير المستودع HERMES_COMPATIBILITY.md يثبت المصدر المستهدف:
commit d923a5eb487a17c0a68801bba9ef0f56c81040a8
tag v0.22.2
هذا دليل فحص مصدر من تقرير المشروع؛ ليس تحققًا مني أن runtime يعمل.
GET /v1/capabilities وPOST /v1/runs مستخدمان في المحوّل القائم.
المتطلبات: run_submission, run_status, run_events_sse, run_stop, run_steer, run_approval_response.
تحقق الحقول المطلوبة كـboolean true مع السماح ببيانات وصفية أخرى؛ لا ترفض الرد كله لأن حقلاً إضافيًا مركب.
اربط missionId بـrun_id، واحفظ cursor/dedup. Stop acknowledgement لا يعني terminal cancelled.
لا تبنِ بروتوكولًا موازيًا أو تعتمد API متخيلة؛ استعمل المصدر المثبت للمسارات الفرعية.

## 4. إعداد البيئة المطابق للكود المرفوع
القالب التالي لـGateway، وليس ملف إعداد Hermes. القيم الفارغة تعني غير مهيأ.
يقرأ main.ts ملف .env من cwd؛ تُحسب المسارات النسبية منه. استخدم مسارات مطلقة عند التشغيل الفعلي.
لا ينسخ القالب فوق .env موجود، ولا يوضع مفتاح في Git.

```dotenv
APP_TOKEN=
HERMES_URL=
HERMES_API_KEY=
NEXUS_PORT=8788
NEXUS_DB_FILE=
WORKSPACE_ROOT=
NEXUS_CONFIG_FILE=
TAVILY_API_KEY=
TAVILY_SEARCH_QUOTE_MICRO_USD=
# قديم: discovery فقط؛ ليس مسار MCP الإنتاجي المقترح
NEXUS_MCP_URL=
NEXUS_MCP_TOKEN=
# اختياريان؛ اختبار اتصال لا يثبت تنفيذًا
OLLAMA_URL=
N8N_URL=
```

لا تُصدّر NEXUS_DB_FILE/WORKSPACE_ROOT/NEXUS_CONFIG_FILE بقيم فارغة عند التشغيل: احذف السطر أو املأه بمسار فعلي. HERMES_URL من listener الفعلي؛ لا نفترض port. HERMES_API_KEY اعتماد اتصال Gateway بالمحرك وليس مفتاح مزود LLM.
TAVILY_SEARCH_QUOTE_MICRO_USD قيمة محاسبية من تسعير الحساب، لا تختلق صفرًا لفتح المسار.
COMPOSIO_API_KEY ليس مدعومًا في main.ts الحالي؛ إضافة الاسم إلى env وحدها لا تربط الخدمة.

## 5. تجهيز MCP وn8n دون بناء جديد
1. افحص catalog/help في نسخة Hermes المثبتة؛ وثائق اليوم قد تتقدم على pin.
2. n8n: فعّل Instance-level MCP في الحساب المخول، انسخ Server URL، واختر workflow اختبار معزول بلا أثر خارجي.
3. إذا كان n8n-official موجودًا في catalog المثبت، أوامر الربط الرسمية:
```sh
hermes mcp catalog
hermes mcp install n8n-official
hermes mcp login n8n-official
hermes mcp configure n8n-official
```
هذه أوامر لاحقة للمشغّل المخول، لم تُنفذ هنا. أدخل URL الحقيقي في معالج الإعداد؛ لا تستخدم editor URL.
إن غاب entry من pin لا تُجرِ upgrade صامتًا: استخدم دعم HTTP MCP الأصلي الموثق في نفس النسخة بعد تحقق التوافق، أو اعرض فرق إصدار محدد.
احصر الأدوات بأسمائها المكتشفة؛ لا تخترع أسماء أو تسمح بكل الأدوات لأن discovery نجح. MCP الرسمي يتيح إنشاء/تعديل أيضًا؛ هذا لا يعني الإذن بها. لا تعِد تشغيل cron القديم.

## 6. تجهيز Composio
استخدم Sessions الحالية؛ جلسة واحدة محفوظة للمستخدم/السياق، لا جلسة لكل رسالة.
- user ID ثابت من التطبيق.
- allowed toolkit ضيق.
- connected account محدد/مثبت إن تعددت الحسابات.
- authorization بواسطة Connect Link؛ لا مفاتيح داخل الواجهة.
- MCP endpoint يؤخذ من نتيجة إنشاء الجلسة الفعلية، لا رابط ثابت متخيل.
- الربط إلى Hermes MCP بعد تحقق دعم المصادقة والنقل في pin.
- أدوات البريد القراءة فقط ضمن allowlist موجبة وصلاحيات الحساب؛ لا تعتمد description وحده.
اختيار Composio لا يثبت تفعيله. لا ننشئ OAuth manager أو SDK لكل خدمة بالتوازي معه.
البديل المباشر MCP للخدمة يستخدم فقط إذا كان أبسط وأكمل للصلاحيات المطلوبة؛ لا مسارين لنفس الحساب.

## 7. توزيع ملكية التنفيذ
| الوظيفة | المالك | ما لا يعاد بناؤه |
|---|---|---|
| model loop/retries/tool dispatch/native delegation | Hermes | agent loop جديد |
| MCP transport/discovery/auth supported by pinned engine | Hermes | MCP client ثانٍ |
| service-account connections | موصل الخدمة أو Composio المختار | OAuth manager لكل خدمة |
| workflow execution | n8n إن استُخدم | workflow engine جديد |
| صلاحيات NEXUS/الميزانية/الهوية/سجل العرض | Gateway الحالي | لوحة حوكمة جديدة موازية |
| العرض والإعدادات | Architect وUnreal | Dashboard بديل للعالم |
الموافقات لا تُلغى لتمكين مسار جاهز. إن كان hook الجاهز لا يمنع الأثر، المكوّن المخصص الأدنى لتلك الفجوة مبرر.

## 8. حزمة القبول المحددة
C01: capabilities الرسمي بmetadata إضافية يقبل مع تحقق flags المطلوبة.
C02: مهمة واحدة محفوظة request→run→tool result→source→terminal؛ التكرار بنفس المفتاح لا يكرر الأثر.
C03: tool غير مسموحة وموافقة مرفوضة/منتهية تنتج صفر آثار.
C04: موافقتان متزامنتان تحلان بالمعرف الصحيح؛ لا موافقة عامة.
C05: stop لrun مختلف يرفض؛ stopping لا يتحول canceled إلا بإقرار نهائي.
C06: انقطاع SSE ثم reconnect/restart يعيدان العرض دون إرسال أداة من جديد؛ فجوة replay معلنة.
C07: بحث Tavily بمصادر وميزانية معلومة؛ fixture يثبت العقد فقط، والاختبار الحي منفصل.
C08: MCP اختبار اكتشاف ثم call مسموح داخل sandbox؛ اختبار read-only/deny.
C09: n8n workflow خامل يعيد run/result فعلية؛ health وحده ليس نجاحًا. لا retry تلقائي لنتيجة أثر مجهولة.
C10: فشل OAuth/انتهاءه/حساب خاطئ لا يتحول إلى حساب افتراضي آخر.
C11: الاستشهاد يربط document/version/chunk؛ مستخدم آخر لا يصل إليه.
C12: Unreal snapshot+events بنفس missionId؛ نجاح الأثر يسبق مؤثر النجاح؛ لا دليل عالم دون build على GPU.

كل نتيجة تسجل: component/version/commit/test/environment/status/evidence.
الحالات المستقلة: configured, reachable, authenticated, discovered, executable, verified.
المفتاح متاح ≠ موصول؛ موصول ≠ منفذ؛ اختبار محلي ≠ اعتماد حي.

## 9. ترتيب التنفيذ الذي لا يكرر البناء
أ. دمج الحزمة معرفيًا مع التغييرات المحلية؛ حفظ الإصلاحات الحالية.
ب. إنهاء محوّل Hermes وC01/C03/C05/C06 بالاختبارات المحلية.
ج. إعداد native MCP ونموذج واحد والبحث الموجود، ثم أول مهمة حية عند توفر الاعتماد.
د. إعادة استخدام التفويض الأصلي ثم موصلات الحسابات المطلوبة فقط.
هـ. n8n/Ollama عند استعمال فعلي؛ العالم الجاهز مسار متوازٍ مستقل.
لا إعادة تقسيم المشروع إلى خدمات جديدة. لا ترحيل قاعدة سليمة أو إضافة vector DB لمجرد القائمة.

## 10. العوائق الحقيقية، دون إيقاف الأعمال المستقلة
- اعتماد النموذج وموديل صالح في Hermes.
- اعتماد البحث وتسعير حسابه.
- حسابات الخدمات وOAuth فقط للتكاملات المختارة.
- أصل سينمائي محدد مع رخصة/سعر واعتماد شراء، وجهاز Unreal.
لم أثبت وجود أي من هذه الاعتمادات أو تشغيلها. لا ينبغي طلب أسرار في المحادثة.
تصحيح ادعائي السابق: عبارة «المشهد جاهز والمحرك جاهز» تعني اختيار حلول جاهزة للتبني، لا أنهما مثبتان ومربوطان بالفعل.

## 11. المراجع
مصادر المشروع المفحوصة، فرع nexus/parallel-foundation:
- https://github.com/as1411307-collab/ahemed--agent-v01/blob/nexus/parallel-foundation/docs/HERMES_COMPATIBILITY.md
- https://github.com/as1411307-collab/ahemed--agent-v01/blob/nexus/parallel-foundation/apps/core/src/nexus/main.ts
- https://github.com/as1411307-collab/ahemed--agent-v01/blob/nexus/parallel-foundation/apps/core/src/nexus/integrations.ts
وثائق رسمية قُرئت بتاريخ الإعداد:
- https://hermes-agent.nousresearch.com/docs/developer-guide/programmatic-integration
- https://hermes-agent.nousresearch.com/docs/user-guide/features/mcp
- https://docs.n8n.io/connect/connect-to-n8n-mcp-server
- https://docs.composio.dev/docs/quickstart
- https://docs.composio.dev/docs/sessions-via-mcp
- https://docs.composio.dev/kb/guide/mcp-tool-router-sessions
