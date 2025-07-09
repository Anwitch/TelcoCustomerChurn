
# Analisis Churn Pelanggan Telco

## Pendahuluan
Proyek ini merupakan studi mendalam tentang churn pelanggan di industri telekomunikasi. Churn pelanggan, atau tingkat pelanggan yang berhenti menggunakan layanan, adalah tantangan signifikan yang dapat mengikis pendapatan dan menghambat pertumbuhan bisnis. Dengan menganalisis data historis pelanggan, proyek ini bertujuan untuk mengidentifikasi faktor-faktor pendorong churn.

## Tujuan Proyek
1.  **Mengidentifikasi Faktor Pendorong Churn**: Menemukan pola dan variabel kunci (demografi, layanan, kontrak, dll.) yang paling berkorelasi dengan keputusan pelanggan untuk churn.

## Sumber Data
Dataset yang digunakan dalam proyek ini adalah `telco_cleaned.csv` yang sudah dilakukan proses pembersihan dari dataset kaggle https://www.kaggle.com/datasets/blastchar/telco-customer-churn, yang berisi 7043 baris data pelanggan dengan 20 fitur yang berbeda. Data ini mencakup informasi demografi pelanggan, layanan yang mereka gunakan, detail tagihan, dan status churn mereka.

**Detail Kolom Data:**
-   `gender`: Jenis kelamin pelanggan (Female, Male)
-   `SeniorCitizen`: Apakah pelanggan adalah warga senior (0: No, 1: Yes)
-   `Partner`: Apakah pelanggan memiliki pasangan (Yes, No)
-   `Dependents`: Apakah pelanggan memiliki tanggungan (Yes, No)
-   `tenure`: Jumlah bulan pelanggan telah berlangganan layanan
-   `PhoneService`: Apakah pelanggan memiliki layanan telepon (Yes, No)
-   `MultipleLines`: Apakah pelanggan memiliki beberapa jalur telepon (Yes, No)
-   `InternetService`: Penyedia layanan internet pelanggan (DSL, Fiber optic, No)
-   `OnlineSecurity`: Apakah pelanggan memiliki keamanan online (Yes, No)
-   `OnlineBackup`: Apakah pelanggan memiliki cadangan online (Yes, No)
-   `DeviceProtection`: Apakah pelanggan memiliki perlindungan perangkat (Yes, No)
-   `TechSupport`: Apakah pelanggan memiliki dukungan teknis (Yes, No)
-   `StreamingTV`: Apakah pelanggan memiliki streaming TV (Yes, No)
-   `StreamingMovies`: Apakah pelanggan memiliki streaming film (Yes, No)
-   `Contract`: Jenis kontrak pelanggan (Month-to-month, One year, Two year)
-   `PaperlessBilling`: Apakah pelanggan menggunakan tagihan tanpa kertas (Yes, No)
-   `PaymentMethod`: Metode pembayaran pelanggan (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
-   `MonthlyCharges`: Jumlah tagihan bulanan pelanggan
-   `TotalCharges`: Total jumlah yang ditagihkan kepada pelanggan
-   `Churn`: Apakah pelanggan churn atau tidak (Yes, No) - **Variabel Target**

## Metodologi Analisis

### Pembersihan Data
-   **Penanganan `TotalCharges`**: Mengidentifikasi dan mengonversi kolom `TotalCharges` dari tipe objek ke numerik. Nilai kosong pada kolom ini (yang kemungkinan besar menunjukkan pelanggan baru tanpa tagihan total) ditangani dengan imputasi dengan data MonthlyCharges.
-   **Konsistensi Data**: Memastikan tidak ada duplikasi data dan format data konsisten.

### Analisis Data Eksplorasi (EDA)
-   **Distribusi Churn**: Menganalisis proporsi churn dan non-churn untuk memahami ketidakseimbangan kelas.
-   **Analisis Univariat & Bivariat**:
    -   Visualisasi distribusi setiap fitur (numerik dan kategorikal).
    -   Menganalisis hubungan antara setiap fitur dengan variabel target `Churn` menggunakan grafik batang, histogram, dan box plot.
    -   Fokus pada fitur-fitur seperti `Contract`, `InternetService`, `PaymentMethod`, `tenure`, `MonthlyCharges`, dan layanan tambahan.
-   **Korelasi**: Menghitung dan memvisualisasikan matriks korelasi untuk fitur numerik.



## Hasil dan Temuan Utama
Berdasarkan analisis, beberapa temuan kunci yang signifikan adalah:

-   **Kontrak Bulanan (Month-to-month)**: Pelanggan dengan kontrak bulanan menunjukkan tingkat churn yang jauh lebih tinggi dibandingkan dengan pelanggan yang memiliki kontrak satu atau dua tahun. Ini menunjukkan kurangnya komitmen jangka panjang.
-   **Layanan Internet Fiber Optic**: Pelanggan yang menggunakan layanan internet Fiber Optic memiliki probabilitas churn yang lebih tinggi. Ini mungkin mengindikasikan masalah kualitas layanan atau harapan pelanggan yang tidak terpenuhi.
-   **Metode Pembayaran Electronic Check**: Pelanggan yang membayar melalui Electronic Check cenderung lebih sering churn. Ini bisa jadi karena proses pembayaran yang kurang nyaman atau indikator demografi tertentu.
-   **Tenure Rendah**: Pelanggan baru (dengan `tenure` rendah) memiliki risiko churn yang lebih tinggi, yang merupakan pola umum di banyak industri.
-   **Layanan Tambahan**: Pelanggan yang tidak berlangganan layanan tambahan seperti Online Security, Online Backup, Device Protection, dan Tech Support juga menunjukkan tingkat churn yang lebih tinggi.

## Rekomendasi Bisnis
Berdasarkan temuan, berikut adalah beberapa rekomendasi strategis untuk perusahaan Telco:

1.  **Strategi Retensi Kontrak**:
    -   Tawarkan insentif menarik (diskon, upgrade gratis) kepada pelanggan dengan kontrak bulanan untuk beralih ke kontrak jangka panjang (1 atau 2 tahun).
    -   Fokus pada komunikasi nilai jangka panjang dari layanan.
2.  **Peningkatan Kualitas Layanan Fiber Optic**:
    -   Lakukan audit kualitas layanan untuk pelanggan Fiber Optic, terutama di area dengan tingkat churn tinggi.
    -   Tingkatkan dukungan teknis dan respons terhadap keluhan pelanggan Fiber Optic.
3.  **Optimalisasi Metode Pembayaran**:
    -   Dorong pelanggan Electronic Check untuk beralih ke metode pembayaran otomatis yang lebih stabil (kartu kredit/transfer bank otomatis) dengan menawarkan bonus kecil atau kemudahan.
    -   Selidiki apakah ada masalah spesifik dengan proses Electronic Check yang menyebabkan frustrasi.
4.  **Program Onboarding & Loyalitas Awal**:
    -   Implementasikan program onboarding yang kuat untuk pelanggan baru (`tenure` rendah) untuk memastikan mereka puas dengan layanan dan merasa dihargai.
    -   Tawarkan layanan tambahan (Online Security, Tech Support) secara gratis untuk periode awal atau dengan diskon untuk meningkatkan keterikatan.

## Teknologi yang Digunakan
-   **Bahasa Pemrograman**: Python
-   **Pustaka Data Analysis**: Pandas
-   **Pustaka Visualisasi**: Matplotlib, Seaborn
-   **Lingkungan Pengembangan**: Jupyter Notebook
