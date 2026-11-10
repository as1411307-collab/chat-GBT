# تدقيق KANON iOS MASTER v1 لصالح تطبيق «ايجنت»
**التاريخ:** 8 نوفمبر 2026  
**النطاق:** مراجعة الأقسام 0–12 في ملف PDF ذي 14 صفحة، مع النص العربي الأصلي الذي أعاد المستخدم إرساله.  
**القرار:** **استخراج وانتقاء، وليس اعتمادًا كاملاً أو استبدالاً لمواصفات ايجنت أو عقد Core**.

## حدود التحقيق والمرجع
1. تمت مراجعة البنية والكود والجداول في 14 صفحة، ومقارنتها بنص المستخدم المقروء. الطبعة المصورة للـPDF تحتوي حروفًا عربية معطوبة؛ النص المعاد لصقه يُعتبر المرجع اللغوي الأوضح.
2. راجعت الملفات الفعلية لمستودع `as1411307-collab/ahemed--agent-v01` على GitHub: `packages/contract/src/index.ts`، `apps/core/src/server.ts`، `apps/core/src/security/device-session.ts`، `apps/core/src/main.ts`.
3. تم تحقق تقاطعي من وثائق Apple الرسمية لـAVPlayerLooper وSwiftUI shader وTabView/Liquid Glass وKeychain والخصوصية والنشر، ومن تحديثات Rive. **لم يُنفذ Xcode Build أو تشغيل على iPhone لهذا الكود**. لذلك نتائج التدقيق الساكنة لا تعني ضمانًا للتجميع.
4. تحليلي يراعي مواصفات «ايجنت» المعتمدة مسبقًا في `rork-github-export/AGENT_APP_SPEC.md`، ولا يفترض أننا قررنا إعادة تسميته «كانون».

## أهم الأخطاء القاطعة التي تمنع الدمج كما هو

### 1) تعارض حالات المهام — §5.3، صفحة 9
التقرير يقترح `RUNNING` و`UNKNOWN_HALTED` وكأنهما قادمان من عقد Core. لكن العقد الحقيقي v0.1 يعرّف بالضبط:
`RECEIVED, PROCESSING, WAITING_FOR_APPROVAL, APPROVED, REJECTED, EXECUTING, VERIFYING, COMPLETED, FAILED`.
الحالات النهائية `COMPLETED, FAILED, REJECTED`. لا تعدّل العقد ليتناسب مع شكل UI؛ عدّل Swift enum ليطابقه حرفيًا، وضع `UNKNOWN` في حالة **نتيجة فعل غير محسوم** وليس حالة `TaskStatus` جديدة.

### 2) SSE endpoint مخترع — §0، §8.2 وصفحة 12
`GET /v1/messages/stream` غير موجود في `apps/core/src/server.ts`؛ الموجود `POST /v1/messages` بـmultipart و`GET /v1/tasks/:taskId`. لذلك مثال SSE **غير قابل للتشغيل مع Core الحالي**. المسار الصحيح الآن: طلب رسالة بـ`request_id` ثابت، ثم polling محدود لحالة المهمة. إذا أُضيف SSE مستقبلًا يجب توثيق `/events` أو مسار حقيقي، مع المصادقة و`event/id/data` متعدد الأسطر وreconnect وbackpressure. تجنب استهلاك `Accept: text/event-stream` وحده كإثبات دعم.

### 3) Idempotency غير متوافق — §8.1، §8.4 وصفحات 11–12
النواة تثبت منع التكرار بمفتاح `request_id` **داخل payload** الخاص بالمحادثة، لا تعتمد حاليًا على ترويسة `Idempotency-Key` كبديل. إضافة ترويسة وحدها لا تضمن أي شيء، خصوصًا للعمليات الخارجية. لا تجعل Outbox يعيد تشغيل كتابة خارجية تلقائيًا بعد Timeout، فقد يكون الأثر وقع رغم غياب الاستجابة. يُسمح بإعادة إرسال الطلب النصي بنفس `request_id` بعد فحص حالة المهمة؛ عمليات الكتابة تحتاج Broker وidempotency منفصلين مثبتين وإجراء تسوية للأثر `UNKNOWN`.

