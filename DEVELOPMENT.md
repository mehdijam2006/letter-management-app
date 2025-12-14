# Development Guide - راهنمای توسعه

## راهنمای سریع برای Flutter پروژه

### 1. ارتباط Flutter
```bash
flutter create letter_management_app
cd letter_management_app
```

### 2. تعریف وابستگی‌ها
```bash
flutter pub get
```

### 3. پروژه را lib/ می کوبی تر کنید

این صاحبری تمام فایل‌های Dart را یا از lib/ بردارید و افزودید.

### 4. ساختار کامل فایل‌های لازم:

- **lib/main.dart** - نقطه ورود
- **lib/models/** - Data models با Hive adapters
- **lib/services/** - Business logic و services
- **lib/screens/** - صفحه‌های UI
- **lib/widgets/** - Components قابل استفاده
- **lib/utils/** - Utilities و helpers

## خطوط اهم توسعه

### 1. سرویس تاریخ شمسی
- استفاده از `jalali_date_time` package
- تنظیم timezone بر Asia/Tehran
- متد لل عملیاتی: add/subtract days, difference calculation

### 2. دیتابیس محلی
- استفاده از Hive برای جسترش:
  - `letters` box برای Letter objects
  - `history` box برای History tracking
  - `syncQueue` box برای pending Google Sheets syncs

### 3. نوتیفیکیشن‌ها
- استفاده `flutter_local_notifications` + `timezone`
- تعریف 4 هشدار (7, 3, 2, 1 روز قبل)
- برای نامه‌های فوری: هر 6 ساعت
- لغو کردن همه نوتیف بعد از بایگانی

### 4. همگام‌سازی Google Sheets
- Google Sheets API endpoint برای apps script
- HTTP POST میخعیس بایگانی‌شده letters
- Background sync وقتی انترنت رفع شود
- SyncQueue برای retry logic

### 5. قفل اپلیکیشن
- BiometricPrompt با local_auth package
- Fallback به Device PIN/Password

### 6. پشتیبان‌گیری
- JSON export شده داتابیس
- Encrypted backup با optional password
- Automatic backup بقبل از reset

## فایل‌های راهنمای

در هر service فاش `TODO` comments بگذارید برای خطوط بعدی.

## تست‌کردن
```bash
flutter run
```

## Build APK
```bash
flutter build apk --release
```

## Web2APK
1. این repository را Clone کنید
2. Web2APK یا تا Appyggy uploads کنید
3. APK را دریافت کنید

---

**نکته مهم**: تمام فایل های Dart باید به دقت بر اساس requirements (30 مرحله) تکمیل شوند.
