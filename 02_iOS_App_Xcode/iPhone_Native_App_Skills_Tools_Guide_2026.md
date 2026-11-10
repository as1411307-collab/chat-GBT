# دليل المهارات والأدوات وأفضل الطرق البرمجية لتصميم تطبيق iPhone أصلي بحساب مطور Apple

**تاريخ البحث:** 8 نوفمبر 2026 — **النطاق:** بحث وعرض معلومات فقط، دون بناء أي شيء.
**الاتجاه المرجعي:** ملف «App_Build_Complete_Guide_2026»، وخلاصته: تطبيق iPhone أصلي بـ SwiftUI وXcode، موقَّع بحساب المطور الخاص بك، يعمل كواجهة تحكم خفيفة لوكيل ذكي شخصي، ويتصل بنواة (Core) مستقلة عبر Tailscale Serve. المحادثة فيه بالنص والصوت، بالعربية من اليمين لليسار وبالإنجليزية، مع مهام وموافقات موقَّعة بمفتاح Secure Enclave، ودون WebView أو React Native.

---

## الخلاصة التنفيذية

البيئة اليوم أنضج مما افترضه الملف المرفق. الإصدار المستقر الحالي هو **Xcode 27.2** مع **iOS 27.2** وعائلة **Swift 6.4**. أصبحت البرمجة بالوكلاء جزءًا رسميًا من Xcode نفسه، إذ يضم Claude Agent وCodex وGemini، ويدعم وكلاء ACP ومهارات وأدوات MCP مخصصة. كما يتيح جسر `xcrun mcpbridge` لأي وكيل خارجي أن يبني ويختبر ويعرض المعاينات من داخل Xcode. لذلك الطريقة الأنسب لمشروعك هي: **مشروع Xcode عادي مملوك لك في Git**، يعمل عليه **وكيل برمجة واحد** (Claude Code أو Codex أو وكيل Xcode المدمج)، مع **مجموعة صغيرة منتقاة من المهارات (Agent Skills)**، و**مصدر توثيق Apple محدَّث**، و**أداة بناء وتشغيل حقيقية** هي MobileBuildMCP أو جسر Xcode.

أهم القرارات البرمجية التي تتفق مع ملفك وتؤكدها المصادر هي:

1. نماذج `@MainActor @Observable` على مستوى كل ميزة، مع حقن الخدمات عبر البروتوكولات.
2. عقد OpenAPI يولّد عميل Swift عبر مكتبة Apple الرسمية `swift-openapi-generator`، وهي تدعم SSE فعليًا.
3. مفتاح موافقة من نوع `SecureEnclave.P256` محمي بـ `SecAccessControl`، وليس بنافذة Face ID شكلية وحدها.
4. SwiftData للكاش والمسودات فقط.
5. مكتبة Textual لعرض Markdown بدل MarkdownUI التي دخلت وضع الصيانة.
6. صفحات PageSpec تُعرض عبر قائمة مكوّنات أصلية مسموحة، دون أي تقييم كود.

ثلاث نقاط يجب أن تراعيها خطتك:

- **دعم Apple للعربية لم يثبت** في Foundation Models ولا في Siri AI. وكذلك دعم SpeechTranscriber للعربية غير مضمون على كل جهاز. لهذا يبقى التعرف على الصوت العربي في النواة هو المسار الأساسي.
- **منصتا Rork وVibecode أصبحتا تولّدان SwiftUI أصليًا** قابلًا للتصدير إلى Xcode، لكن بشروط اشتراك محددة.
- **المناسب لتطبيق شخصي** هو التثبيت المباشر من Xcode على جهازك، أو TestFlight الداخلي، دون الحاجة إلى نشر في App Store.

---

## 1. حالة المنصة الآن (نوفمبر 2026)

| العنصر | الحالة الحالية | ملاحظة لمشروعك |
|---|---|---|
| Xcode | المستقر 27.2 (27B52) صدر في 29 أكتوبر، والتجريبي 27.3 صدر في 3 نوفمبر | يعمل على أجهزة Mac بمعالج Apple Silicon فقط، ويحتاج macOS Tahoe 26.6 أو أحدث |
| iOS | المستقر 27.2، والتجريبي 27.3 | إرشادات Liquid Glass في iOS 26 ما زالت سارية، وiOS 27 حسّن وضوحها وأضاف شريط تحكم بالشفافية للمستخدم |
| Swift | العائلة 6.4، وآخر إصدار مستقل 6.4.2 (30 أكتوبر) | مفاهيم «التزامن الميسَّر» (Approachable Concurrency) التي ظهرت في 6.2 ما زالت هي الأساس |
| شرط الرفع إلى App Store Connect | منذ 28 أبريل 2026 يجب البناء بـ Xcode 26 أو أحدث وبـ iOS 26 SDK أو أحدث | هذا شرط على الـ SDK وليس على الحد الأدنى لإصدار iOS الذي يدعمه التطبيق |