### 4) Metal shader: تمرير معامل ناقص — §1.2 وصفحة 2
التوقيع في Metal هو `sceneGradient(position,color,bounds,time,c1,c2,glow)`، لكن SwiftUI يمرر الوقت والألوان فقط؛ **`bounds` مفقود**؛ ترتيب المعاملات لا يطابق الدالة. يلزم تمرير حجم العرض فعليًا، مثل GeometryReader ثم `.float4(0,0,Float(size.width),Float(size.height))` قبل `.float(time)`. تأكد من التعامل مع أبعاد صفرية وإيقاف Timeline في Reduce Motion. والأهم: هذا Shader **تدرج ثنائي الأبعاد**، ليس مشهد 3D احترافيًا، فلا يُقبل بديلًا عن أصل المشهد المستورد.

### 5) AVPlayerLooper: اسم وسيط خاطئ + تغيير المشهد لا يطبق — §1.3 وصفحة 3
المثال يكتب `AVPlayerLooper(player: q, loopItem: item)`، بينما توقيع Apple الرسمي هو `AVPlayerLooper(player: q, templateItem: item)`؛ الخطأ يمنع التجميع. يُفضّل `AVQueuePlayer()` فارغًا كي يدير Looper الطابور. كما أن `updateUIView` يوقف/يشغّل فقط، ولا يعيد تهيئة الفيديو إذا تغيّر `scene.videoName`. يتطلب كشف تغيّر الأصل وتنظيف طبقة الفيديو القديمة والتعامل مع حدث الخلفية/المشهد. الفيديو المتكرر قد يكون خلفية اختيارية **لكنه ليس جسم الوكيل ثلاثي الأبعاد المتفاعل** المطلوب.

### 6) Rive example قديم ويحتاج أصلًا غير موجود — §2.3 وصفحة 5
المثال يعتمد `RiveViewModel` و`setInput` و`triggerInput`. في runtime الحالي v6.29، الواجهات القديمة deprecated ومُرشح الانتقال إلى Swift Concurrency وStateMachine.bindViewModelInstances. الأهم لا يوجد ضمن المستند ملف `kanon_falcon.riv` أو شخصيات جاهزة أو ترخيص؛ التعليمات ترسم API على الورق، **لا تسلّم شخصية قابلة للعرض**. احتفظ بفكرة state-driven animation فقط، وادرس Rive كعنصر مساعد 2D/2.5D صغير لا كبديل لمشهد 3D الرئيسي.

### 7) CoreSignals يخلط المستخدم والنواة — §5.5 وصفحة 9–10
`inputFocused` لا يعني أن الميكروفون يستمع: قد يكون المستخدم يكتب؛ `requestInFlight` لا يعني `PROCESSING` لأن الإرسال قد انتهى بالاستجابة 202 قبل انتهاء المهمة. `connected=true` الافتراضي يجعل واجهة غير موثقة تبدو متصلة. افصل أربع قنوات: `Connection/AuthState` (حقيقة جلسة)، `TaskStatus` (رد Core)، `VoiceState` (ميكروفون/STT/TTS محلي)، و`ProofState` (REAL/DEMO/UNKNOWN). حركة idle زخرفية مسموحة إن لم تدَّعِ وجود معالجة.

### 8) مثال Keychain ليس طريقة استبدال موثقة — §8.3 وصفحة 12
مثال `SecItemDelete(q); SecItemAdd(q)` يخلط query الخاصة بالبحث والخصائص (بما فيها `kSecValueData`)، ولا يفحص أي `OSStatus`. الأفضل `SecItemUpdate` باستعلام class/service/account وكتابة القيمة في attributes منفصلة؛ أضف العناصر إن لم توجد، وتعامل مع حالات الفشل. انتهت صلاحية جلسة Core بعد **5 دقائق** طبقًا لـ`device-session.ts`؛ تحتاج دورة تجديد جلسة بتحدي موقّع، وليس Token دائم. احتفظ بحماية `ThisDeviceOnly` لكن مفتاح P-256 داخل Secure Enclave وJWT/session bearer شيئان مختلفان.

