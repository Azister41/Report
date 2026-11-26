Generator Test Report (Excel & PDF)

Aplikasi web satu file untuk mengisi data laporan uji tekstil, lalu mengekspornya ke Excel (.xlsx) dan PDF dengan format yang mengikuti file contoh. Semuanya berjalan di browser, tanpa server dan tanpa instalasi.

Fitur

• Form per halaman: Hal 1 (header, applicant, foto sampel), Hal 2 (sample description), Hal 3 (summary dan kontak), Hasil Uji (Seam Strength, Dimensional Change, Wash and Wear, Appearance, Attachment).
• Tabel dinamis: tambah atau hapus baris, tambah grup (mis. Shell dan Lining). Halaman bertambah otomatis dan nomor "Page x of N" ikut menyesuaikan.
• Shrinkage (%) dihitung otomatis sebagai rumus Excel asli.
• Rating FAIL otomatis berwarna merah, seperti di template.
• Upload foto sampel, otomatis pas di kotaknya.
• Export Excel: memakai template asli sebagai dasar, jadi gaya, merge, dan logo tetap sama.
• Export PDF: digambar langsung dari isi Excel yang sama.
• Nama file otomatis, mis. 3155_Report_SGR-1211263155_L_L__BEAN.xlsx.

Cara pakai

1. Buka halaman web (atau file index.html langsung di browser).
2. Isi data di tab Hal 1, Hal 2, Hal 3, dan Hasil Uji.
3. Tekan Export ke Excel atau Export ke PDF.

Untuk hasil PDF yang paling identik dengan cetakan Excel, buka file .xlsx hasil export di Microsoft Excel lalu Save as PDF.

Deploy ke GitHub Pages

1. Ganti nama file HTML menjadi index.html.
2. Buka Settings → Pages.
3. Pilih Deploy from a branch, branch main, folder / (root).
4. Tunggu beberapa menit, lalu buka URL yang muncul.

Cara kerja

Bagian
Penjelasan
Template
File Excel contoh disematkan di dalam HTML (base64). Saat export, hanya isi sel yang diganti lewat XML, sehingga format asli tidak berubah.
Halaman dinamis
Tabel hasil uji disusun ulang dari blok bergaya template, lalu ditata per halaman (baris 8–50). Tabel yang tidak muat pindah ke halaman berikutnya.
Excel
Paket .xlsx diolah dengan JSZip. Excel menghitung ulang rumus saat file dibuka.
PDF
Penulis PDF sendiri membaca isi xlsx (sel, merge, border, gambar) dan menggambarnya ke halaman A4. Font memakai Carlito.

Batasan

• PDF dibuat ulang dari isi Excel, bukan hasil cetak Excel asli. Bisa ada selisih tipis pada skala, ukuran kertas (A4), dan ketebalan garis.
• Jumlah baris di halaman 3 (Summary Of Test Result) tetap 5.
• Tinggi baris belum menyesuaikan otomatis untuk semua teks panjang yang membungkus.
• Tanggal yang di template berupa rumus TODAY() disimpan sebagai tanggal tetap.
• Hasil diuji lewat LibreOffice dan poppler. Sebaiknya cek juga di Excel asli.

Privasi

Semua data diproses di browser. Tidak ada data atau foto yang dikirim ke server.

Struktur repo

index.html   # aplikasi (template Excel, JSZip, dan font sudah tertanam)
README.md

Pengembangan

• Template baru: ganti string base64 template di bagian TEMPLATE_B64 dan sesuaikan alamat sel yang diisi.
• Tambah jenis uji: tambahkan bagian baru di SEC dan makeUnits (pembuat tabel per halaman).

Lisensi dan atribusi

• Kode aplikasi: tentukan sendiri (mis. MIT).
• JSZip: MIT atau GPLv3.
• Font Carlito (subset, tertanam di PDF): SIL Open Font License 1.1.
• Logo dan nama Texlab adalah milik pemiliknya. Pastikan kamu berhak memakainya sebelum repo dibuat publik.
