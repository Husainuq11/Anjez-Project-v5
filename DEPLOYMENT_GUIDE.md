# دليل النشر والتشغيل - موقع أنجز

## 📋 المحتويات
1. [رفع المشروع على GitHub](#رفع-المشروع-على-github)
2. [تشغيل المشروع محلياً](#تشغيل-المشروع-محلياً)
3. [نشر المشروع على الإنترنت](#نشر-المشروع-على-الإنترنت)
4. [استكشاف الأخطاء](#استكشاف-الأخطاء)

## 🚀 رفع المشروع على GitHub

### الخطوة 1: إنشاء مستودع GitHub جديد
1. اذهب إلى [GitHub.com](https://github.com)
2. انقر على "New repository" أو "+"
3. اسم المستودع: `anjez-task-manager`
4. الوصف: `موقع إدارة المهام وتتبع العادات - Task Management and Habit Tracking Website`
5. اختر "Public" أو "Private" حسب رغبتك
6. **لا تضع** علامة على "Initialize with README" (لأن لدينا README بالفعل)
7. انقر "Create repository"

### الخطوة 2: ربط المشروع المحلي بـ GitHub
```bash
# في مجلد المشروع Anjez
git remote add origin https://github.com/YOUR_USERNAME/anjez-task-manager.git
git branch -M main
git push -u origin main
```

**استبدل `YOUR_USERNAME` باسم المستخدم الخاص بك في GitHub**

## 💻 تشغيل المشروع محلياً

### المتطلبات
- Node.js 18+ ([تحميل](https://nodejs.org/))
- Python 3.8+ ([تحميل](https://python.org/))
- Git ([تحميل](https://git-scm.com/))

### الخطوة 1: تشغيل الواجهة الخلفية (Flask)
```bash
cd anjez-backend

# إنشاء بيئة افتراضية
python -m venv venv

# تفعيل البيئة الافتراضية
# على Windows:
venv\Scripts\activate
# على Mac/Linux:
source venv/bin/activate

# تثبيت المتطلبات
pip install -r requirements.txt

# تشغيل الخادم
python src/main.py
```

الخادم سيعمل على: http://localhost:5001

### الخطوة 2: تشغيل الواجهة الأمامية (React)
```bash
# في نافذة طرفية جديدة
cd anjez-frontend

# تثبيت المتطلبات
npm install
# أو إذا كان لديك pnpm:
pnpm install

# تشغيل خادم التطوير
npm run dev
# أو:
pnpm dev
```

الموقع سيعمل على: http://localhost:5173

## 🌐 نشر المشروع على الإنترنت

### خيار 1: Vercel (للواجهة الأمامية)
1. اذهب إلى [vercel.com](https://vercel.com)
2. ربط حساب GitHub
3. استيراد مشروع `anjez-task-manager`
4. تحديد مجلد `anjez-frontend` كمجلد المشروع
5. النشر

### خيار 2: Netlify (للواجهة الأمامية)
1. اذهب إلى [netlify.com](https://netlify.com)
2. "New site from Git"
3. اختيار GitHub وربط المستودع
4. Build command: `cd anjez-frontend && npm run build`
5. Publish directory: `anjez-frontend/dist`

### خيار 3: Heroku (للواجهة الخلفية)
1. إنشاء حساب في [heroku.com](https://heroku.com)
2. تثبيت Heroku CLI
3. في مجلد `anjez-backend`:
```bash
heroku create anjez-backend-app
git subtree push --prefix anjez-backend heroku main
```

## 🔧 استكشاف الأخطاء

### مشاكل شائعة وحلولها

#### 1. خطأ في تثبيت المتطلبات
```bash
# تحديث pip
python -m pip install --upgrade pip

# تثبيت المتطلبات مرة أخرى
pip install -r requirements.txt
```

#### 2. خطأ في تشغيل React
```bash
# حذف node_modules وإعادة التثبيت
rm -rf node_modules package-lock.json
npm install
```

#### 3. مشكلة في الاتصال بين الواجهة الأمامية والخلفية
- تأكد من تشغيل الخادم الخلفي على المنفذ 5001
- تأكد من إعدادات CORS في Flask

#### 4. مشكلة في قاعدة البيانات
```bash
# في مجلد anjez-backend/src
rm database/app.db
python main.py  # سيتم إنشاء قاعدة البيانات تلقائياً
```

## 📱 الميزات المتاحة

### إدارة المهام
- ✅ إضافة مهام جديدة
- ✅ تحديد الأولوية (عالية، متوسطة، منخفضة)
- ✅ تحديد تاريخ الاستحقاق
- ✅ تحديد المهام كمكتملة
- ✅ تصفية المهام (الكل، قيد الانتظار، مكتملة، متأخرة)
- ✅ تعديل وحذف المهام

### تتبع العادات
- ✅ إضافة عادات جديدة
- ✅ تحديد التكرار (يومي، أسبوعي، شهري)
- ✅ تسجيل الدخول اليومي
- ✅ تتبع السلاسل (Streaks)
- ✅ عرض التقدم بصرياً
- ✅ تقويم أسبوعي للعادات

### المزايا العامة
- ✅ دعم اللغتين العربية والإنجليزية
- ✅ تبديل المظهر (فاتح/داكن)
- ✅ تصميم متجاوب (يعمل على الهاتف والكمبيوتر)
- ✅ واجهة مستخدم أنيقة ومرتبة
- ✅ حفظ البيانات محلياً

## 📞 الدعم

إذا واجهت أي مشاكل:
1. تأكد من تثبيت جميع المتطلبات
2. راجع رسائل الخطأ في وحدة التحكم
3. تأكد من تشغيل كل من الواجهة الأمامية والخلفية
4. راجع ملف README.md للمزيد من التفاصيل

---

**تم تطوير هذا المشروع بعناية ليكون جاهزاً للاستخدام الفوري. استمتع بتنظيم مهامك وتتبع عاداتك! 🎯**