المصادر: [Apple Releases](https://developer.apple.com/news/releases/)، [Xcode Support](https://developer.apple.com/support/xcode/)، [Swift Releases](https://github.com/swiftlang/swift/releases)، [Upcoming Requirements](https://developer.apple.com/news/upcoming-requirements/).

**توصية الحد الأدنى للنظام (Deployment Target):** بما أن التطبيق شخصي على جهازك، فاختيار **iOS 26** حد أدنى منطقي. فهو يعطيك SpeechAnalyzer وLiquid Glass ومحرر `TextEditor` الغني بـ `AttributedString` دون شروط توافق إضافية. مكتبة Textual تحتاج iOS 18 فقط، فلا تعارض.

---

## 2. المهارات (Agent Skills) الموصى بها

المهارات هي ملفات تعليمات ومراجع (`SKILL.md` ومجلد `references/`) يقرؤها وكيل البرمجة عند الحاجة. فائدتها أنها تمنعه من استخدام واجهات مهجورة أو أنماط خاطئة. تحققتُ منها في سجل [skills.sh](https://skills.sh) وفي مستودعاتها على GitHub بتاريخ اليوم. **أرقام التثبيت والنجوم مؤشر انتشار، لا ضمان جودة.**

### 2.1 الحزمة الأساسية المقترحة (6 إلى 8 مهارات تكفي)

| المهارة | المؤلف | ماذا تفعل لمشروعك | المؤشرات |
|---|---|---|---|
| **swiftui-pro** | Paul Hudson (Hacking with Swift) | مراجعة شاملة لكود SwiftUI تغطي الواجهات المهجورة وتدفق البيانات والتنقل وإرشادات HIG وإمكانية الوصول (Dynamic Type وVoiceOver وReduce Motion) والتوطين والأداء والتزامن. تستهدف iOS 26 وSwift 6.2 فأحدث | 36.9 ألف تثبيت، 6.5 ألف نجمة، اجتازت فحوص الأمان الثلاثة |
| **swiftui-expert-skill** | Antoine van der Lee (SwiftLee) | بديل أو مكمّل. لا يفرض معمارية معينة، ويطبّق Liquid Glass فقط عند طلبه صراحة، ويضبط الواجهات حسب إصدار النظام | 36.1 ألف تثبيت، 3.8 ألف نجمة |
| **swift-concurrency** | Antoine van der Lee | يقرأ إعدادات المشروع أولًا (`SWIFT_DEFAULT_ACTOR_ISOLATION` و`SWIFT_APPROACHABLE_CONCURRENCY`)، ثم يقترح أصغر إصلاح آمن لأخطاء Swift 6 | 17.4 ألف تثبيت، 1.7 ألف نجمة |
| **swift-testing-pro** | Paul Hudson | Swift Testing لاختبارات الوحدة والتكامل، وXCTest لاختبارات الواجهة | 10.4 ألف تثبيت |
| **swift-security-expert** | Ivan Magda | Keychain وFace ID وCryptoKit وSecure Enclave وتثبيت الشهادات ومعايير OWASP. يتضمن قائمة بأكثر 10 أخطاء أمنية يرتكبها الذكاء الاصطناعي، مثل حفظ الرمز في UserDefaults أو الاعتماد على قيمة منطقية من `evaluatePolicy` يمكن تجاوزها | ترخيص MIT، وكل ادعاء موثّق بمرجع من Apple |
| **Dimillian/Skills**: swiftui-liquid-glass وswiftui-ui-patterns وswiftui-view-refactor وios-debugger-agent | Thomas Ricouard (مطوّر IceCubes) | استخدام Liquid Glass بشكل صحيح، وأنماط الشاشات، وإعادة هيكلة الواجهات على نمط MV، وتصحيح الأخطاء على المحاكي عبر XcodeBuildMCP | ترخيص MIT، وswiftui-liquid-glass وحدها 5.9 ألف تثبيت |
| **xcodebuildmcp** | Sentry | تعليمات استخدام أداة MobileBuildMCP للبناء والتشغيل والاختبار وLLDB وأتمتة الواجهة | مستودعها 6.5 ألف نجمة |

### 2.2 مهارات متخصصة اختيارية حسب الميزة

مجموعة **dpearson2699/swift-ios-skills** تضم 86 مهارة تستهدف iOS 26 وSwift 6.3. اختر منها ما يطابق ميزات ملفك فقط:

- `ios-localization`: كتالوجات النصوص والكتابة من اليمين لليسار.
- `ios-networking`.
- `speech-recognition`: SpeechAnalyzer.
- `app-intents`.
- `activitykit`.
- `cryptokit`.
- `device-integrity`: App Attest.
- `background-processing`.
- `push-notifications`.
- `ios-accessibility`.
- `app-store-review`.

**تنبيه:** ترخيصها **PolyForm Perimeter** وليس MIT، فاقرأ شروطه قبل أي استخدام تجاري. [المستودع](https://github.com/dpearson2699/swift-ios-skills).

خيارات أخرى:

- **Axiom** (Charles Wiltgen): المجموعة الأشمل، وترخيصها MIT. تضم 289 مهارة و44 وكيلًا، مع أدوات `axbuild` و`xclog` و`xcsym` و`xcui` و`xcprof`، ولها دليل ربط مع Xcode. لكنها ثقيلة؛ استخدمها بديلًا عن الحزمة الأساسية لا إضافة إليها. [المستودع](https://github.com/CharlesWiltgen/Axiom)
- **إضافة OpenAI الرسمية `build-ios-apps`** لمستخدمي Codex: تجمع مهارات Dimillian مع ios-app-intents وأدوات تحليل الذاكرة والأداء، وتربط XcodeBuildMCP تلقائيًا. [المصدر](https://github.com/openai/plugins/tree/main/plugins/build-ios-apps)
- **مهارات asc** (rorkai/app-store-connect-cli-skills): أتمتة TestFlight وApp Store Connect لاحقًا.
- **مهارات التصميم:** `ios-hig-design` (wondelai)، وتقيّم الواجهة من 10 وفق HIG.

**تحذير:** المهارة `uizze.sh@ios-design` تظهر بـ 418 ألف تثبيت، لكن مصدرها غير قابل للتحقق. **لا يُنصح بها.**

### 2.3 أوامر التثبيت (للعلم فقط)

```bash
npx skills add https://github.com/twostraws/swiftui-agent-skill --skill swiftui-pro
npx skills add https://github.com/avdlee/swift-concurrency-agent-skill --skill swift-concurrency
npx skills add https://github.com/twostraws/swift-testing-agent-skill --skill swift-testing-pro
npx skills add https://github.com/ivan-magda/swift-security-skill --skill swift-security-expert
npx skills add https://github.com/getsentry/mobilebuildmcp --skill xcodebuildmcp
npx skills add dpearson2699/swift-ios-skills --skill ios-localization --skill speech-recognition --skill app-intents
# Dimillian: انسخ مجلدات المهارات المطلوبة إلى ~/.codex/skills أو ~/.claude/skills
```

**مبدأ مهم:** كثرة المهارات تزحم سياق الوكيل. ثبّت فقط ما يخدم المرحلة الحالية من خطتك.

---

## 3. أدوات Apple الرسمية

### 3.1 البرمجة بالوكلاء داخل Xcode

ظهرت البرمجة بالوكلاء أول مرة في Xcode 26.3 (فبراير 2026) مع Claude Agent وOpenAI Codex. ثم وسّعها Xcode 27 لتشمل:

- تكاملات Anthropic وGoogle وOpenAI.
- وضع تخطيط تفاعلي عبر الأمر `/plan`.
- وكلاء فرعيين متوازين.
- التحقق على المحاكي.
- دعم مهارات وأدوات MCP مخصصة، ووكلاء متوافقين مع بروتوكول ACP.

خدمات المزوّدين ليست مشمولة في اشتراك المطور؛ تحتاج حسابًا لدى كل مزوّد. [Xcode What's New](https://developer.apple.com/xcode/whats-new/)، [Setting up coding intelligence](https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence).

**ربط وكيل خارجي بـ Xcode** يتم بالجسر الرسمي. فعّل الخيار «Allow external agents to use Xcode tools» من Xcode › Settings › Intelligence، وافتح المشروع، ثم سجّل الجسر:

```bash
claude mcp add --transport stdio xcode -- xcrun mcpbridge
codex mcp add xcode -- xcrun mcpbridge
```

يعطي هذا الجسر الوكيل أدوات البناء وتشغيل الاختبارات وتشخيصات المحرر وعرض معاينات SwiftUI والبحث في توثيق Apple وجلسات WWDC. وفي Xcode 27 توجد معاينة مبكرة لخادم MCP مستقل عن المشروع (`sudo xcrun mcp-server enable`). تجنّب معه خيار `--unsafe-always-allow-all-agents`. [Giving external agents access to Xcode](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode).

### 3.2 أدوات التصميم والجودة الرسمية

- **Icon Composer:** لإنشاء أيقونة متعددة الطبقات متوافقة مع Liquid Glass. يحتاج macOS 26.4 أو أحدث. [المصدر](https://developer.apple.com/icon-composer/)
- **SF Symbols 27:** ما زالت كل الرموز المذكورة في ملفك متاحة، مثل `bubble.left` و`square.stack` و`checklist` و`checkmark.shield`. [المصدر](https://developer.apple.com/sf-symbols/)
- **موارد التصميم:** حزمة Figma الرسمية لـ iOS 26 (حُدّثت في يوليو 2026)، وموارد iOS 27 على [Apple Design Resources](https://developer.apple.com/design/resources/).
- **صيغة المشروع الجديدة:** يستخدم Xcode 27.2 افتراضيًا صيغة JSON هرمية داخل `.xcodeproj` بدل `.pbxproj`. هذه الصيغة أسهل في المقارنة والدمج وفي تعديل الوكلاء لها. تأكد من توافق أي أداة خارجية قبل التحويل إليها.
- **الاختبار:** Swift Testing للاختبارات الجديدة، وXCTest/XCUIAutomation لاختبارات الواجهة والأداء. أصبح Swift 6.4 يسمح بتداخل منضبط بين الإطارين.
- **Instruments 27:** يضيف مقارنة التشغيلات وعرض الدوال الأكثر استهلاكًا، مع أداتي Swift Concurrency وTime Profiler.

---

## 4. أدوات الوكلاء الخارجية وخوادم MCP

| الأداة | الحالة الحالية | الدور في مشروعك |
|---|---|---|
| **Claude Code** | الإصدار 2.1.319 (6 نوفمبر) | وكيل طرفية على جهاز Mac. يقرأ `CLAUDE.md`، ويرجع إلى `AGENTS.md` إن لم يجده |
| **Codex CLI** | الإصدار 0.167.0 (6 نوفمبر)، ترخيص Apache-2.0 | يقرأ `AGENTS.md` بحد أقصى 32 كيلوبايت. نفّذه محليًا على جهاز Mac، لا في بيئة Linux سحابية |
| **Cursor** | الإصدار 3.27 | قواعده في `.cursor/rules/*.mdc` وفي `AGENTS.md`، ويتكامل مع Xcode 26.3 فأحدث عبر 20 أداة |
| **MobileBuildMCP** (الاسم الجديد لـ XcodeBuildMCP) | الإصدار 2.7.1، نحو 6.5 ألف نجمة، تملكه Sentry | البناء والتشغيل والاختبار على المحاكي والجهاز الحقيقي، مع LLDB ولقطات الشاشة وأتمتة الواجهة. التثبيت: `brew tap getsentry/xcodebuildmcp && brew install mobilebuildmcp` |
| **Sosumi** | الإصدار 1.1.0 (7 نوفمبر) | يجلب توثيق Apple المحدَّث بصيغة Markdown لتقليل اختلاق الوكيل لواجهات غير موجودة |
| **xdocs / apple-docs-mcp** | بديلان. الثاني يغطي جلسات WWDC حتى 2025 فقط | مصدر توثيق إضافي |
| **ios-simulator-mcp** (Joshua Yoes) | الإصدار 2.2.0. استخدم 1.3.3 فأحدث بسبب ثغرة حقن أوامر في الإصدارات الأقدم | فحص شجرة إمكانية الوصول والنقر والتصوير، إن لم تكفِ MobileBuildMCP |
| **SweetPad** | إضافة محرر وأداة CLI بالإصدار 0.1.18 | بناء مشروع Xcode من VS Code أو Cursor |
| **XcodeGen / Tuist** | XcodeGen 2.46.0، وTuist 4.215.1 | اختياريان. مشروع بهدف واحد مثل مشروعك يكفيه ملف Xcode عادي |
| **SwiftLint / swift-format** | SwiftLint 0.65.1، وswift-format مدمج مع Xcode | للفحص والتنسيق. اختر منسّقًا واحدًا فقط |
| **Periphery** | المستودع الأصلي مؤرشف، والبديل المدعوم Periphery Pro (نسخة تجريبية) | لاكتشاف الكود الميت |
| **asc CLI** | انتقل إلى حساب rorkai، الإصدار 6.5.3 | أتمتة TestFlight وApp Store Connect |
| **fastlane** | الإصدار 2.241.2 | بديل ناضج، لكنه غير ضروري في البداية |
| **Xcode Cloud** | 25 ساعة حوسبة شهريًا مشمولة في العضوية | تكامل مستمر (CI) ورفع تلقائي إلى TestFlight |

المصادر: [MobileBuildMCP](https://github.com/getsentry/MobileBuildMCP)، [Sosumi](https://sosumi.ai/)، [Claude memory](https://code.claude.com/docs/en/memory)، [Codex AGENTS.md](https://developers.openai.com/codex/guides/agents-md/)، [Cursor Xcode](https://cursor.com/docs/integrations/xcode)، [Xcode Cloud](https://developer.apple.com/xcode-cloud/)، [ASC CLI](https://github.com/rorkai/App-Store-Connect-CLI).

**أداة يجب تجنبها:** أوقف تطبيق **Alex Sidebar** التنزيلات الجديدة في 1 أكتوبر 2025 بعد انضمام فريقه إلى OpenAI. [المصدر](https://www.alexcodes.app/blog/alex-team-joins-openai)

**أدوات تحويل التصميم إلى كود:** مهارة Figma الرسمية `figma-swiftui` عبر Figma MCP. وتطبيق DetailsPro الذي يصدّر ملفات Swift. انتبه إلى أن محلّل SwiftUI القديم في Code Connect توقفت صيانته في 17 أغسطس 2026.

---

## 5. منصات التوليد (Rork وVibecode وغيرهما)

تغيّر هذا القطاع جذريًا. ملفك يعامل هذه المنصات كأدوات مساعدة فقط، وهذا ما زال صحيحًا. لكن بعضها أصبح يولّد **SwiftUI أصليًا حقيقيًا**:

| المنصة | ما تولّده | التصدير والملكية | السعر الحالي | المخاطر |
|---|---|---|---|---|
| **Rork** | لم تعد تنشئ مشاريع Expo جديدة؛ مشاريع iPhone الجديدة **Swift/SwiftUI أصلية** | تصدير المصدر عبر GitHub كمشروع Xcode كامل يمكن توقيعه بفريقك | خطة Pro بـ 20 دولارًا شهريًا تشمل SwiftUI و100 رصيد. خطة Max من 200 دولار | الاعتماد على خلفية Rork وأرصدة الذكاء الاصطناعي إن استُخدمت. بعض صفحات الأسئلة الشائعة القديمة تتعارض مع الوثائق الأحدث |
| **Vibecode** | SwiftUI أصلي عند اختيار «iOS app»، وليس «Mobile app» المبني على Expo | تنزيل مشروع Xcode/SPM قياسي في خطتي Pro (50 دولارًا) وMax (200 دولار) فقط | خطة Plus (20 دولارًا) لا تشمل تنزيل المشروع | الشروط المنشورة لعام 2025 فيها عبارات قديمة عن التصدير، وحقوق تدريب واسعة، وقيود إقامة أمريكية |
| **Bitrig** | مشاريع Xcode محلية أصلية | التصدير متاح حتى في الخطة المجانية | Pro بـ 15 دولارًا، مع اشتراك ذكاء اصطناعي منفصل. يحتاج جهاز Mac بمعالج Apple Silicon | في الشروط صياغات عن ترخيص قابل للإلغاء |
| **Bolt / Anything (Create)** | Expo/React Native | يمكن التصدير، لكن يبقى بداخله وقت تشغيل React | Bolt من 25 دولارًا، وAnything بـ 24 دولارًا | لا يتوافق مع شرط «أصلي بالكامل» في ملفك |
| **Lovable** | تطبيقات ويب فقط | — | — | غير مناسبة |
| **iSwift.dev** | SwiftUI | لم أتمكن من التحقق من إمكانية تنزيل `.xcodeproj` كاملًا | 29 و99 و250 دولارًا | غير محسوم |

المصادر: [Rork Expo migration](https://docs.rork.com/expo)، [Rork subscriptions](https://docs.rork.com/introduction/subscriptions)، [Rork code export](https://docs.rork.com/faq/code-export)، [Vibecode native iOS](https://www.vibecodeapp.com/docs/getting-started/native-ios-apps)، [Vibecode plans](https://www.vibecodeapp.com/docs/getting-started/plans-and-credits)، [Bitrig pricing](https://bitrig.com/pricing).

**الطريقة المثلى لاستخدامها** تتفق مع ملفك: استعملها لتوليد **مسودة واجهة** فقط. انقل الكود فورًا إلى مستودعك، واحذف منه أي اعتماد على خلفية المنصة. ثم أعد بناء طبقات الشبكة والأمان يدويًا وفق العقد. لا تعتمد على مفاتيح أو خدمات ذكاء اصطناعي مستضافة لدى المنصة.

---

## 6. أفضل الطرق والتعليمات البرمجية لكل طبقة

### 6.1 المعمارية والتزامن

**الموصى به:** نماذج `@MainActor @Observable` على مستوى الميزة، مثل `ChatModel` و`TasksModel` و`ApprovalModel` و`SessionModel`، تحملها الواجهات عبر `@State`. الخدمات تُحقن عبر بروتوكولات من نوع `Sendable`، مثل `CoreAPI` و`ApprovalSigner` و`CredentialStore` و`CacheStore`، باستخدام المُهيِّئ (initializer) أو قيمة Environment مخصصة. **لا Singletons، ولا تجعل كل خدمة قابلة للمراقبة.** هذا يطابق نمط Apple في WWDC25 ومهارات Dimillian وPaul Hudson، ويطابق `RuntimeAdapter` و`LiveCoreClient` في ملفك.

```swift
protocol CoreAPI: Sendable {
    func tasks() async throws -> [TaskDTO]
}

@MainActor @Observable final class TasksModel {
    private let api: any CoreAPI
    var tasks: [TaskDTO] = []
    init(api: any CoreAPI) { self.api = api }
    func refresh() async throws { tasks = try await api.tasks() }
}
```

إعدادات البناء الموصى بها:

```text
SWIFT_VERSION = 6
SWIFT_STRICT_CONCURRENCY = complete
SWIFT_DEFAULT_ACTOR_ISOLATION = MainActor
SWIFT_APPROACHABLE_CONCURRENCY = YES
```

**قواعد التزامن الأساسية:**

- الدالة `async` لا تعني تلقائيًا أنها تعمل في الخلفية. استخدم `@concurrent` للعمليات الثقيلة، مثل فك تشفير JSON الكبير وتطبيع النص العربي.
- استخدم `actor` لتنسيق حالة الجلسة وتجديد الرموز ومؤشرات البث وإعادة الاتصال.
- لا تخفِ أخطاء المترجم بـ `@unchecked Sendable` أو `Task.detached` بشكل عشوائي.

**مكتبة TCA** (الإصدار 1.26.2، ترخيص MIT): بديل قوي، لكنها تعقيد إضافي لا يحتاجه عميل خفيف كتطبيقك. [WWDC25-266](https://developer.apple.com/videos/play/wwdc2025/266/)، [Swift 6.2](https://www.swift.org/blog/swift-6.2-released/).

**مرجع معماري للتعلّم:** تطبيق IceCubes (7.1 ألف نجمة). انتبه إلى أن ترخيصه **AGPL-3.0**، فهو للدراسة لا للنسخ.

### 6.2 العقد والشبكة (Contract-First)

هذه المكتبات الرسمية من Apple تطابق مبدأ «العقد أولًا» في ملفك:

- `swift-openapi-generator` بالإصدار 1.14.4 (5 نوفمبر).
- `swift-openapi-runtime` بالإصدار 1.13.4.
- `swift-openapi-urlsession` بالإصدار 1.4.0.

كلها بترخيص Apache-2.0. تحفظ النواة عقد OpenAPI 3.1، ويولّد Xcode منه أنواع Swift والعميل عند البناء. ثم تغلّف هذا العميل خلف بروتوكول `CoreAPI` تكتبه بنفسك. المكتبة تدعم **SSE فعليًا** دون تخزين الاستجابة كاملة:

```swift
let response = try await client.streamTaskEvents(path: .init(taskId: id))
let events = try response.ok.body.textEventStream
    .asDecodedServerSentEventsWithJSONData(of: TaskEvent.self)
for try await event in events { /* حدّث الحالة من حدث Core الحقيقي فقط */ }
```

**قواعد عملية:**

- ابدأ بـ SSE للمهام، مع لقطات دورية (polling) كمسار احتياطي.
- إن كتبت محلّل SSE بنفسك، فيجب أن يدمج أسطر `data:` المتعددة، ويحترم `id` و`retry` و`Last-Event-ID`.
- لعمليات الكتابة (إرسال رسالة، أو بدء مهمة، أو موافقة) أنشئ **مفتاح idempotency مرة واحدة** واحفظه مع المسودة، وأعد استخدامه بعد أي انقطاع.
- لا تولّد nonce أو توقيعًا جديدًا تلقائيًا بعد انتهاء المهلة. استعلم عن الحالة أولًا، وهذا يطابق حالة `OUTCOME_UNKNOWN` في ملفك.
- استخدم `URLSessionWebSocketTask` فقط إن احتجت قناة تحكم ثنائية الاتجاه.

[swift-openapi-generator](https://github.com/apple/swift-openapi-generator)، [مثال SSE الرسمي](https://github.com/apple/swift-openapi-generator/blob/main/Examples/event-streams-client-example/Sources/EventStreamsClient/EventStreamsClient.swift).

### 6.3 الأمان: Secure Enclave وKeychain وFace ID وTailscale

```swift
// إنشاء مفتاح الجهاز مرة واحدة عند الاقتران
let access = SecAccessControlCreateWithFlags(
    nil, kSecAttrAccessibleWhenUnlockedThisDeviceOnly,
    [.privateKeyUsage, .biometryCurrentSet], nil)!
let key = try SecureEnclave.P256.Signing.PrivateKey(
    accessControl: access, authenticationContext: LAContext())
let blob = key.dataRepresentation      // كتلة مشفّرة، ليست المفتاح الخام؛ تُحفظ في Keychain
let publicKey = key.publicKey.derRepresentation   // تُرسل إلى Core أثناء الاقتران

// عند الموافقة
let restored = try SecureEnclave.P256.Signing.PrivateKey(
    dataRepresentation: blob, authenticationContext: context)
let signature = try restored.signature(for: canonicalApprovalBytes).derRepresentation
```

- **فرض Face ID تشفيريًا:** يتحقق بوضع سياسة الوصول على عملية المفتاح نفسها عبر `SecAccessControl`. نافذة Face ID مستقلة تسبق التوقيع لا تكفي.
- **اختيار السياسة:** `.biometryCurrentSet` يُبطل المفتاح عند تغيير البصمات المسجلة. `.userPresence` يسمح برمز الجهاز بديلًا. حدّد السياسة عند إنشاء المفتاح.
- **ما يُوقَّع:** غلاف ثابت الشكل ومُصدَّر بالنسخة (canonical) يُعرَّف في العقد. يحوي `proposalId` و`intentHash` و`nonce` و`expiresAt`، ومعرّف الجهاز والنواة، والقرار. حدّد خوارزمية SHA-256 مع ECDSA P-256 وصيغة DER حتى يتطابق التحقق في Node.js.
- **انتبه:** لا توقّع ملخصًا (digest) جاهزًا عبر الدالة التي تستقبل `Data`، وإلا ستُحسب الدالة التجزئة مرتين.
- **رمز الجلسة:** عنصر generic-password بخاصية `kSecAttrAccessibleWhenUnlockedThisDeviceOnly` و`kSecAttrSynchronizable = false`. لا يُحفظ في SwiftData ولا UserDefaults ولا السجلات.
- **مكتبة تغليف Keychain:** Valet من Square (الإصدار 5.1.1، سبتمبر 2026، Apache-2.0) أحدث من KeychainAccess، التي يعود آخر إصدار لها إلى 2021.
- **App Attest:** طبقة دفاع إضافية اختيارية. له مفتاحه المستقل، ولا يثبت موافقة المستخدم، ولا ينتقل مفتاحه مع إعادة التثبيت.
- **Tailscale:** ثبّت تطبيق Tailscale الرسمي على iPhone، واتصل بالعنوان `https://device.tailnet.ts.net` عبر HTTPS عادي، دون SDK داخل تطبيقك. استخدم **Serve** وليس Funnel لأن الأخير علني. واربط Core بالعنوان `127.0.0.1` خلف Serve، وهذا ما يطابق مخطط ملفك.

[Storing CryptoKit keys](https://developer.apple.com/documentation/cryptokit/storing-cryptokit-keys-in-the-keychain)، [Secure Enclave](https://developer.apple.com/documentation/security/protecting-keys-with-the-secure-enclave)، [Valet](https://github.com/square/Valet)، [App Attest](https://developer.apple.com/documentation/devicecheck/establishing-your-app-s-integrity)، [Tailscale Serve](https://tailscale.com/kb/1312/serve).

### 6.4 التخزين المحلي والبحث العربي

- **SwiftData** يكفي للكاش والمسودات كما في ملفك. لدى Apple مثال رسمي باسم «Maintaining a local copy of server data».
- افصل المسودات عن الكاش القابل للحذف، ولا تمرّر نماذج SwiftData الحية بين الـ actors؛ مرّر DTOs أو معرّفات بدلًا منها.
- **GRDB.swift** (الإصدار 7.11.1، ترخيص MIT) هو الخيار إن احتجت لاحقًا بحثًا محليًا بـ FTS5.
- **البحث العربي:** الخيار `unicode61 remove_diacritics` مصمَّم للحروف اللاتينية، ومُجذِّع Porter إنجليزي فقط. لذلك احفظ النص الأصلي، وأضف حقل بحث مُطبَّعًا (حذف الحركات والتطويل، وتوحيد الألف والياء وفق قرار موثَّق)، وطبّق التحويل نفسه على الاستعلام.

[SwiftData local copy](https://developer.apple.com/documentation/swiftdata/maintaining-a-local-copy-of-server-data)، [GRDB](https://github.com/groue/GRDB.swift)، [SQLite FTS5](https://sqlite.org/fts5.html).

### 6.5 عرض المحادثة والكتابة من اليمين لليسار

- **Textual** (الإصدار 0.5.0، ترخيص MIT، يحتاج iOS 18 أو أحدث) هو الخليفة الذي أعلنه مؤلف MarkdownUI. يعتمد على مسار النص الأصلي في SwiftUI، ويدعم الجداول وتلوين الكود والتحديد والنسخ.
- لأنه قبل الإصدار 1.0: ثبّت نسخة محددة، واختبره بنصوص عربية مختلطة الاتجاه وكتل كود غير مكتملة أثناء البث.
- **MarkdownUI** (الإصدار 2.4.1) في وضع الصيانة، ويبقى بديلًا احتياطيًا محافظًا.
- **Highlightr** لم تعد مطوَّرة، فتجنّبها.

```swift
StructuredText(markdown: message.body)
    .textual.structuredTextStyle(.gitHub)
    .textual.textSelection(.enabled)
```

**قواعد الكتابة من اليمين لليسار:**

- استخدم كتالوجات النصوص `.xcstrings` لنصوص التطبيق.
- استخدم `leading/trailing` بدل `left/right`.
- لا تفرض اتجاهًا واحدًا على كل الرسائل؛ حاذِ كل فقرة حسب لغتها.
- اجعل كتل الكود من اليسار لليمين عبر `.environment(\.layoutDirection, .leftToRight)`.
- لا تعكس الشعارات والصور.
- اختبر جملًا عربية تحوي معرّفات إنجليزية وروابط وأرقامًا، مع أحجام Dynamic Type كبيرة.

[Textual](https://github.com/gonzalezreal/textual)، [HIG Right-to-left](https://developer.apple.com/design/human-interface-guidelines/right-to-left).

### 6.6 الصوت

- **SpeechAnalyzer وSpeechTranscriber وAssetInventory** متاحة من iOS 26، وتعمل دون اتصال بعد تنزيل النماذج. وأضاف iOS 27 مزوّدات إدخال جديدة.
- **دعم العربية على جهازك تحديدًا غير مؤكد.** تحقق منه وقت التشغيل، واجعل `DictationTranscriber` أو التعرّف في Core بديلًا:

```swift
let locales = await SpeechTranscriber.supportedLocales
let arabicOnDevice = locales.contains { $0.language.languageCode == .arabic }
```

- **النطق (AVSpeechSynthesizer):** اعرض الأصوات المتاحة فعليًا عبر `AVSpeechSynthesisVoice.speechVoices()` بدل افتراض اسم صوت عربي بعينه.
- **التدرّج الموصى به:** ابدأ بالضغط للتحدث مع تحويل الصوت إلى نص في Core. لاحقًا، إن احتجت محادثة فورية، فاستخدم **LiveKit Swift SDK** (الإصدار 2.19.0، Apache-2.0) مع `agent-starter-swift`. هذا يحتاج بنية SFU إضافية، ولا يكفي Tailscale Serve وحده لها.
- **OpenAI Realtime:** يعمل عبر WebRTC برمز مؤقت تصدره النواة. لكن الصوت حينها يغادر شبكتك الخاصة.
- **إدارة جلسة الصوت (AVAudioSession):** اجعل جهة واحدة تملكها، وعالج المقاطعات وتغيّر مخرج الصوت (مثل AirPods) ورفض الإذن.

[SpeechTranscriber](https://developer.apple.com/documentation/speech/speechtranscriber)، [WWDC25-277](https://developer.apple.com/videos/play/wwdc2025/277/)، [LiveKit Swift](https://github.com/livekit/client-sdk-swift)، [OpenAI Realtime WebRTC](https://developers.openai.com/api/docs/guides/realtime-webrtc).

### 6.7 Siri وShortcuts وLive Activities والعمل في الخلفية

- **App Shortcuts** المبنية على App Intents تصبح متاحة تلقائيًا بعد التثبيت. ابدأ بفعل أو فعلين، مثل «أرسل مهمة» و«افتح الموافقات المعلّقة»، ولا تحاكِ شجرة التطبيق كاملة.
- **Siri AI والإجراءات المخصصة الجديدة** ما زالت **Developer Preview**. تعمل في البناء الموقَّع للتطوير وفي TestFlight الداخلي فقط، و**لا تدعم العربية** حاليًا.
- **Live Activities:** تعرض تقدّم المهمة على شاشة القفل وفي Dynamic Island. تُحدَّث من التطبيق أو عبر APNs، ولا تتصل بالشبكة بنفسها. حدودها 8 ساعات نشاط، و4 كيلوبايت حجمًا للبيانات.
- **`BGContinuedProcessingTask`:** للأعمال المحددة التي يبدؤها المستخدم وهو داخل التطبيق، ولا يصلح للاستطلاع الدائم. هذا يؤكد ما في ملفك من أن التنفيذ الحقيقي يتم في Core.

[App Shortcuts](https://developer.apple.com/documentation/appintents/app-shortcuts)، [Siri AI preview](https://developer.apple.com/documentation/appintents/siri-ai-developer-preview)، [Live Activities](https://developer.apple.com/documentation/activitykit/displaying-live-data-with-live-activities)، [Long-running tasks](https://developer.apple.com/documentation/backgroundtasks/performing-long-running-tasks-on-ios-and-ipados).

### 6.8 Liquid Glass وFoundation Models

**Liquid Glass:** ينص دليل HIG صراحة على أن الزجاج **لطبقة التنقل والتحكم العائمة، وليس لطبقة المحتوى**، وهذا ما قرره ملفك. لذلك لا يُستخدم في فقاعات المحادثة ولا صفوف المهام.

```swift
Button("إرسال", systemImage: "arrow.up") { send() }
    .buttonStyle(.glass)

GlassEffectContainer {
    HStack { attachButton; micButton }
        .glassEffect(.regular.interactive(), in: .capsule)
}
```

**Foundation Models:** تضيف في iOS 27 نماذج AFM 3 وفهم الصور والوصول إلى Private Cloud Compute، وطول السياق متغير فاستعلم عن `contextSize` وقت التشغيل. لكن **دعم العربية غير مثبت** في قوائم Apple الحالية. يمكن استخدامها لمهام محلية صغيرة بالإنجليزية فقط، مثل تلخيص عنوان. وتبقى النواة هي العقل الأساسي.

[Applying Liquid Glass](https://developer.apple.com/documentation/swiftui/applying-liquid-glass-to-custom-views)، [HIG Materials](https://developer.apple.com/design/human-interface-guidelines/materials)، [Foundation Models languages](https://developer.apple.com/documentation/foundationmodels/supporting-languages-and-locales-with-foundation-models).

### 6.9 الكرة أو المشهد البصري

| الخيار | متى تختاره | ملاحظات |
|---|---|---|
| **Metal Shader داخل SwiftUI** (`.colorEffect` و`.layerEffect` و`ShaderLibrary`) | كرة متوهجة تتفاعل مع شدة الصوت، بأقل اعتماديات | الأخف وزنًا، ودون أي مكتبة خارجية |
| **RealityKit / RealityView + USDZ** | مجسّم ثلاثي الأبعاد حقيقي | يحتاج iOS 18، ولا يتطلب إذن الكاميرا |
| **Spline Native** (`.splineswift`) | مشهد مصمَّم في Spline | محرّك Metal أصلي يُوزَّع كـ XCFramework مغلق، ويحتاج اشتراك Pro للتصدير. **ترخيص المحرّك غير منشور**، فلا تجعله أساسًا إلزاميًا |
| **Rive** (الإصدار 6.29.0، MIT) | تحريك تفاعلي بآلة حالات | الإصدار الحالي أوقف الواجهة القديمة `RiveViewModel`. استخدم المسار Worker ثم File ثم Rive ثم `RiveUIViewRepresentable` |

كل الخيارات يجب أن تحترم `accessibilityReduceMotion`، وتتوقف حين تكون خارج الشاشة أو في الخلفية. ولا يجوز أن تكون الحركة المؤشر الوحيد على حالة التطبيق؛ أرفقها بنص وحالة VoiceOver. [WWDC24 Shaders](https://developer.apple.com/videos/play/wwdc2024/10151/)، [Spline iOS](https://docs.spline.design/exporting-your-scene/apple-platform/native-3d-embeds-for-i-os)، [Rive migration](https://rive.app/docs/runtimes/apple/migrating-from-legacy).

### 6.10 PageSpec: واجهات يحددها الخادم بأمان

أنسب طريقة هي شجرة مكوّنات `Codable` مميَّزة بالنوع، مع `schemaVersion` ومعرّفات ثابتة وقائمة مكوّنات مسموحة. تُفك وتُتحقق أولًا، ثم تُعرض عبر `switch` داخل `@ViewBuilder`. **لا WebView، ولا eval، ولا أسماء أصناف ديناميكية.** وتبقى شاشة الموافقة شاشة أصلية ثابتة لا يرسمها الخادم. هذا يتوافق مع البند 2.5.2 من إرشادات المراجعة.

```swift
enum PageComponent: Decodable, Identifiable {
    case text(TextBlock), markdown(MarkdownBlock), list(ListBlock),
         table(TableBlock), taskCard(TaskRef), sourceCard(SourceRef),
         unsupported(id: String)
    var id: String { /* ... */ "" }
}
```

ضع حدودًا لحجم المستند وعمق التداخل وعدد المكوّنات، واقصر الروابط على قائمة مسموحة. **DivKit** (Apache-2.0) بديل ناضج، لكنه مبني على UIKit وسطح أوامره أوسع مما تحتاجه.

---

## 7. حساب المطور والتوزيع وإرشادات المراجعة

**العضوية:**

- الاشتراك 99 دولارًا سنويًا، ويشمل TestFlight وApp Store Connect و25 ساعة شهريًا من Xcode Cloud.
- الحساب المجاني يصدر ملفات تعريف (provisioning profiles) صالحة 7 أيام فقط.
- في الحساب المدفوع تصل صلاحية ملف تعريف التطوير أو Ad Hoc إلى سنة **كحد أقصى**. العبرة بتاريخ الانتهاء المضمَّن في الملف، لا بتاريخ التثبيت.
- التثبيت المباشر من Xcode يتطلب تفعيل **Developer Mode** على جهاز iPhone، ولا يلزم ذلك مع TestFlight.
- الحد 100 جهاز مسجَّل لكل فئة أجهزة سنويًا.

[Compare memberships](https://developer.apple.com/support/compare-memberships/)، [TN3125](https://developer.apple.com/documentation/technotes/tn3125-inside-code-signing-provisioning-profiles)، [Developer Mode](https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device).

**TestFlight:**

- حتى 100 مختبِر داخلي دون مراجعة، وحتى 10,000 مختبِر خارجي بعد مراجعة أولى.
- صلاحية كل بناء 90 يومًا.
- البناء المخصص للاختبار الداخلي فقط لا يمكن تقديمه لاحقًا للاختبار الخارجي أو للمتجر.
- القيمة `ITSAppUsesNonExemptEncryption=false` تعني أن التطبيق لا يستخدم إلا تشفيرًا معفى (مثل HTTPS القياسي)، ولا تعني أنه بلا تشفير.

[TestFlight overview](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/).

**أنسب مسار لتطبيق شخصي:**

1. **التثبيت المباشر من Xcode** بفريقك المدفوع، وهو الأنسب لهدف «الاستخدام الشخصي أولًا».
2. **TestFlight الداخلي**، وهو مريح لكنه يحتاج بناءً جديدًا كل 90 يومًا. وميزة جانبية مهمة: إجراءات Siri AI التجريبية تعمل فيه.
3. خيارا **Unlisted** و**Custom Apps** يحتاجان مراجعة كاملة أو بنية مؤسسية، فلا داعي لهما الآن.

**إرشادات المراجعة ذات الصلة إن نشرت لاحقًا:**

- **5.1.2(i)**، وأُضيف في نوفمبر 2025: إفصاح صريح وإذن قبل مشاركة البيانات الشخصية مع ذكاء اصطناعي من طرف ثالث.
- **2.5.2:** منع تنزيل كود قابل للتنفيذ، وهذا ما يجعل تصميم PageSpec الآمن ضروريًا.
- **4.2:** الحد الأدنى من الوظائف.
- **5.1.1(v):** حذف الحساب، إن كان التطبيق يتيح إنشاء حسابات.
- ملف `PrivacyInfo.xcprivacy` وواجهات Required Reason.
- نصوص طلب الأذونات `NSMicrophoneUsageDescription` و`NSSpeechRecognitionUsageDescription` و`NSFaceIDUsageDescription`. نص إذن التعرف على الكلام مطلوب حتى مع التعرّف المحلي على الجهاز.
- **تقييم العمر:** هناك أسئلة جديدة (Shared Location وDating/Companions) تبدأ في 16 نوفمبر 2026، وتُستكمل لكل التطبيقات قبل 12 يناير 2027.

[App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)، [5.1.2(i) news](https://developer.apple.com/news/?id=ey6d8onl)، [Privacy manifests](https://developer.apple.com/documentation/bundleresources/privacy-manifest-files)، [Age rating update](https://developer.apple.com/news/?id=yxkh08us).

---

## 8. نموذج تعليمات للوكيل (AGENTS.md) مقترح للمشروع

هذا مثال للعرض فقط، يجمع أفضل الممارسات أعلاه في قواعد مختصرة يمكن التحقق منها. يُفضَّل أن يبقى أقل من 200 سطر، وأن يحتوي أوامر البناء والاختبار الفعلية.

```markdown
# AGENTS.md — Personal Agent iPhone App
## Platform
- SwiftUI only, iOS 26+ deployment target, Swift 6 language mode, strict concurrency complete,
  default actor isolation MainActor, approachable concurrency ON. No UIKit unless bridging is required.
- No WebView, no React Native/Expo, no eval, no remote code. PageSpec renders only allowlisted native components.
## Architecture
- Feature folders: App/, Design/, Features/{Chat,Spaces,Activity,Settings}/, Infrastructure/{CoreAPI,Contracts,Security,Persistence,Connectivity}/.
- @MainActor @Observable feature models; services injected via Sendable protocols; no singletons.
- CoreAPI is generated from Contracts/openapi.yaml (swift-openapi-generator). Never hand-edit generated code.
- DEMO data only through DemoCoreClient behind the same protocol; UI must label DEMO/OFFLINE/STALE.
## Truth rules
- Task status only from Core (CoreTaskStatus enum). 202 != COMPLETED. Unknown write outcome => OUTCOME_UNKNOWN, never auto-retry.
- Every write uses a persisted idempotency key.
## Security
- Session token: Keychain, WhenUnlockedThisDeviceOnly, non-synchronizable. Never UserDefaults/SwiftData/logs.
- Approvals: SecureEnclave.P256 key with SecAccessControl(.privateKeyUsage + biometry); sign canonical envelope from contract.
- No provider API keys in the app.
## UI
- SF Symbols with accessibility labels; Dynamic Type; leading/trailing only; RTL + LTR previews for every screen.
- Liquid Glass for navigation/controls only, never for content cards or bubbles. Respect Reduce Motion.
## Verify before claiming done
- Build: xcodebuild -scheme App -destination 'platform=iOS Simulator,name=<installed iPhone simulator>' build
- Test: xcodebuild test ... (Swift Testing for unit/integration, XCTest for UI)
- Lint: swiftlint lint --strict
- Use Apple docs (Xcode MCP / sosumi) to confirm any API newer than your training data.
```

---

## 9. الحزمة النهائية المقترحة (ملخص القرار)

| الطبقة | الاختيار الموصى به | البديل |
|---|---|---|
| بيئة العمل | Xcode 27.2 على جهاز Mac بمعالج Apple Silicon، ومشروع Xcode عادي في Git | XcodeGen إن كثرت الأهداف |
| وكيل البرمجة | وكيل Xcode المدمج، أو Claude Code أو Codex عبر `xcrun mcpbridge` | Cursor مع SweetPad |
| أدوات الوكيل | MobileBuildMCP مع Sosumi | ios-simulator-mcp وxdocs |
| المهارات | swiftui-pro، swift-concurrency، swift-testing-pro، swift-security-expert، مهارات Dimillian | Axiom كحزمة شاملة |
| المعمارية | `@Observable` مع حقن البروتوكولات والـ actors | TCA |
| الشبكة | Swift OpenAPI Generator مع SSE واللقطات الدورية | URLSession يدوي |
| الأمان | CryptoKit Secure Enclave مع Keychain عبر Valet أو غلاف صغير خاص، وTailscale Serve | App Attest كطبقة إضافية |
| التخزين | SwiftData للكاش والمسودات | GRDB مع FTS5 |
| عرض Markdown | Textual | MarkdownUI |
| الصوت | الضغط للتحدث مع التعرّف في Core، وSpeechAnalyzer إن ثبت دعمه للعربية | LiveKit للمحادثة الفورية |
| المشهد البصري | Metal Shader | RealityKit أو Rive أو Spline |
| الجودة | Swift Testing وXCUITest وSwiftLint وInstruments | Periphery Pro |
| التوزيع | التثبيت من Xcode ثم TestFlight الداخلي | Xcode Cloud أو asc CLI أو fastlane |
| توليد الواجهة (اختياري) | Rork Pro أو Bitrig كمسودة SwiftUI فقط | Vibecode Pro |

---

## 10. نقاط لم يمكن التحقق منها نهائيًا

- دعم SpeechTranscriber للعربية بلهجاتها، وجودة التعرّف عند خلط العربية بالإنجليزية، على جهازك وإصدار نظامك تحديدًا. يجب فحصه وقت التشغيل.
- دعم Foundation Models للعربية، وأهلية تطبيق شخصي للوصول المجاني إلى Private Cloud Compute.
- القائمة الكاملة الحالية للأصوات العربية في AVSpeechSynthesizer على iOS 27.
- شروط ترخيص محرّك Spline لإعادة التوزيع.
- إمكانية تنزيل مشروع Xcode كامل من iSwift.dev.
- رقم إصدار Swift الدقيق المضمَّن داخل Xcode 27.2.

أرقام النجوم والإصدارات مأخوذة بتاريخ 8 نوفمبر 2026، وتتغير باستمرار.