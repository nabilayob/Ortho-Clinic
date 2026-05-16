# 🦴 نظام عيادة العظام — Ortho Clinic Management System
**Demo MVP v1.0 — Complete 15-Page System**

---

## 📁 الملفات (15 صفحة)

| الملف | الوصف |
|-------|-------|
| `login.html` | صفحة تسجيل الدخول |
| `dashboard.html` | لوحة التحكم الرئيسية |
| `book.html` | الحجز الإلكتروني للمرضى (عام) |
| `booking-requests.html` | مراجعة طلبات الحجز |
| `appointments.html` | إدارة المواعيد |
| `patients.html` | قائمة المرضى |
| `patient-profile.html` | ملف المريض الكامل |
| `doctor-visit.html` | مساحة عمل الطبيب |
| `prescriptions.html` | الوصفات الطبية |
| `result-upload.html` | رفع نتائج الأشعة والتحاليل |
| `patient-progress.html` | تقدم المريض ومقارنة النتائج |
| `payments.html` | المدفوعات والفواتير |
| `messages.html` | مركز الرسائل |
| `reports.html` | التقارير والإحصائيات |
| `settings.html` | إعدادات النظام |

---

## 🚀 التشغيل الفوري (بدون Firebase)

### الطريقة 1 — Python Server (الأسهل)
```bash
cd ortho-clinic-demo
python -m http.server 8080
```
ثم افتح: **http://localhost:8080/login.html**

### الطريقة 2 — VS Code Live Server
1. افتح المجلد في VS Code
2. انقر يمين على `login.html`
3. اختر **"Open with Live Server"**

### الطريقة 3 — مباشرة من file://
افتح `login.html` مباشرة — يعمل تلقائياً في وضع العرض

---

## 🔥 إعداد Firebase الكامل

### الخطوة 1: إنشاء المشروع
1. اذهب إلى [console.firebase.google.com](https://console.firebase.google.com)
2. أنشئ مشروعاً جديداً
3. فعّل **Anonymous Authentication** من:
   `Authentication → Sign-in methods → Anonymous → Enable`
4. (اختياري) فعّل **Email/Password Authentication**

### الخطوة 2: إنشاء Firestore
1. `Firestore Database → Create database`
2. اختر **Start in test mode**
3. اختر أقرب region

### الخطوة 3: إنشاء Storage
1. `Storage → Get started → Test mode`

### الخطوة 4: نسخ Config
1. `Project Settings → Your apps → Add app (Web)`
2. انسخ `firebaseConfig`

### الخطوة 5: تحديث الملفات
في **كل ملف HTML** ابحث عن هذا الجزء واستبدله:

```javascript
const firebaseConfig = {
  apiKey:            "YOUR_API_KEY",           // ← استبدل
  authDomain:        "YOUR_PROJECT_ID.firebaseapp.com",
  projectId:         "YOUR_PROJECT_ID",
  storageBucket:     "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId:             "YOUR_APP_ID"
};
```

### الخطوة 6: قواعد Firestore (للتجربة فقط ⚠️)
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

### الخطوة 7: قواعد Storage (للتجربة فقط ⚠️)
```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

> ⚠️ **تحذير:** هذه القواعد للتجربة فقط ولا تصلح للإنتاج.

---

## 🌐 النشر على Firebase Hosting

```bash
npm install -g firebase-tools
firebase login
firebase init hosting
# Public directory: . (نقطة)
# Single page app: No
firebase deploy
```

---

## 🌱 زرع البيانات التجريبية

بعد إعداد Firebase:
1. افتح `dashboard.html`
2. اضغط **"زرع بيانات تجريبية"**
3. انتظر اكتمال العملية (~10 ثواني)

البيانات تشمل: 3 أطباء، 2 فروع، 8 مرضى، 10 مواعيد، 5 زيارات، وصفات، فواتير، طلبات حجز، تحاليل ومقارنات.

---

## 🎨 تصميم النظام

| العنصر | التفاصيل |
|--------|---------|
| اللغة | عربي RTL أولاً |
| الخط | Cairo + Tajawal |
| اللون الرئيسي | `#1a6fce` أزرق طبي |
| الإطار | Mobile-first responsive |
| Firebase | v10.12.0 SDK |

---

## 📋 Firestore Collections

```
users, clinics, branches, doctors, patients,
appointments, online_booking_requests, visits,
diagnoses, prescriptions, prescription_items,
imaging_requests, lab_requests, attachments,
invoices, payments, messages, notifications,
lab_results, lab_result_items, imaging_results,
imaging_comparisons, progress_reviews
```

---

*نظام عيادة العظام — نسخة تجريبية للعرض*
