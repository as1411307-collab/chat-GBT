# إضافات AGENTS.md الجديدة إلى مكتبة أبحاث iPhone

هذه الحزمة تستخرج ما أضافه PDF الجديد وقالب ZIP إلى الأبحاث السابقة، مع التفريق بين الجديد، والموجود سابقًا بمزيد من التفصيل، والمكرر، والادعاءات المتعارضة.

**ابدأ بقراءة:** `01_UNIQUE_ADDITIONS_AR.md`؛ ثم `02_CODE_AND_COMMANDS_AR.md`، ثم `03_REFERENCES_AND_VERIFICATION.md`.

**المحتويات:**

1. `01_UNIQUE_ADDITIONS_AR.md` — مواضع الإضافة والتشابه والتعارض، مع رقم الصفحة واسم الملف.
2. `02_CODE_AND_COMMANDS_AR.md` — مقتطفات البرامج والإعدادات والأوامر.
3. `03_REFERENCES_AND_VERIFICATION.md` — جميع الروابط الـ16 وحالة المراجعة الفعلية.
4. `04_LOCAL_CHECKS.md` و`LOCAL_AUDIT.json` — فحوص محلية وحدودها.
5. `template_files/` — جميع الملفات الثمانية في الـZIP محفوظة حرفيًا.
6. `AGENTS_md_Guide_Customization_original.pdf` و`agents_md_template_original.zip` — نسختا المصدر الأصليتان دون تغيير.
7. `PDF_Extract_By_Page.md` — تفريغ كامل لنص الدليل بحسب الصفحة، مع التنبيه إلى احتمال اختلاط اتجاه العربية في الاستخراج.
8. `previous_research_AGENTS_template.md` و`previous_753_AGENTS_template.md` — النموذجان السابقان.
9. `DIFF_research_TO_NEW.patch` و`DIFF_753_TO_NEW.patch` — الفروق النصية المباشرة.
10. `FILE_INVENTORY.csv` — أسماء ملفات القالب وحجم كل ملف وبصمته SHA-256.

**لم يُحذف من أصول المستخدم شيء.** لم تُدمج هذه المواد في مستودع أو تُفعَّل كتوجيهات. أي قيد مدون في القالب هو جزء من المرفق المصدر، وليس اختيارًا جديدًا من المستخدم.


---

# التفاصيل الإضافية غير المتكررة — AGENTS.md وتخصيص وكلاء بناء iPhone

**التاريخ:** 9 نوفمبر 2026  
**المواد:** `AGENTS_md_Guide_Customization_2026.pdf` (13 صفحة)، و`agents_md_template.zip` (8 ملفات فعلية)، مقارنةً بالقالبين السابقين والأبحاث الموسعة المحفوظة.  
**الهدف:** حفظ المعلومات وتنظيم الفرق، وليس فرض قيود أو اختيارات على مشروع المستخدم. كل الأصول موجودة حرفيًا في الحزمة.

## أولًا: إضافات فعلية أو تفاصيل تنفيذية أعمق

