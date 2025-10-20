[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/XxdT5pUo)
Repository for final lesson before mid term of computer graphic course

# Laporan Analisis Windowing dan Deteksi Segmen (UTS Komputer Grafik)

## Nama : Agastya Dava Nurrahman

## NIM : 1313623052

# 1. Analisis Ukuran Window Ideal (Objective 1)

Ukuran Window yang Digunakan: 3 x 3 piksel.

Justifikasi Ukuran 3x3:
Penggunaan window 3x3 dianggap ideal karena:

Representasi Geometri Dasar: Ukuran 3x3 adalah matriks terkecil yang dapat secara lengkap merepresentasikan keempat orientasi dasar segmen garis (horizontal, vertikal, diagonal) yang tipis (1-piksel).

Efisiensi Komputasi: Meminimalkan beban pemrosesan hanya 9 operasi per piksel sambil tetap efektif dalam deteksi fitur minimal.

Penentuan Pusat: Memiliki pusat yang jelas, penting untuk menandai lokasi segmen yang terdeteksi dengan akurat (Goal 3).

# 2. Pola Window Segmen yang Tepat (Objective 2)

Berdasarkan dumping semua window 3x3 non-empty dari console output, berikut adalah empat pola matriks boolean yang digunakan sebagai filter windows untuk mengidentifikasi segmen lurus tipis.

# Pola Horizontal (H)

Digunakan untuk mendeteksi segmen garis mendatar 1-piksel.

0 0 0
1 1 1
0 0 0

# Pola Vertikal (V)

Digunakan untuk mendeteksi segmen garis tegak 1-piksel.

0 1 0
0 1 0
0 1 0

# Pola Diagonal 45 Derajat (D1)

Digunakan untuk mendeteksi segmen diagonal (kiri atas ke kanan bawah).

1 0 0
0 1 0
0 0 1

# Pola Diagonal 135 Derajat (D2)

Digunakan untuk mendeteksi segmen diagonal (kanan atas ke kiri bawah).

0 0 1
0 1 0
1 0 0

Logika Pencocokan (Filtering):
Algoritma pencocokan (compareMatrix) hanya mencari kesesuaian pada posisi di mana elemen filter bernilai '1'. Ini memastikan detektor bersifat toleran terhadap noise yang mungkin berada di sekitar segmen garis utama.

# 3. Verifikasi Implementasi (Objective 3)

Algoritma deteksi otomatis telah diimplementasikan di drawingcanvas.cpp. Keberhasilan algoritma diverifikasi secara visual dengan menggambar persegi panjang kecil berwarna ungu pada setiap lokasi piksel yang berhasil dicocokkan oleh salah satu filter segmen di atas.

1. Pengumpulan Detektor: Semua pola ideal yang ditemukan pada Objective 2 (Pola H, V, D1, D2) digunakan sebagai detektor dalam fungsi segmentDetection.

2. Penyaringan Wilayah: Perbandingan matriks dilakukan menggunakan fungsi compareMatrix untuk menyaring (filter) wilayah yang cocok (matching region) di seluruh canvas.

3. Verifikasi Visual: Keberhasilan deteksi diverifikasi secara visual dengan menggambar persegi panjang kecil berwarna ungu pada setiap lokasi piksel pusat dari window yang cocok. Penanda ungu ini secara langsung memverifikasi solusi algoritma pada canvas.

4. Kebenaran Kode Sumber: Karena Objective 3 hanya menilai kebenaran source code (yang berarti implementasi detektor mencerminkan hasil analisis), kode telah dikonfigurasi untuk secara eksplisit menggunakan pola dari Objective 2, menjamin konsistensi antara laporan dan implementasi.