### 9) Retry implementation غير آمن وغير مكتمل — §8.1 وصفحة 11
لا يعالج `Retry-After` على 429؛ لا يحدد بوضوح التعامل مع الأخطاء الشبكية العابرة؛ يحاول 500/429 أربع مرات دون التأكد من أن العملية idempotent؛ يرمي `Authorization: Bearer ` حين لا يوجد token، ولا يربط refresh session بصلاحيتها. يجب تحديد retry policy بحسب نوع الطلب، وطريقة idempotency الحقيقية، وضبط timeouts، وإظهار UNKNOWN بعد write غير محسوم. لا تُطبق هذا actor كنسخ ولصق إنتاجي.

### 10) أوامر GitHub ومواصفات النشر مشروطة — §7، صفحات 10–11
- نعم: منذ **28 أبريل 2026** تستخدم App Store Connect التطبيقات المرفوعة المبنية بـXcode 26 أو أحدث / iOS 26 SDK أو أحدث؛ ويمكن الآن Xcode 27، فلا تعني عبارة «Xcode 26 فقط» قيدًا أعلى.
- `PrivacyInfo.xcprivacy`: يجب إعلان الاستخدام الفعلي لـrequired-reason APIs، والتأكد من manifests المطلوبة لـSDKs؛ ليس تفسيرًا صحيحًا أن كل التطبيقات يجب أن تضع Reason ثابتًا لـUserDefaults دون تدقيق الاستخدام.
- «حذف الحساب داخل التطبيق» إلزامي **لو التطبيق يتيح إنشاء حساب**؛ ليس بالضرورة لو عميل مالك واحد لا يتيح إنشاء حسابات. احتفظ بحذف بيانات/جلسة/جهاز وسجل الخصوصية بحسب المنتج.
- `ITSAppUsesNonExemptEncryption = NO` صحيح فقط إذا لا يوجد تشفير غير معفى، بما في ذلك أي مكتبات؛ افحص استخدام Secure Enclave/HTTPS وكل المكتبات الفعلية، ولا تضع NO كحيلة تتخطى استبيان التشفير.
- الأرقام المذكورة لدقائق TestFlight، زمن Beta Review، تكلفة Xcode Cloud وصور 6.9-inch محددة زمنيًا؛ لا تجعلها شروط تصميم ثابتة دون إعادة تحقق في وقت الرفع.

## تقييم الأقسام بندًا بندًا

