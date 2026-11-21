# Fujifilm Instax Sales & Business Performance Analysis (2022–2025)

## Overview
Sebuah *dashboard* analitik interaktif multi-halaman (*5 pages*) yang dirancang untuk membedah performa penjualan produk Fujifilm Instax sepanjang periode 2022 hingga 2025. Proyek ini mengubah data transaksi mentah menjadi wawasan visual strategis guna memantau pertumbuhan pendapatan, tren penjualan bulanan dan harian, peringkat performa produk per kategori, efektivitas kanal penjualan (*Online* vs *Offline*), hingga distribusi metode pembayaran menggunakan **Power BI Desktop** dan **Python (Pillow)**.
<img width="1280" height="720" alt="Fujifilm Instax Sales Dashboard" src="LINK_GAMBAR_DASHBOARD_KAMU_DI_SINI" />


---

## Business Questions Framework
Tabel berikut menguraikan pertanyaan bisnis dan analitik utama yang dijawab melalui visualisasi pada *dashboard*:

| Dimensi Analisis | Pertanyaan Bisnis Utama |
| :--- | :--- |
| **Performa & Pertumbuhan Penjualan** | • Bagaimana tren pertumbuhan *Total Revenue*, *Total Orders*, *Products Sold*, dan *Average Order Value* (AOV) selama periode 2022–2025 |
| **Pola Temporal & Musiman** | • Pada hari apa (*Day of Week*) dan bulan apa penjualan mencapai titik puncak tertinggi secara konsisten |
| **Kontribusi Produk & Kategori** | • Kategori produk (*Camera*, *Film*, *Accessories*) mana yang mendominasi pendapatan dibandingkan dengan volume unit terjual |
| **Efektivitas Kanal & Promosi** | • Bagaimana perbandingan kontribusi transaksi antara kanal *Online* dan *Offline*, serta seberapa besar peran promo dalam mendorong pesanan |
| **Preferensi Metode Pembayaran** | • Bagaimana distribusi pendapatan di seluruh metode pembayaran (*Credit Card*, *Bank Transfer*, *PayLater*, dan *E-Wallet*) |

---

## Data Preparation & DAX Modeling (Power BI)
- **Pemodelan Data Relasional (`Fact_Sales` & `Dim_Date`):** Menyusun struktur skema bintang (*star schema*) dan pembersihan tipe data di **Power Query** guna memastikan akurasi *cross-filtering* serta sinkronisasi *slicer* (`Year`, `Month`, `Store / Channel`) di seluruh 5 halaman laporan.
- **Kalkulasi KPI & Pertumbuhan Dinamis (DAX):** Membangun *measures* dinamis untuk metrik inti (*Total Revenue*, *Total Orders*, *Products Sold*, dan *Average Order Value*) beserta perbandingan variansi pertumbuhan terhadap paruh periode pertama (*vs 1st half period*).
- **Pengurutan Kronologis Hari (`Day_Num`):** Mengimplementasikan kolom kunci pengurutan berbasis fungsi `WEEKDAY(Fact_Sales[Tanggal], 2)` dengan fitur *Sort by Column* untuk memastikan urutan grafik dari *Monday* hingga *Sunday* tanpa memicu *circular dependency*.
- **Desain UI/UX Terprogram (*Programmatic Background*):** Menggunakan skrip **Python (`Pillow`)** berskala *high-DPI* (2x *scale* dengan *LANCZOS resampling*) untuk menghasilkan *canvas background* yang seragam, tajam, dan ringan, menggantikan penumpukan *native shapes* di Power BI.

---