| # | الإضافة | الاستخراج العملي | الموضع |
|---|---|---|---|
| 1 | حزمة تشغيل وكلاء متعددة | توجد ملفات تعليمات مشتركة في الجذر، وتوجيه Claude للاستيراد، وتعليمات مركّزة لأمان التطبيق ولتوليد الـAPI. | الدليل ص2، ص5، ص10–13؛ ZIP |
| 2 | استيراد Claude دون نسخ المحتوى | يحتوي `CLAUDE.md` على `@AGENTS.md` ثم توجيه خاص بـClaude. الملفان الفرعيان يستوردان ملف `AGENTS.md` المحلي بنفس الطريقة. | الدليل ص1، ص2؛ ملفات CLAUDE الثلاثة |
| 3 | Codex يقرأ حسب دليل التشغيل | يبدأ البحث من الجذر حتى مجلد العمل الحالي؛ تشغيله من الجذر لا يضمن قراءة تعليمات المجلدات الأدنى، لذا يذكر الملف الجذري صراحة الرجوع إليها. | الدليل ص1، ص5 |
| 4 | تفضيل ملفات override | توضيح `AGENTS.override.md`، الحد الافتراضي الكلي 32 KiB، وإمكانية تعديله بـ`project_doc_max_bytes`. أصل الفكرة سبق، والتطبيق الإجرائي موضح هنا. | الدليل ص1، ص2 |
| 5 | فحص اكتشاف التعليمات داخل Xcode | خطوة اختبار مؤقتة: أضف توجيهًا متعمدًا مميزًا مثل بادئة `ABC` لاسم نوع جديد، واطلب من وكيل Xcode تنفيذه، ثم أزل التوجيه. | الدليل ص2، ص8 |
| 6 | حماية التعديلات عبر إعدادات Claude | ملف `.claude/settings.json` يحوي **6 أنماط طلب موافقة** على تعديل entitlements وInfo.plist وPrivacyInfo.xcprivacy وOpenAPI وملفات التعليمات نفسها. | الدليل ص6؛ ZIP |
| 7 | ضعف الحماية النصية وحدها | ملفات التعليمات لا تمنع جميع العمليات فعليًا؛ `Edit` و`Read` لا يغطيان بالضرورة سكربتًا آخر يكتب مباشرة إلى الملفات، لذلك تُذكر الاختبارات والعزل والـCI كطبقات منفصلة. | الدليل ص6 |
| 8 | SwiftLint: Keychain | ملف `.swiftlint.yml` يضيف `no_weak_keychain_accessibility` لمنع صيغ مثل `AfterFirstUnlock` أو `Always`. | الدليل ص7؛ ZIP |
| 9 | SwiftLint: السجلات | `no_print` يلتقط `print(...)` مع استثناء ملفات الاختبارات عبر نمط مسارات. | الدليل ص7؛ ZIP |
| 10 | SwiftLint: واجهة التنقل القديمة | `no_navigation_view` يحذر من `NavigationView` ويقترح `NavigationStack`. | الدليل ص7؛ ZIP |
| 11 | ملف أمان مختص | `Infrastructure/Security/AGENTS.md`: فصل حالات `errSecItemNotFound` و`errSecInteractionNotAllowed`، أثر إلغاء تثبيت التطبيق على Keychain، حفظ `dataRepresentation`، وإعادة الاقتران إذا بطل مفتاح القياسات الحيوية. | الدليل ص5، ص12؛ ZIP |
| 12 | ملف عقد API مختص | `CoreAPIKit/AGENTS.md`: تهيئة `generate: [types, client]` و`accessModifier: internal`، وتثبيت حزم Swift OpenAPI المتوافقة، ومنع تسريب الأنواع المولّدة إلى واجهة التطبيق. | الدليل ص5، ص13؛ ZIP |
| 13 | حالة HTTP غير منصوص عليها | تعليمة لتحويل `.undocumented(status, _)` إلى `CoreError.undocumented(status)`، بدل تجاهل الحالة أو اعتبارها نجاحًا. | الدليل ص13 |
| 14 | فحص كسر عقد الـAPI | تمرير تغييرات العقد على `oasdiff` داخل CI، مع عدم تعديل النسخة الموجودة في عميل iPhone بمعزل عن Core. | الدليل ص5، ص13 |
| 15 | مراجعة الحقول المؤقتة | يورد الدليل أوامر `grep` لاكتشاف الحقول `<...>`، و`wc -l -c` لمقارنة طول الملفات، مع استخراج Scheme وUDID الفعليين. | الدليل ص8 |
| 16 | الاختبار السلوكي للتوجيه | اقتراحان تحققيان: محاولة دفع الوكيل لتخزين session token في UserDefaults، وطلب API أحدث من هدف النشر؛ المتوقع كشف التعارض قبل التنفيذ. | الدليل ص8 |
| 17 | فحص تحميل ذاكرة الوكيل | `codex --ask-for-approval never "Summarize the current instructions."`، وفي Claude عبر `/memory` و`/context` وفق نسخة الأداة. | الدليل ص8 |
| 18 | السجل التنفيذي المصاحب | أمر اختبار بنتائج `.xcresult` جديدة في كل تشغيل، وفصل ما اختُبر على المحاكي عما لم يُختبر إلا على الجهاز. | الدليل ص3، ص8؛ AGENTS.md |