| القسم / الصفحة | الحكم | ما نحتفظ به | ما نغيّره أو نزيله |
|---|---|---|---|
| §0 ص1 | انتقاء | SwiftUI/Swift 6، SF Symbols، Keychain، Liquid Glass مشروط، Native TabView | لا تقرر Metal shader أو looping video كبديل لمشهد 3D؛ SSE غير موجود |
| §1.1 ص1–2 | جزئي | `Scene` كاختيار محدود وتسمية عربية/ألوان | أربع بيئات متحركة ليست أصولًا حقيقية؛ استخدم أصلًا بصريًا واحدًا مرخصًا أولًا، دون ربط غير موجود |
| §1.2 ص2 | يحتاج إصلاح | Shader خفيف لهالة خلفية أو fallback | أصلح bounds والـsize، ولا تستخدم gradient كـhero 3D |
| §1.3 ص3 | ليس للمشهد الرئيسي | AVQueuePlayer/Looper صحيح بعد الإصلاح في الخلفيات الاختيارية | لا تجعل الفيديو حيلة توهم بتفاعل مجسم 3D؛ أصلح `templateItem`, scene update والموارد |
| §1.4 ص4 | مشروط | Overlay scrim والوضوح وReduce Motion | `missionActive` لا يستخدم في الكود؛ `isActive: true` يتجاهل pause؛ ربط فعلي بـscenePhase |
| §2.1 ص4 | لا نعتمد الشخصيات الآن | فكرة اختيار هوية أصلية قصيرة البصمة | «الصقر/قلم/عثة» توسّع زائد واسم «كانون» ليس اسم المنتج، ولا توجد ملفات Rive أصلًا |
| §2.2 ص4–5 | يحتفظ بالمنطق المصحح | حركة مرتبطة بأحداث موثقة، وهدوء وقت التركيز | `on_input_focus` ليس ميكروفون؛ `on_request_start` ليس processing server؛ Idle Fidget حركة زخرفية لا حدث Core |
| §2.3 ص5 | يحتاج تحديث | Rive state machine لو اخترنا أصل 2D فعليًا | Runtime API قديم؛ مسار 6.29 Swift concurrency؛ لا تنشئ أسهم وأزرار بلا asset |
| §2.4 ص5 | مفيد | عدم مقاطعة المستخدم، احترام التركيز، إخفاء اختياري | لا تعتمد «قواعد Replika/Duolingo/Clippy» كحقائق قياسية من دون دراسة أصلية/سند مباشر |
| §2.5 ص5–6 | اختياري | `.sensoryFeedback` وsilent by default | `&approval` ضمن Array مثال غير مناسب للاعتماد؛ افصل تحميل النغمات وتنظيف SystemSoundID وتحقق من التكرار والأذونات |
| §3 ص6 | يحتفظ مع ضبط | SF Symbols متناسقة، المؤثرات الصغيرة المبنية على أحداث | لا تكثر 10 أيقونات/animation، ولا تحوّل SF Symbol إلى هوية التطبيق التجارية |
| §4.1 ص7 | تعديل | Native TabView + minimized + accessory متاحان فعلاً | 5 tabs مبالغ فيها؛ اتفقنا على 3: محادثة، مساحات، نشاط؛ التحكم Sheet، الموافقات داخل Activity |
| §4.2 ص7 | جزئي | Liquid Glass في controls iOS26 فقط | صيغة `.buttonStyle(.glass) / .glassProminent` وصفية وليست Swift جاهزًا؛ لا تكسو كل الصفحة زجاجًا |
| §4.3 ص7–8 | يحتفظ مع تغيير | Router/Deep Linking للمهام والموافقات، تحقق جلسة وملاك | غيّر schema `kanon://` إلى `agent://` أو Universal Links عند التفعيل، ولا تعتبر scheme حدًا أمنيًا |
| §5.1 ص8 | جزئي | Color Tokens/Motion presets كمصادر تصميم | `Color(hex:)` تنفيذ ناقص؛ لا تضف ثلاث حزم خطوط قبل اختبار خط Apple الافتراضي وRTL |
| §5.2 ص9 | **اعتماد** | `loading/empty/ready/stale/denied/failed` | أضف `unauthenticated`/`expired` إذا كانت الحاجة حقيقية بدل التخمين، مع lastSync حقيقي |
| §5.3 ص9 | **رفض** | فكرة ترجمة الحالات للعربية | استبدل enum بعقد Core الرسمي من 9 حالات |
| §5.4 ص9 | **اعتماد بتحقق** | REAL/DEMO/UNKNOWN مع دليل | الحقيقة تُشتق من event/receipt لا من الألوان، وأضف OFFLINE للحالة الشبكية لا badge completion |
| §5.5 ص9–10 | **رفض بصيغته** | Visual Coordinator موحد | افصل Voice/Task/Auth/Proof؛ لا InputFocused==Listening ولا RequestInFlight==PROCESSING |
| §6 ص10 | **اعتماد** | RTL direction-aware، تقليل الحركة/الشفافية، LTR للكود | لا تعكس الرموز غير الاتجاهية، دعم VoiceOver وديناميكية الخط |
| §7.1 ص10 | جزئي | Swift 6 strict concurrency ومشروع Xcode أصلي | Xcode 26 أدنى وقت النشر، 27 مدعوم؛ Version support يتبع الجهاز المستهدف وإمكانات الفريق |
| §7.2 ص10 | بحذر | automatic signing + Team | `Revoke` ليس أول خطوة لأي No Profile؛ افحص أولاً Bundle ID والعضوية والثقة والصلاحيات |
| §7.3 ص10 | تعديل | Privacy manifest, scheme/AASA, encryption review | شروط privacy وaccount deletion/encryption تحتاج تدقيق حالة المنتج، لا نسخ ثابت |
| §7.4–7.7 ص11 | تحديث وقت النشر | TestFlight/Xcode Cloud ولقطات فعلية، اختبار Release | مدد مراجعة وتكاليف وأبعاد صور غير ثابتة؛ افحص بوابة Apple عند الرفع |
| §8.1 ص11–12 | **إصلاح جذري** | URLSession غير shared، actor، cancellation | Header idempotency مختلف عن Core؛ retry غير آمن؛ تجديد 5 دقائق؛ 429 Retry-After |
| §8.2 ص12 | **غير منفذ في Core** | هندسة Streaming عند إضافة API | لا ترسل طلبًا لمسار غير موجود؛ الآن polling `/v1/tasks/:id` |
| §8.3 ص12 | تعديل | Keychain ThisDeviceOnly | تقسيم SecItemUpdate/query ونتائج OSStatus، عدم تخزين المفتاح الخاص Secure Enclave في UserDefaults |
| §8.4 ص12 | بحذر | Local drafts / resend text only | لا تعيد إرسال external write من outbox؛ تحفظ source of truth في Core، وتحل UNKNOWN يدويًا أو بمصالحة آمنة |
| §9.0 ص13 | **اعتماد** | LoadableView/ContentUnavailableView | فحص generics/StateObject مع Xcode، وعدم عرضه ككود مضمُون البناء دون compile |
| §9.1 ص13 | اعتماد مع ربط | scroll-smart، LazyVStack، message bubble، receipts | لا streaming UI ما لم يوجد endpoint؛ افتح core task result الحقيقي |
| §9.2 ص13 | اعتماد مع تعديل | حالة المهمة، تفاصيل الأدلة والآخر sync | استبدل TaskState بقائمة Core الرسمية، لا اختلاق audit events |
| §9.3 ص13 | اعتماد مع تصحيح | expiresAt server-backed وتوقيت مستقل، بطاقة واضحة | تنسيق Server Clock drift، timer لا يضمن expiry server؛ لا APPROVE legacy للمالك الموقَّع |
| §9.4 ص14 | اختياري | JSON pretty print/RTL exclusion | لا حاجة Syntax highlight معقد قبل تشغيل receipts، راعِ PII وسلامة الحجم |
| §9.5 ص14 | تعديل | VPS, audio, appearance/privacy | مشاهد أربعة وشخصية كانون/حذف حساب غير ضروري حاليًا؛ انقل التشخيص خارج الرئيسية |
| §9.6 ص14 | اعتماد بتحكم | tactile feedback نادر ومستند لحدث | لا تستخدم success haptic عند approval المقدمة كنجاح تنفيذ |
| §10 ص14 | مرحلة لاحقة | App Intents + Shortcuts + SnippetIntent API حقيقي | لا تضع «اسأل كانون»، استخدم «ايجنت»؛ App Intents تلتزم بدور API لا تتجاوز الصلاحيات |
| §11–12 ص14 | تعاد صياغتها | Checklist مرتبط بحالات Core + device + RTL + Build | لا علامة صح على SSE/3D/60fps/outbox إذا لم تُختبر؛ «6 موجات بحث موثقة» ليست قائمة مراجع مستقلة مدققة |

