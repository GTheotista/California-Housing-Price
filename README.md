# **California Housing Price**

**Tools:** Python <br>
**Visualizations:** Python(Matplotlib/Seaborn)<br> 
**Dataset:** California Housing Price

**Table of Contents:**

- [**Supermarket Customers Analysis**](#California-Housing-Price)
- [**Langkah 0: Business Problem Understanding**](#Langkah-0-Business-Problem-Understanding)
- [**Langkah 1: Data Understanding**](#Langkah-1-Data-Understanding)
- [**Langkah 2: Data Preprocessing**](#Langkah-2-Data-Preprocessing)
- [**Langkah 3: Modeling**](#Langkah-3-Modeling)
- [**Langkah 4: Conclusion And Recommendations**](#Langkah-4-Conclusion-And-Recommendations)
- [**Langkah 5: Save Model**](#Langkah-5-Save-Model)

---

# **Langkah 0: Business Problem Understanding**

---
Dalam dinamika kompleks pasar perumahan, konsumen berusaha untuk mendapatkan nilai terbaik untuk investasi mereka, sementara pengusaha properti bertujuan untuk menjaga profitabilitas dan pertumbuhan bisnis. Praktik overpricing dapat merugikan kepercayaan konsumen, sementara underpricing dapat menghambat pertumbuhan bisnis dan menyebabkan kerugian finansial.

**Problem Statement**
- Perspektif Konsumen: Konsumen sering mengalami ketidakpastian dalam menilai apakah harga properti mencerminkan nilai sebenarnya. Keinginan untuk menghindari pembelian dengan harga yang tidak sesuai dengan nilai properti menjadi kendala utama dalam pengambilan keputusan.
- Perspektif Bisnis: Pengusaha perumahan menghadapi tantangan menetapkan harga yang seimbang. Overpricing dapat menghambat penjualan dan merugikan reputasi, sementara underpricing dapat menyebabkan kerugian finansial dan pertumbuhan bisnis yang terbatas.

**Goals**
- Pemberdayaan Konsumen: Memberdayakan konsumen dengan informasi yang akurat dan transparan mengenai faktor-faktor yang mempengaruhi harga properti, sehingga mereka dapat membuat keputusan pembelian yang lebih cerdas.
- Keberlanjutan Bisnis: Membantu pengusaha perumahan menetapkan harga yang seimbang, mengurangi risiko overpricing dan underpricing, serta menciptakan hubungan yang berkelanjutan dengan konsumen.

**Analytics Approach**
- Model Regresi Machine Learning: Membangun model regresi machine learning untuk memprediksi harga properti berdasarkan faktor-faktor seperti lokasi geografis, usia perumahan, jumlah kamar, dan lainnya.
- Analisis Pentingnya Fitur: Melakukan analisis terhadap faktor-faktor yang memiliki dampak signifikan terhadap harga properti, sehingga konsumen dapat memahami dengan lebih baik faktor-faktor yang mempengaruhi harga properti.
- Optimasi Strategi Harga: Menggunakan model untuk membantu pengusaha mengoptimalkan strategi penetapan harga, memastikan bahwa harga yang ditawarkan mencerminkan nilai sebenarnya dari properti tanpa mengalami overpricing atau underpricing.

---

# **Langkah 1: Data Understanding**

---

**Penjelasan Fitur**
Menjelaskan makna dan signifikansi setiap fitur yaitu:
- Longitude: Merupakan koordinat geografis yang menunjukkan lokasi timur atau barat suatu titik pada peta bumi.
- Latitude: Merupakan koordinat geografis yang menunjukkan lokasi utara atau selatan suatu titik pada peta bumi.
- Housing Median Age: Merupakan usia rata-rata perumahan di daerah tersebut, diukur dalam tahun.
- Total Rooms: Jumlah total kamar di semua rumah di daerah tersebut.
- Total Bedrooms: Jumlah total kamar tidur di semua rumah di daerah tersebut.
- Population: Jumlah total penduduk di daerah tersebut.
- Households: Jumlah kepala keluarga atau rumah tangga di daerah tersebut.
- Median Income: Pendapatan rata-rata rumah tangga di daerah tersebut.
- Ocean Proximity: Informasi tentang seberapa dekat suatu rumah dengan pantai atau lautan, dapat berupa kategori seperti "dekat laut", "pantai", dll.
- Median House Value **(FItur Target)**: Nilai median rumah di daerah tersebut, yang merupakan nilai tengah dari harga rumah di daerah tersebut.

**Pengecekan Nilai Unik dalam Kolom 'Ocean Proximity'**
Melakukan pengecekan terhadap nilai unik dalam kolom kategoris 'ocean_proximity', memberikan wawasan tentang distribusi kategori kedekatan dengan laut.

**Korelasi Data dan Distribusi**
Memeriksa korelasi antara fitur-fitur dan variabel target, visualisasi distribusi data melalui pair plot dan heatmap. Diketahui bahwa 'median_income' menunjukkan korelasi yang kuat dengan 'median_house_value.'

---

# **Langkah 2: Data Preprocessing**

---

**Missing Value**
Mengonfirmasi adanya nilai yang hilang dalam dataset, penanganan missing value dilakukan dengan imputation by median karena datanya tidak normal

**Outlier**
Menangani pencilan untuk berbagai fitur seperti 'median_house_value,' 'total_rooms,' 'population,' 'households,' dan 'median_income.'

---

# **Langkah 3: Modeling**

---

**Penentuan Variabel (X) dan Variabel Target (y)**
Dalam pembangunan model ini, variabel independen (X) yang saya pilih melibatkan koordinat geografis, usia rata-rata perumahan, jumlah kamar, populasi, jumlah rumah tangga, pendapatan rata-rata, dan informasi kedekatan dengan laut. Variabel dependen (y) yang ingin saya prediksi adalah nilai median rumah di daerah tersebut ('median_house_value').

**Encoding**
Untuk memproses data kategoris, khususnya kolom 'ocean_proximity', saya menerapkan proses one hot encoding. Ini dilakukan agar model dapat memahami dan menggunakan informasi ini dalam proses pembelajaran.

**Pembagian Data**
Data saya bagi menjadi dua set utama: data latih (train set) dan data uji (test set). Data latih digunakan untuk melatih model, sedangkan data uji digunakan untuk mengevaluasi kinerja model yang sudah dilatih.

**Pemilihan Model Benchmark**
Saya memilih beberapa model regresi sebagai benchmark untuk memahami performa dasar sebelum melakukan peningkatan. Model-model tersebut melibatkan:
- Linear Regression
- K-Nearest Neighbors (KNN)
- Decision Tree
- Random Forest
- XGBoost

**Scaling**
Sebelum melatih model, saya melakukan proses scaling pada data. Pemilihan scaler dapat disesuaikan, antara Min-Max Scaler dan Standard Scaler, berdasarkan evaluasi kinerja model.

**Pemilihan Model Terbaik**
Setelah melatih semua model benchmark, saya mengevaluasi kinerja masing-masing model menggunakan metrik seperti Root Mean Squared Error (RMSE), Mean Absolute Error (MAE), dan Mean Absolute Percentage Error (MAPE). Berdasarkan evaluasi tersebut, model terbaik yang dipilih adalah XGBoost Regressor.

**Tuning Hiperparameter pada XGBoost**
Saya melakukan tuning hiperparameter pada model XGBoost untuk meningkatkan performa lebih lanjut. Proses ini melibatkan eksplorasi kombinasi parameter menggunakan GridSearchCV untuk menemukan kombinasi terbaik.

**Evaluasi Kinerja Model Setelah Tuning**
Setelah proses tuning hiperparameter, saya membandingkan kinerja model XGBoost sebelum dan sesudah tuning menggunakan metrik RMSE, MAE, dan MAPE. Dapat disimpulkan bahwa tunning berjalan dengan baik karena menghasilkan RMSE, MAE, dan MAPE yang lebih kecil.


---

# **Langkah 4: Conclusion And Recommendations**

---

**Conclusion**

**Evaluasi Model:**
- Model yang dibangun adalah model yang menggunakan fitur-x: longitude, latitude, housing_median_age, total_rooms	total_bedrooms, population, households, median_income,  dan Ocean Proximity: Near Ocean, Ocean Proximity: Inland, Ocean Proximity: Island, Ocean Proximity: Near Bay, dan Ocean Proximity: <1H Ocean terhadap fitur target-y: median_house_value.
- Model yang dibangun adalah model dengan batasan fitur-x longitude: -124.35 s/d -114.55, latitude: 32.54 s/d 41.95, housing_median_age: 1 s/d 52, total_rooms: 2 s/d 5688, total_bedrooms: 2 s/d 1168, population: 3 s/d 3134, households: 2 s/d 1091, median_income: 0.4999 s/d 7.9794,  dan Ocean Proximity: Near Ocean, Ocean Proximity: Inland, Ocean Proximity: Island, Ocean Proximity: Near Bay, dan Ocean Proximity: <1H Ocean terhadap fitur target-y median_house_value: 14999-480100.
- Meskipun RMSE dan MAE model cukup besar, hal ini dapat diterima mengingat rentang nilai target 'Median_House_Value' yang besar 14999-480100 (range 465101). Besarnya nilai-nilai tersebut sesuai dengan skala keseluruhan masalah prediksi harga rumah.
- MAPE yang rendah sebesar 17% menunjukkan bahwa model memiliki tingkat akurasi yang tinggi dalam memprediksi harga rumah. Model mampu memperkirakan nilai aktual dengan kesalahan yang kecil dalam persentase. dengan menggunakan model ini maka perkiraan harganya rata-rata akan meleset kurang lebih sebesar 17% dari harga seharusnya.
- Tidak menutup kemungkinan juga prediksinya meleset lebih jauh (terutama ketika harga aktual lebih dari 400000) karena bias yang dihasilkan model masih cukup tinggi bila dilihat dari visualisasi antara harga aktual dan prediksi. Bias yang dihasilkan oleh model ini dikarenakan oleh terbatasnya fitur pada dataset yang bisa merepresentasikan aspek properti lainnya seperti Rasio Kamar Tidur terhadap Jumlah Kamar, Luas Bangunan per Luas Tanah, Fasilitas Umum di Sekitar, dan lain-lain. 

**Mengikuti Pola Garis Lurus dalam Plot Nilai Prediksi dan Nilai Aktual:**
- Adanya pola garis lurus dalam plot antara nilai prediksi dan nilai aktual menunjukkan bahwa model memiliki kemampuan yang baik dalam menyesuaikan diri dengan pola data. Ini mengindikasikan bahwa model secara konsisten dapat memprediksi harga rumah dengan tingkat kesalahan yang seragam.

**Feature Importance:**
- Lima fitur terbesar yang mempengaruhi prediksi harga rumah adalah 'Ocean Proximity: Inland', 'Median Income', 'Longitude', 'Latitude', dan 'Ocean Proximity: Near Ocean'.
- 'Median Income' memiliki tingkat penting tinggi, menunjukkan bahwa pendapatan tengah rumah tangga di suatu daerah adalah faktor kunci dalam memprediksi harga rumah. Semakin tinggi pendapatan, semakin besar kemungkinan harga rumah lebih tinggi.

**Kesimpulan:**
- Kesimpulan keseluruhan adalah bahwa model dapat dianggap baik dalam memprediksi harga rumah yang tentunya sesuai pada batasan fitur yang telah disebutkan sebelumnya, jika data yang diprediksi lebih / kurang dari batasan yang telah dijelaskan sebelumnya maka model tidak akan memprediksi dengan baik.
- Perhatian khusus pada Ocean Proximity: Inland, 'Median Income' di area tersebut,Longitude, Latitude, dan Ocean Proximity: Near Ocean sebagai 5 faktor utama yang mempengaruhi harga properti jika seseorang memiliki rencana untuk membeli rumah yang sesuai dengan budget dan tidak overprice, serta kepada pengusaha agar tidak menjual dengan overprice / underprice yang keduanya dapat menurunkan pendapatan (overprice menyebabkan konsumen tidak jadi membeli dan underprice harga jauh di bawah market). 

**Recommendations**

1. Penambahan fitur data dapat menjadi langkah yang signifikan untuk meningkatkan performa model prediksi harga rumah. Berikut adalah beberapa ide penambahan fitur yang dapat dipertimbangkan:
    - Rasio Kamar Tidur terhadap Jumlah Kamar: Menambahkan fitur yang mencerminkan rasio kamar tidur terhadap jumlah total kamar bisa memberikan wawasan tentang seberapa besar rasio ruang tidur terhadap ruang umum. Ini dapat memberikan informasi tambahan tentang tata letak dan proporsi rumah.
     - Luas Bangunan per Luas Tanah: Menambahkan fitur yang mencerminkan rasio luas bangunan terhadap luas tanah dapat memberikan informasi tentang sejauh mana tanah digunakan dan memungkinkan model memperhitungkan efisiensi penggunaan lahan.
     - Fasilitas Umum di Sekitar: Menambahkan fitur yang mencantumkan jarak ke fasilitas umum seperti sekolah, pusat perbelanjaan, atau rumah sakit dapat memberikan gambaran tentang kepraktisan lokasi properti dan memengaruhi harga.
     - Pertumbuhan Ekonomi Daerah: Menyertakan indikator pertumbuhan ekonomi di daerah tersebut, seperti pembangunan baru atau proyek-proyek infrastruktur, dapat memberikan pemahaman tentang potensi kenaikan nilai properti di masa depan.
     - Pendekatan Jarak ke Pusat Kota: Menambahkan fitur yang mencerminkan jarak relatif ke pusat kota atau pusat bisnis dapat memberikan informasi tentang seberapa strategis lokasi properti.
     - Indeks Kualitas Hidup: Jika data tersedia, fitur yang mencerminkan indeks kualitas hidup di daerah tersebut dapat menjadi faktor penting dalam menentukan harga rumah.
     - Fitur Interaksi Antara Variabel: Eksplorasi fitur interaksi antara variabel-variabel utama, seperti produk atau rasio antara dua fitur, untuk melihat apakah ada hubungan yang lebih kompleks yang dapat ditemukan.
2. Menyelidiki prediksi dengan nilai error yang signifikan, kita dapat mengkategorikan error tersebut ke dalam dua grup, yaitu overestimation (penilaian terlalu tinggi) dan underestimation (penilaian terlalu rendah). Kita akan memilih 5% prediksi dengan error terbesar dari masing-masing grup untuk dianalisis lebih lanjut. Sementara itu, 90% prediksi dengan error mendekati nilai rata-rata akan membentuk grup mayoritas. Langkah selanjutnya adalah mengevaluasi hubungan antara error dan setiap variabel independen. Analisis ini akan memberikan wawasan tentang variabel mana dan aspek apa yang mempengaruhi model menghasilkan error tinggi. Dengan pemahaman ini, dapat dilakukan pelatihan ulang dengan penerapan teknik feature engineering yang lebih baik untuk meningkatkan kinerja model.
3. Untuk meningkatkan jumlah data, bisa dilakukan pengumpulan data tambahan. Jika ingin mengevaluasi model yang lebih kompleks, misalnya menggunakan recursive neural networks (RNN), tetapi perlu diingat bahwa jika jumlah data dan fitur tetap seperti dataset saat ini, perubahan mungkin tidak signifikan.

---

# **Langkah 5: Save Model**

---
Setelah model yang dibangun selesai, model disimpan ke dalam file menggunakan modul pickle. Model disimpan dalam format file yang dapat digunakan kembali nanti.
