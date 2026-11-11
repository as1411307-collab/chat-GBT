# فهرس ChatGPT المنقح — تطبيق iPhone والنواة والأبحاث
آخر تنظيم: 11 نوفمبر 2026

## حدود العمل
هذا الفهرس يخص فقط الملفات والمخرجات التي جُمعت أو كُتبت في مسار **ChatGPT** داخل الفرع `chatgpt/two-months-complete`.
ملفات ونواتج أي نموذج آخر **خارج نطاق الفهرسة والتنظيف**؛ لا تُقرأ ولا تُنقل ولا تُعدّل ولا تُحذف دون توجيه صريح.
فرع `main` لا يتغير.

**تنبيه:** هذه مكتبة أبحاث ومتطلبات ومقتطفات تاريخية، وليست شهادة بأن التطبيق موجود أو يعمل. ملفات الحزم البرمجية الأصلية التي لم تُنقل بعد ليست ضمن الشيفرة القابلة للبناء في هذا الفرع.

## 1) الملفّات الأساسية — اقرأها أولًا
ترتيب قراءة مقترح للعثور على المعلومة دون الغرق في الملفات الطويلة:

| الغرض | الملف المرجعي | المعنى |
|---|---|---|
| المتطلبات الأصلية | [Original_168_User_96_Assistant_Requirements](01_Requirements_History/Original_168_User_96_Assistant_Requirements.md) | تجميع تاريخي للطلبات والتعليمات وليس قائمة قرارات نهائية |
| التسلسل والقرارات | [CHRONOLOGY](01_Requirements_History/CHRONOLOGY.md) | متى تغيّرت الاختيارات وما هو تاريخها |
| أحدث مراجعة للمعماريات | [Last_Architectures_Review](03_Architecture_Core/2026-11-06-Last_Architectures_Review.md) | مرجع للمقارنة والقرار الهندسي |
| تفاصيل واجهة iPhone | [iOS_Sovereign_Master_Blueprint](02_iOS_App_Xcode/2026-11-08-iOS_Sovereign_Master_Blueprint.md) | مواصفات بحثية لـ SwiftUI وXcode والواجهة |
| التعلم والتسجيل | [DESIGN_REQUIREMENTS_AND_EVIDENCE](04_Memory_Learning/DESIGN_REQUIREMENTS_AND_EVIDENCE.md) | متطلبات التسجيل السلبي والذاكرة |
| مراجعة الأمان | [NEXUS_Reference_Audit](06_Verification_Security/2026-11-01-NEXUS_Reference_Audit.md) | ملاحظات المراجعة، لا تعني تنفيذ الإصلاحات |
| حقيقة الاختبارات | [VERIFICATION_REPORT](06_Verification_Security/2026-11-09-VERIFICATION_REPORT.md) | الاختبارات المبلّغ عنها وحدودها |
| حالـة الادعاءات | [VERIFICATION_POLICY](12_Claims_Status/VERIFICATION_POLICY.md) | تمييز المدّعى والمُراجع والمُختبر |

## 2) مراجع متخصصة — افتحها عند الحاجة فقط
- **أبحاث iPhone:** [iPhone_Unique_Findings](02_iOS_App_Xcode/iPhone_Unique_Findings_2026-11-09.md) ثم [iPhone_753_Research_One_File_FULL](02_iOS_App_Xcode/iPhone_753_Research_One_File_FULL.md).
- **تصحيحات بناء iOS والأدلة:** [practical-corrections-and-sources](02_iOS_App_Xcode/2026-11-09-practical-corrections-and-sources.md) و[753_URLS_CORRECTED_EVIDENCE_LEDGER](06_Verification_Security/753_URLS_CORRECTED_EVIDENCE_LEDGER.csv).
- **الأدوات والتكاملات:** [iOS_Tools_Skills_Expanded_Master](07_Tools_Skills_Integrations/iOS_Tools_Skills_Expanded_Master_2026.md) و[agents-all-in-one](07_Tools_Skills_Integrations/2026-11-09-agents-all-in-one.md).
- **الأكواد التاريخية والمقتطفات:** [Extracted_Code_From_Files](08_Implementation_Artifacts/Extracted_Code_From_Files_2026-11-08.md) و[Historical_Agent_Core.py](08_Implementation_Artifacts/Historical_Agent_Core.py). لا تُعامل على أنها منتج جاهز.
- **أبحاث المستودعات العامة:** [Report_05_Cross_Comparison](05_Repository_Research/Report_05_Cross_Comparison.md) ثم التقارير التفصيلية عند الحاجة.

## 3) أرشيف مرجعي — ليس مسار التنفيذ اليومي
- `01_Requirements_History/`: الوثائق التاريخية القديمة والموسوعات الطويلة، منها `Unified_Encyclopedia_FULL.md`.
- `02_iOS_App_Xcode/`: نسخ متعدّدة من التفريغ البحثي الكبير. التشابه في الفصول لا يعني تطابقًا تامًا.
- `03_Architecture_Core/`: تصورات قديمة وبدائل تصميم سابقة؛ لا تعتبر تعليمات للتنفيذ تلقائيًا.
- `05_Repository_Research/`: كتالوجات مطولة HTML وMarkdown للبحث المرجعي.
- `08_Implementation_Artifacts/`: حزم وأكواد ومحاولات سابقة تحتاج مراجعة وتشغيل فعلي قبل الاعتماد.
- `10_Raw_Indexes/`: فهارس ضخمة للملفات والفروع، وهي أدلة مصدر وليست ملفات بناء للتطبيق.
- `11_Asset_Register/`: سجل ما وصل وما لم يصل من المواد الأصلية.

## 4) نتيجة التدقيق على ملفات هذا الفرع
- **68 ملفًا** عند فحص Git tree السابق، ببيانات إجمالية قدرها **15,103,201 بايت**.
- **صفر أزواج متطابقة في Git blob SHA**: لا توجد نسخة مطابقة بالكامل يمكن حذفها بثقة اعتمادًا على البصمة وحدها.
- فحص تشابه لأربعة أزواج من وثائق ChatGPT الصغيرة والمتوسطة لم يُظهر احتواءً نصيًا كاملًا يبرر حذف إحداها.
- كُتِب هذا الفهرس لتقليل التصفح والتشتت؛ **لم تُحذف ملفات مستقلة لمجرد تشابهها في الموضوع، ولم تُنقل مصادر أخرى**.
- **لا تثق بعناوين مثل «working source» و«verification» وحدها**؛ راجع ملف إثبات الاختبارات وما لم يُنفّذ بالفعل.
- المواد الأصلية الكبيرة/الثنائية وبعض مستندات Library لم تُنقل بعد بالكامل، لذا ليست هذه المكتبة إحصاءً نهائيًا لكل المصادر.

## 5) حدود السلامة
- لا تعديل لأي ملفات من خارج عمل ChatGPT، حتى لو ظهرت ضمن شجرة المستودع نفسها.
- لا تغيير لفرع `main` أو أي مستودع آخر.
- لا حذف للأصول غير المكررة دون دليل قابل للتحقق على أنها غير مفيدة إطلاقًا.