## اختيار ما يفيد تطبيق «ايجنت» مع تقليل المكونات

**ندمج فورًا في المواصفات التنفيذية (لا يعني أن الكود موجود):**
1. Native TabView بسيط (3 عناصر فقط) + Control Sheet؛ ثلاثة أو أربعة SF Symbols متناسقة لكل وظيفة موجودة.
2. LoadState وStale/Retry وRTL وReduce Motion وVoiceOver.
3. Keychain + Secure Enclave + session refresh + Deep Links للمهام والموافقات بعد فحص owner/session.
4. `AgentVisualStateCoordinator` يقرأ `TaskStatus` + Voice + Auth + Truth منفصلة.
5. بطاقة Approval countdown مبنية على وقت الخادم مع server authoritative validation، وReceipt readable.
6. Draft-first محلي للرسائل غير المرسلة، لكن عدم عمل outbox تلقائي للأفعال الحساسة.
7. Shortcuts/App Intents لاحقًا كواجهة للعمليات الموجودة فعليًا في Core.

**لا ندمج حاليًا:**
- أربعة فيديوهات متكررة في Bundle أو أربع بيئات قبل نجاح مشهد واحد.
- شخصيات صقر/قلم/عثة وRive بدون ملفات مرخَّصة وأصول فعلية.
- Shader gradient كبديل عن الـ3D، أو loop كإيهام سينمائي تفاعلي.
- SSE وهمي، وحالات `RUNNING/UNKNOWN_HALTED` مخالفة للعقد، وHeader idempotency كبديل لـrequest_id.
- 5 tabs مع شاشات موافقات وأدلة منفصلة بدل Activity قابلة للتفصيل.
- Firebase/Supabase/Backend آخر أو خدمات Background jobs على iPhone؛ Core يبقى VPS مستقلًا.

