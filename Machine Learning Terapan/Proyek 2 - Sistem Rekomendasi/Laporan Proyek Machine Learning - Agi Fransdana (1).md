# Laporan Proyek Machine Learning - Agi Fransdana
---
## Project Overview
---
Proyek ini bertujuan untuk mengembangkan sistem rekomendasi film berdasarkan genre yang dimiliki oleh film-film tersebut. Sistem ini menggunakan teknik Content-Based Filtering yang menganalisis kesamaan antara genre film untuk memberikan rekomendasi kepada pengguna.

Sistem rekomendasi ini penting karena membantu pengguna menemukan film baru yang sesuai dengan preferensi mereka, terutama ketika mereka memiliki kesulitan dalam memilih film berdasarkan genre. Selain itu, sistem rekomendasi dapat meningkatkan pengalaman pengguna dan memperkenalkan mereka pada film-film yang mungkin tidak mereka temui sebelumnya.

## Business Understanding
---
### Problem Statement
1. Bagaimana cara membuat sistem rekomendasi film yang mampu memberikan saran berdasarkan genre film?
2. Bagaimana sistem rekomendasi dapat mengidentifikasi film dengan genre yang relevan?

### Goals
1. Membangun sistem rekomendasi film berbasis genre dengan memanfaatkan pendekatan Content-Based Filtering.
2. Menghasilkan rekomendasi film yang akurat untuk meningkatkan kepuasan pengguna.

### Solution Approach
1. Sistem ini menggunakan representasi genre film sebagai fitur utama untuk menghasilkan rekomendasi. Teknik ini memungkinkan sistem untuk merekomendasikan film yang serupa dengan genre dari film yang dipilih oleh pengguna.
2. Pendekatan:  Menggunakan Content-Based Filtering dengan metode TF-IDF untuk mengukur kesamaan genre antar film. 
3. Dengan implementasi Cosine Similarity untuk menghitung kemiripan antara film yang berbasis genre.

## Data Understanding
Dataset yang digunakan adalah dataset film yang mencakup informasi tentang judul film, genre, rating, dan tahun rilis. Dataset ini diambil dari [Tautan ini](https://https://www.kaggle.com/datasets/octopusteam/full-imdb-dataset). dataset ini bernama Full IMDb Dataset (1M+)
Jumlah data: 1037553 baris dengan 7 kolom, yaitu:
1. Fitur Kategorik:
    - id: ID unik film
    - title: Judul film
    - type: Jenis film (movie/TV show)
    - genres: Genre film

2. Fitur Numerik:
    - averageRating: Rata-rata rating film
    - numVotes: Jumlah suara yang diberikan untuk film
    - releaseYear: Tahun rilis film

Dataset ini mencakup kombinasi variabel numerik dan kategorikal

**1. Kondisi data**

<img width="305" height="212" alt="Image" src="https://github.com/user-attachments/assets/ab58e520-243e-4a1c-8142-89fd52678814" />

**2. Mengecek missing value**

<img width="147" height="250" alt="Image" src="https://github.com/user-attachments/assets/e242f55b-91da-4821-ae1e-8f2e80d5cf26" />

Terdapat banyak missing value pada beberapa kolom seperti genres, averageRating, numVotes, releaseYear. untuk kolom title ada sedikit missing value.

**3. Mengecek data duplikat**

<img width="150" height="63" alt="Image" src="https://github.com/user-attachments/assets/096305cd-f66d-4e8d-baf5-d071735c0a6d" />

tidak ada duplikat

**4. Mengecek Outlier pada kolom numerik**

- Kolom numVote

<img width="520" height="432" alt="Image" src="https://github.com/user-attachments/assets/289b8491-1a0d-4e13-85c7-108b2f645762" />

ada banyak outlier pada kolom numVotes

- Kolom averageRating

<img width="520" height="432" alt="Image" src="https://github.com/user-attachments/assets/1e79ef6c-87e4-4a44-bb6b-559d21d383b6" />

Bisa dilihat dari visualisasi diatas, terdapat outlier pada kolom averageRating

- Kolom releaseYear

<img width="520" height="432" alt="Image" src="https://github.com/user-attachments/assets/5335607b-c9c9-40a1-a903-0c27f178634d" />

pada kolom releaseYear juga ada outlier

## Data Preparation
---
Data Preparation
Pada tahap ini, dilakukan beberapa teknik untuk mempersiapkan data:

1. Membersihkan missing value.
2. Menghapus outlier menggunakan teknik Interquartile Range (IQR).
3. Reduksi Tipe Data: Mengubah tipe data kolom numerik  yang sebelum bertipe float64 menjadi float32 untuk menghemat memori.
4. Pemilihan Sample Data: Mengambil sampel data sebesar 5% dari total data untuk mempercepat eksperimen.
3. Pemrosesan Genre: Genre yang berisi beberapa kategori diproses dengan teknik TF-IDF untuk menghasilkan representasi numerik dari genre-genre tersebut.

Proses tersebut penting untuk meminimalisir penggunaan memori dan mempercepat waktu eksekusi, khususnya saat bekerja dengan dataset besar.

## Modeling
---
Sistem Rekomendasi:

1. Pendekatan yang Digunakan: Sistem rekomendasi berbasis Content-Based Filtering dengan menggunakan TF-IDF untuk mengubah genre film menjadi representasi numerik dan Cosine Similarity untuk menghitung kesamaan antar film.
2. Top-N Recommendation: Sistem menghasilkan 5 rekomendasi film teratas berdasarkan genre yang sama dengan film yang diminta pengguna.

<img width="465" height="162" alt="Image" src="https://github.com/user-attachments/assets/48cf0d24-61e2-46c9-b864-920713df6128" />


## Evaluation
---
Metrik Evaluasi: Evaluasi dilakukan menggunakan Precision untuk mengukur seberapa akurat rekomendasi yang diberikan sesuai dengan genre yang dicari pengguna.

Saya melakukan evaluasi terhadap model menggunakan metrik precision. Precision di sini mengukur seberapa banyak genre yang cocok dengan anime yang dipilih dibandingkan dengan jumlah rekomendasi yang diberikan. Untuk itu, saya menggunakan sebuah loop if yang akan menambah nilai variabel 'a' setiap kali genre yang direkomendasikan sesuai dengan genre anime yang dipilih. Berikut adalah kode yang saya gunakan:

<img width="275" height="25" alt="Image" src="https://github.com/user-attachments/assets/9742f1cc-37dc-4a0f-a01e-2a5b74d8a325" />

Hasil Evaluasi: Dari hasil pengujian, presisi sistem adalah 100%, yang berarti seluruh rekomendasi film yang dihasilkan memiliki genre yang relevan dengan genre film yang dicari pengguna.

## Conclusion
---
Sistem rekomendasi yang dikembangkan berhasil memberikan rekomendasi film yang relevan berdasarkan genre yang dicari pengguna. Penggunaan Content-Based Filtering dengan Cosine Similarity terbukti efektif untuk mencocokkan genre film dan memberikan rekomendasi yang sesuai dengan preferensi pengguna. Model ini dapat ditingkatkan lebih lanjut dengan menggabungkan metode lain, seperti Collaborative Filtering, untuk meningkatkan akurasi dan cakupan rekomendasi.
