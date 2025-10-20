# Analisis Deteksi Anomali pada Dataset Inventaris dan Pembelian

Repositori ini berisi notebook dan analisis untuk Ujian Tengah Semester mata kuliah Penambangan Data, dengan fokus pada deteksi anomali dari dataset `Stok` dan `Pembelian`.

---
## Deskripsi Proyek

Proyek ini bertujuan untuk melakukan analisis data secara komprehensif untuk mengidentifikasi berbagai jenis anomali dalam sistem inventaris. Analisis mencakup dua dataset dengan format non-standar:
1.  **Dataset Stok:** Berisi data master produk.
2.  **Dataset Pembelian:** Berisi data transaksi masuk dan keluar.

Tantangan utama proyek ini adalah format data mentah yang kompleks (laporan teks), yang memerlukan teknik parsing khusus sebelum analisis dapat dilakukan.

---
## Metodologi

Alur kerja analisis yang digunakan adalah sebagai berikut:
1.  **Pemuatan & Pembersihan Data:** Mengembangkan skrip parsing custom untuk membaca format file yang unik dan membersihkan data, termasuk koreksi tipe data dan penanganan nilai yang hilang.
2.  **Analisis Data Eksploratif (EDA):** Menggunakan visualisasi seperti Box Plot dan Time-Series Plot untuk memahami distribusi data dan mengidentifikasi outlier secara visual.
3.  **Deteksi Anomali:** Menerapkan pendekatan **statistik (IQR)** dan **berbasis aturan (Rule-Based)** untuk mengidentifikasi anomali secara kuantitatif dan logis.
4.  **Analisis Gabungan:** Membandingkan kedua dataset untuk menemukan anomali sistemik.

---
## Temuan Anomali Utama

Analisis berhasil mengidentifikasi dua kategori anomali utama:

### 1. Anomali Sistemik (Paling Kritis)
Kegagalan sinkronisasi fundamental antara sistem Stok dan Pembelian.
* **2.026 "Produk Hantu":** Produk yang tercatat dalam transaksi pembelian, tetapi tidak terdaftar di data master stok.
* **1.516 "Stok Ajaib":** Produk yang ada di stok tetapi tidak memiliki riwayat pembelian sama sekali.

### 2. Anomali Kualitas Data Internal
Masalah pada kualitas data di dalam masing-masing file.
* **Outlier Statistik:** Ditemukan **164 produk** dengan kuantitas stok ekstrem dan ribuan transaksi pembelian dengan kuantitas yang tidak wajar.
* **Integritas Data:** Ditemukan adanya **duplikasi kode produk** di dalam data master stok.

---
## Rekomendasi

Berdasarkan temuan di atas, rekomendasi utama adalah:
1.  **Perbaiki Proses Bisnis:** Implementasikan alur kerja yang mewajibkan pendaftaran produk baru di sistem master stok sebelum transaksi pembelian dicatat.
2.  **Lakukan Audit Data:** Lakukan pembersihan total pada data master `Stok` untuk memperbaiki duplikasi kode dan menstandarkan data.
3.  **Selidiki Data Historis:** Lakukan investigasi terhadap 1.516 "Stok Ajaib" untuk memahami asal-usulnya.

---
## Cara Menjalankan
1.  Pastikan Anda memiliki file `Dataset UTS - Stok.csv` dan `Dataset UTS - Pembelian.csv`.
2.  Buka notebook `tugas_UTS.ipynb` di lingkungan Jupyter atau Google Colab.
3.  Jika menggunakan Google Colab, jalankan sel pertama untuk menghubungkan Google Drive.
4.  Sesuaikan path file di dalam notebook agar sesuai dengan lokasi dataset Anda.
5.  Jalankan semua sel secara berurutan.

---
## Tautan Video Penjelasan
Tautan video presentasi yang menjelaskan alur kerja dan temuan proyek ini dapat diakses di sini:
* **https://drive.google.com/file/d/1kS8OZvwMu4KsQUY-zJsZ4XOiEwTsDXzI/view?usp=sharing**
