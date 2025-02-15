# Laporan Proyek Machine Learning - Magrozan Qobus Zaidan

## Domain Proyek

Forecasting harga saham adalah area yang menarik dan menantang dalam machine learning. Pasar saham sangat dinamis dan dipengaruhi oleh berbagai faktor, seperti sentimen investor, kondisi ekonomi makro, berita perusahaan, dan bahkan peristiwa global. Akurasi forecast harga saham dapat memberikan keuntungan signifikan bagi investor dan pelaku pasar lainnya. Proyek ini berfokus pada peramalan harga saham BBNI (Bank Negara Indonesia), sebuah perusahaan yang terdaftar di Bursa Efek Indonesia (BEI).

**harga saham menjadi penting karena beberapa alasan**:
- Pengambilan Keputusan Investasi: Investor menggunakan prediksi harga saham untuk membuat keputusan beli, jual, atau tahan. Prediksi yang akurat dapat membantu memaksimalkan keuntungan dan meminimalkan risiko.
- Manajemen Risiko: Perusahaan dan investor menggunakan prediksi harga saham untuk mengelola risiko portofolio.
- Analisis Pasar: Analis pasar menggunakan prediksi harga saham untuk memahami tren pasar dan membuat rekomendasi investasi.
  
Referensi: [Forecasting dengan LSTM](https://www.kaggle.com/code/jeanfi/forecasting-saham) 

## Business Understanding

### Problem Statements

- Volatilitas Harga Saham: Harga saham BBNI sangat fluktuatif dan sulit diprediksi dengan metode konvensional.
- Kurangnya Model Prediksi Akurat: Model prediksi yang ada belum mampu memberikan akurasi yang memadai untuk pengambilan keputusan.
- 

### Goals

- Mengembangkan Model Prediksi: Membuat model machine learning yang mampu memprediksi harga saham BBNI dengan akurasi yang lebih baik.
- Memberikan Rekomendasi: Memberikan rekomendasi trading berdasarkan hasil prediksi.

    ### Solution statements
    - Model Recurrent Neural Network (RNN): Menggunakan model RNN, khususnya LSTM atau GRU, karena kemampuannya dalam memproses data deret waktu dan menangkap pola temporal.
    - Model Time Series (ARIMA): Menggunakan model ARIMA sebagai pembanding atau baseline karena model ini umum digunakan dalam peramalan deret waktu.
    - Hyperparameter Tuning: Melakukan tuning pada hyperparameter model RNN untuk meningkatkan akurasi prediksi.
  
## Data Understanding
Data yang digunakan dalam proyek ini adalah data historis harga saham BBNI yang diambil dari Yahoo Finance. Data mencakup periode dari tahun 2020 hingga sekarang dan terdiri dari beberapa fitur, antara lain:

### Variabel-variabel dataset adalah sebagai berikut:
- Tanggal: Waktu transaksi.
- Harga Pembukaan (Open): Harga saham saat pembukaan pasar.
- Harga Tertinggi (High): Harga tertinggi saham pada hari tersebut.
- Harga Terendah (Low): Harga terendah saham pada hari tersebut.
- Harga Penutupan (Close): Harga saham saat penutupan pasar.
- Volume: Volume saham yang diperdagangkan.

## Exploratory Data Analysis (EDA)

Dilakukan visualisasi data untuk melihat tren harga saham, volume perdagangan, dan korelasi antar fitur. Analisis statistik deskriptif juga dilakukan untuk memahami distribusi dan karakteristik data.

## Data Preparation

**Tahap persiapan data meliputi**: 
- Pengumpulan Data: Mengunduh data historis harga saham BBNI dari Yahoo Finance.
- Pembersihan Data: Menangani data yang hilang (missing values) jika ada.
- Membuat fitur baru jika diperlukan, seperti indikator teknikal
- Normalisasi/Standarisasi: Menskalakan data ke rentang tertentu menggunakan min-max scaling atau standardization.
- Pembentukan Data Latih dan Data Uji: Membagi data menjadi data pelatihan, validasi, dan pengujian.

## Modeling
Model yang digunakan dalam proyek ini adalah model Recurrent Neural Network (RNN) dengan arsitektur LSTM atau GRU. Model ini dipilih karena kemampuannya dalam memproses data deret waktu dan menangkap pola temporal.

## Kelebihan dan Kekurangan RNN
### Kelebihan:

- Cocok untuk data deret waktu.
- Dapat menangkap pola jangka panjang.
### Kekurangan:

- Sulit dilatih jika urutan terlalu panjang (masalah vanishing gradient).
- Membutuhkan data yang cukup banyak.

## Evaluation

Metrik evaluasi yang digunakan adalah Mean Squared Error (MSE) dan Mean Absolute Error (MAE).

- Mean Squared Error (MSE): Rata-rata kuadrat perbedaan antara prediksi dan nilai aktual.
- Mean Absolute Error (MAE): Rata-rata nilai absolut perbedaan antara prediksi dan nilai aktual.
  
## Hasil Evaluasi
Berdasarkan hasil evaluasi, model RNN dengan arsitektur LSTM atau GRU menunjukkan kinerja yang lebih baik dibandingkan model ARIMA atau model baseline lainnya. Nilai MSE dan MAE yang diperoleh cukup rendah, menunjukkan bahwa model mampu memprediksi harga saham BBNI dengan cukup akurat.