## كود مختصر مصحح وفق عقد Core (Swift؛ مثال مراجعة وليس Build مثبتًا)
```swift
enum CoreTaskStatus: String, Codable, CaseIterable {
    case received = "RECEIVED"
    case processing = "PROCESSING"
    case waitingForApproval = "WAITING_FOR_APPROVAL"
    case approved = "APPROVED"
    case rejected = "REJECTED"
    case executing = "EXECUTING"
    case verifying = "VERIFYING"
    case completed = "COMPLETED"
    case failed = "FAILED"
    var isFinal: Bool { self == .completed || self == .failed || self == .rejected }
}
```

إصلاح الوسيط: `AVPlayerLooper(player: q, templateItem: item)` وليس `loopItem`.

إصلاح shader إذا استُخدم كـbackground ناعم فقط (تمثيل توضيحي):
```swift
GeometryReader { geometry in
    TimelineView(.animation(paused: reduceMotion)) { timeline in
        let size = geometry.size
        Rectangle().colorEffect(
            ShaderLibrary.sceneGradient(
                .float4(0, 0, Float(size.width), Float(size.height)),
                .float(Float(timeline.date.timeIntervalSinceReferenceDate)),
                .color(scene.colors[0]),
                .color(scene.colors[1]),
                .color(DesignTokens.accentCore)
            )
        )
    }
}
```
**ملاحظة:** لا بد من اختبار هذا الكود في Xcode والتحقق من سلوك Metal فعليًا؛ لم يُجر بناء على macOS ضمن هذا التدقيق.

## المصادر المرجعية التي استُخدمت للتحقق
- Apple AVPlayerLooper: https://developer.apple.com/documentation/avfoundation/avplayerlooper
- Apple SwiftUI colorEffect shader signature: https://developer.apple.com/documentation/swiftui/view/coloreffect(_:isenabled:)
- Apple SwiftUI tab bar: https://developer.apple.com/documentation/swiftui/tabbarminimizebehavior
- Apple Liquid Glass: https://developer.apple.com/documentation/swiftui/glasseffectcontainer
- Apple SDK minimum 2026: https://developer.apple.com/news/upcoming-requirements/
- Apple Privacy/Required Reason APIs: https://developer.apple.com/documentation/technotes/tn3183-adding-required-reason-api-entries-to-your-privacy-manifest
- Apple account deletion conditional: https://developer.apple.com/help/app-review/guideline-reference/5-1-1-account-deletion
- Apple encryption export: https://developer.apple.com/documentation/security/complying-with-encryption-export-regulations
- Apple Keychain update: https://developer.apple.com/documentation/security/updating-and-deleting-keychain-items
- Rive Swift iOS changelog: https://github.com/rive-app/rive-ios/blob/main/CHANGELOG.md
- Repo source of truth: https://github.com/as1411307-collab/ahemed--agent-v01/blob/main/packages/contract/src/index.ts
- Core route implementation: https://github.com/as1411307-collab/ahemed--agent-v01/blob/main/apps/core/src/server.ts
- Core P256 sessions: https://github.com/as1411307-collab/ahemed--agent-v01/blob/main/apps/core/src/security/device-session.ts
- AGENT canonical specification: https://github.com/as1411307-collab/rork-github-export/blob/main/AGENT_APP_SPEC.md

**الخلاصة:** كان التقرير مفيدًا لتجربة الاستخدام والبنية المحلية، لكنه ليس مصدرًا أصيلًا لحقائق Core أو دليلًا على أن أصول المشاهد/الشخصيات موجودة، وليس كودًا جاهزًا للدمج بلا تعديل. اعتماد الجزء السليم يُختبر في Xcode، وما لم يُبنَ أو يُثبت يبقى مؤجلًا.