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

### Goals

- Mengembangkan Model Prediksi: Membuat model machine learning yang mampu memprediksi harga saham BBNI dengan akurasi yang lebih baik.
- Memberikan Rekomendasi: Memberikan rekomendasi trading berdasarkan hasil prediksi.

    ### Solution statements
    - Model Recurrent Neural Network (RNN): Menggunakan model RNN, khususnya LSTM atau GRU, karena kemampuannya dalam memproses data deret waktu dan menangkap pola temporal.
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
  
Data tidak memiliki missing value 

Dataset: [Saham BBNI di Yahoo finance](https://finance.yahoo.com/quote/BBNI.JK/)

## Exploratory Data Analysis (EDA)

Dilakukan visualisasi data untuk melihat tren harga saham :
- Pada 10 dan 11 Februari, harga saham BBNI mengalami tekanan jual
- 12 Februari menunjukkan lonjakan harga signifikan dengan volume transaksi yang meningkat.
- 13 Februari kembali mengalami tekanan kecil, tetapi masih dalam rentang stabil.
- 14 Februari terjadi kenaikan harga yang kuat, ditandai dengan candle hijau besar, menandakan sentimen bullish.
- Harga terlihat cukup volatile antara 10-14 Februari.
- ![image](https://github.com/user-attachments/assets/979e8959-a57c-4d5d-874c-0e5239137e0f)

  
## Data Preparation

**Tahap persiapan data meliputi**: 
- Pengumpulan Data: Mengunduh data historis harga saham BBNI dari Yahoo Finance dengan libarary yfinance.
- mengambil data dari kolom close untuk dijadikan harga price
- menghapus data stockssplit dan dividen
- mengecek missing value
- membuat data prices diambil dari kolom close dan dijadikan array 2d dengan shape (1240,1)
- Normalisasi/Standarisasi: Menskalakan data ke rentang tertentu menggunakan min-max scaling atau standardization.
- Pembentukan Data Latih dan Data Uji: Membagi data menjadi 80% data pelatihan dan 80% data pengujian.
- memfilter data frame mulai tanggal 01-01-2020 dan membuat salinan (copy) dari DataFrame df yang berisi data historis harga saham
- ![image](https://github.com/user-attachments/assets/3395a16c-f8f2-4c41-a9ad-54b0c5fb14b2)



## Modeling
Model yang digunakan dalam proyek ini adalah model Recurrent Neural Network (RNN) dengan arsitektur LSTM atau GRU. Model ini dipilih karena kemampuannya dalam memproses data deret waktu dan menangkap pola temporal.
### Arsitektur model
SimpleRNN (Recurrent Neural Network):
- units=32: Lapisan ini memiliki 32 unit atau neuron. Setiap unit RNN memiliki memori internal yang memungkinkan mereka untuk memproses urutan data dan mempertahankan informasi dari langkah waktu sebelumnya.
- input_shape=(lookback, 1): Ini menentukan bentuk masukan ke lapisan RNN.
lookback: Ini adalah jumlah langkah waktu ke belakang yang digunakan untuk memprediksi nilai berikutnya dalam urutan. Misalnya, jika lookback=10, model akan melihat 10 nilai sebelumnya untuk memprediksi nilai selanjutnya.
- 1: Ini menunjukkan bahwa setiap langkah waktu memiliki satu fitur. Dalam kasus deret waktu univariat (satu variabel), nilainya adalah 1.
Dense :
- units=1: Lapisan ini adalah lapisan fully connected yang memiliki satu neuron. Ini digunakan untuk menghasilkan output akhir model, yang dalam hal ini adalah prediksi nilai tunggal.
Cara kerja algoritma :

Lapisan SimpleRNN memproses urutan data langkah demi langkah. Pada setiap langkah waktu, unit RNN menerima input dan status tersembunyi dari langkah waktu sebelumnya. Unit RNN kemudian memperbarui status tersembunyi dan menghasilkan output. 

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
  
Nilai MSE 12780.9 menunjukkan bahwa rata-rata kuadrat kesalahan prediksi adalah sekitar 12780.9 unit (kuadrat dari satuan harga saham) Nilai MAE 92.33 berarti bahwa rata-rata kesalahan prediksi adalah sekitar 92.33 unit (satuan harga saham).
  
## Hasil Evaluasi
Berdasarkan hasil evaluasi, model RNN dengan arsitektur LSTM atau GRU menunjukkan kinerja baik. Nilai MSE dan MAE yang diperoleh cukup rendah, menunjukkan bahwa model mampu memprediksi harga saham BBNI dengan cukup akurat. dengan ini dari problem statements diatas kita sudah memenuhi goals yang ada yaitu mengembangkan model prediksi saham dan rekomendasi trading berdasarkan hasil prediksi.

![image](https://github.com/user-attachments/assets/0d1d843b-35b5-4f4b-8481-47d58c49fbb3)


