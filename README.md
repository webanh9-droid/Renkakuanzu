# WebViewApp

Android WebView app sederhana: splash screen → loading bar → pull to refresh.

## Cara pakai

1. Buka folder ini di **Android Studio** (Open Project).
2. Ganti URL target di:
   `app/src/main/res/values/strings.xml` → `target_url`
3. (Opsional) Ganti nama app & package:
   - Nama app: `strings.xml` → `app_name`
   - Package: `applicationId` di `app/build.gradle` + folder `com/bintang/webviewapp`
4. (Opsional) Ganti icon app di `res/mipmap-*` (default masih bawaan Android Studio, generate lewat Image Asset Studio).
5. Run ke device/emulator, atau Build > Generate Signed Bundle/APK untuk rilis.

## Fitur

- Splash screen (1.5 detik, warna bisa diganti di `colors.xml`)
- Loading bar tipis di atas saat halaman loading
- Pull to refresh (swipe ke bawah untuk reload)
- Tombol back Android navigasi history WebView dulu, baru keluar app
- JS, DOM storage, dan wide viewport sudah aktif

## Build otomatis via GitHub Actions (tanpa Android Studio)

1. Buat repo baru di GitHub (bisa public atau private).
2. Upload semua isi folder ini ke repo itu (lewat web GitHub "Add file > Upload files", atau `git push` kalau ada akses terminal).
3. Buka tab **Actions** di repo → workflow "Build APK" akan jalan otomatis setiap push ke branch `main`.
   - Kalau tidak otomatis jalan, klik workflow itu → **Run workflow** (tombol manual trigger).
4. Tunggu sampai selesai (ikon hijau ✓), lalu klik run yang selesai itu → scroll ke bagian **Artifacts** → download `app-debug.apk`.
5. Pindahkan APK ke HP, install (mungkin perlu izinkan "install dari sumber tidak dikenal").

Catatan: APK ini debug build (belum di-sign untuk rilis ke Play Store), tapi sudah bisa diinstall dan dipakai normal di HP Android manapun.

## Catatan

- `usesCleartextTraffic="true"` diaktifkan supaya HTTP (non-https) juga jalan saat development. Hapus baris itu di `AndroidManifest.xml` kalau target URL sudah HTTPS dan mau lebih aman.
- minSdk 23 (Android 6.0+), targetSdk 34.
