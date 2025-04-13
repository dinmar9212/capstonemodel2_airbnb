Berikut adalah file `README.md` dalam bahasa Indonesia untuk proyek Airbnb Capstone berdasarkan Jupyter Notebook yang diberikan. File ini mencakup gambaran umum, tujuan, detail dataset, metodologi, hasil, dan panduan untuk menjalankan analisis.

---

# Analisis Optimalisasi Pendapatan Airbnb di Bangkok

## Gambaran Umum
Proyek ini menganalisis dampak durasi sewa dan strategi penetapan harga dinamis terhadap peningkatan pendapatan listing Airbnb di Bangkok. Dengan memanfaatkan wawasan berbasis data, tujuan proyek ini adalah memberikan rekomendasi yang dapat ditindaklanjuti bagi host untuk mengoptimalkan listing mereka dan memaksimalkan pendapatan.

**Penulis**: Dinmar Pratama  
- GitHub: [dinmar9212](https://github.com/dinmar9212)  
- LinkedIn: [Dinmar Pratama](https://www.linkedin.com/in/dinmar-pratama-2516b8224/)  
- Medium: [dinmarpratama](https://medium.com/@dinmarpratama)

## Tujuan
- Memahami bagaimana durasi sewa (`minimum_nights`) dan strategi penetapan harga dinamis memengaruhi pendapatan Airbnb di Bangkok.
- Mengidentifikasi karakteristik listing dengan pendapatan tinggi.
- Memberikan rekomendasi berbasis data untuk mengoptimalkan durasi sewa dan strategi harga.

## Dataset
Dataset berisi daftar listing Airbnb di Bangkok, yang dapat diakses melalui:  
[Google Drive Link](https://drive.google.com/drive/folders/1A_KBMRFTS5Mthpp46nulso679ML4ZwTF)

### Kolom Utama
- `id`: Identifikasi unik untuk listing
- `name`: Nama listing
- `host_id`, `host_name`: Informasi host
- `neighbourhood`: Lokasi di Bangkok
- `latitude`, `longitude`: Koordinat geografis
- `room_type`: Tipe akomodasi (misalnya, Entire home/apt, Private room)
- `price`: Harga per malam (THB)
- `minimum_nights`: Durasi minimum menginap
- `number_of_reviews`, `reviews_per_month`: Metrik ulasan
- `availability_365`: Hari tersedia dalam setahun
- `estimated_revenue`: Metrik pendapatan yang dihitung

## Metodologi
1. **Pembersihan Data**:
   - Menangani nilai yang hilang pada kolom `name`, `host_name`, `last_review`, dan `reviews_per_month`.
   - Menghapus outlier dan data yang tidak konsisten (misalnya, harga negatif).
2. **Pengolahan Fitur**:
   - Membuat kolom `minimum_nights_category` untuk mengelompokkan listing sebagai:
     - Jangka pendek (1-7 hari)
     - Jangka menengah (8-30 hari)
     - Jangka panjang (>30 hari)
   - Menghitung `estimated_revenue` berdasarkan harga, ketersediaan, dan asumsi pemesanan.
3. **Analisis Eksplorasi Data (EDA)**:
   - Menganalisis distribusi harga dan durasi sewa di berbagai wilayah.
   - Mengidentifikasi listing dengan pendapatan nol untuk optimalisasi.
4. **Strategi Optimalisasi**:
   - **Strategi 1**: Menurunkan harga ke median (1.400 THB) untuk listing jangka pendek dengan pendapatan nol.
   - **Strategi 2**: Menyesuaikan `minimum_nights` menjadi 30 hari untuk listing jangka panjang dengan pendapatan nol.
   - **Strategi 3**: Menghapus listing tidak aktif (tanpa ulasan dan pendapatan nol).
5. **Visualisasi**:
   - Diagram batang bertumpuk untuk membandingkan listing dengan pendapatan nol berdasarkan wilayah sebelum dan sesudah strategi.
   - Histogram untuk menunjukkan distribusi `minimum_nights`.
   - Boxplot untuk menganalisis distribusi harga berdasarkan kategori durasi sewa.
6. **Analisis**:
   - Mengevaluasi efektivitas strategi dengan membandingkan jumlah listing berpendapatan nol sebelum dan sesudah.
   - Merangkum statistik harga dan distribusi wilayah setelah optimalisasi.

## Hasil
- **Sebelum Strategi**:
   - Banyak listing memiliki pendapatan nol, terutama di wilayah dengan permintaan tinggi seperti Vadhana dan Khlong Toei.
   - Listing jangka pendek mendominasi kasus pendapatan nol.
- **Setelah Strategi**:
   - Penurunan signifikan dalam jumlah listing berpendapatan nol (angka pasti tergantung pada versi dataset).
   - Listing jangka pendek mendapat manfaat dari penyesuaian harga, sementara listing jangka panjang memiliki potensi okupansi yang lebih baik.
   - Listing tidak aktif dihapus, menyederhanakan dataset.
- **Wawasan Utama**:
   - Sewa jangka pendek (1-7 hari) lebih umum tetapi membutuhkan harga kompetitif.
   - Sewa jangka menengah (8-30 hari) dapat menarik pemesanan stabil dengan durasi yang disesuaikan.
   - Wilayah seperti Vadhana dan Khlong Toei memiliki potensi tinggi tetapi juga persaingan ketat.

## Rekomendasi
1. **Penetapan Harga Dinamis**:
   - Tetapkan harga mendekati median pasar (misalnya, 1.400 THB) untuk sewa jangka pendek di wilayah kompetitif.
   - Gunakan penyesuaian musiman untuk memanfaatkan permintaan puncak.
2. **Durasi Sewa**:
   - Tawarkan durasi fleksibel, terutama jangka menengah (8-30 hari), untuk menarik pemesanan lebih lama.
   - Batasi `minimum_nights` pada 30 hari untuk listing jangka panjang untuk menyeimbangkan okupansi dan pendapatan.
3. **Manajemen Listing**:
   - Perbarui listing secara rutin untuk menghindari ketidakaktifan (misalnya, pastikan ada ulasan dan ketersediaan).
   - Fokus pada wilayah dengan permintaan tinggi tetapi bedakan melalui fasilitas unik atau harga.

## Persyaratan
Untuk menjalankan analisis, instal pustaka Python berikut:
```bash
pip install pandas matplotlib seaborn missingno scipy statsmodels
```

## Cara Menjalankan
1. Kloning repositori:
   ```bash
   git clone https://github.com/dinmar9212/airbnb-bangkok-analysis.git
   ```
2. Unduh dataset dari [Google Drive link](https://drive.google.com/drive/folders/1A_KBMRFTS5Mthpp46nulso679ML4ZwTF) dan letakkan di direktori proyek sebagai `Airbnb Listings Bangkok.csv`.
3. Buka Jupyter Notebook:
   ```bash
   jupyter notebook Airbnb_Capstone_M2.ipynb
   ```
4. Jalankan semua sel untuk mengulang analisis, visualisasi, dan hasil.

## Struktur Folder
```
airbnb-bangkok-analysis/
├── Airbnb_Capstone_M2.ipynb        # Notebook analisis utama
├── Airbnb Listings Bangkok.csv     # Dataset (unduh terpisah)
├── README.md                      # Dokumentasi proyek
```

## Lisensi
Proyek ini dilisensikan di bawah Lisensi MIT. Silakan gunakan dan modifikasi kode untuk keperluan pendidikan atau pribadi.

## Penghargaan
- Data bersumber dari listing Airbnb di Bangkok.
- Terima kasih kepada komunitas open-source untuk pustaka seperti Pandas, Matplotlib, dan Seaborn.

---
