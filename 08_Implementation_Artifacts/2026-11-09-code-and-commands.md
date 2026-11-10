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