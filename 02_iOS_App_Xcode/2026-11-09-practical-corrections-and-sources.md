# تصحيح عملي للمراجعات السابقة — 9 نوفمبر 2026

هذه إضافة بحثية **جديدة** على الأرشيف الموجود، وليست إعادة ضغط أو إعادة تسمية له. لم يُجر تعديل على مستودع iPhone لأنه غير موجود في هذه الجلسة، ولم يُنشأ تطبيق أو يُختبر Xcode. أُبقيت كافة الاختيارات التقنية المذكورة في أبحاثك للمقارنة، وليس بصفتها التزامات على المشروع.

## 1) ما نُفذ فعلياً

1. فُحص سجل الروابط الـ753 السابق؛ اتضح أن B=585 وT=120 وX=48 **حالات استخراج آلي وليست شهادات صحة**.
2. أُعيدت مراجعة **ادعاءات محددة** من 14 مصدرًا مباشرًا: 10 روابط مدرجة ضمن القائمة الأصلية و4 مراجع جديدة. القائمة الكاملة ومصدر كل ادعاء في `Verification/DIRECTLY_CHECKED_SOURCES.csv`.
3. صُحح مثال `SSEParser.swift` في ملف جديد `Code/SSEParser_Fixed.swift`، وثُبت عيبان في النسخة القديمة بإعادة تشغيلها. النسخة الجديدة نجحت في 23 اختبارًا على Swift 6.2.1/Linux؛ النتائج الخام محفوظة.
4. أُضيف مثال بحث عربي يميز بين التطبيع المتطابق NFC وبين فهرس بحث متسامح اختياري. نجح في 7 اختبارات على Linux.
5. صُحح السجل الأصلي في `Verification/753_URLS_CORRECTED_EVIDENCE_LEDGER.csv` دون حذف الروابط الـ753 أو تحويل محاولات الوصول إلى تحقق زائف.

**حدود هذا العمل:** تم إثبات صحة سلوك النماذج البرمجية المحمولة في Linux؛ لم يُثبت نجاحها داخل iOS SDK أو توافقها مع العقد الحقيقي أو أمن التطبيق الفعلي. وقد روجع من الوثائق فقط الادعاء المذكور بجانب كل رابط، وليس جميع محتويات الصفحة.

## 2) أخطاء واضحة في المخرجات السابقة وتصحيحها

