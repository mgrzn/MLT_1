# Laporan Proyek Machine Learning - Magrozan Qobus Zaidan

## Domain Proyek

Perdagangan saham melibatkan risiko tinggi dan ketidakpastian.  Investor seringkali mengandalkan analisis teknikal untuk memprediksi pergerakan harga saham, dengan harapan dapat mengambil keputusan investasi yang lebih baik.  Metode machine learning, khususnya Recurrent Neural Network (RNN), semakin populer dalam prediksi harga saham karena kemampuannya menangani data deret waktu (time series).  RNN, terutama varian LSTM (Long Short-Term Memory), sangat efektif dalam mempelajari pola dan ketergantungan jangka panjang dalam data harga saham.

## Business Understanding

### Problem Statements

- Bagaimana cara memprediksi harga saham BBNI dengan akurat menggunakan data historis?
- Apakah model RNN dapat memberikan kinerja prediksi yang lebih baik dibandingkan metode baseline sederhana (misalnya, moving average)?

### Goals

- Membangun dan melatih model RNN (kemungkinan besar LSTM) untuk memprediksi harga penutupan saham BBRI.
- Mengevaluasi kinerja model RNN dibandingkan dengan metode baseline, dan mengidentifikasi potensi peningkatannya.

    ### Solution statements
    - Menggunakan arsitektur LSTM karena kemampuannya menangani ketergantungan jangka panjang dalam data deret waktu harga saham.
    - Melakukan tuning hyperparameter pada model LSTM untuk mengoptimalkan kinerja prediksi. Kemungkinan juga akan dieksplorasi penggunaan beberapa layer LSTM dan variasi arsitektur lainnya.
## Data Understanding
Data yang digunakan adalah data historis harga saham BBRI hingga periode waktu februaru 2025

### Variabel-variabel dataset adalah sebagai berikut:
- Tanggal: Waktu transaksi.
- Harga Pembukaan (Open): Harga saham saat pembukaan pasar.
- Harga Tertinggi (High): Harga tertinggi saham pada hari tersebut.
- Harga Terendah (Low): Harga terendah saham pada hari tersebut.
- Harga Penutupan (Close): Harga saham saat penutupan pasar.
- Volume: Volume saham yang diperdagangkan.

## Data Preparation

**Tahap persiapan data meliputi**: 
- Pengumpulan Data: Mengunduh data historis harga saham BBRI dari sumber yang terpercaya.
- Pembersihan Data: Menangani data yang hilang (missing values) atau anomali. Metode yang umum digunakan adalah imputasi atau penghapusan baris yang mengandung missing values.
- Normalisasi/Standarisasi: Menskalakan data agar berada dalam rentang tertentu (misalnya, 0-1) untuk meningkatkan kinerja model. Metode yang umum digunakan adalah MinMaxScaler atau StandardScaler.
- Pembentukan Data Latih dan Data Uji: Memisahkan data menjadi dua bagian: data latih untuk melatih model, dan data uji untuk mengevaluasi kinerja model. Biasanya, pembagian dilakukan berdasarkan waktu (80% data awal untuk latih, 20% data akhir untuk uji).

## Modeling
Model yang digunakan adalah RNN dengan arsitektur LSTM.  Model LSTM akan dilatih untuk memprediksi harga penutupan saham BBRI berdasarkan data historis.  Proses training melibatkan penyesuaian bobot jaringan saraf agar model dapat memprediksi dengan akurat.

## Evaluation

Metrik evaluasi yang umum digunakan untuk mengukur kinerja model forecasting adalah:

- Mean Squared Error (MSE): Rata-rata kuadrat perbedaan antara prediksi dan nilai aktual.
- Mean Absolute Error (MAE): Rata-rata nilai absolut perbedaan antara prediksi dan nilai aktual.


