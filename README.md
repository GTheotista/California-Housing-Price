# **California Housing Price**

**Tools:** Python & Tableau<br>
**Visualizations:** Python(Matplotlib/Seaborn) & Tableau<br> 
**Dataset:** Supermarket Customers

**Table of Contents:**

- [**Supermarket Customers Analysis**](#California Housing Price)
- [**Langkah 0: Business Problem Understanding**](#Langkah-0-Business-Problem-Understanding)
- [**Langkah 1: Data Understanding**](#Langkah-1-Data-Understanding)
- [**Langkah 2: Data Preprocessing**](#Langkah-2-Data-Preprocessing)
- [**Langkah 3: Modeling**](#Langkah-3-Modeling)
- [**Langkah 4: Visualisasi Tableau**](#Langkah-4-Visualisasi-Tableau)

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

**Kesimpulan**
Dengan menggunakan model XGBoost dan melakukan tuning hiperparameter, saya berhasil menghasilkan model yang dapat memberikan prediksi harga properti dengan tingkat akurasi yang lebih tinggi. Meskipun terdapat batasan dalam nilai RMSE dan MAE yang cukup besar, MAPE yang rendah menunjukkan bahwa model mampu memberikan estimasi harga properti dengan tingkat kesalahan yang kecil. Pemahaman fitur penting juga memberikan wawasan yang berharga bagi konsumen dan pengusaha properti untuk membuat keputusan yang lebih informasional dan tepat.