## Visualizations & Dashboard Layout (Power BI)
- **Halaman Overview (Executive Summary):** Menampilkan 4 kartu KPI dinamis dengan *sparkline*, grafik tren bulanan (*Area Chart* — *Sales Trend* 2022–2025), peringkat *Top 5 Best-Selling Products* (*Bar Chart*), panel *Key Insights*, komposisi *Sales by Category* (*Donut Chart*), *Channel & Promo Analysis* (*Online vs Offline* & *Promo vs Regular*), serta ringkasan *Payment Methods*.
- **Halaman Sales (Temporal & Category Trends):** Memuat dua *Clustered Column Chart* simetris untuk membedah *Revenue by Day of Week* (Senin–Minggu) serta perbandingan *Annual Revenue by Category* sepanjang tahun 2022–2025.
- **Halaman Products (Full SKU Performance):** Diagram batang horizontal (*Stacked Bar Chart*) yang memetakan *Full Product Revenue Ranking* untuk seluruh SKU produk yang disegmentasikan berdasarkan kategori (*Camera*, *Film*, *Accessories*).
- **Halaman Channels (Store & Platform Breakdown):** Diagram batang vertikal (*Stacked Column Chart*) yang membandingkan *Revenue by Store / Platform* (*Website*, *Tokopedia Official*, *Surabaya Branch*, *Shopee Mall*, dan *Jakarta Official Store*) dengan pembedaan warna kanal *Online* dan *Offline*.
- **Halaman Payments (Payment Method Distribution):** Diagram batang vertikal (*Column Chart*) dengan label data terintegrasi untuk menampilkan *Total Revenue by Payment Method* secara komparatif antara *Credit Card*, *Bank Transfer*, *PayLater*, dan *E-Wallet (GoPay/OVO)*.
- **Navigasi Sidebar Interaktif:** Menggunakan tombol *Page Navigation* kustom di sisi kiri dengan tab halaman bawah disembunyikan (*Hidden Pages*) guna menghadirkan pengalaman pengguna layaknya aplikasi web (*app-like UX*).

---

## Key Business Insights
- **Pertumbuhan Pendapatan yang Kuat:** Total pendapatan mencapai **IDR 6,42 miliar** dari **12,3 ribu pesanan** (AOV: **IDR 520,6 ribu**), mencatatkan lonjakan pertumbuhan sebesar **+47,6%** dibandingkan paruh periode pertama.
- **Perbedaan Kontribusi Revenue vs Volume:** Kategori **Camera** mendominasi perolehan pendapatan sebesar **56,8%** (dipimpin oleh *Instax Mini Evo*), sementara dari sisi volume unit terjual dipimpin oleh produk habis pakai (*consumables*) **Instax Square Film (10s)** sebanyak **5.291 unit** dan **Instax Mini Film (20s)** sebanyak **5.275 unit**.
- **Dominasi Kanal Online & Puncak Akhir Pekan:** Kanal **Online** menyumbang **59,9%** dari total pesanan (dipimpin oleh *Website* dan *Tokopedia Official*) dengan tingkat penggunaan promo sebesar **29,1%**, sementara puncak pendapatan secara konsisten terjadi pada akhir pekan (**Jumat hingga Minggu**).
- **Distribusi Pembayaran yang Seimbang:** Pendapatan terdistribusi sangat merata di seluruh metode pembayaran utama—**Credit Card (IDR 1,64B)**, **Bank Transfer (IDR 1,64B)**, **PayLater (IDR 1,61B)**, dan **E-Wallet (IDR 1,53B)**—menunjukkan fleksibilitas pembayaran yang tinggi di kalangan konsumen.

---

## Strategic Recommendations
- **Strategi Bundling Kamera & Film:** Memanfaatkan tingginya permintaan *Instax Square Film* dan *Instax Mini Film* dengan menawarkan paket *bundling* (Kamera + Film + Aksesoris) untuk meningkatkan *Average Order Value* (AOV) yang sempat mengalami sedikit penurunan (-2,1%).
- **Optimalisasi Kampanye Akhir Pekan (*Weekend Flash Sale*):** Memfokuskan anggaran iklan digital dan promosi terbatas pada hari **Jumat–Minggu** di kanal *Website*, *Tokopedia Official*, dan *Shopee Mall* guna memaksimalkan konversi saat trafik belanja berada di puncaknya.
- **Penguatan Pengalaman Omnichannel di Toko Fisik:** Meningkatkan program *in-store experience* dan *pickup-in-store* di cabang *Surabaya Branch* dan *Jakarta Official Store* untuk mendorong kontribusi kanal *Offline* agar lebih kompetitif terhadap kanal *Online*.

---

## Tools Used
- **Power BI Desktop:** Platform utama untuk pemodelan data relasional (*Data Modeling*), pembersihan data di *Power Query*, penulisan formula **DAX**, pembuatan visualisasi interaktif, serta konfigurasi navigasi multi-halaman.
- **Google Colab (Python / Pillow):** Lingkungan komputasi berbasis *cloud* untuk merancang dan menghasilkan *high-DPI custom canvas backgrounds* beserta elemen kartu dan ikon vektor secara terprogram.
- **Dataset:** Data transaksi penjualan Fujifilm Instax periode 2022–2025 (`Fact_Sales` & `Dim_Date`).
