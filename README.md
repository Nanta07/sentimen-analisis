# Sentiment Analysis Review Tokopedia menggunakan Machine Learning

## Ringkasan Proyek

Proyek ini merupakan implementasi **analisis sentimen ulasan Tokopedia** menggunakan pendekatan **Natural Language Processing (NLP)** dan **machine learning**. Tujuan utama proyek adalah mengklasifikasikan ulasan pengguna ke dalam dua kelas sentimen, yaitu **positif** dan **negatif**, berdasarkan teks review yang diberikan oleh pengguna.

Proyek ini dirancang sebagai **portfolio teknikal** untuk menunjukkan kemampuan end-to-end dalam pengolahan data teks: mulai dari data preprocessing bahasa Indonesia, feature engineering, pelabelan sentimen, eksplorasi data, hingga pelatihan dan evaluasi beberapa model machine learning.

---

## Problem Statement

Dalam platform e-commerce, ulasan pengguna berperan penting dalam:

* Menentukan reputasi produk dan penjual
* Membantu calon pembeli mengambil keputusan
* Menjadi sumber feedback bagi penjual dan platform

Namun, jumlah ulasan yang sangat besar membuat analisis manual tidak efisien. Oleh karena itu, dibutuhkan sistem otomatis berbasis machine learning untuk memahami sentimen pengguna dari teks ulasan.

---

## Tujuan Proyek

1. Membangun pipeline NLP untuk bahasa Indonesia.
2. Membersihkan dan menormalisasi teks ulasan Tokopedia.
3. Melakukan pelabelan sentimen menggunakan pendekatan leksikon.
4. Mengekstraksi fitur teks menggunakan TF-IDF.
5. Melatih dan membandingkan beberapa model machine learning.
6. Mengevaluasi performa model dan menganalisis hasilnya.

---

## Dataset

* **Sumber**: Ulasan aplikasi Tokopedia (file CSV hasil scraping)
* **Jumlah Data**: Puluhan hingga ratusan ribu ulasan
* **Kolom Utama**:

  * `content`: teks ulasan pengguna

Setelah proses preprocessing, dataset diperluas dengan berbagai kolom hasil transformasi teks dan label sentimen.

---

## Alur Kerja Proyek

Proyek ini mengikuti alur kerja machine learning berbasis teks sebagai berikut:

### 1. Data Understanding & Cleaning

Tahap awal meliputi:

* Membaca dataset dari file CSV
* Menghapus nilai kosong (missing values)
* Menghapus data duplikat
* Pemeriksaan struktur dan distribusi data

Tahap ini memastikan data yang digunakan berkualitas dan siap diproses lebih lanjut.

---

### 2. Text Preprocessing (Bahasa Indonesia)

Pipeline preprocessing teks dirancang khusus untuk karakteristik bahasa Indonesia dan ulasan informal.

Tahapan preprocessing:

1. **Text Cleaning**

   * Menghapus mention, hashtag, URL, angka, dan tanda baca
   * Menghilangkan karakter tidak relevan

2. **Case Folding**

   * Mengubah seluruh teks menjadi huruf kecil

3. **Normalisasi Slang Words**

   * Mengonversi kata slang ke bentuk formal menggunakan kamus slang bahasa Indonesia
   * Penting untuk menangani bahasa informal pada ulasan e-commerce

4. **Tokenization**

   * Memecah teks menjadi token kata menggunakan NLTK

5. **Stopword Removal**

   * Menghapus stopword bahasa Indonesia dan Inggris
   * Menambahkan custom stopword sesuai konteks ulasan

6. **Stemming**

   * Menggunakan Sastrawi untuk mengembalikan kata ke bentuk dasar

Hasil akhir preprocessing adalah teks bersih yang siap digunakan untuk ekstraksi fitur.

---

### 3. Pelabelan Sentimen (Lexicon-Based)

Sebelum training model, label sentimen ditentukan menggunakan pendekatan leksikon:

* Menggunakan kamus kata positif dan negatif bahasa Indonesia
* Setiap kata diberi skor sentimen
* Skor total menentukan polaritas:

  * Skor ≥ 0 → Positif
  * Skor < 0 → Negatif

Pendekatan ini digunakan untuk menghasilkan label awal yang kemudian digunakan sebagai target pada supervised learning.

---

### 4. Exploratory Data Analysis (EDA)

Analisis eksploratif dilakukan untuk memahami karakteristik data:

* Distribusi kelas sentimen (positif vs negatif)
* Panjang teks ulasan
* Word cloud untuk keseluruhan data, ulasan positif, dan ulasan negatif
* Analisis kata yang paling sering muncul menggunakan TF-IDF

EDA membantu dalam memahami bias data dan pola bahasa pengguna.

---

### 5. Feature Engineering

Untuk mengubah teks menjadi representasi numerik, digunakan:

* **TF-IDF Vectorizer**

  * Unigram dan bigram
  * Pengaturan `min_df`, `max_df`, dan `max_features`

TF-IDF dipilih karena efektif untuk klasifikasi teks dan mampu menangkap pentingnya kata dalam dokumen.

---

### 6. Model Training & Evaluation

Beberapa model machine learning dilatih dan dibandingkan:

1. **Support Vector Machine (LinearSVC)**

   * Digunakan dengan pipeline TF-IDF
   * Hyperparameter tuning menggunakan GridSearchCV

2. **Logistic Regression**

   * Model baseline yang kuat untuk klasifikasi teks
   * Regularisasi dikontrol melalui parameter C

3. **LightGBM Classifier**

   * Model gradient boosting berbasis tree
   * Digunakan untuk membandingkan performa model non-linear

Evaluasi dilakukan menggunakan:

* Accuracy pada data training dan testing
* Perbandingan performa antar model

---

### 7. Inference (Prediksi Kalimat Baru)

Proyek ini juga mendukung prediksi sentimen untuk kalimat baru:

* Input teks dari pengguna
* Menggunakan pipeline preprocessing yang sama
* Transformasi TF-IDF
* Prediksi sentimen menggunakan model terlatih

Hal ini menunjukkan kesiapan model untuk digunakan pada skenario nyata.

---

## Teknologi dan Library

* Python
* Pandas, NumPy
* NLTK
* Sastrawi
* Scikit-learn
* LightGBM
* Matplotlib, Seaborn
* WordCloud

---

## Nilai Teknis Proyek

Proyek ini menunjukkan kemampuan dalam:

* NLP bahasa Indonesia
* Data preprocessing skala besar
* Feature extraction teks
* Pelabelan sentimen berbasis leksikon
* Training dan evaluasi multiple model ML
* Penggunaan pipeline dan hyperparameter tuning
* Analisis dan visualisasi data teks

---

## Potensi Pengembangan

Pengembangan lanjutan yang dapat dilakukan:

* Menambahkan kelas sentimen netral
* Menggunakan deep learning (LSTM, Transformer, IndoBERT)
* Menyimpan model sebagai API (FastAPI / Flask)
* Menggunakan dataset dengan label manual
* Evaluasi dengan metrik tambahan (precision, recall, F1-score)