| الخطأ السابق | التصحيح المثبت | المصدر / الإجراء |
|---|---|---|
| تقديم روابط الـ753 كأنها مراجع راجَعنا محتواها تفصيليًا | عدد الروابط التي أُعيد التحقق من ادعاء محدد فيها الآن هو **10 من الـ753**؛ و**743** مدخلًا آخر ليس له تحقق تفصيلي جديد في هذه الجلسة. سجل B/T/X لا يساوي تحققًا | `Verification/753_URLS_CORRECTED_EVIDENCE_LEDGER.csv` |
| ترك رقم Swift patch داخل Xcode 27.2 غير محسوم | إعلان Swift الرسمي الصادر 30 أكتوبر يذكر بوضوح أن Xcode 27.2 يتضمن **Swift 6.4.2** | [Swift Forums](https://forums.swift.org/t/announcing-swift-6-4-2/90337) |
| الإيحاء بأن Claude Code يمكن الاعتماد عليه في قراءة AGENTS.md مباشرة دون ملف وسيط | الوثائق الحالية تشرح استخدام `CLAUDE.md` وفيه `@AGENTS.md`، مع التأكد باستخدام `/context` | [Claude Code Memory](https://code.claude.com/docs/en/memory) |
| وصف محلل SSE القديم بأنه اختُبر دون إبراز محدوديته | النسخة القديمة فشلت في **CR-only** واستوعبت 1000 سطر `data:` متراكمًا بلا حد لحجم الحدث. النسخة الجديدة تختبر CR/CRLF/LF وحجم الحدث والـBOM والأحرف العربية والـID | [WHATWG SSE](https://html.spec.whatwg.org/multipage/server-sent-events.html#parsing-an-event-stream) + ملفات الاختبار |
| عدم تمييز أسلوب فهرسة العربية عن التطبيع النصي | NFC معيار احتفاظ؛ إسقاط الحركات ومد الألف وتوحيد الهمزات اختيار **بحث متسامح** قد ينتج تطابقات أوسع، فكل منهما حقل مستقل | [GRDB Full Text Search](https://github.com/groue/GRDB.swift/blob/master/Documentation/FullTextSearch.md) + اختبارات محمولة |
| إيراد أدوات وكيل Xcode من غير خطوات فحص تكوين واضحة | توثيق Apple يعطي مفتاح الإذن وأوامر `mcpbridge` وفحص `claude mcp list` و`codex mcp list` | [Apple Xcode MCP](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) |
| نقل اسم الأداة القديمة XcodeBuildMCP كأنه لم يتغير | وثائق الأداة الحالية تستخدم **MobileBuildMCP** وتضيف `mobilebuildmcp-doctor` لتشخيص البيئة | [MobileBuildMCP Installation](https://www.mobilebuildmcp.com/docs/installation) |

## 3) إجراءات عملية مستخرجة مباشرة من المراجع

### أولًا: بيئة البناء والتحقق (على Mac فقط)

```bash
xcodebuild -version
xcrun simctl list devices available
xcodebuild -list -project YOUR_APP.xcodeproj

# عند استخدام جسر Apple الرسمي لوكيل يعمل خارج Xcode:
claude mcp add --transport stdio xcode -- xcrun mcpbridge
claude mcp list
# أو بديلًا:
codex mcp add xcode -- xcrun mcpbridge
codex mcp list

# عند استخدام MobileBuildMCP:
brew tap getsentry/xcodebuildmcp
brew install mobilebuildmcp
mobilebuildmcp-doctor
```

قبل `mcpbridge` افتح المشروع في Xcode ثم فعّل: `Xcode > Settings > Intelligence > Model Context Protocol > Allow external agents to use Xcode tools`. **لم تُشغّل هذه الأوامر هنا** لعدم وجود macOS/Xcode في بيئة التشغيل.

المصادر: [Apple Xcode](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode)، [MobileBuildMCP](https://www.mobilebuildmcp.com/docs/installation).

### ثانيًا: مسار الواجهة والتصميم

- **ملفات التصميم الأصلية:** صفحة Apple Design Resources تنشر **iOS 27 UI Kit** لكل من Figma وSketch، إضافة لقوالب الأيقونات. يمكن الاستفادة من حالات المكونات والمرونة في إعادة التحجيم. **لم أنقل ملفات Figma/Sketch نفسها ولم أزعم استخراج طبقاتها.** [Apple Design Resources](https://developer.apple.com/design/resources/).
- **SwiftUI Liquid Glass:** الوثائق تشرح `glassEffect`, `GlassEffectContainer`, `glassEffectID` و`interactive`. وتذكر أن كثرة الحاويات والمؤثرات قد تضر الأداء. استخرجت منها طريقة التطبيق وأسباب القياس، لا مجرد أسماء المكونات. [Apple Glass](https://developer.apple.com/documentation/swiftui/applying-liquid-glass-to-custom-views).
- **العربية وRTL:** مكونات النظام تتكيف مع الاتجاه افتراضيًا، بينما تحتاج التخطيطات المخصصة والنصوص المختلطة مراجعة. [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/right-to-left).
- **الترجمة:** أنشئ `Localizable.xcstrings` في Xcode؛ البناء يلتقط النصوص القابلة للترجمة، وبعدها أضف صيغ الجمع والمتغيرات حسب الجهاز عند الحاجة. [Apple String Catalog](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog).

### ثالثًا: عميل API والتواصل الخاص

- **OpenAPI:** أداة Apple `swift-openapi-generator` تولّد عميل Swift عند البناء من عقد OpenAPI، بحيث لا يلزم حفظ الكود المُولّد بالمستودع؛ هذا مسار متاح، ولا يلغي البدائل اليدوية. [Swift OpenAPI Generator](https://github.com/apple/swift-openapi-generator).
- **SSE:** تنص المواصفة على القراءة من UTF-8، وإرسال حدث فقط عند السطر الفارغ، والاستمرار في قيمة `Last-Event-ID`، وقراءة `retry` كأرقام ASCII فقط. الإصلاح الحالي اختُبر مع التقطيع عبر البايتات. [WHATWG](https://html.spec.whatwg.org/multipage/server-sent-events.html).
- **Tailscale Serve:** يتيح الوصول لخدمة محلية داخل tailnet، وتتطلب ميزته تمكين شهادة HTTPS، مع خضوع الوصول لسياسات الشبكة. **Serve ليس Funnel العام**. [Tailscale](https://tailscale.com/docs/features/tailscale-serve).
- **المفاتيح الحيوية:** توفر Apple أعلام `biometryCurrentSet` و`privateKeyUsage` مع معانٍ مختلفة. **لم تُختبر Secure Enclave على جهاز فعلي هنا.** [Apple Security](https://developer.apple.com/documentation/security/secaccesscontrolcreateflags).

## 4) أكواد مصححة تم اختبارها فعلًا

### A. SSEParser_Fixed.swift

تستقبل `append(bytes: Data)`، وتتجنب فقدان محارف UTF-8 العربية عندما يُقسّم البث بين البايتات. تتعامل مع CR/LF/CRLF؛ وتحتفظ بـID آخر **حدث مُرسل** عند الانقطاع، وتمنع تراكم حدث بلا حد. **ليست عميل SSE شبكيًا كاملًا**: التحقق من Content-Type، وإعادة الاتصال، والتوثيق، والتنقل الخلفي مسؤوليات طبقة الشبكة؛ وليست بديلًا عن OpenAPI إن كان يولد SSE مطابقًا لعقدك.

```bash
swiftc -swift-version 6 -o sse_tests Code/SSEParser_Fixed.swift Code/SSEParser_Tests.swift
./sse_tests
# نتيجة التنفيذ: 23 PASS, 0 FAIL (Swift 6.2.1 on Linux)
```

### B. ArabicSearchKeys.swift

`canonical` تحفظ التطبيع NFC (مناسب لمطابقة النصوص المكافئة)، بينما `forgiving` توسع البحث اختياريًا بحذف الحركات والتطويل وطي بعض أشكال الألف. **لا تستخدم النسخة المتسامحة بدل نص العرض الأصلي أو لتوقيع الرسائل**، ولا تفترض أنها إعداد GRDB الافتراضي.

```bash
swiftc -swift-version 6 -o arabic_tests Code/ArabicSearchKeys.swift Code/ArabicSearchKeys_Tests.swift
./arabic_tests
# نتيجة التنفيذ: 7 PASS, 0 FAIL (Swift 6.2.1 on Linux)
```

## 5) خطوات مراجعة المصادر التي أصبحت قابلة للتدقيق

- افتح `Verification/DIRECTLY_CHECKED_SOURCES.csv` لترى المصدر المحدد والادعاء الذي دعمه والإجراء القابل للتطبيق.
- افتح `Verification/753_URLS_CORRECTED_EVIDENCE_LEDGER.csv` لتجد **كل الروابط الـ753**، مع فصل حالة وصول سابقة `B/T/X` عن خانة تحقق ادعاء محدد في الجلسة الحالية `YES/NO`.
- المدخلات غير المراجعة بعمق لم تُحذف، ولم يُعتبر ظهور أي رابط في أرشيف أو مستودع إثباتًا لجودته أو ملاءمته.

## 6) ما لا يصح أن أدّعيه

- لم أقرأ جميع الروابط الـ753 قراءة تقنية تفصيلية؛ ما نُفذ حاليًا هو فحص 14 مصدرًا في ادعاءات محددة وكتابة/اختبار نموذجين.
- لم أختبر Xcode 27.2 أو SwiftUI / Keychain / Secure Enclave أو Tailscale على جهاز iPhone؛ بيئة التشغيل هنا Linux.
- لم أجرب ربط خدمة Core حقيقية ولا أشغّل AppKit/UIKit/iOS SDK؛ لا يوجد مستودع تطبيق حالي في الملفات المُراجعة.
- إصلاح SSE صالح كنموذج قابل للبناء واختبار الوحدة على Swift/Linux وليس كإثبات توافق كامل مع كل خوادم الشبكة أو الأداء تحت الضغط.