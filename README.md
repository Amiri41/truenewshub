# TrueNews Hub — دليل الرفع والتشغيل

## 1) رفع الملفات على GitHub (سحب وإفلات)

1. افتح مستودعك: `github.com/Amiri41/truenewshub`
2. اضغط **Add file → Upload files**
3. اسحب كل الملفات والمجلدات التالية وأفلتها هناك:
   - `index.html`
   - `index-ar.html`
   - `index-fr.html`
   - `style.css`
   - مجلد `assets/` كاملاً
   - مجلد `admin/` كاملاً
4. اكتب رسالة commit (مثلاً: "أول نسخة من الموقع") واضغط **Commit changes**

## 2) تفعيل GitHub Pages

1. من داخل المستودع: **Settings → Pages**
2. تحت "Build and deployment" اختر:
   - Source: **Deploy from a branch**
   - Branch: **main** / مجلد **/(root)**
3. احفظ. بعد دقيقة أو دقيقتين، رابط موقعك يصير:
   `https://amiri41.github.io/truenewshub/`

## 3) تفعيل لوحة تحكم Decap CMS (لإضافة الأخبار بنفسك)

لوحة التحكم موجودة بمجلد `admin/` وتفتح من: `yoursite.com/admin/`

لكن تحتاج خطوة واحدة إضافية لتفعيل تسجيل الدخول بحساب GitHub (OAuth)، لأن GitHub Pages وحدها لا تكفي لهذا الغرض:

**الطريقة الأسهل (مجانية):**
1. روح لـ https://vercel.com وسجل حساب مجاني (بحساب GitHub)
2. استورد هذا المستودع الجاهز: `github.com/vencax/netlify-cms-github-oauth-provider`
   (أو ابحث في Google عن "decap cms github oauth provider vercel deploy" وستجد زر "Deploy" بضغطة واحدة)
3. أضف فيه بيانات GitHub OAuth App (تُنشأ من: GitHub → Settings → Developer settings → OAuth Apps → New OAuth App)
   - Homepage URL: رابط موقعك
   - Authorization callback URL: الرابط اللي يعطيك ياه Vercel بعد الرفع + `/callback`
4. بعدها تقدر تدخل لـ `yoursite.com/admin/` وتسجل دخول بحساب GitHub مباشرة وتضيف أخبار

> ملاحظة: هذه الخطوة اختيارية بالبداية — الموقع يشتغل ويظهر بشكل احترافي كامل بدونها. تحتاجها فقط عندما تريد تفعليًا إضافة أخبار من لوحة التحكم بدل تعديل الملفات يدويًا.

## 4) تفعيل إعلانات Adsterra

في كل صفحة (`index.html`, `index-ar.html`, `index-fr.html`) ستجد داخل `<head>`:

```html
<!-- ADSTERRA_HEAD_SCRIPT_START -->
<!-- ADSTERRA_HEAD_SCRIPT_END -->
```

الصق سكريبت التحقق/الإعلان اللي تعطيك ياه منصة Adsterra بين هذين السطرين.

كذلك يوجد 3 صناديق إعلانات جاهزة داخل كل صفحة (ابحث عن `ADSTERRA_LEADERBOARD_SLOT`, `ADSTERRA_NATIVE_SLOT`, `ADSTERRA_RECTANGLE_SLOT`) — استبدل النص التوضيحي بكود الإعلان المخصص لكل مكان.

## 5) ربط نطاق مخصص (اختياري)

من **Settings → Pages → Custom domain** تقدر تربط نطاق مدفوع لو اشتريت واحد لاحقًا، وGitHub يفعّل شهادة SSL تلقائيًا.

---

**بنية الملفات:**
```
truenewshub/
├── index.html          ← الصفحة الرئيسية (إنجليزي)
├── index-ar.html        ← الصفحة الرئيسية (عربي)
├── index-fr.html        ← الصفحة الرئيسية (فرنسي)
├── style.css             ← كل التصميم
├── assets/
│   └── logo.svg          ← الشعار
└── admin/
    ├── index.html         ← لوحة التحكم
    └── config.yml         ← إعدادات لوحة التحكم
```