## ثانيًا: معلومات موجودة سابقًا لكنها محفوظة في القالب الجديد بتفصيل جديد

هذه **ليست مستبعدة**، لكنها لا تُحتسب اكتشافات جديدة لمجرد إعادة صياغتها:

- iPhone أصلي بـSwiftUI، ولغة عربية RTL، وتبويبات Chat / Spaces / Activity مع Settings كورقة.
- فكرة عميل خفيف ونواة Core منفصلة، مع `CoreAPI` ونسختي REAL وDEMO والتعامل مع OFFLINE.
- Swift 6 وعزل MainActor، وبروتوكولات Sendable، واستخدام SwiftData للكاش والمسودات.
- `openapi.yaml` وSwift OpenAPI Generator وidempotency و`OUTCOME_UNKNOWN`.
- Keychain لحماية الجلسة وSecure Enclave P-256 لتوقيع الموافقات، وTailscale Serve للاتصال الخاص.
- العربية والإتاحة، Dynamic Type وLiquid Glass وSF Symbols.
- Swift Testing وXCTest/XCUIAutomation، ومراجعة النتائج على جهاز حقيقي.

## ثالثًا: تضارب بين النص والتوثيق العام — مع الحفاظ على الاثنين

**قراءة Claude Code لملف AGENTS.md مباشرة:** الصفحة الأولى من الـPDF تقول إن Claude Code منذ إصدار معين يقرأ AGENTS.md كبديل عند غياب CLAUDE.md. التوثيق الرسمي الذي فُتح بتاريخ هذه المقارنة يقول صراحة إن Claude Code يقرأ `CLAUDE.md`، وليس `AGENTS.md`، ويقترح تضمين `@AGENTS.md`. لذا أبقيت النص الأصلي ووصفت هذه النقطة بأنها **بحاجة إلى تأكيد عملي بحسب إصدار العميل المستخدم**، دون حذف الادعاء التاريخي.

**توجيه تعليمات الملف:** القالب يقول إن تعليماته تتقدم على المهارات، لكن الوثائق توضح أن ملفات التعليمات سياق يُعطى للوكيل وليست آلية منع شاملة. وهذا لا يعني اعتماد القيود المكتوبة فيه من المستخدم تلقائيًا.

## رابعًا: ما يحتاج ملء أو قرار قبل استخدام القالب في مشروع حقيقي

- الاسم: `<AppName>`، واسم المالك: `<name>`، والتاريخ: `<YYYY-MM-DD>`.
- المشروع والمخطط ومعرّف المحاكي: `<App>`، `<UDID>`، `<fresh-dir>`.
- عناصر الأمان: `<bundle-id>`، `<account>`، ومرجع `<docs/signing-protocol.md>` (اسم/مسار مؤقت).
- لا يوجد مشروع Xcode مُعتمد في هذه الحزمة. العبارات التي تبدأ بـ`Never` أو `Ask first` تعليمات موجودة في القالب المصدر، وليست قرارات جديدة صادرة عن المستخدم.

## خامسًا: مواد المصدر دون فقد

1. `AGENTS_md_Guide_Customization_original.pdf` — نسخة المستخدم كاملة.
2. `agents_md_template_original.zip` — القالب الأصلي كاملًا.
3. `template_files/` — جميع الملفات الثمانية مفكوكة بمساراتها الحقيقية، مع الملفات المخفية.
4. `previous_research_AGENTS_template.md` و`previous_753_AGENTS_template.md` — النموذجان السابقان للمقارنة.
5. ملفا `DIFF_*.patch` — فرق الأسطر الفعلي، وليس تقرير التشابه الدلالي وحده.


---

# الأكواد والتعليمات التنفيذية — مقتطفات منتقاة من المواد الجديدة

