# Laporan Proyek Machine Learning - Agi Fransdana
---------------
## Domain Proyek
-------
Pendidikan adalah kunci utama yang memegang peranan penting dalam membentuk masa depan generasi muda. Salah satu indikator utama keberhasilan pendidikan adalah hasil belajar siswa, yang sering diukur melalui nilai ujian. Namun, prestasi akademik siswa dipengaruhi oleh berbagai faktor baik dari sisi internal maupun eksternal. Dalam praktiknya, tidak semua siswa memiliki kondisi yang sama untuk belajar secara optimal. Beberapa siswa mungkin memiliki akses ke internet dan sumber daya tambahan, sementara yang lain tidak. selain itu, lingkungan sosial dan kesejahteraan fisik juga dapat memainkan peranan penting. memahami faktor-faktor ini sangat penting untuk menciptakan intervensi yang lebih tepat sasaran dalam meningkatkan hasi belajar siswa [[1]](https://journal.uny.ac.id/index.php/jrpm/article/view/15246/12678).

Melalui analisis data ini, bertujuan untuk mengindentifikasi faktor-faktor yang paling memengaruhi nilau ujian siswa. Dengan wawasan ini, pendidik, orang tua, dan pembuat kebijakan dapat mengembangkan strategi yang lebih efektif untuk mendukung pembelajaran siswa, baik melalui perbaikan lingkungan belajar maupun pengembangan kebijakan yang lebih inklusif.

## Business Understanding
-----
### Problem Statement:
* Faktor apa saja yang paling berpengaruh terhadap nilai ujian (Exam_Score)?
* Model Machine Learning apa yang paling cocok untuk memprediksi nilai tersebut secara akurat?

### Goals/Tujuan:
* Mengidentifikasi variabel-variabel yang memiliki pengaruh terbesar terhadap Nilai Ujian (Exam_Score), sehingga dapat memberikan wawasan tentang faktor-faktor kunci yang mendukung pretasi akademik.
* membangun model Machine Learning yang paling sesuai untuk memprediksi nilai ujian (Exam_Score) siswa dengan akurat

### Solution Statement:
* Melalui Exploratory Data Analysis (EDA), proyek ini akan mengindentifikasi fitur-fitur yang memiliki korelasi dengan nilai ujian (Exam_Score).
* Tiga model Machine Learning dengan pendekatan berbeda akan dibangun, yaitu:
    1. K-Nearest Neighbor
    2. Random Forest
    3. Boosting Algorithm

## Data Understanding
---
Dataset yang digunakan dalam proyek ini bernama "Student Performance Factors" dan dapat diakses melalui [tautan](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors). Dataset ini berisi 6607 baris data, yang merepresentasikan berbagai informasi terkait faktor-faktor yang memengaruhi nilai ujian siswa (Exam_Score), dataset ini mencakup 20 variabel, dengan rincian sebagai berikut:
1. Fitur Numerik:
* Hours_Studied: Jumlah jam yang dihabiskan siswa untuk belajar.
* Attendance: Tingkat kehadiran siswa.
* Sleep_Hours: Jumlah jam tidur siswa setiap malam.
* Previous_Scores: Skor siswa pada tes sebelumnya.
* Tutoring_Sessions: Jumlah sesi les tambahan yang diikuti siswa.
* Physical_Activity: Frekuensi aktivitas fisik siswa dalam seminggu.
* Exam_Score: Nilai ujian siswa.

2. Fitur Kategorikal
* Parental_Involvement: Tingkat keterlibatan orang tua dalam pendidikan siswa.
* Access_to_Resources: Ketersediaan sumber daya pendidikan untuk siswa.
* Extracurricular_Activities: Partisipasi siswa dalam kegiatan ekstrakurikuler.
* Motivation_Level: Tingkat motivasi siswa untuk belajar.
* Internet_Access: Ketersediaan akses internet untuk siswa.
* Family_Income: Tingkat pendapatan keluarga siswa.
* Teacher_Quality: Persepsi siswa terhadap kualitas pengajaran guru.
* School_Type: Jenis sekolah tempat siswa belajar.
* Peer_Influence: Pengaruh teman sebaya terhadap siswa.
* Learning_Disabilities: Indikasi apakah siswa memiliki kesulitan belajar.
* Parental_Education_Level: Tingkat pendidikan tertinggi yang dicapai oleh orang tua siswa.
* Distance_from_Home: Jarak antara rumah siswa dan sekolah.
* Gender: Jenis kelamin siswa.

Dataset ini mencakup kombinasi variabel numerik dan kategorikal, memberikan peluang untuk melakukan eksplorasi mendalam terhadap berbagai faktor yang dapat memengaruhi kinerja akademik siswa. Dengan data ini.

## Exploratory Data Analysis - Univariate Analysis
---
Ada 7 barplot yang saya buat dinotebook.
- Barplot pertama

![Image](https://github.com/user-attachments/assets/1de1d394-5988-4482-8246-4b64a563a0f7)

Dari visualisasi diatas dapat disimpulkan bahwa:
- Sebagian besar sampel Parental Involvement berada pada tingkat Medium dengan jumlah 2992 yang mewakili 51,3% dari total data.
- Tingkat ketelibatan orang tua pada kategori High lebih sedikit dibandingkan dengan kategori Medium, tetapi lebih tinggi dibandingkan kategori low.
- Kategori Low merupakan jumlah paling sedikit diantara kegita kategori.

- Barplot kedua

![Image](https://github.com/user-attachments/assets/65459e0e-8374-4b2a-acae-1f38cc5c6466)
Dari visualisasi diatas dapat disimpulkan bahwa:
- Sebagian besar sampel Access to Resources berada pada tingkat Medium dengan jumlah 2936 yang mewakili 50,3% dari total data.
- Tingkat ketersediaan sumber daya pendidikan untuk siswa pada kategori High lebih sedikit dibandingkan dengan kategori Medium, tetapi lebih tinggi dibandingkan kategori low.
- Kategori Low merupakan jumlah paling sedikit diantara kegita kategori.

- Barplot ketiga

![Image](https://github.com/user-attachments/assets/8a56cd76-66d1-438b-bde7-e1b0e99086ce)
Dari visualisasi diatas dapat disimpulkan bahwa:
- siswa yang mengikuti kegiatan ekstrakurikuler memiliki jumlah yang lebih banyak dari pada siswa yang tidak mengikuti ekstrakurikuler.


- Barplot keempat

![Image](https://github.com/user-attachments/assets/88dac927-f6a8-4af4-9188-876c723099cf)
Dari visualisasi diatas dapat disimpulkan bahwa:
- Sebagian besar sampel Motivation Level berada pada tingkat Medium dengan jumlah 2967 yang mewakili 50,8% dari total data.
- Tingkat motivasi siswa untuk belajar pada kategori Low lebih sedikit dibandingkan dengan kategori Medium, tetapi lebih tinggi dibandingkan kategori High.
- Kategori High merupakan jumlah paling sedikit diantara kegita kategori.

- Barplot kelima

![Image](https://github.com/user-attachments/assets/b5efc812-c50d-4411-b856-f2bdea91af63)
Dari visualisasi diatas dapat disimpulkan bahwa:
- siswa yang memiliki akses internet memiliki jumlah yang lebih banyak dari pada siswa yang tidak memiliki akses internet.

- Barplot keenam

![Image](https://github.com/user-attachments/assets/cae57fea-9a33-418e-a47b-dc5a1e266a4f)
Dari visualisasi diatas dapat disimpulkan bahwa:
- Sebagian besar sampel Family Income berada pada tingkat Medium dengan jumlah 2364 yang mewakili 40,5% dari total data.
- Tingkat pendapatan keluarga siswa pada kategori Low hampir sama banyak dengan kategori Medium, tetapi lebih tinggi dibandingkan kategori High.
- Kategori High merupakan jumlah paling sedikit diantara kegita kategori.

**7. Barplot ketujuh**
![Image](https://github.com/user-attachments/assets/f09c74e4-a91f-417e-98c5-15a56a9384a7)
Dari visualisasi diatas dapat disimpulkan bahwa:
- Sebagian besar sampel Persepsi siswa terhadap kualitas pengajaran guru berada pada tingkat Medium dengan jumlah 3499 yang mewakili 60% dari total data.
- Tingkat Persepsi siswa terhadap kualitas pengajaran guru pada kategori High lebih sedikit dibandingkan dengan kategori Medium, tetapi lebih tinggi dibandingkan kategori Low.
- Kategori Low merupakan jumlah paling sedikit diantara kegita kategori.

**8. Barplot kedelapan**
![Image](https://github.com/user-attachments/assets/25740beb-ad80-4d3e-ac74-32cd5d705a0f)
Dari visualisasi diatas dapat disimpulkan bahwa:
- School Type dengan kategori Public memiliki jumlah yang lebih banyak dari pada kategori Private.

**9. Barplot kesembilan**
![Image](https://github.com/user-attachments/assets/c5fec92a-a779-4c25-b43c-9d80686f1fd7)
Dari visualisasi diatas dapat disimpulkan bahwa:
sebagian besar sampel memiliki pengaruh teman yang positif atau netral, sementara pengaruh negatif relatif lebih kecil.

**10. Barplot kesepuluh**
![Image](https://github.com/user-attachments/assets/79a025e6-2e9b-4829-823d-a82d7c536540)
Dari visualisasi diatas dapat disimpulkan bahwa:
Sebagian besar sampel tidak memiliki gangguan belajar.

**11. Barplot sebelas**
![Image](https://github.com/user-attachments/assets/a0e3c679-241d-424d-9f56-7df5e66cc055)
Dari visualisasi diatas dapat disimpulkan bahwa:
Sebagian besar orang tua memiliki tingkat pendidikan setara High School, sementara tingkat Postgraduate merupakan yang paling sedikit.

**12. Barplot duabelas**
![Image](https://github.com/user-attachments/assets/ce6749f5-cca8-437a-bc3a-3b6e897068de)
Dari visualisasi diatas dapat disimpulkan bahwa:
Mayoritas individu dalam sampel memiliki jarak rumah yang dekat dengan lokasi yang dianalisis, yaitu 59.6% dari total sampel. Sementara itu, sekitar 30.5% memiliki jarak yang sedang, dan hanya 9.9% yang memiliki jarak jauh.

**13. Barplot tigabelas**
![Image](https://github.com/user-attachments/assets/918a31c0-ea79-4340-b2b6-0e05ab8f7f1c)
Dari visualisasi diatas dapat disimpulkan bahwa:
jumlah pria lebih banyak dari jumlah perempuan.

**14. histogram**
![Image](https://github.com/user-attachments/assets/3260c444-ccdb-4afe-b565-b2362ef30903)
Saya juga menggunakan histogram untuk menganalisis data, karena grafik ini memudahkan saya melihat distribusi dan pola data dengan jelas, sehingga bisa menarik kesimpulan yang lebih tepat.
dan hasilnya Sebagian besar siswa belajar sekitar 15-25 jam per minggu, dengan distribusi waktu belajar yang menyerupai pola normal. Kehadiran siswa di kelas cukup merata, berada di kisaran 60-100 persen. Mayoritas siswa tidur 7-8 jam, sesuai dengan durasi tidur yang ideal. Nilai sebelumnya menunjukkan tren meningkat, dengan lonjakan signifikan pada nilai tertinggi (100). Banyak siswa tidak mengikuti sesi bimbingan belajar, tetapi bagi yang mengikuti, mereka cenderung menghadiri 1-3 sesi. Aktivitas fisik siswa didominasi oleh tingkat sedang, dengan puncak di tingkat aktivitas 3. Nilai ujian juga menunjukkan distribusi normal, dengan mayoritas siswa mendapatkan nilai rata-rata sekitar 68-70.

## Exploratory Data Analysis - Multivariate Analysis
---
Untuk analisis multivariat, saya menggunakan barplot, pairplot, dan heatmap. Barplot membantu untuk membandingkan kategori, pairplot memungkinkan melihat hubungan antar variabel, dan heatmap memberi gambaran visual tentang korelasi antar variabel.

Barplot:
![Image](https://github.com/user-attachments/assets/ec801a62-8af0-4c1a-be87-03304a539d6d)
![Image](https://github.com/user-attachments/assets/c23aeb68-223c-4c29-85a5-f580d717200e)
![Image](https://github.com/user-attachments/assets/01b9d47a-ae9e-4260-afbb-cd0b120f99e6)
![Image](https://github.com/user-attachments/assets/72042687-f340-4590-8e7d-392ec7114d0d)
![Image](https://github.com/user-attachments/assets/865853e9-ddd2-4d78-a14c-dacf70c782f6)
![Image](https://github.com/user-attachments/assets/651441b5-ed28-4a83-8634-ffc6df95a7f7)
![Image](https://github.com/user-attachments/assets/1166856f-13a3-499c-8df0-7180e951c1ce)
![Image](https://github.com/user-attachments/assets/50c41edf-4943-41b4-9b75-4b8aa8df90cd)
![Image](https://github.com/user-attachments/assets/93fa0707-2101-44af-90d7-dcfd0e666348)
![Image](https://github.com/user-attachments/assets/2d0533d4-08b0-4c85-b41e-2a52b336c8c5)
![Image](https://github.com/user-attachments/assets/97209de7-6ded-4015-b890-cb3d9ff931ac)
![Image](https://github.com/user-attachments/assets/fa60e1aa-4c8a-4ae6-8332-4b9fb3170450)
![Image](https://github.com/user-attachments/assets/4ab898c3-a6f7-44d6-ba93-344c359bff59)

Dari bar plot ini, dapat disimpulkan bahwa siswa dengan tingkat Access_to_Resources yang tinggi memiliki rata-rata Exam Score tertinggi sebesar 67.8. Hal ini menunjukkan bahwa ketersediaan sumber daya pendidikan yang tinggi cenderung memberikan dampak positif terhadap hasil ujian siswa.

Pairplot:
![Image](https://github.com/user-attachments/assets/419cfc9f-f99a-4a55-828d-094f58e08ac3)
Hours_Studied dan Attendance adalah dua fitur numerik yang paling berkorelasi dengan Exam_Score. Oleh karena itu, kedua variabel ini dapat menjadi prediktor yang baik dalam model prediksi performa ujian.

Heatmap:
![Image](https://github.com/user-attachments/assets/2957a5a1-4cb2-499c-b4bd-9fa78f1e1013)
Berdasarkan korelasi ini, Attendance (kehadiran) dan Hours_Studied (jam belajar) punya hubungan yang kuat dengan skor ujian, jadi ini adalah faktor penting yang memengaruhi hasil ujian. Sebaliknya, fitur seperti Sleep_Hours, Tutoring_Sessions, dan Physical_Activity hampir tidak ada hubungannya dengan skor, jadi mereka kurang relevan. Hubungan antar fitur juga lemah, jadi tidak ada fitur yang saling tumpang-tindih informasi di antaranya.


## Data Preparation
----
- Feature Selection
Menghapus fitur yang memiliki korelasi rendah terhadap variabel target (Exam_Score) berdasarkan analisis korelasi sebelumnya. Hal ini dilakukan untuk menyederhanakan model dan mengurangi noise yang dapat mengganggu proses prediksi. Hasilnya, dataset menjadi lebih fokus hanya pada fitur-fitur yang relevan, sehingga analisis dan modeling lebih efisien.

- Encoding Fitur Kategori
untuk mengubah data kategorikal menjadi format numerik menggunakan one-hot encoding, sehingga dapat digunakan oleh algoritma pembelajaran mesin. Fitur-fitur seperti Parental_Involvement, Access_to_Resources, Gender, dan lainnya dikonversi menjadi beberapa kolom dummy. Hasilnya, dataset menjadi sepenuhnya numerik dengan kolom representasi baru untuk setiap kategori, yang memudahkan proses analisis dan modeling.

- Reduksi Dimensi dengan PCA (Principal Component Analysis)
PCA dilakukan untuk menggabungkan dua fitur utama, yaitu Attendance dan Hours_Studied, menjadi satu dimensi baru (dimension). Langkah ini bertujuan untuk mengurangi kompleksitas data dengan tetap mempertahankan informasi penting. Hasilnya, dua fitur ini menunjukkan tidak adanya hubungan linear yang jelas antara Attendance (kehadiran) dan Hours_Studied (jam belajar), dengan sebaran data yang merata. Histogram Attendance memiliki distribusi seragam di kisaran 60-100, sementara Hours_Studied mengikuti distribusi normal dengan puncak di sekitar 20 jam. Kedua fitur ini memiliki pola distribusi yang berbeda, sehingga penting untuk memverifikasi efektivitas PCA jika digunakan untuk mengurangi dimensi data.

- Split data untuk pelatihan dan pengujian
Data dibagi menjadi dua bagian, yaitu data latih (90%) untuk melatih model dan data uji (10%) untuk mengevaluasi kinerja model. Langkah ini bertujuan untuk memastikan model dapat belajar dari sebagian besar data, sekaligus menyediakan data terpisah untuk menguji kemampuan generalisasi model. Hasilnya, dari total 5836 data, sebanyak 5252 data digunakan untuk pelatihan, sementara 584 data digunakan untuk pengujian.
Kesimpulannya: membagi dataset menjadi fitur (X) dan target (y), kemudian memisahkan data tersebut menjadi data latih dan data uji dengan rasio 90:10. Proses ini penting untuk memastikan model dapat dilatih dengan data latih dan diuji dengan data uji untuk mengevaluasi performanya pada data baru.

- Standarisasi Fitur Numerik
untuk menstandarkan fitur numerik seperti Tutoring_Sessions, Previous_Scores, dan dimension agar memiliki distribusi dengan rata-rata 0 dan standar deviasi 1. Hal ini penting untuk memastikan model bekerja dengan baik, terutama algoritma yang sensitif terhadap skala data. Hasilnya, fitur numerik telah dinormalisasi dengan statistik yang seragam, yaitu rata-rata 0 dan standar deviasi 1, yang meningkatkan konsistensi dan performa model.

## Modeling
ini model yang saya gunakan:
1. K-Nearest Neighbors (KNN):
Algoritma K-Nearest Neighbors (KNN) adalah metode prediksi yang didasarkan pada "kedekatan" atau "kesamaan" antara data yang baru dengan data pelatihan yang sudah ada. Pada kode ini, model KNeighborsRegressor digunakan untuk memprediksi nilai numerik (regresi).

    - n_neighbors=10: Parameter n_neighbors menentukan jumlah tetangga terdekat yang akan digunakan untuk menghitung prediksi. Dalam hal ini, model akan mencari 10 data pelatihan terdekat dari data yang akan diprediksi. 

    Kode ini mengukur performa model KNN pada data pelatihan dengan menghitung Mean Squared Error (MSE) antara prediksi model dan nilai asli dari data pelatihan. Hasil MSE ini disimpan pada DataFrame models di baris train_mse untuk model KNN.

2. Random Forest:
Random Forest adalah algoritma ensemble learning yang bekerja dengan membangun banyak pohon keputusan (decision trees), yang kemudian digabungkan untuk menghasilkan prediksi akhir. Setiap pohon dalam hutan melakukan prediksi independen, dan hasil akhir adalah rata-rata dari semua pohon tersebut.

    - n_estimators=50: Menentukan jumlah pohon keputusan yang akan dibangun. Dalam hal ini, model akan menggunakan 50 pohon.
    max_depth=16: Menentukan kedalaman maksimum dari setiap pohon. Ini mengontrol seberapa dalam pohon dapat tumbuh, yang berpengaruh pada kompleksitas model.
    random_state=55: Menetapkan nilai acak untuk memastikan hasil yang dapat direproduksi setiap kali model dijalankan.
    n_jobs=-1: Menggunakan semua inti prosesor yang tersedia untuk memparalelkan perhitungan, sehingga proses pelatihan menjadi lebih cepat.

    Pada kode ini, model RandomForest dilatih menggunakan data pelatihan dan hasil prediksi pada data pelatihan dibandingkan dengan nilai asli untuk menghitung train_mse (MSE untuk data pelatihan). Hasilnya disimpan dalam DataFrame models.

3. Boosting:
Boosting adalah teknik ensemble learning lain yang membangun model secara bertahap, di mana setiap model baru berfokus untuk memperbaiki kesalahan dari model sebelumnya. Pada kode ini, model AdaBoostRegressor digunakan, yang merupakan salah satu algoritma boosting yang populer.

    - learning_rate=0.05: Parameter ini mengontrol seberapa besar kontribusi setiap model baru terhadap prediksi keseluruhan. Dengan nilai 0.05, model baru akan memiliki kontribusi yang lebih kecil dalam perbaikan kesalahan model sebelumnya.
    random_state=55: Sama seperti pada Random Forest, ini digunakan untuk memastikan hasil yang konsisten saat kode dijalankan berulang kali.

## Evaluasi
---
Model dievaluasi menggunakan tiga metrik utama. Pertama, Mean Squared Error (MSE), yang menghitung rata-rata selisih kuadrat antara nilai aktual dan prediksi; nilai MSE yang lebih rendah menunjukkan prediksi yang lebih akurat. Kedua, Root Mean Squared Error (RMSE), yang merupakan akar dari MSE, sehingga lebih mudah diinterpretasikan karena memiliki satuan yang sama dengan data asli. Terakhir, Mean Absolute Error (MAE), yang menghitung rata-rata selisih absolut antara nilai aktual dan prediksi. Ketiga metrik ini memberikan gambaran tentang seberapa jauh hasil prediksi dari nilai sebenarnya, dengan nilai yang lebih kecil menunjukkan performa model yang lebih baik.
1. MSE

|index|train|test|
|---|---|---|
|KNN|3\.6621686976389944|4\.270736301369863|
|RF|0\.5155140494793835|3\.288765952628483|
|Boosting|4\.937516142821449|5\.136217030879779|
Hasilnya menunjukkan bahwa RF memiliki performa terbaik dengan MSE rendah (0.515514 pada data latih dan 3.288766 pada data uji), sementara Boosting memiliki MSE tertinggi dan kurang optimal. KNN cukup baik tetapi masih kalah dari RF.

2. MSE

|index|train|test|
|---|---|---|
|KNN|3\.6621686976390015|4\.270736301369864|
|RF|0\.5155140494793846|3\.2887659526284834|
|Boosting|4\.937516142821443|5\.136217030879783|
Hasilnya sama, menunjukkan konsistensi penghitungan.
Hasil menunjukkan:
KNN: MSE moderat untuk latih (3.662) dan uji (4.271), menunjukkan keseimbangan performa.
Random Forest: MSE terendah pada data uji (3.289), menunjukkan performa terbaik, meski ada sedikit overfitting.
Boosting: MSE tertinggi pada latih (4.938) dan uji (5.136), menunjukkan performa paling lemah.
Kesimpulannya, Random Forest adalah model terbaik untuk data ini.

3. RMSE

|index|train|test|
|---|---|---|
|KNN|1\.9136793612408014|2\.0665759849010787|
|RF|0\.7179930706346578|1\.8134955066468963|
|Boosting|2\.2220522367445468|2\.266322358112319|
Hasil:
KNN: RMSE moderat pada latih (1.914) dan uji (2.067), menunjukkan performa stabil.
Random Forest: RMSE terendah pada uji (1.813), mengindikasikan performa terbaik dengan sedikit overfitting.
Boosting: RMSE tertinggi pada latih (2.222) dan uji (2.266), mengindikasikan performa kurang optimal.
Kesimpulan: Random Forest memiliki performa terbaik, diikuti oleh KNN. Boosting memberikan hasil terburuk pada data ini.

4. MAE

|index|train|test|
|---|---|---|
|KNN|1\.5374904798172144|1\.6703767123287678|
|RF|0\.5670366803256368|1\.4577529272986716|
|Boosting|1\.7855063133407911|1\.8066666026586684|
Hasil:
KNN: MAE pada latih (1.537) dan uji (1.670) relatif stabil.
Random Forest: MAE terendah pada uji (1.458), menunjukkan performa terbaik dan prediksi yang lebih akurat.
Boosting: MAE tertinggi pada latih (1.786) dan uji (1.807), mengindikasikan performa kurang optimal dibandingkan model lainnya.
Kesimpulan: Random Forest memberikan hasil terbaik dalam hal kesalahan absolut, diikuti oleh KNN, sedangkan Boosting menunjukkan performa terburuk pada data ini.


Berikut adalah hasil evaluasi dari ketiga model:
![Image](https://github.com/user-attachments/assets/2247305c-405d-4418-9e09-7d3e4f32df9e)

Bisa dilihat algoritma Random Forest memiliki nilai error yang paling kecil.

Prediksi:
|index|y\_true|prediksi\_KNN|prediksi\_RF|prediksi\_Boosting|
|---|---|---|---|---|
|4653|70|68\.6|68\.7|69\.1|
|3488|69|69\.4|69\.3|68\.5|
|5432|74|71\.7|72\.1|70\.5|
|2423|69|67\.8|69\.4|69\.5|
|4756|71|73\.0|72\.1|70\.5|
Berdasarkan hasil prediksi untuk 5 sampel pertama pada data uji, dapat dilihat perbandingan antara nilai sebenarnya (y_true) dan prediksi dari masing-masing model:

*   KNN cenderung memiliki prediksi yang lebih sedikit lebih rendah dibandingkan nilai sebenarnya (y_true).
*   Random Forest menghasilkan prediksi yang lebih akurat dengan sedikit dari nilai sebenarnya, meskipun sedikit lebih rendah pada beberapa sampel.
*   Boosting memberikan prediksi yang sedikit lebih rendah atau lebih jauh dari nilai yang sebenarnya dibandingkan dengan RF, meskipun hasilnya masih cukup dekat.

Kesimpulannya:  

1.   Model yang paling akurat: Berdasarkan hasil prediksi, Random Forest (RF) adalah model yang paling akurat untuk memprediksi nilai ujian (Exam_Score) dibandingkan dengan KNN dan Boosting, karena prediksinya lebih dekat dengan nilai asli (y_true).

2.   Menjawab Business Understanding: Dalam konteks Business Understanding yang bertujuan untuk memprediksi nilai ujian siswa (Exam_Score), model RF lebih sesuai untuk tujuan ini karena memberikan prediksi yang lebih konsisten dan akurat. Random Forest adalah model yang terbaik dalam kasus ini, karena prediksi yang lebih dekat dengan nilai sebenarnya.