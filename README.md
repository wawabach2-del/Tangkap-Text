# Tangkap Teks (Android, ML Kit)

Mengambil teks dari foto dengan tata letak yang sama, lalu bisa diedit, disalin, dan ditulis ulang di atas foto. OCR berjalan offline di HP (Google ML Kit, model ikut di dalam APK).

## Membuat APK

1. Pasang Android Studio (versi terbaru, JDK 17 sudah ikut).
2. File > Open, pilih folder `TangkapTeks`. Jika diminta membuat Gradle wrapper atau memakai Gradle 8.7, setujui. Tunggu sinkronisasi selesai (butuh internet untuk mengunduh pustaka).
3. Untuk mencoba di HP: aktifkan Opsi Pengembang dan Debug USB, sambungkan HP, tekan Run.
4. Untuk file APK: Build > Build Bundle(s) / APK(s) > Build APK(s). Hasilnya di `app/build/outputs/apk/debug/app-debug.apk`. Salin ke HP dan pasang (izinkan pemasangan dari sumber ini).

Android 10 (API 29) atau lebih baru.

## Cara pakai

1. Pilih foto dari Galeri atau ambil dengan Kamera. Tombol Putar memutar foto 90°.
2. Tekan Tangkap teks.
3. Tab Tata letak: teks di posisi aslinya. Ketuk baris untuk mengubah teks, tebal, atau miring. Geser slider untuk memperbesar.
4. Tab Teks: teks dengan jarak baris dan lekuk kiri dipertahankan. Salin teks, Salin berformat (tempel ke Word atau Docs), atau Bagikan.
5. Tab Ganti di foto: baris yang diedit ditulis ulang di atas foto asli. Simpan gambar menyimpan ke Galeri.

## Batasan

- ML Kit memberi posisi per baris, bukan huruf tebal atau miring. Tebal dan miring diatur manual di dialog edit. Warna dan latar diperkirakan dari piksel foto.
- Ganti di foto paling rapi pada latar polos atau gradasi lembut.
- Aksara yang dibaca: Latin (Indonesia, Inggris, dan bahasa Latin lain).

## Struktur

- `MainActivity.kt`: layar, foto, OCR, tab, salin, simpan
- `LayoutView.kt`: tampilan tata letak yang bisa diketuk
- `TextDrawer.kt`: menggambar satu baris pas di kotaknya
- `TextBuilder.kt`: teks biasa dan HTML dengan jarak dan lekuk
- `Compositor.kt`: menghapus tulisan lama dan menulis teks baru di foto
- `ImageUtils.kt`: membuka foto, orientasi EXIF, pengambilan warna

## Membuat APK lewat GitHub (tanpa Android Studio)

1. Buat repositori baru di GitHub, lalu unggah seluruh isi folder ini (termasuk folder `.github`).
2. Buka tab Actions. Workflow "Build APK" jalan otomatis setiap ada push, atau tekan Run workflow.
3. Setelah centang hijau, buka run tersebut, lalu unduh `TangkapTeks-debug-apk` di bagian Artifacts. Ekstrak zip-nya untuk mendapat `app-debug.apk`.
