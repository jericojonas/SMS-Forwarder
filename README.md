# SMS Forwarder Android

Aplikasi Android untuk **meneruskan SMS ke Telegram** secara otomatis, dengan filter berdasarkan **sender** dan **isi pesan**.  

---

## ⚡ Fitur

- Forward semua SMS yang masuk ke Telegram sesuai **setting**.  
- Setting Telegram bot token, chat ID, **sender**, dan **isi pesan**.  
- Menu **Test** untuk mencoba forward SMS manual.  
- Menu **History** untuk melihat semua SMS yang dikirim ke Telegram beserta waktu dan status (Terkirim / Gagal).  
- Bisa berjalan **di background** setiap HP menyala.  
- Simpel, mudah digunakan, cocok untuk tim internal.  

---

## 🛠 Persyaratan

- Android Studio (versi terbaru disarankan)  
- Android SDK minimum: 21 (Lollipop)  
- Device / emulator dengan akses SMS (untuk testing)  

---

## 📦 Instalasi & Build APK

1. Clone repository:

```bash
git clone https://github.com/username/mysmsforwarder.git
cd mysmsforwarder
```

2. Buka project di Android Studio.

3. Tambahkan permission di AndroidManifest.xml:
```bash
<uses-permission android:name="android.permission.RECEIVE_SMS"/>
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
```

4. Build APK debug (untuk testing):
Menu Build → Build Bundle(s) / APK(s) → Build APK(s)
APK debug akan berada di:
```bash
app/build/outputs/apk/debug/app-debug.apk
```

5. Build APK release (untuk distribusi internal):
Menu Build → Generate Signed Bundle / APK → APK → Release
Buat keystore baru atau gunakan yang sudah ada.
Pilih build type: release.
APK release akan berada di:
```bash
app/build/outputs/apk/release/app-release.apk
```

Anggota tim cukup install APK ini, aktifkan Install unknown apps di Android.

---

## 🔧 Setup Telegram
Buat Telegram Bot di BotFather
Dapatkan Bot Token.
Tambahkan Chat ID dari grup atau chat tujuan.
Masukkan token & chat ID di menu Setting di aplikasi.
Tambahkan rule (Sender & Contains) jika ingin filter SMS.

---

## 📝 Catatan
Semua setting disimpan lokal di device menggunakan SharedPreferences.
Jika aplikasi di-uninstall → semua data setting dan history akan hilang.
APK debug hanya untuk internal testing, release APK lebih aman.
Background service akan otomatis berjalan saat HP menyala.

---

## 🔗 Struktur Project
```bash
app/
 └─ src/
     └─ main/
         ├─ java/com/example/mysmsforwarder/
         │   ├─ MainActivity.kt
         │   ├─ TestActivity.kt
         │   ├─ SmsReceiver.kt
         │   ├─ BootReceiver.kt
         │   ├─ TelegramHelper.kt
         │   ├─ PrefsHelper.kt
         │   ├─ HistoryHelper.kt
         │   └─ TelegramSettingDialog.kt
         └─ res/
             ├─ layout/
             │   ├─ activity_main.xml
             │   ├─ activity_test.xml
             │   └─ item_history.xml
             ├─ values/strings.xml
             └─ mipmap/
```

---

## 📌 License
MIT License. Bebas digunakan, modifikasi, dan distribusikan untuk tujuan internal tim.


