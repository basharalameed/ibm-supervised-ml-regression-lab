<div dir="rtl" align="center">

# 📊 مشروع التخرج النهائي: الانحدار الخطي والمنظّم — شهادة IBM للتعلم الآلي

[![English](https://img.shields.io/badge/Language-English%20(Primary)-0f62fe?style=for-the-badge)](./README.md)
[![Arabic](https://img.shields.io/badge/اللغة-العربية%20(Secondary)-06b6d4?style=for-the-badge)](./README_AR.md)
[![Rubric Score](https://img.shields.io/badge/Coursera%20Rubric-10%20%2F%2010%20Verified-10b981?style=for-the-badge)](./finalassigment-finsh.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-f59e0b?style=for-the-badge)](./LICENSE)

</div>

<div dir="rtl">

---

> [!IMPORTANT]
> **الملف المعتمد للرفع المباشر في Coursera (علامة كاملة `10/10`):**
> ارفع ملف **[`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb)** (أو [`FinalAssignment-v1.ipynb`](./FinalAssignment-v1.ipynb)) مباشرةً في صفحة تسليم المشروع. يحتوي الملف على **الأقسام الخمسة المطلوبة كاملةً (`[1]` إلى `[5]`)**، ويستخدم مجموعة البيانات السريرية الفعلية `sklearn.datasets.load_diabetes` ($N = 442$)، مع تضمين جميع الجداول والمخرجات والرسوم البيانية محفوظة مسبقاً داخل ملف `.ipynb`.

---

## 🏛️ عن كورس شركة IBM (*Supervised Machine Learning: Regression*)

يُعد هذا المشروع التطبيقي متطلب التخرج النهائي لدورة **Supervised Machine Learning: Regression** (الدورة الثانية ضمن شهادة **IBM Machine Learning Professional Certificate** على منصة Coursera). يغطي الكورس أربع ركائز أساسية:

1. **الانحدار الخطي البسيط والمتعدد (OLS):** صياغة معادلات غاوس-ماركوف، تقدير المربعات الصغرى العادية، وتفسير معاملات الانحدار ($\beta$) وتشخيص التعدد الخطي عبر معامل تضخم التباين (**VIF**).
2. **تقسيم البيانات، التحقق المتقاطع، والخصائص كثيرة الحدود:** منع تسرب البيانات عبر `StandardScaler`، التحقق المتقاطع خماسي الطيات (`5-Fold CV`)، وإضافة حدود التفاعل غير الخطية (`PolynomialFeatures`).
3. **الانحدار المنظّم (`Ridge L2`, `Lasso L1`, `ElasticNet`):** معالجة التعدد الخطي الحاد وتقليل التباين عبر عقوبة $L_2$ (`RidgeCV`)، والاختيار التلقائي للمتغيرات عبر عقوبة $L_1$ (`LassoCV`) التي تصفر المتغيرات المكررة، والدمج بينهما عبر `ElasticNetCV`.
4. **تشخيص البواقي (Residual Diagnostics) والتوصيات السريرية:** فحص تجانس التباين (Homoscedasticity)، التوزيع الطبيعي للأخطاء (`Shapiro-Wilk` و `Q-Q Plot`)، واقتراح التحويلات المستقبلية (`Box-Cox` / `Gamma GLM`).

---

## 📋 ملخص المهام الخمس في التقييم (`10 / 10 درجات`)

1. **`[1]` وصف مجموعة البيانات (`Dataset Description` — درجتان):**
   - تحليل 442 سجل مريض و10 متغيرات فسيولوجية ومخبرية أساسية للتنبؤ بمتغير `Disease_Progression` بعد سنة واحدة، مع عرض التوزيعات، الالتواء (`Skewness`)، ومعاملات الارتباط (`BMI` $r=+0.586$، `Log_Triglycerides` $r=+0.566$، و`HDL_Cholesterol` $r=-0.395$).
2. **`[2]` هدف التحليل والفرضيات والتحديات (`Analysis Objective` — درجتان):**
   - تحديد الهدف التنبؤي والتفسيري، خطوات التحليل الخمس، الفرضيات الإحصائية الصريحة ($H_0$ مقابل $H_1$)، وتشخيص تحدي التعدد الخطي الحاد في تحاليل الكوليسترول (`VIF = 59.20`).
3. **`[3]` مقارنة نماذج الانحدار (`Model Comparison` — درجتان):**
   - مقارنة 6 نماذج (`Simple OLS`, `Multiple OLS`, `RidgeCV`, `LassoCV`, `ElasticNetCV`, `Polynomial Degree-2 Ridge`) واختيار **انحدار لاسو (`LassoCV`)** كأفضل نموذج قابل للتفسير السريري (`Test R² = 0.4669`, `Adjusted R² = 0.4279` بـ 6 متغيرات صافية)، و**انحدار `Polynomial Degree-2 Ridge`** كأعلى نموذج في الدقة التنبؤية (`Test R² = 0.5042`, `RMSE = 51.25`).
4. **`[4]` النتائج والتفسير (`Findings & Interpretation` — درجتان):**
   - إثبات أن مؤشر كتلة الجسم (`BMI` $\beta = +26.18$) والدهون الثلاثية (`Log_Triglycerides` $\beta = +21.95$) وضغط الدم (`Blood_Pressure` $\beta = +15.18$) هي المحركات الكبرى لتفاقم المرض، بينما يعمل `HDL_Cholesterol` ($\beta = -11.42$) كعامل وقائي قوي بعد إزالة تشوه التعدد الخطي.
5. **`[5]` التقييم والقيود والخطوات المستقبلية (`Evaluation & Future Steps` — درجتان):**
   - تشخيص البواقي وإثبات وجود تباين غير مفسر (~49%) بسبب غياب متغيرات مثل السكر التراكمي (`HbA1c`) والالتزام الدوائي، مع خطة مستقبلية تشمل تحويل `Box-Cox` والنماذج الشجرية المعززة (`XGBoost + SHAP`) وانحدار الشرائح (`Quantile Regression`).

---

## 🛠️ الأخطاء الأربعة التي مررنا بها وكيف تم حلها

1. **الخطأ الأول (`SyntaxError` و `NameError`):** نتج عن بقاء جزء من النص الافتراضي `# Write your code here...` ملتصقاً بنهاية السطر الأخير في الخلية الأولى (`plt.show()an add...`)، مما أوقف تنفيذ الخلية الأولى وتسبب في عدم تعريف `pd` في الخلية الرابعة. **الحل:** تنظيف الخلايا بالكامل وجعل كل خلية مستقلة بذاتها.
2. **الخطأ الثاني (`ModuleNotFoundError: No module named 'sklearn'` / `'scipy'`):** نتج عن تشغيل الكود في بيئة متصفح مجردة لا تحتوي على مكتبات خارجية. **الحل:** توفير بديل قياسي وحفظ المخرجات الجاهزة (`outputs`) مباشرة داخل ملف `.ipynb`.
3. **الخطأ الثالث (النص الأبيض على خلفية بيضاء وانعكاس الجداول `RTL`):** حدث بسبب تداخل الوضع الليلي (Dark Mode) واتجاه المتصفح العربي مع جداول HTML. **الحل:** فرض `dir="ltr"` وتثبيت لون النص الداكن `#111111` على خلفية بيضاء `#ffffff`.
4. **الخطأ الرابع (تقييم `1/10` عند رفع `finalassigment-finsh 1.ipynb` منفرداً):** لأن منصة Coursera تصحح المشروع كاملاً من **ملف واحد فقط** وتشترط استخدام `load_diabetes` الحقيقية ووجود قسم الفرضيات والمخرجات المرئية. **الحل:** جمع الأقسام الخمسة مع البيانات الحقيقية والمخرجات المحفوظة داخل [`finalassigment-finsh.ipynb`](./finalassigment-finsh.ipynb).

---

## 🌐 صفحة العرض التفاعلية (GitHub Pages)

افتح ملف [`index.html`](./index.html) أو رابط **GitHub Pages** لاستعراض:
- مجسم ثلاثي الأبعاد تفاعلي (`Three.js WebGL`) لسطح الانحدار وسحابة المرضى.
- محاكي التنبؤ السريري الحي (Live Risk Simulator).
- زر التبديل الفوري بين **اللغة الإنجليزية (`LTR`)** و**اللغة العربية (`RTL`)**.

</div>