**المصدر:** دليل AGENTS.md، الصفحات 6–8 و12–13، والملفات الأصلية في `template_files/`. جميع المحتويات كما وردت محفوظة في الملفات الأصلية؛ هنا أمثلة نافعة دون التكرار الطويل.

## 1) استيراد التعليمات المشتركة في Claude Code

**`CLAUDE.md`**:

```md
@AGENTS.md

## Claude Code
- Use plan mode for security, contract and cross-layer changes, then wait for approval.
```

أما `Infrastructure/Security/CLAUDE.md` و`CoreAPIKit/CLAUDE.md` فيحتوي كل منهما `@AGENTS.md` داخل مجلده.

## 2) تصفية الملفات التي تتطلب موافقة مسبقة

مقتطف من `.claude/settings.json` (الملف الأصلي داخل ZIP):

```json
{
  "permissions": {
    "ask": [
      "Edit(/**/*.entitlements)",
      "Edit(/**/Info.plist)",
      "Edit(/**/PrivacyInfo.xcprivacy)",
      "Edit(/CoreAPIKit/**/openapi.yaml)",
      "Edit(/AGENTS.md)",
      "Edit(/CLAUDE.md)"
    ]
  }
}
```

**حد عملي:** هذه آلية سؤال ضمن الأداة، وليست ضمانًا شاملًا ضد برامج خارجية تكتب الملفات مباشرة.

## 3) SwiftLint المخصص

ثلاثة أسماء فحوص موجودة كاملة داخل `.swiftlint.yml`: `no_weak_keychain_accessibility`، و`no_print`، و`no_navigation_view`. أمثلة من تعابيرها:

```yaml
custom_rules:
  no_weak_keychain_accessibility:
    regex: "kSecAttrAccessible(Always|AfterFirstUnlock)(ThisDeviceOnly)?\\b"
    severity: error
  no_print:
    regex: "^[ \\t]*print\\("
    excluded:
      - ".*Tests?\\.swift"
    severity: error
  no_navigation_view:
    regex: "\\bNavigationView\\b"
    match_kinds:
      - identifier
    severity: error
```

يظل ملف SwiftLint الأصلي المرجع للرسائل الكاملة والتكوين. فحوص regex نجحت في اختبار محلي بلغة Python فقط؛ لا يوجد ادعاء تشغيل SwiftLint نفسه.

## 4) إنشاء ملف API مولّد دون كشف الأنواع

من `CoreAPIKit/AGENTS.md`:

```yaml
generate: [types, client]
accessModifier: internal
```

**ملاحظة:** هذه هي القيم المذكورة لوثيقة الإعداد `openapi-generator-config.yaml`؛ الملف التنفيذي نفسه **غير موجود** ضمن ZIP الجديد. توجد تعليمات لاختبار حالات الاستجابات غير الموثقة وفحص `oasdiff` في CI.

## 5) اكتشاف المشروع والتحقق من تحميل التعليمات

```bash
grep -rn "<[A-Za-z]" AGENTS.md CLAUDE.md */AGENTS.md */*/AGENTS.md
xcodebuild -list -project <App>.xcodeproj
xcrun simctl list devices available
wc -l -c AGENTS.md */AGENTS.md */*/AGENTS.md
codex --ask-for-approval never "Summarize the current instructions."
```

أمر `grep` يستخرج الحقول المعلّمة بالزاويتين، لكنه قد يلتقط وسوم Markdown أخرى؛ راجع مخرجاته. `xcodebuild` **مثال غير قابل للتشغيل بصيغته الحالية** حتى يُملأ اسم مشروع حقيقي.

## 6) سلوكيات الأمان في الملف المختص

- استخدام `actor` صريح لنداءات `SecItem*`؛ لا تمرير رمز الجلسة إلى `UserDefaults`.
- `errSecItemNotFound`: العنصر غير موجود. `errSecInteractionNotAllowed`: تعذر تفاعل Keychain عادةً بسبب القفل، لا تخزين بديل.
- الحفاظ على بيانات `SecureEnclave.P256.Signing.PrivateKey` الممثلة بـ`dataRepresentation`، وإعادة الاقتران عند إبطال المفتاح.
- عزل `ApprovalSigner` خلف بروتوكول قابل للاستبدال في الاختبارات.

