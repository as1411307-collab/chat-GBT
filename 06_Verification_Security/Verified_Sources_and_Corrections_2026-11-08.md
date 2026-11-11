# التحقق من المصادر والتصحيحات وتعارض النسخ

**تاريخ مراجعة صفحات عامة:** 8 نوفمبر 2026. التحقق يعني فحص المستند أو سجل الإصدار المنشور، وليس تنزيل SDK أو التجربة على iPhone.

| المصدر/الأداة | نتيجة الفحص | معلومة جوهرية | صفحة المصدر |
|---|---|---|---|
| Apple releases / Xcode 27.2 | مؤكد من Apple | Xcode 27.2 (27B52) بتاريخ 2026-10-29؛ 27.3 ما زالت beta 2026-11-03 | [فتح المصدر](https://developer.apple.com/news/releases/) |
| Xcode 27.2 host/SDK | مؤكد من Apple | macOS Tahoe 26.6+؛ Swift compiler 6.4؛ طريقة التطوير قد تتطلب Apple Silicon | [فتح المصدر](https://developer.apple.com/xcode/system-requirements) |
| Xcode MCP bridge | مؤكد من Apple | تفعيل Intelligence؛ فتح المشروع؛ أوامر xcrun mcpbridge | [فتح المصدر](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) |
| MCP workspace-independent | معاينة مبكرة موثقة | sudo xcrun mcp-server enable Preview؛ لا تساويه بالجسر المستقر | [فتح المصدر](https://developer.apple.com/documentation/xcode-release-notes/xcode-27-release-notes) |
| MobileBuildMCP v2.7.1 | مؤكد من صاحب المستودع | إعادة تسمية XcodeBuildMCP إلى MobileBuildMCP بتاريخ 2026-09-23 | [فتح المصدر](https://github.com/getsentry/MobileBuildMCP/releases) |
| Swift OpenAPI generator 1.14.4 | مؤكد من Apple GitHub | إصدار 1.14.4 بتاريخ 2026-11-05؛ tools version 6.2 في السلسلة الجديدة | [فتح المصدر](https://github.com/apple/swift-openapi-generator/releases) |
| GRDB.swift 7.12.0 | مؤكد بعد تحديث الصفحة | إصدار v7.12.0 بتاريخ 2026-11-01؛ بعض لقطات نتائج البحث تعرض 7.11.1 قديمة | [فتح المصدر](https://github.com/groue/GRDB.swift/releases) |
| Textual 0.5.0 | مؤكد من المستودع | أحدث إصدار ظاهر 0.5.0 بتاريخ 2026-06-15؛ ما زال pre-1.0 | [فتح المصدر](https://github.com/gonzalezreal/textual/releases) |
| MarkdownUI 2.4.1 | مؤكد من المستودع | إصدار 2.4.1 بتاريخ 2026-10-13؛ لا يعني إلغاءه من التطبيقات السابقة | [فتح المصدر](https://github.com/gonzalezreal/swift-markdown-ui/releases) |
| SwiftFormat 0.64.5 | مؤكد من المستودع | إصدار 0.64.5 بتاريخ 2026-10-31 | [فتح المصدر](https://github.com/nicklockwood/SwiftFormat/releases) |
| SnapshotTesting 1.19.7 | مؤكد من المستودع | إصدار 1.19.7 بتاريخ 2026-10-21 | [فتح المصدر](https://github.com/pointfreeco/swift-snapshot-testing/releases) |
| Rork Max / Pro | مؤكد من FAQ الرسمي | Rork Max = SwiftUI/Xcode؛ Rork Pro = React Native/Expo؛ التصدير عبر GitHub في الخطط المدفوعة | [فتح المصدر](https://rork.com/faq) |
| Tailscale Serve/Funnel | مؤكد من المورد | Serve داخل tailnet؛ Funnel يصل إلى الإنترنت العام | [فتح المصدر](https://tailscale.com/docs/features/tailscale-serve) |
| Secure Enclave | مؤكد من Apple | مفاتيح P-256 وتوقيع الأجهزة؛ لا تُصدَّر مادة المفتاح السري خارج الحماية | [فتح المصدر](https://developer.apple.com/documentation/security/protecting-keys-with-the-secure-enclave) |
| SecureEnclave signing initializer | مؤكد من Apple | init(compactRepresentable:accessControl:authenticationContext:) | [فتح المصدر](https://developer.apple.com/documentation/cryptokit/secureenclave/p256/signing/privatekey) |
| SpeechTranscriber | مؤكد للواجهة وليس لدعم كل لهجة | isAvailable وsupportedLocales وinstalledLocales؛ تحقق من العربية على الجهاز الفعلي | [فتح المصدر](https://developer.apple.com/documentation/speech/speechtranscriber) |
| Speech AssetInventory | مؤكد من Apple | تنزيل وإدارة أصول الصوت محليًا مع حدود للحجز والتخزين | [فتح المصدر](https://developer.apple.com/documentation/speech/assetinventory) |
| Foundation Models | مؤكد للواجهة، العربية غير محسومة | SystemLanguageModel يتطلب جهازًا ولغة/منطقة وأصولًا مناسبة؛ فحص supportsLocale في وقت التشغيل | [فتح المصدر](https://developer.apple.com/documentation/foundationmodels/systemlanguagemodel) |
| App Intents | مؤكد من Apple | تكامل Shortcuts/Siri/Spotlight عبر نوايا التطبيق؛ لا يمنح صلاحيات عامة لكل التطبيقات | [فتح المصدر](https://developer.apple.com/documentation/appintents) |
| Siri AI Developer Preview | تجريبي مؤكد | التكامل الجديد معاينة مطور في 2026؛ يتطلب الأجهزة واللغات والإصدارات المؤهلة | [فتح المصدر](https://developer.apple.com/news/?id=gdk2umrf) |
| Live Activities duration | مؤكد من Apple | حتى 8 ساعات نشطة ثم 4 ساعات إضافية محتملة على شاشة القفل | [فتح المصدر](https://developer.apple.com/documentation/activitykit/displaying-live-data-with-live-activities) |
| BackgroundTasks continuous | مؤكد من Apple | BGContinuedProcessingTask يبدأ إثر فعل مستخدم في المقدمة ثم قد يواصل مهمة محدودة في الخلفية | [فتح المصدر](https://developer.apple.com/documentation/backgroundtasks/performing-long-running-tasks-on-ios-and-ipados) |
| Apple HIG materials | مؤكد من Apple | Liquid Glass لطبقة التحكم والتنقل؛ لا تبنِ كل المحتوى كزجاج | [فتح المصدر](https://developer.apple.com/design/human-interface-guidelines/materials) |
| App Review AI sharing | مؤكد من Apple | القسم 5.1.2(i) يطلب إفصاحًا صريحًا وموافقة مشاركة البيانات مع طرف AI ثالث عند النشر | [فتح المصدر](https://developer.apple.com/app-store/review/guidelines/) |
| SwiftLint | مؤكد من المستودع | Lint اختياري؛ لا تعطّل تحقق package plugins دون فهم المخاطر | [فتح المصدر](https://github.com/realm/SwiftLint) |
| Nuke | مؤكد من المستودع | مكتبة صور واستخدام التخزين المؤقت؛ Nuke 13 منشور و14 قيد التطوير | [فتح المصدر](https://github.com/kean/Nuke) |
| ios-simulator-mcp warning | مؤكد من إشعار أمني | إصلاح Command Injection في 1.3.3 للإصدارات الأقدم | [فتح المصدر](https://github.com/joshuayoes/ios-simulator-mcp/security) |


## تصحيحات محددة عند المقارنة

1. **Rork Pro/Max:** صفحة Rork الرسمية تحدد مسار Expo لـPro ومسار SwiftUI لـMax؛ أُبقيت صياغات الأبحاث الأقدم ضمن المراجع لإظهار التحول أو الاختلاف.
2. **GRDB 7.12.0:** وجدت نتيجة بحث عارضًا مخزنًا لإصدار 7.11.1؛ فحص صفحة GitHub المفتوحة من جديد أظهر 7.12.0 بتاريخ 1 نوفمبر. تحقق من الصفحة مباشرة عند تثبيت أي نسخة.
3. **MobileBuildMCP:** اسم مشروع/ملف CLI تغير عن XcodeBuildMCP. أمر Homebrew ما زال يبدأ `brew tap getsentry/xcodebuildmcp` بينما الحزمة المثبتة `mobilebuildmcp`.
4. **Swift OpenAPI Generator:** ظهرت نسخة 1.14.4 بتاريخ 5 نوفمبر؛ التوافق Swift tools 6.2 في 1.14.x، فلا تخلط مع إرشادات الحزم الأقدم.
5. **Siri AI:** Developer Preview في iOS 27.3 beta وشروط لغة وجهاز وموقع. App Intents العامة ليست نفس خاصية Siri AI.
6. **Apple العربية:** دعم واجهات RTL متاح أصلًا؛ دعم Foundation Models بالعربية أو SpeechTranscriber في كل لهجات العربية غير مثبت من صفحات API وحدها، ويُسأل الجهاز أثناء التشغيل.
7. **Secure Enclave:** يدعم مفتاح P-256 وإجراء توقيع على جهاز مؤهل؛ استخدام Face ID لكل عملية يتطلب إعداد access control ومسار تعامل مع فشل البيومترية.
8. **Live Activities:** مدة محددة ولا تحمل دورة تنفيذ خادم طويلة إلى iPhone؛ Backend يحتاج الاحتفاظ بحالة المهمة.
9. **iOS Simulator MCP:** إصلاح Command Injection في 1.3.3 منشور؛ لا تثبت نسخة قديمة تلقائيًا.
10. **طرق التوليد:** وجود نسخة كود في GitHub بعد التصدير لا يضمن شمول موارد المشروع ومفاتيح التوقيع واختبارات التشغيل؛ هذا تقييم هندسي لا اقتباس من متجر.

## مصادر أصلية داخل المرفقات لا يساوي ظهور رابطها إعادة التحقق منه

فهرس الروابط الكامل في الملف `13_روابط_البحث_الإضافية.md` يسجل الروابط الواردة في الأبحاث وأماكنها. الروابط التي راجعتها فعليًا أثناء هذه المهمة تظهر في الجدول أعلاه فقط. البيانات التاريخية عن نجوم GitHub والأسعار والإصدارات واللغات قد تختلف عند تاريخ بناء التطبيق.

## ما لم يُختبر هنا

- لم يُفتح Xcode على Mac داخل هذه الجلسة؛ لا إثبات من مترجم Swift أن الأمثلة قابلة للبناء كما هي.
- لم يتم تسجيل دخول Apple Developer أو App Store Connect أو استخدام شهادة/هوية iPhone.
- لم تُختبر شبكة Tailscale على جهاز المستخدم ولا اتصال Core حي.
- لم يتم نقل ملفات إلى GitHub أو إنشاء مستودع بديل بعد حذف المستودع السابق.
- لم تُختبر دقة الصوت بالعربية أو سرعة أدوات الواجهة على iPhone.
- لم تُراجع كل مئات روابط الملحق واحدًا واحدًا، بل جرى تحقق مباشر لعينة واسعة ومهمة إضافة إلى الاحتفاظ بتفاصيل البحث الأصلي.


---

# النصوص المصدرية الكاملة المرتبطة بهذا القسم

> نسخة تقرير التحقق الأصلي بمراجعه محفوظة في ملف الأدوات أيضًا.



---

## المصدر: `11_verified_tool_table.md`

**مكان النسخة الأصلية داخل الأرشيف:** `المصادر_الأصلية/محتويات_الارشيفات/iPhone_App_Research_Nov2026/11_verified_tool_table.md`

# Verified tool and API reference — November 8, 2026

Author: Manus AI. Research only: no software installed, no app built, and no browser used. Versions and dates below come from live official/vendor pages and GitHub release/commit endpoints. A bundled framework does not have an independently verified package version just because its compiler or SDK has one. Apple proprietary software/resources are governed by [Apple agreements](https://developer.apple.com/support/terms/), not an assumed MIT license.

## A. Tool table

| Tool | Version | License | Install | First command | Needed for | Source |
|---|---|---|---|---|---|---|
| [Xcode](https://developer.apple.com/xcode/) | **Stable 27.2, build 27B52, 2026-10-29**; Swift 6.4 compiler. Requires **Apple silicon and macOS Tahoe 26.6+** | Apple proprietary Xcode/SDK agreements | Mac App Store or Apple Developer Downloads; full Xcode, not just Command Line Tools | `xcodebuild -version` | Required Mac IDE, Apple SDKs, signing and simulator baseline for native iOS development | [Releases](https://developer.apple.com/news/releases/) [requirements](https://developer.apple.com/support/xcode/) [Apple-silicon announcement](https://www.apple.com/newsroom/2026/06/apple-aids-app-development-with-new-intelligence-frameworks-and-advanced-tools/) |
| [xcodebuild / simctl](https://developer.apple.com/documentation/xcode/command-line-tools) | Bundled with Xcode 27.2, 2026-10-29; no independent release | Apple Xcode terms | Install full Xcode and select its developer directory | `xcodebuild -version`; `xcodebuild -list -project MyApp.xcodeproj`; `xcrun simctl list devices available` | Reproducible terminal/CI build and test; simulator destination discovery | [Apple command-line guide](https://developer.apple.com/library/archive/technotes/tn2339/_index.html) [Xcode releases](https://developer.apple.com/news/releases/) |
| [Xcode agentic coding / mcpbridge](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) | Introduced **Xcode 26.3**; bundled in 27.2, 2026-10-29 | Apple proprietary | Xcode > Settings > Intelligence > Model Context Protocol > **“Allow external agents to use Xcode tools.”** Open the project in Xcode | `xcrun mcpbridge`, launched by an MCP stdio client | Optional external-agent access to Xcode project, build, test and preview capabilities; no provider-specific requirement for the MCP connection | [Setup](https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence) [permission/bridge](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) [26.3 introduction](https://www.apple.com/newsroom/2026/02/xcode-26-point-3-unlocks-the-power-of-agentic-coding/) |
| [MobileBuildMCP](https://github.com/getsentry/MobileBuildMCP) | **2.7.1, 2026-09-23**; renamed from XcodeBuildMCP in this release | MIT; separate third-party notices | `brew tap getsentry/xcodebuildmcp && brew install mobilebuildmcp` OR `npm install -g mobilebuildmcp@latest`; macOS 14.5+, Xcode 16+, Node 18+ for npm | `mobilebuildmcp --help`; server: `mobilebuildmcp mcp`; tools: `mobilebuildmcp tools` | Optional agent/CLI builds, simulator/device interaction, logs and debugging. Not necessary if direct xcodebuild/Xcode tools suffice | [README](https://github.com/getsentry/MobileBuildMCP) [latest](https://api.github.com/repos/getsentry/MobileBuildMCP/releases/latest) [license](https://api.github.com/repos/getsentry/MobileBuildMCP/license) |
| [Apple Developer Documentation](https://developer.apple.com/documentation/) | Continuously updated; no single stable version/date | Apple documentation copyright/site terms | None; web or Xcode documentation | Look up the exact symbol and its platform availability | Authoritative declarations, API status, migrations and examples | [Documentation](https://developer.apple.com/documentation/) [terms](https://developer.apple.com/support/terms/) |
| [Sosumi](https://sosumi.ai/) | **1.1.0, 2026-11-07** | MIT implementation; underlying Apple content remains Apple's copyright | MCP endpoint **`https://sosumi.ai/mcp`**, supporting Streamable HTTP/SSE; optional CLI `npm i -g @nshipster/sosumi` | `sosumi search "SwiftData"`; `sosumi fetch /documentation/swiftui`; MCP `searchAppleDocumentation` / `fetchAppleDocumentation` | Optional Markdown documentation/transcript access for agents; unofficial and not Apple-endorsed | [Usage/endpoint](https://sosumi.ai/) [latest](https://api.github.com/repos/NSHipster/sosumi.ai/releases/latest) [license](https://api.github.com/repos/NSHipster/sosumi.ai/license) |
| [swiftui-pro skill — twostraws/swiftui-agent-skill](https://github.com/twostraws/swiftui-agent-skill) | Stable tag **2.0.0, 2026-10-09**; latest branch commit 2026-10-26 16:53:18Z, `f2920b6` | MIT | `npx skills add https://github.com/twostraws/swiftui-agent-skill --skill swiftui-pro` | Ask an agent to review a SwiftUI file using `swiftui-pro` | Optional SwiftUI review guidance; not a runtime dependency or compiler | [Exact install](https://skills.sh/twostraws/swiftui-agent-skill/swiftui-pro) [release](https://api.github.com/repos/twostraws/swiftui-agent-skill/releases/latest) [commit](https://api.github.com/repos/twostraws/swiftui-agent-skill/commits?per_page=1) [license](https://api.github.com/repos/twostraws/swiftui-agent-skill/license) |
| [swift-concurrency skill — avdlee/swift-concurrency-agent-skill](https://github.com/avdlee/swift-concurrency-agent-skill) | Stable tag **2.3.1, 2026-11-06**; latest commit 2026-11-06 08:11:43Z, `3b1580d` | MIT | `npx skills add https://github.com/avdlee/swift-concurrency-agent-skill --skill swift-concurrency` | Ask an agent to diagnose a concurrency diagnostic with actual project settings | Optional migration/actor-isolation review; not a concurrency library | [Exact install](https://skills.sh/avdlee/swift-concurrency-agent-skill/swift-concurrency) [release](https://api.github.com/repos/avdlee/swift-concurrency-agent-skill/releases/latest) [commit](https://api.github.com/repos/avdlee/swift-concurrency-agent-skill/commits?per_page=1) [license](https://api.github.com/repos/avdlee/swift-concurrency-agent-skill/license) |
| [swift-testing-pro skill — twostraws/swift-testing-agent-skill](https://github.com/twostraws/swift-testing-agent-skill) | Stable tag **1.0.0, 2026-03-11**; latest commit 2026-05-17 15:49:43Z, `2d6bba1` | MIT | `npx skills add https://github.com/twostraws/swift-testing-agent-skill --skill swift-testing-pro` | Ask an agent to review or migrate a unit test | Optional Swift Testing guidance; not the testing framework itself | [Exact install](https://skills.sh/twostraws/swift-testing-agent-skill/swift-testing-pro) [release](https://api.github.com/repos/twostraws/swift-testing-agent-skill/releases/latest) [commit](https://api.github.com/repos/twostraws/swift-testing-agent-skill/commits?per_page=1) [license](https://api.github.com/repos/twostraws/swift-testing-agent-skill/license) |
| [swift-security-expert skill — ivan-magda/swift-security-skill](https://github.com/ivan-magda/swift-security-skill) | Stable tag **1.0.0, 2026-03-06**; latest commit 2026-06-17 11:50:39Z, `bda2e0c` | MIT | `npx skills add https://github.com/ivan-magda/swift-security-skill --skill swift-security-expert` (skills.sh form); release README also gives `npx skills add ivan-magda/swift-security-skill --skill swift-security-expert` | Ask an agent to review Keychain, biometric or signing code | Optional security reference; not a cryptographic implementation | [Exact install](https://skills.sh/ivan-magda/swift-security-skill/swift-security-expert) [release](https://api.github.com/repos/ivan-magda/swift-security-skill/releases?per_page=1) [commit](https://api.github.com/repos/ivan-magda/swift-security-skill/commits?per_page=1) [license](https://api.github.com/repos/ivan-magda/swift-security-skill/license) |
| [ios-localization skill — dpearson2699/swift-ios-skills](https://github.com/dpearson2699/swift-ios-skills) | Repository release **3.9.1, 2026-07-31**; latest commit same day 20:22:31Z, `8d90fd1` | **PolyForm Perimeter 1.0.0, NOT MIT**; includes noncompete restrictions | `npx skills add https://github.com/dpearson2699/swift-ios-skills --skill ios-localization` | Ask an agent to review catalogs, plurals and RTL | Optional localization guidance; assess license before redistribution or competing offerings | [Exact install](https://skills.sh/dpearson2699/swift-ios-skills/ios-localization) [release](https://api.github.com/repos/dpearson2699/swift-ios-skills/releases/latest) [commit](https://api.github.com/repos/dpearson2699/swift-ios-skills/commits?per_page=1) [license endpoint](https://api.github.com/repos/dpearson2699/swift-ios-skills/license) [actual text](https://raw.githubusercontent.com/dpearson2699/swift-ios-skills/main/LICENSE) |
| [swiftui-liquid-glass skill — Dimillian/Skills](https://github.com/Dimillian/Skills) | **No published GitHub releases**; latest default-branch commit **2026-03-29 15:28:00Z**, `05ba982` (repository-wide date) | MIT | `npx skills add https://github.com/dimillian/skills --skill swiftui-liquid-glass` | Ask an agent to review native Liquid Glass usage | Optional iOS 26+ glass guidance; not needed for all SwiftUI apps | [Exact install](https://skills.sh/dimillian/skills/swiftui-liquid-glass) [empty release list](https://api.github.com/repos/Dimillian/Skills/releases?per_page=1) [commit](https://api.github.com/repos/Dimillian/Skills/commits?per_page=1) [license](https://api.github.com/repos/Dimillian/Skills/license) |
| [Swift OpenAPI Generator](https://github.com/apple/swift-openapi-generator) | **1.14.4, 2026-11-05**; pinned Swift tools minimum **6.2** | Apache-2.0 | SPM `.package(url: "https://github.com/apple/swift-openapi-generator", from: "1.14.4")`; target plugin `OpenAPIGenerator` | Add schema/config with `generate: [types, client]`; `swift build` | Optional generated contract-based types/client. Generator runs during build, not on iPhone | [README](https://github.com/apple/swift-openapi-generator) [latest](https://api.github.com/repos/apple/swift-openapi-generator/releases/latest) [license](https://api.github.com/repos/apple/swift-openapi-generator/license) [pinned manifest](https://github.com/apple/swift-openapi-generator/blob/1.14.4/Package.swift) |
| [Swift OpenAPI Runtime](https://github.com/apple/swift-openapi-runtime) | **1.13.4, 2026-11-03**; Swift tools **6.2**, iOS 13+ | Apache-2.0 | SPM `.package(url: "https://github.com/apple/swift-openapi-runtime", from: "1.13.4")`; product `OpenAPIRuntime` | `import OpenAPIRuntime` | Required by generated OpenAPI code; HTTP bodies, protocols, middleware and streaming helpers | [README](https://github.com/apple/swift-openapi-runtime) [latest](https://api.github.com/repos/apple/swift-openapi-runtime/releases/latest) [license](https://api.github.com/repos/apple/swift-openapi-runtime/license) [manifest](https://github.com/apple/swift-openapi-runtime/blob/1.13.4/Package.swift) |
| [Swift OpenAPI URLSession](https://github.com/apple/swift-openapi-urlsession) | **1.4.0, 2026-10-22**; own Swift tools minimum **6.1**, but selected latest runtime/generator require 6.2. iOS 13+, streaming iOS 15+ | Apache-2.0 | SPM `.package(url: "https://github.com/apple/swift-openapi-urlsession", from: "1.4.0")`; product `OpenAPIURLSession` | `let client = Client(serverURL: url, transport: URLSessionTransport())` after generation/imports | URLSession transport for generated client; the backend does not need a Swift OpenAPI server library | [README](https://github.com/apple/swift-openapi-urlsession) [latest](https://api.github.com/repos/apple/swift-openapi-urlsession/releases/latest) [license](https://api.github.com/repos/apple/swift-openapi-urlsession/license) [manifest](https://github.com/apple/swift-openapi-urlsession/blob/1.4.0/Package.swift) |
| [SwiftData](https://developer.apple.com/documentation/swiftdata) | Bundled Apple framework, iOS **17+**; SDK 27.2 shipped with Xcode 27.2 on 2026-10-29; no independent package version | Apple SDK terms | None; `import SwiftData` | `let container = try ModelContainer(for: MyModel.self)` for a defined `@Model` type | Simple managed local persistence/cache integrated with SwiftUI; no external database package required | [Framework](https://developer.apple.com/documentation/swiftdata) [server-data cache sample](https://developer.apple.com/documentation/swiftdata/maintaining-a-local-copy-of-server-data) |
| [GRDB.swift](https://github.com/groue/GRDB.swift) | **7.12.0, 2026-11-01**; iOS 13+, Swift 6.1+/Xcode 16.3+, SQLite 3.20+ | MIT | SPM URL `https://github.com/groue/GRDB.swift.git`, version from 7.12.0, product `GRDB` | `let dbQueue = try DatabaseQueue(path: databaseURL.path)` | Optional explicit SQL, migrations, observation and FTS5. Not necessary for a basic SwiftData cache | [Release README](https://github.com/groue/GRDB.swift/blob/v7.12.0/README.md) [latest](https://api.github.com/repos/groue/GRDB.swift/releases/latest) [license](https://api.github.com/repos/groue/GRDB.swift/license) |
| [SQLite / FTS5](https://sqlite.org/fts5.html) | OS-bundled SQLite version on current iOS **unverified**; no official per-iOS version matrix found. Upstream FTS5 included since SQLite **3.9.0, 2015-10-14**; this is not an iOS bundled-version claim | SQLite deliverable code/documentation is **public domain** | Link system SQLite / use GRDB; for custom SQLite, compile with `SQLITE_ENABLE_FTS5` | SQL: `SELECT sqlite_version();`; feature probe `SELECT sqlite_compileoption_used('ENABLE_FTS5');`; usage `CREATE VIRTUAL TABLE messages_fts USING fts5(body);` | Full-text index only when search requirements justify it; verify actual OS build/runtime support | [FTS5 compilation](https://sqlite.org/fts5.html) [copyright](https://sqlite.org/copyright.html) |
| [Textual](https://github.com/gonzalezreal/textual) | **0.5.0, 2026-06-15**; not flagged prerelease, but **pre-1.0**; Swift tools 6.0, iOS **18+** | MIT; additional third-party notices | SPM `.package(url: "https://github.com/gonzalezreal/textual", from: "0.5.0")`; product **`Textual`** | `import Textual`; `StructuredText(markdown: content)` | Optional native structured Markdown/rich-text rendering and selection | [README](https://github.com/gonzalezreal/textual) [latest](https://api.github.com/repos/gonzalezreal/textual/releases/latest) [license](https://api.github.com/repos/gonzalezreal/textual/license) [pinned manifest](https://github.com/gonzalezreal/textual/blob/0.5.0/Package.swift) |
| [CryptoKit](https://developer.apple.com/documentation/cryptokit) | Bundled framework, iOS **13+**; no separate package release | Apple SDK terms | None; `import CryptoKit` | `let digest = SHA256.hash(data: data)` | Hashing, authenticated encryption, signatures/key agreement; use only the operations the app requires | [Framework](https://developer.apple.com/documentation/cryptokit) |
| [Secure Enclave — CryptoKit P256 signing](https://developer.apple.com/documentation/cryptokit/secureenclave) | Bundled hardware/API; requested CryptoKit initializer iOS **13+**; device support must be checked | Apple SDK terms | None; CryptoKit plus Security access control | Check `SecureEnclave.isAvailable`; `let key = try SecureEnclave.P256.Signing.PrivateKey(accessControl: access)` | Optional nonexportable hardware-backed signing key; requires actual supported hardware and recovery design | [Initializer](https://developer.apple.com/documentation/cryptokit/secureenclave/p256/signing/privatekey/init%28compactrepresentable:accesscontrol:authenticationcontext:%29) [security guidance](https://developer.apple.com/documentation/security/protecting-keys-with-the-secure-enclave) |
| [Keychain Services](https://developer.apple.com/documentation/security/keychain-services) | Bundled Security framework; no independent semantic version | Apple SDK terms | None; `import Security` | `let status = SecItemAdd(query as CFDictionary, nil)` with a valid item dictionary; inspect OSStatus | Credentials, tokens and persisted key representations. Not UserDefaults or ordinary model storage | [Adding a password](https://developer.apple.com/documentation/security/adding-a-password-to-the-keychain) |
| [Square Valet](https://github.com/square/Valet) | **5.1.1, 2026-09-09** | Apache-2.0 | SPM `.package(url: "https://github.com/Square/Valet", from: "5.1.1")`, product `Valet` | `let vault = Valet.valet(with: Identifier(nonEmpty: "Session")!, accessibility: .whenUnlockedThisDeviceOnly)` | Optional ergonomic Keychain wrapper; not required for CryptoKit/Secure Enclave key creation | [README](https://github.com/square/Valet) [latest](https://api.github.com/repos/square/Valet/releases/latest) [license](https://api.github.com/repos/square/Valet/license) |
| [Tailscale iOS app](https://apps.apple.com/us/app/tailscale/id1470499037) | App Store **1.104.5**; vendor changelog **2026-11-02**. US App Store requires iOS/iPadOS **16.6+**; store rollout date not independently fixed | Open-source client core **BSD-3-Clause**; distributed app/service terms are separate | App Store; sign in and join tailnet | Enable/connect the VPN in the app | Phone access to private tailnet services; no embedded Tailscale SDK required | [App Store](https://apps.apple.com/us/app/tailscale/id1470499037) [changelog](https://tailscale.com/changelog) [client license](https://github.com/tailscale/tailscale/blob/main/LICENSE) |
| [Tailscale Serve](https://tailscale.com/kb/1242/tailscale-serve) | Current client **1.104.5**; changelog 2026-11-02; GitHub release publication **2026-11-03 UTC** | BSD-3-Clause client core; service terms separate | Install Tailscale on backend host and enable tailnet HTTPS | `tailscale serve --bg 8787`; `tailscale serve status`; `tailscale serve reset` | Private-tailnet HTTPS proxy to localhost:8787. `--bg` persists configuration. **Funnel exposes it publicly** | [Serve CLI](https://tailscale.com/kb/1242/tailscale-serve) [Funnel](https://tailscale.com/kb/1223/funnel) [latest](https://api.github.com/repos/tailscale/tailscale/releases/latest) [license](https://github.com/tailscale/tailscale/blob/main/LICENSE) |
| [SF Symbols](https://developer.apple.com/sf-symbols/) | Current official download **SF Symbols 27**; exact release date not exposed on fetched pages. Desktop app requires macOS **Sonoma+**; new symbols require iOS 27 | Apple SF Symbols license/restrictions; not OSS | Official DMG `SF-Symbols-27.dmg` | SwiftUI `Image(systemName: "gear")`; desktop app browses symbol availability | System icons; desktop download needed only for browsing/editing/exporting | [Official site/download](https://developer.apple.com/sf-symbols/) [resources](https://developer.apple.com/design/resources/) |
| [Apple Design Resources](https://developer.apple.com/design/resources/) | Current **iOS/iPadOS 27** and macOS 27 kits; other kits vary; no universal version/date | Apple Design Resources agreements | Download/open the official Figma, Sketch or artwork templates | Open the UI kit matching the design OS | Optional visual reference/templates, not executable app components | [Official resources](https://developer.apple.com/design/resources/) |
| [Icon Composer](https://developer.apple.com/icon-composer/) | **Exact current app version/date unverified from public official pages**; dedicated page requires **macOS Tahoe 26.4+** | Apple software terms | [Apple Downloads](https://developer.apple.com/download/all/?q=Icon%20Composer); fetched download listing yielded no version metadata | Open app, import artwork layers, annotate, add icon file to Xcode | Optional layered Liquid Glass app-icon creation | [Product page](https://developer.apple.com/icon-composer/) [resources](https://developer.apple.com/design/resources/) |
| [Swift Testing](https://developer.apple.com/documentation/testing) | Bundled in **Xcode 27.2 / Swift 6.4**; introduced Swift 6/Xcode16. Exact separately bundled library patch **not verified** | Open-source Swift Testing **Apache-2.0 with Runtime Library Exception**; Xcode distribution terms also apply | None in Xcode test target; `import Testing` | `@Test func example() { #expect(1 + 1 == 2) }`; package tests: `swift test` | New unit/integration tests; does not replace XCTest UI/performance testing | [Framework](https://developer.apple.com/documentation/testing) [Xcode matrix](https://developer.apple.com/support/xcode/) [license endpoint](https://api.github.com/repos/swiftlang/swift-testing/license) [exception text](https://raw.githubusercontent.com/swiftlang/swift-testing/main/LICENSE.txt) |
| [XCTest](https://developer.apple.com/documentation/xctest) | Bundled with Xcode 27.2, 2026-10-29; no separately verified library patch | Apple SDK terms for Xcode framework | None; create test target and `import XCTest` | `XCTAssertTrue(condition)` | Existing unit tests, performance tests and UI-test runner | [Framework](https://developer.apple.com/documentation/xctest) [migration guide](https://developer.apple.com/documentation/testing/migratingfromxctest) |
| [XCUIAutomation](https://developer.apple.com/documentation/xcuiautomation) | Bundled Xcode 27.2; current standalone framework namespace documented **Xcode 16.3+** | Apple SDK terms | None; UI-test target, XCTest plus XCUIAutomation | `let app = XCUIApplication(); app.launch()` | UI interactions/state inspection, accessibility audit; UI tests still use XCTest | [Framework](https://developer.apple.com/documentation/xcuiautomation) |
| [Instruments](https://developer.apple.com/tutorials/instruments) | Bundled with Xcode 27.2, 2026-10-29; independent app patch not verified | Apple Xcode terms | Installed with Xcode | Xcode **Product > Profile**, choose Time Profiler or relevant template | CPU, hangs, memory, energy and Swift concurrency measurement; use actual devices for higher-fidelity profiling | [Performance guidance](https://developer.apple.com/documentation/xcode/improving-your-app-s-performance) [WWDC2026/268](https://developer.apple.com/videos/play/wwdc2026/268/) |
| [TestFlight](https://developer.apple.com/testflight/) | Client **4.4.1, 2026-10-22**; service continuously updated. Builds expire after **90 days**; up to **100 internal testers** | Apple TestFlight terms | App Store TestFlight for testers; archive/upload using Xcode/App Store Connect; Developer Program for distribution | Xcode Product > Archive > Distribute App > **TestFlight Internal Only**; add internal group in App Store Connect | Team beta distribution without Beta App Review for internal testing; upload processing/export compliance still apply. External testing requires the review flow | [Official page](https://developer.apple.com/testflight/) [overview/expiry](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview) [internal testers](https://developer.apple.com/help/app-store-connect/test-a-beta-version/add-internal-testers) [release notes](https://developer.apple.com/testflight/release-notes/) |
| [Direct install from Xcode / Developer Mode](https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device) | Bundled workflow; Developer Mode required on applicable modern iOS devices, introduced iOS16 | Apple development/SDK terms | Pair device; Settings > Privacy & Security > Developer Mode; restart and confirm; configure development signing | Select the physical device destination and **Product > Run** | Local development install/debugging. **TestFlight and ordinary App Store installs do not require Developer Mode** | [Apple Developer Mode guide](https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device) |

### Basic terminal build and test commands

These are illustrative commands, not commands executed during this research. Replace `MyApp` and `SIMULATOR_UDID` with the actual scheme/project and an available simulator ID returned by `simctl`; do not assume any particular device name is installed. Apple's command-line guide documents build/test destination selection. [1]

```bash
xcodebuild -version
xcodebuild -list -project MyApp.xcodeproj
xcrun simctl list devices available
xcodebuild -project MyApp.xcodeproj -scheme MyApp \
  -destination 'platform=iOS Simulator,id=SIMULATOR_UDID' build
xcodebuild -project MyApp.xcodeproj -scheme MyApp \
  -destination 'platform=iOS Simulator,id=SIMULATOR_UDID' test
```

### Generic Xcode MCP stdio configuration

The enclosing configuration key varies by MCP client. The generic executable and argument are `xcrun` and `mcpbridge`; no particular agent/model service is required by the connection. Enable **“Allow external agents to use Xcode tools”** and keep the project open in Xcode. This is the established bridge, not the standalone preview. [2]

```json
{
  "mcpServers": {
    "xcode": {
      "command": "xcrun",
      "args": ["mcpbridge"]
    }
  }
}
```

### Swift OpenAPI SPM/plugin usage

The official URLSession example places `openapi.yaml` and `openapi-generator-config.yaml` in the target source directory, links runtime and transport products, and attaches the build plugin. The following concise configuration is equivalent to the official multiline `generate` list. The latest chosen generator/runtime stack requires Swift **6.2+**, even though URLSession 1.4.0's own manifest says 6.1. [3] [4]

```swift
// Relevant entries inside the target declaration in Package.swift:
dependencies: [
    .product(name: "OpenAPIRuntime", package: "swift-openapi-runtime"),
    .product(name: "OpenAPIURLSession", package: "swift-openapi-urlsession")
],
plugins: [
    .plugin(name: "OpenAPIGenerator", package: "swift-openapi-generator")
]
```

```yaml
# openapi-generator-config.yaml
generate: [types, client]
accessModifier: internal
namingStrategy: idiomatic
```

Run `swift build` for a package, or build the Xcode target. The generated `Client` is used with `URLSessionTransport()`. Generated-code deployment targets and the **host compiler minimum** are separate requirements.

## B. Sensitive API status table

“Stable” below means available in a released SDK/toolchain and not marked deprecated in the fetched official documentation. It does not mean hardware availability, every locale being supported, or every third-party pre-1.0 API being frozen.

| API / item | Status | iOS / toolchain version | Verified detail | Official documentation |
|---|---|---|---|---|
| `@Observable` / Observation | **Stable** | **iOS 17+**; Swift macro support | Synthesizes observation tracking and Observable conformance | [Observable macro](https://developer.apple.com/documentation/observation/observable%28%29) |
| `SWIFT_DEFAULT_ACTOR_ISOLATION = MainActor` | **Stable**, opt-in build setting | Swift **6.2+ / Xcode 26+**; not an iOS26-only API | Sets default isolation for eligible unannotated declarations. Does not make all Swift code globally main-isolated | [Build-settings reference](https://developer.apple.com/documentation/xcode/build-settings-reference) [Swift6.2](https://www.swift.org/blog/swift-6.2-released/) |
| `SWIFT_APPROACHABLE_CONCURRENCY = YES` | **Stable**, compiler setting | Swift **6.2+ / Xcode 26+**; no independent iOS gate | Enables DisableOutwardActorInference, GlobalActorIsolatedTypesUsability, InferIsolatedConformances, InferSendableFromCaptures and NonisolatedNonsendingByDefault | [Build-settings reference](https://developer.apple.com/documentation/xcode/build-settings-reference) |
| `@concurrent` | **Stable** | Swift **6.2**, released 2025-09-15; compiler feature, not iOS26-only | Explicitly opts an async function into concurrent execution away from caller isolation | [Swift6.2 release](https://www.swift.org/blog/swift-6.2-released/) |
| SwiftData `ModelActor` / `@ModelActor` | **Stable** | **iOS 17+**, Swift5.9+ | Mutually exclusive actor-isolated model access; macro supplies boilerplate. Actor use alone does not prove heavy work leaves the main executor | [ModelActor](https://developer.apple.com/documentation/swiftdata/modelactor) |
| `SecureEnclave.P256.Signing.PrivateKey(accessControl:...)` | **Stable** | **iOS 13+**, supported hardware | Exact declaration is `init(compactRepresentable:accessControl:authenticationContext:)`; first and third parameters have defaults, so the shorter call is valid | [Exact initializer](https://developer.apple.com/documentation/cryptokit/secureenclave/p256/signing/privatekey/init%28compactrepresentable:accesscontrol:authenticationcontext:%29) |
| `SecAccessControlCreateWithFlags` | **Stable** | **iOS 8+** | Produces access-control object; protected operations may block main thread. Handle optional return/error | [Function](https://developer.apple.com/documentation/security/secaccesscontrolcreatewithflags%28_:_:_:_:%29) |
| `.biometryCurrentSet` | **Stable** | **iOS 11.3+** | Requires current enrolled biometric set; enrollment changes invalidate access. For enclave private-key operations also consider `.privateKeyUsage` | [Flag](https://developer.apple.com/documentation/security/secaccesscontrolcreateflags/biometrycurrentset) [enclave access control](https://developer.apple.com/documentation/security/protecting-keys-with-the-secure-enclave) |
| `kSecAttrAccessibleWhenUnlockedThisDeviceOnly` | **Stable** | **iOS 4+** | Item accessible only while unlocked and does not migrate to another device | [Accessibility value](https://developer.apple.com/documentation/security/ksecattraccessiblewhenunlockedthisdeviceonly) |
| `glassEffect` | **Stable** | **iOS 26+** | Native Liquid Glass modifier; default regular glass/capsule; appearance/layout modifiers precede glass effect | [Modifier](https://developer.apple.com/documentation/swiftui/view/glasseffect%28_:in:%29) |
| `.buttonStyle(.glass)` | **Stable** | **iOS 26+** | Native context-aware glass button style | [Style](https://developer.apple.com/documentation/swiftui/primitivebuttonstyle/glass) |
| `GlassEffectContainer` | **Stable** | **iOS 26+** | Combines glass shapes for shared rendering and morphing; spacing governs blending | [Container](https://developer.apple.com/documentation/swiftui/glasseffectcontainer) |
| `.defaultScrollAnchor(_:)` | **Stable** | **iOS 17+** | Controls initial/content-size-change positioning; does not prevent a person scrolling away | [Modifier](https://developer.apple.com/documentation/swiftui/view/defaultscrollanchor%28_:%29) |
| `.defaultScrollAnchor(_:for:)` | **Stable** | **iOS 18+** | Distinct initial-offset, size-change and alignment roles | [Role-specific modifier](https://developer.apple.com/documentation/swiftui/view/defaultscrollanchor%28_:for:%29) |
| `onScrollGeometryChange` | **Stable** | **iOS 18+** | Transform frequently changing geometry into a small Equatable value before updating state | [Modifier](https://developer.apple.com/documentation/swiftui/view/onscrollgeometrychange%28for:of:action:%29) |
| `ScrollPosition` | **Stable** | **iOS 18+** | ID/edge/point state and `isPositionedByUser` help detect user scrolling. Gate programmatic auto-follow using state/geometry; there is no universal “disable auto-follow” switch | [Type](https://developer.apple.com/documentation/swiftui/scrollposition) |
| String Catalogs `.xcstrings` | **Stable** | **Xcode15+**; no new minimum iOS target required solely for catalogs | Compile to `.strings` and `.stringsdict`; can coexist with legacy resources; Swift package example uses tools5.9 | [Catalog guide](https://developer.apple.com/documentation/xcode/localizing-and-varying-text-with-a-string-catalog) [official WWDC23 transcript](https://developer.apple.com/videos/play/wwdc2023/10155/) |
| `SpeechTranscriber` | **Stable** | **iOS 26+**, runtime hardware support | New on-device transcription module; no official static Arabic guarantee found | [Type](https://developer.apple.com/documentation/speech/speechtranscriber) |
| `SpeechTranscriber.isAvailable` | **Stable** | **iOS 26+** | Synchronous Bool checks device hardware/capabilities, not whether a chosen language's asset is installed | [Property](https://developer.apple.com/documentation/speech/speechtranscriber/isavailable) |
| `SpeechTranscriber.supportedLocales` | **Stable** | **iOS 26+** | **Async** list includes downloadable, not necessarily installed, locales; empty if device unsupported | [Property](https://developer.apple.com/documentation/speech/speechtranscriber/supportedlocales) |
| `SpeechTranscriber.installedLocales` | **Stable** | **iOS 26+** | **Async** list only considers locales installed on that device | [Property](https://developer.apple.com/documentation/speech/speechtranscriber/installedlocales) |
| `DictationTranscriber` | **Stable** | **iOS 26+**; supports older hardware than SpeechTranscriber, not older iOS | Uses system dictation/on-device SFSpeechRecognizer models. Does **not** support locales available only through SFSpeechRecognizer network transcription | [Type](https://developer.apple.com/documentation/speech/dictationtranscriber) |
| `AssetInventory.assetInstallationRequest(supporting:)` | **Stable** | **iOS 26+** | `async throws -> AssetInstallationRequest?`; configure modules, get optional request, call `downloadAndInstall()` and await completion; assets managed/shared by system | [Inventory](https://developer.apple.com/documentation/speech/assetinventory) |
| `AssetInventory.status(forModules:)` / `.Status` | **Stable** | **iOS 26+** | Async readiness; cases **unsupported, supported, downloading, installed**. Supported means download needed; installed means ready | [Status enum](https://developer.apple.com/documentation/speech/assetinventory/status) [inventory](https://developer.apple.com/documentation/speech/assetinventory) |
| `AVSpeechSynthesisVoice.speechVoices()` | **Stable** | **iOS 7+** | Enumerates actual available device voices; inspect language/locale instead of assuming a voice name | [Method](https://developer.apple.com/documentation/avfaudio/avspeechsynthesisvoice/speechvoices%28%29) |
| Swift Testing `@Test` / `#expect` | **Stable** | **Swift6+ / Xcode16+**; current bundled compiler Swift6.4 | Toolchain test APIs, not an ordinary app runtime dependency. UI/performance still XCTest | [Framework](https://developer.apple.com/documentation/testing) [migration guide](https://developer.apple.com/documentation/testing/migratingfromxctest) |
| `XCUIApplication.performAccessibilityAudit` | **Stable** | **iOS 17+**; current XCUIAutomation namespace Xcode16.3+ | Throwing UI-test audit, default audit types `.all`. Framework namespace version is distinct from original API introduction | [Method](https://developer.apple.com/documentation/xcuiautomation/xcuiapplication/performaccessibilityaudit%28for:_:%29) |
| `ObservableObject` | **Stable, legacy but NOT deprecated** | **iOS 13+** | Still documented Combine protocol; Observation is the modern alternative, not evidence of formal deprecation | [Protocol](https://developer.apple.com/documentation/combine/observableobject) |
| `NavigationView` | **Deprecated** | Introduced **iOS13**; Apple migration boundary **iOS16+** | Use NavigationStack / NavigationSplitView. Live availability range formatting does not reliably identify original deprecation date | [Type](https://developer.apple.com/documentation/swiftui/navigationview) [migration](https://developer.apple.com/documentation/swiftui/migrating-to-new-navigation-types) |
| MarkdownUI | **Maintenance mode**, not formal Apple API deprecation | **iOS15+**, some features iOS16+ | Maintainer directs new development to Textual | [Official project README](https://github.com/gonzalezreal/swift-markdown-ui) |
| Textual | Latest tag **not prerelease**, but **pre-1.0** | **0.5.0**, iOS18+ | Do not conflate “latest stable-tagged release” with a frozen 1.x public API | [README](https://github.com/gonzalezreal/textual) [release metadata](https://api.github.com/repos/gonzalezreal/textual/releases/latest) |
| Xcode27.3 | **Beta** | **27C5020n, 2026-11-03**; host macOS26.6+, SDK iOS27.3 beta | Not the current stable IDE; stable is27.2 | [Apple release feed](https://developer.apple.com/news/releases/) [requirements](https://developer.apple.com/support/xcode/) |
| Standalone `xcrun mcp-server` | **Preview** per current official Xcode27 release notes | Introduced **Xcode27 beta5**; no app iOS availability gate | Runs without open workspace. Apple documents `sudo xcrun mcp-server enable` and `xcrun mcp-server status`; early-preview limitations remain documented. Do not default to unsafe all-agent permission mode | [Xcode27 release notes](https://developer.apple.com/documentation/xcode-release-notes/xcode-27-release-notes) |

## C. Requested link checks

All seven requested URLs returned meaningful content through `fetch`. None was established as broken or moved. Titles below are readable page titles; the GitHub page represents a file rather than an Apple documentation article.

| Requested URL | Result / title | One verified key fact |
|---|---|---|
| https://developer.apple.com/videos/play/wwdc2026/268/ | **Resolves — “Profile, fix, and verify: Improve app responsiveness with Instruments”** | Uses an Instruments27 workflow with Swift Concurrency, Time Profiler and System Trace. It is **not** the Swift-concurrency session with ID268 in WWDC2025 |
| https://developer.apple.com/documentation/testing/migratingfromxctest | **Resolves — “Migrating a test from XCTest”** | Live guide includes Swift6.4 XCTest/Swift Testing interop: none before6.4; limited with toolchain6.4+ and package tools<6.4; complete when both are6.4+ |
| https://developer.apple.com/documentation/speech/assetinventory | **Resolves — “AssetInventory”** | iOS26+ system-managed module assets; handles installation, locale reservations and readiness |
| https://developer.apple.com/documentation/swiftdata/maintaining-a-local-copy-of-server-data | **Resolves — “Maintaining a local copy of server data”** | iOS17+/Xcode15 sample caches **read-only server-authoritative** earthquake data using unique stable codes for insert-or-update |
| https://developer.apple.com/design/human-interface-guidelines/right-to-left | **Resolves — “Right to left”** | Standard UI mirrors automatically; paragraph alignment follows its own language; do not flip logos/photos or digits within a number |
| https://developer.apple.com/documentation/swiftui/applying-liquid-glass-to-custom-views | **Resolves — “Applying Liquid Glass to custom views”** | Containers share rendering and enable morphing; excessive glass effects/containers can hurt performance |
| https://github.com/apple/swift-openapi-generator/blob/main/Examples/event-streams-client-example/Sources/EventStreamsClient/EventStreamsClient.swift | **Resolves — “apple/swift-openapi-generator — Examples/event-streams-client-example/Sources/EventStreamsClient/EventStreamsClient.swift”** | Includes JSON Lines, JSON Sequence and SSE JSON decoding examples using async iteration and URLSessionTransport |

## D. Conflicts and uncertainties

**Stable Xcode versus beta.** The current stable is **27.2/27B52**, not27.3. Apple lists27.3/27C5020n as beta dated November3. Xcode27 is Apple-silicon-only and requires macOS26.6+; do not reuse Xcode26's Intel/macOS15.6 assumptions. [5] [6]

**Bridge versus standalone server.** `mcpbridge` belongs to the established external-agent flow introduced in26.3 and needs an open project plus the exact settings permission. Standalone `mcp-server` was introduced as a **preview in Xcode27 beta5** and is still described that way in27's release notes. A stable Xcode bundle does not make every contained preview experience GA. No provider or model subscription was researched. [2] [7]

**MobileBuildMCP rename.** Release2.7.1 changes package/binary names and associated configuration/environment/resource naming. The Homebrew **tap still uses `getsentry/xcodebuildmcp`**, but the installed formula/binary is **mobilebuildmcp**. Old `xcodebuildmcp` instructions are not interchangeable with current commands. [8]

**Skill versions versus branch activity.** Five requested skill repositories have tagged releases; Dimillian/Skills has an empty published release list, so it is reported by latest default-branch commit. Commit dates are repository-wide, not proof of the individual skill folder's last edit. `npx skills add ...` normally follows current source and is not a promise to install the release tag listed in this snapshot.

**Localization skill license.** `ios-localization` is **PolyForm Perimeter1.0.0**, not MIT. GitHub's generic “Other/NOASSERTION” metadata is insufficient; the actual LICENSE text includes noncompete restrictions. [9]

**Sosumi repository and correctness.** The actual repository is **NSHipster/sosumi.ai**, not NSHipster/sosumi. Its1.1.0 release warns that extracted conditional-conformance conditions can be incorrect. Use Apple declarations/SDK/compiler as authority for those details; MIT covers the renderer, not Apple's underlying docs. [10]

**Swift OpenAPI minima.** Old universal Swift5.9 guidance is stale for the selected latest stack: generator1.14.4/runtime1.13.4 require Swift6.2; URLSession1.4.0's own manifest is6.1. Runtime iOS13 deployment and iOS15 streaming support are separate from host compiler requirements.

**SQLite on iOS.** No live official Apple per-iOS bundled SQLite version matrix was found. Do not label an upstream SQLite release number as the version bundled on iOS27. FTS5's upstream introduction in3.9.0 is verified, but actual iOS runtime/compile options remain device/OS-build checks. [11]

**Textual and MarkdownUI.** Textual0.5.0 is not flagged prerelease, yet it remains **pre-1.0**, with iOS18 minimum. MarkdownUI is in maintenance mode, not formally deprecated by Apple. Pin and test integrations rather than claim Textual API stability equivalent to1.x. [12] [13]

**Speech locales, including Arabic.** The official docs expose async `supportedLocales`/`installedLocales` rather than a static locale guarantee. Arabic support for SpeechTranscriber was **not documented/verified** here. Check the exact requested locale at runtime on supported hardware. DictationTranscriber can broaden older-hardware/on-device locale coverage but is **not** guaranteed Arabic and is **not** an automatic network fallback. All these newer types still require iOS26+. [14] [15]

**Icon Composer and SF Symbols.** Current official SF Symbols download is named **SF Symbols27**; older8-beta references should not override that page. Its exact release date was not exposed. Icon Composer's public product/download pages did not expose a verifiable exact current app version/date. A search lead suggested27.2, but this was **not corroborated by a public official page**, so it is not asserted. The generic resources page says macOSSequoia+, while the dedicated Icon Composer page says **Tahoe26.4+**; prefer the stricter product-specific requirement. [16] [17] [18]

**Tailscale release dates and platform requirement.** Vendor changelog dates1.104.5 **November2**, while GitHub's release `published_at` is **November3 UTC**. App Store rollout displays a relative date, so no exact store rollout date is inferred. The current US store requires **iOS16.6+**, superseding older setup-page iOS15 guidance. The BSD license is for the open client core, not blanket licensing of every App Store distribution or hosted service. Serve is tailnet-private; **Funnel is public internet exposure**, not a synonym for Serve. [19] [20] [21]

**Swift Testing interoperability.** The general XCTest page still says not to mix APIs within a test, but the specific live migration guide now documents **Swift6.4 interop modes** and cross-library assertions. Apply the specific toolchain/package-tools rules instead of repeating an unconditional “never mix.” The exact bundled Swift Testing library patch is not established merely by “Swift6.4.” [22] [23]

**Legacy and deprecation precision.** ObservableObject is legacy relative to Observation but **not marked deprecated**. NavigationView is explicitly deprecated; Apple's migration guide uses iOS16 as the modern-navigation boundary. The current fetched type page's range “iOS13–27.2 Deprecated” is not evidence that deprecation only began in27.2. [24] [25]

**TestFlight is not direct development install.** Internal testing supports **100 App Store Connect users** and a build expires after **90 days**. Internal distribution does not require Beta App Review, though processing/export compliance remain. External testing follows the review flow. Developer Mode is required for applicable direct development installs from Xcode, but not TestFlight/App Store installs. [26] [27] [28]

**Task3 session mismatch.** WWDC**2026**/268 is the **Instruments responsiveness** session. A same-number WWDC2025 concurrency link would be a different source. All seven requested URLs themselves resolved. [29]

## References

Each table row contains direct official/vendor release, license and documentation URLs. The numbered references below support the cross-cutting instructions and conflicts.

[1]: https://developer.apple.com/library/archive/technotes/tn2339/_index.html "Apple command-line build and test guide"
[2]: https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode "Giving external agents access to Xcode"
[3]: https://github.com/apple/swift-openapi-generator/blob/main/Examples/hello-world-urlsession-client-example/Package.swift "Official OpenAPI URLSession example manifest"
[4]: https://github.com/apple/swift-openapi-generator/blob/main/Examples/hello-world-urlsession-client-example/Sources/HelloWorldURLSessionClient/openapi-generator-config.yaml "Official OpenAPI generator configuration"
[5]: https://developer.apple.com/news/releases/ "Apple developer software release feed"
[6]: https://developer.apple.com/support/xcode/ "Xcode SDKs and system requirements"
[7]: https://developer.apple.com/documentation/xcode-release-notes/xcode-27-release-notes "Xcode27 release notes and standalone MCP preview"
[8]: https://api.github.com/repos/getsentry/MobileBuildMCP/releases/latest "MobileBuildMCP latest release and rename"
[9]: https://raw.githubusercontent.com/dpearson2699/swift-ios-skills/main/LICENSE "Swift iOS Skills PolyForm Perimeter license"
[10]: https://api.github.com/repos/NSHipster/sosumi.ai/releases/latest "Sosumi latest release and extraction limitations"
[11]: https://sqlite.org/fts5.html "SQLite FTS5 extension and compilation"
[12]: https://github.com/gonzalezreal/textual "Textual project documentation"
[13]: https://github.com/gonzalezreal/swift-markdown-ui "MarkdownUI maintenance-mode notice"
[14]: https://developer.apple.com/documentation/speech/speechtranscriber/supportedlocales "SpeechTranscriber supported locales"
[15]: https://developer.apple.com/documentation/speech/dictationtranscriber "DictationTranscriber on-device scope"
[16]: https://developer.apple.com/sf-symbols/ "Current SF Symbols download and requirements"
[17]: https://developer.apple.com/icon-composer/ "Icon Composer product-specific requirement"
[18]: https://developer.apple.com/design/resources/ "Apple Design Resources and generic requirements"
[19]: https://tailscale.com/changelog "Tailscale release changelog"
[20]: https://api.github.com/repos/tailscale/tailscale/releases/latest "Tailscale GitHub release publication metadata"
[21]: https://tailscale.com/kb/1223/funnel "Tailscale Funnel public exposure"
[22]: https://developer.apple.com/documentation/testing/migratingfromxctest "Migrating a test from XCTest and Swift6.4 interoperability"
[23]: https://developer.apple.com/documentation/xctest "XCTest general framework guidance"
[24]: https://developer.apple.com/documentation/combine/observableobject "ObservableObject current status"
[25]: https://developer.apple.com/documentation/swiftui/migrating-to-new-navigation-types "Navigation migration boundary and deprecation"
[26]: https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview "TestFlight overview and90-day build expiry"
[27]: https://developer.apple.com/help/app-store-connect/test-a-beta-version/add-internal-testers "TestFlight internal testers and internal-only builds"
[28]: https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device "Direct development installation and Developer Mode"
[29]: https://developer.apple.com/videos/play/wwdc2026/268/ "Profile fix and verify Improve app responsiveness with Instruments"