## 7) الأكواد المحفوظة دون تعديل

- `template_files/AGENTS.md`
- `template_files/CLAUDE.md`
- `template_files/Infrastructure/Security/AGENTS.md`
- `template_files/Infrastructure/Security/CLAUDE.md`
- `template_files/CoreAPIKit/AGENTS.md`
- `template_files/CoreAPIKit/CLAUDE.md`
- `template_files/.claude/settings.json`
- `template_files/.swiftlint.yml`

هذه مواد توجيه وضبط مشروع؛ ليست مشروع تطبيق أو مكتبات مثبتة.


---

# سجل المصادر والتحقق — دليل AGENTS.md

**المصدر الأصلي:** صفحة 13 من ملف `AGENTS_md_Guide_Customization_2026.pdf`. أدرجت جميع المراجع الستة عشر كما وردت فيه. عبارة «فُتح» تعني مراجعة الصفحة أو قسمها ذي الصلة، لا اختبار التطبيق أو الماك.

| # | الموضوع | الرابط | فُتح في هذه الجلسة؟ |
|---|---|---|---|
| 1 | OpenAI Codex — ملفات AGENTS.md | https://developers.openai.com/codex/guides/agents-md | نعم |
| 2 | Claude Code — ذاكرة المشروع | https://code.claude.com/docs/en/memory | نعم |
| 3 | صيغة AGENTS.md | https://agents.md/ | لا، محفوظ من المصدر |
| 4 | وصول الوكلاء الخارجيين لأدوات Xcode | https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode | لا، محفوظ من المصدر |
| 5 | توسيع وتخصيص وكلاء Xcode | https://developer.apple.com/documentation/xcode/extending-and-customizing-agents | لا، محفوظ من المصدر |
| 6 | تعليمات مهارات Xcode | https://www.hackingwithswift.com/articles/283/how-to-install-and-use-ai-agent-skills-in-xcode | لا، محفوظ من المصدر |
| 7 | SwiftAgents | https://github.com/twostraws/swiftagents | لا، محفوظ من المصدر |
| 8 | صلاحيات Claude Code | https://code.claude.com/docs/en/permissions | نعم |
| 9 | SwiftLint والضوابط المخصصة | https://github.com/realm/SwiftLint | نعم |
| 10 | أفضل ممارسات Claude Code | https://code.claude.com/docs/en/best-practices | لا، محفوظ من المصدر |
| 11 | Swift SE-0466 | https://github.com/swiftlang/swift-evolution/blob/main/proposals/0466-control-default-actor-isolation.md | لا، محفوظ من المصدر |
| 12 | الوصول إلى عناصر Keychain | https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility | لا، محفوظ من المصدر |
| 13 | biometryCurrentSet | https://developer.apple.com/documentation/security/secaccesscontrolcreateflags/biometrycurrentset | لا، محفوظ من المصدر |
| 14 | تجربة Xcode 26.3 | https://swiftjectivec.com/Agentic-Coding-Codex-Claude-Code-in-Xcode/ | لا، محفوظ من المصدر |
| 15 | سجلات Apple Logging | https://developer.apple.com/documentation/os/generating-log-messages-from-your-code | لا، محفوظ من المصدر |
| 16 | إرشادات SF Symbols | https://developer.apple.com/design/human-interface-guidelines/sf-symbols | لا، محفوظ من المصدر |

## نقاط مدعومة مباشرة بالمراجع التي فُتحت

**Codex:** ملف `AGENTS.override.md` له أولوية داخل المجلد، ويجري جمع الملفات من الجذر إلى مكان التشغيل، بحد افتراضي `32 KiB`. المرجع: [وثائق Codex](https://developers.openai.com/codex/guides/agents-md).

**Claude Code:** تشير صفحة الذاكرة التي فُتحت إلى قراءة `CLAUDE.md` واستيراد `@AGENTS.md` عند الرغبة في مشاركة التعليمات، وليس إلى الاعتماد الافتراضي على AGENTS.md وحده. هذه صياغة مختلفة عما ورد في الصفحة الأولى من PDF، لذا حفظت الاختلاف دون إزالة أي منهما. المرجع: [وثائق Claude memory](https://code.claude.com/docs/en/memory).

**صلاحيات Claude:** أنماط `Edit(path)` تعترض أدوات تحرير معينة، لكن لا تمنع تلقائيًا كل سكربت خارجي يفتح ملفات، والعزل على مستوى النظام منفصل. المرجع: [وثائق Claude permissions](https://code.claude.com/docs/en/permissions).

**SwiftLint:** الوثائق الرسمية تعرض `custom_rules` و`regex` و`match_kinds` و`excluded`، وهو نفس شكل الضبط الموجود في ZIP. **لم أشغّل برنامج SwiftLint نفسه** في هذه الجلسة. المرجع: [مستودع SwiftLint](https://github.com/realm/SwiftLint).

## حدود التحقق

- عدد المصادر الجديدة بالمرفق: **16**؛ فُتحت **4** صفحات/مراجع منها لهذا الفحص الانتقائي.
- لم أجرِ اختبارًا على Xcode 27 أو iPhone أو حساب Apple Developer.
- المحتوى المستخرج من PDF لا يُعامل باعتباره موثقًا رسميًا بحد ذاته.
- التوجيهات التي قد تختلف حسب إصدار أداة البرمجة معلمة بحاجة إلى التحقق في بيئتها.


---

# نتائج الفحص المحلي للمرفقات الجديدة

**تم فعليًا:**

- استخراج جميع محتويات `agents_md_template.zip` بأسمائها ومساراتها، بما فيها الملفات المخفية.
- فحص سلامة ZIP باستخدام `ZipFile.testzip()`؛ لم تظهر أخطاء سلامة.
- فحص الـPDF وعدد صفحاته **13**، وتحويل الصفحات إلى صور PNG للمعاينة البصرية، واستخراج النص حسب الصفحة.
- التأكد من أن الأرشيف يضم **8 ملفات فعلية** و**4 مداخل مجلدات**؛ أي إن العدد 12 في جدول ZIP ليس عدد ملفات نصية.
- `AGENTS.md`: **100 سطر، 6,878 بايت**؛ وهذه عدد/حجم الملف الجذري بالضبط.
- تحليل ملف `.claude/settings.json` بنجاح والتحقق من وجود **6 أنماط** داخل `permissions.ask`.
- تحليل `.swiftlint.yml` بنجاح باستخدام PyYAML، والبحث عن **3** custom rules.
- تشغيل فحص دخان للتعابير الثلاثة باستخدام **Python re** على مثال إيجابي وآخر سلبي لكل تعبير؛ نجحت الفحوص الستة.
- رصد **9 عناصر مؤقتة** من نوع `<...>` في ملفات القالب، منها `<App>` و`<UDID>` و`<account>` و`<docs/signing-protocol.md>`.
- إنشاء مقارنتين نصيتين مع القالبين الموجودين في الأبحاث السابقة.

**لم يحدث:**

- لم يُشغل `xcodebuild` أو `simctl`، ولا يوجد بناء Xcode أصلي ضمن المرفقات الحالية.
- لم يُشغل `swiftlint` على مشروع Swift؛ اختبار Python ليس بديلًا من تشغيله.
- لم يُختبر قفل الجهاز، أو Keychain، أو Secure Enclave، أو سلوك وكلاء Xcode/Claude/Codex داخل بيئة المستخدم.
- لم تُطبق تعليمات القالب على مشروع حقيقي؛ هي مواد مستخرجة للدراسة والاختيار.

**ملفات التتبع:** `LOCAL_AUDIT.json` و`FILE_INVENTORY.csv` و`DIFF_*.patch`.
