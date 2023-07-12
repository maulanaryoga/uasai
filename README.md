# Laporan Akhir Kecerdasan Buatan - Kelompok 3

**Anggota Kelompok :**

1. Agustinus Ricad Simbolon - NIM. 3.34.21.3.03
2. Maulana Arya Yoga Juliansyah - NIM. 3.34.21.3.13

## Domain Proyek

Dalam era digital saat ini, *smartphone* telah menjadi suatu kebutuhan yang sangat penting dalam mendukung aktivitas pembelajaran dan pekerjaan. Menurut data dari Asosiasi Penyelenggara Jasa Internet Indonesia (APJII) tahun 2022 menunjukan bahwa 89,03% penduduk Indonesia memiliki smartphone [1]. Bahkan lebih dari 70% penduduk memiliki *smartphone* lebih dari dua. Harga *smartphone* menjadi parameter yang paling berpengaruh terhadap kecenderungan seseorang membeli *smartphone*. Oleh karena itu kemampuan *machine learning* dalam memprediksi harga *smartphone* menjadi sangat penting untuk masyarakat yang ingin mencari *smartphone* sesuai kebutuhannya.  Dalam konteks ini, harga *smartphone* menjadi faktor yang sangat berpengaruh dalam keputusan pembelian.

Terdapat beberapa parameter untuk memprediksi harga *smartphone*. Salah satu parameter tersebut adalah ukuran RAM, ukuran Layar, Prosesor, ukuran memori internal, kapasitas baterai dan sebagainya [2]. Salah satu bidang penelitian machine learning yang didapat digunakan untuk melakukan predikasi adalah regresi. Algoritma regresi dapat memprediksi nilai dari sebuah variabel target berdasarkan nilai dari beberapa variabel input (atau fitur). Terdapat beberapa penelitian terkait prediksi harga *smartphone*. Salah satu diantaranya adalah penelitian yang dilakukan oleh [3] yang memprediksi harga *smartphone* menggunakan beberapa algoritma *machine learning* seperti Random Forest, Logistic Regression, Decision Tree, Linear Discriminant Analysis, K-Nearest Neighbor and SVC. Hasilnya algoritma SVC memiliki akurasi paling baik.

## Business Understanding

Setiap tahun, berbagai jenis *smartphone* dengan fitur yang beragam tersedia di pasaran. Biasanya, tipe *smartphone* tertentu akan mengalami peningkatan dengan penambahan fitur seperti peningkatan ukuran kamera, kapasitas RAM dan memori internal, serta kecepatan prosesor. Penambahan fitur ini berdampak pada kenaikan harga *smartphone*. Oleh karena itu, calon konsumen perlu memahami spesifikasi *smartphone* yang ingin dibeli dan menyesuaikannya dengan budget yang dimiliki. Dalam hal ini, model *machine learning* yang dapat memprediksi harga *smartphone* dengan akurat sangat diperlukan. Dengan demikian, calon konsumen dapat menentukan budget yang sesuai untuk membeli *smartphone* dengan spesifikasi yang diinginkan.

#### Problem Statements

Berdasarkan permasalahan yang telah dijelaskan, *problem statements* dari proyek ini adalah sebagai berikut.

1. Fitur-fitur apa saja yang paling berpengaruh terhadap harga *smartphone* ?
2. Bagaimana proses *Pre-Processing* yang dilakukan agar menghasilkan model *machine learning* yang akurat ?
3. Bagaimana membuat atau memilih model *machine learning* yang memiliki akurasi terbaik dalam memprediksi harga *smartphone* ?

#### Goals

Tujuan yang hendak dicapai dari proyek ini adalah sebagai berikut 

1. Mengetahui fitur yang paling berkorelasi dengan penentuan harga *smartphone*.
2. Membuat model *machine learning* yang dapat memprediksi harga *smartphone*.
3. Memilih model *machine learning* yang menghasilkan prediksi paling akurat berdasarkan proses *preprocessing* yang dilakukan

####  Solution Statements

Solusi yang diajukan untuk menyelesaikan masalah yang telah diuraikan adalah sebagai berikut.

1. Melakukan analisis deskriptif untuk mengetahui pola dan informasi yang tersimpan di data mengenai fitur atau spesifikasi yang mempengaruhi harga *smartphone*.
2. Melakukan proses *Data Manipulation* untuk menggabungkan kolom-kolom yang berpengaruh terhadap akurasi predisi harga *smartphone* 
3. Melakukan  Proses *Preprocessing* seperti :
   - Mengecek *missing value* dan duplikasi data. Kebetulan dataset yang digunakan tidak ada *missing value* dan duplikasi data.
   - Menghapus kolom yang tidak berpengaruh terhadap prediksi harga
   - Melakukan visualisasi data untuk melihat persebaran dan korelasi antar kolom
   - Membagi data menjadi *training* dan *test set*, dengan prosentase 85% banding 15%. Alasan menggunakan 15% karena jumlah data yang digunakan banyak, jadi hanya dengan 15% sudah didapatkan banyak data tes.
   - Melakukan *Encoding* terhadap kolom yang bertipe objek / kategorikal menggunakan fungsi `Map`.
4. Melakukan pemilihan model terbaik menggunakan LazyPredict
   - Memilih 4 algoritma yang menghasilkan model dengan performa terbaik
   - Perfoma model terbaik dilihat dari skor *Mean Square Error* (MSE), *Root Mean Square Error* (RMSE), dan *R Square* (R2).

## Data Understanding

Dataset yang digunakan pada proyek ini diperoleh dari Kaggle. Silahkan kunjungi tautan berikut [Mobile Phones Data](https://www.kaggle.com/datasets/pratikgarai/mobile-phone-specifications-and-prices) untuk mengakses dataset yang dipakai. Adapun variabel-variabel yang terdapat pada dataset adalah sebagai berikut :

1. **Name**: Nama Smartphone
2. **Brand**: Nama Brand
3. **Model**: Model Smartphone
4. **Battery Size**: Kapasitas Baterai dalam mAh
5. **memory_size**: Kapasitas memori internal dalam GB
6. **popularity**: Popularitas smartphone pada pasar
7. **best_price**: Harga terbaik smartphone pada pasaran
8. **lowest_price**: Harga terendah smartphone pada pasaran
9. **highest_price**: Harga tertinggi smartphone pada pasaran
10. **seller_amount**: Jumlah penjual smartphone
11. **screen_size**: Ukuran layar smartphone
12. **release_date**: Tanggal smartphone rilis

Pada dataset, terdapat 12 fitur numerikal dan 9 fitur kategorikal. Ringkasan statistik dari data-data numerikal dapat dilihat pada Tabel 1.

<div style="text-align:center">Tabel 1. Ringkasan Statistik Data-Data Numerikal Pada Dataset</div>

| Unnamed: 0 | brand_name | model_name                                   | os      | popularity | best_price  | lowest_price | highest_price | sellers_amount | screen_size | memory_size | battery_size | release_date |
| ---------- | ---------- | -------------------------------------------- | ------- | ---------- | ----------- | ------------ | ------------- | -------------- | ----------- | ----------- | ------------ | ------------ |
| 0          | ALCATEL    | 1 1/8GB Bluish Black (5033D-2JALUAA)         | Android | 422        | 1359.000000 | 1359.000000  | 1359.000000   | 36             | 5.00        | 8.0         | 2000.0       | 10-2020      |
| 1          | ALCATEL    | 1 5033D 1/16GB Volcano Black (5033D-2LALUAF) | Android | 323        | 5.551141    | 2488.777778  | 30.654864     | 36             | 5.00        | 16.0        | 2000.0       | 9-2020       |
| 2          | ALCATEL    | 1 5033D 1/16GB Volcano Black (5033D-2LALUAF) | Android | 299        | 2.196562    | 1664.440386  | 36.950241     | 36             | 5.00        | 16.0        | 2000.0       | 9-2020       |
| 3          | ALCATEL    | 1 5033D 1/16GB Volcano Black (5033D-2LALUAF) | Android | 287        | 1.000000    | 64.000000    | 0.064000      | 36             | 5.00        | 16.0        | 2000.0       | 9-2020       |
| 4          | Nokia      | 1.3 1/16GB Charcoal                          | Android | 1047       | 4.000000    | 1000.000000  | 8.000000      | 10             | 5.71        | 16.0        | 3000.0       | 4-2020       |



Pada tahap *Data Understanding* dilakukan analisis data eksploratif untuk mendapatkan wawasan tentang karakteristik data, memahami struktur data, dan mengidentifikasi potensi masalah atau kesalahan yang mungkin terjadi. Kegiatan Data Understanding yang dilakukan pada Proyek ini antara lain :

- Memberikan informasi seperti jumlah data, *missing value*, duplikasi data, korelasi antar kolom, dan sebaran data.

- Melakukan manipulasi data untuk mendapatkan variabel atau fitur baru seperti menggabungkan kolom Resolution X dan Resolution Y untuk mendapatkan nilai PPI (*Pixel Per Inch*).

- Melakukan visualisasi data untuk mengetahui korelasi dan sebaran data. Visualisasi korelasi antar kolom digambarkan dalam heatmap seperti ditunjukan Gambar 1. Berdasarkan diagaram heatmap Gambar 1 diketahui bahawa terdapat beberapa kolom seperti Battery, Processor, RAM, dll yang berkorelasi dengan kolom 'Price'.  Semakin mendekati nilai 1 maka korelasi semakin tinggi. Kemudian hasil visualisasi heatmap hanya menampilkan korelasi pada kolom yang memberikan data numerikal, sedangkan kolom yang memberikan hasil kategorikal tidak dapat diketahui korelasinya.

  <img src="https://github.com/maulanaryoga/uasai/assets/116423822/6b4d8dc2-2d29-48fe-a7b7-44630663d168" />

  <div style="text-align:center">Gambar 1. Visualisasi Korelasi Data dengan Heatmap</div>

  Sedangkan contoh visualisasi dari sebaran data ditunjukan pada Gambar 2. Visualisasi yang ditunjukan pada Gambar 2 menunjukan bahwa ada ketidakseimbangan data pada kolom Battery, Screen_Size, Processor, dan RAM.

  ![](https://github.com/maulanaryoga/uasai/assets/116423822/b34bdbdd-4742-4c38-9c81-0238d36b1c83)

<div style="text-align:center">Gambar 2. Visualisasi Data pada Dataset</div>

## Data Preparation

Teknik data preparation yang dilakukan pada proyek ini adalah sebagai berikut : 

1. Feature Selection : Melakukan seleksi fitur untuk menyeleksi kolom yang berperan sebagai data fitur dan kolom yang menjadi data label.

2. Data Splitting: Membagi dataset menjadi data latih dan data uji. Pada proyek ini perbandingan data latih dan data uji adalah 85 : 15.

3. Menampilkan informasi jumlah data latih dan data uji. Jumlah data latih adalah 1155, sedangkan data uji terdat 204 data. jumlah data fitur yang dipakai untuk pelatihan adalah 10.

   


## Modelling

Pada tahap ini dilakukan proses pelatihan untuk mendapatkan model dengan performa terbaik. Tahapan yang dilakukan pada proses Modelling adalah sebagai berikut.

1. Memprediksi algoritma dengan performa terbaik menggunakan Lazy Predict

   Lazy Predict adalah library Python yang membantu dalam membuat model *machine learning* dengan cepat dan mudah. Library ini dikembangkan untuk mempercepat proses eksplorasi data dan pemodelan awal. Hasil dari proses pelatihan yang dilakukan Lazy Predict ditunjukan pada Tabel 2.

   <div style="text-align:center">Tabel 2. Hasil Perbandingan model menggunakan Lazy Predict</div>

   | Model                         | Adjusted R-Squared | R-Squared | RMSE | Time Taken |
   | ----------------------------- | ------------------ | --------- | ---- | ---------- |
   | ExtraTreesRegressor           | 0.87               | 0.88      | 0.31 | 0.47       |
   | RandomForestRegressor         | 0.86               | 0.87      | 0.32 | 0.82       |
   | BaggingRegressor              | 0.86               | 0.87      | 0.32 | 0.11       |
   | SVR                           | 0.80               | 0.81      | 0.39 | 0.10       |
   | NuSVR                         | 0.79               | 0.81      | 0.39 | 0.15       |
   | LGBMRegressor                 | 0.85               | 0.86      | 0.34 | 0.32       |
   | HistGradientBoostingRegressor | 0.85               | 0.86      | 0.34 | 0.40       |
   | LassoLarsIC                   | 0.66               | 0.68      | 0.51 | 0.05       |
   | LassoCV                       | 0.66               | 0.68      | 0.50 | 0.17       |
   | LarsCV                        | 0.65               | 0.68      | 0.51 | 0.05       |
   | LassoLarsCV                   | 0.66               | 0.68      | 0.43 | 0.08       |
   | HuberRegressor                | 0.68               | 0.70      | 0.49 | 0.08       |
   | ElasticNetCV                  | -0.04              | 0.03      | 0.88 | 0.04       |
   | Lars                          |                    | 0.68      | 0.51 | 0.03       |
   | LinearRegression              | 0.66               | 0.68      | 0.50 | 0.02       |
   | TransformedTargetRegressor    | 0.66               | 0.68      | 0.50 | 0.02       |
   | RidgeCV                       | 0.66               | 0.68      | 0.50 | 0.03       |
   | Ridge                         | 0.66               | 0.68      | 0.50 | 0.02       |
   | BayesianRidge                 | 0.66               | 0.68      | 0.51 | 0.26       |

   Algoritma dengan performa terbaik dilihat dari nilai R-Square dan RMSE. Semakin besar nilai R-Square (mendekati 1) maka model semakin akurat. Sedangkan pada RMSE, apabila nilai semain kecil (mendekati 0), maka akurasi model akan semakin tinggi. Berdasarkan hasil R-Square dan RMSE menggunakan Lazy Predict pada Tabel 1, disimpulkan bahwa 3 algoritma terbaik yang akan digunakan untuk mempredikasi harga adalah **GradientBoostingRegressor**, **RandomForestRegressor**, dan **BaggingRegressor**.

2. Menggunakan `ColumnTransformer` untuk mengubah data kategorik menjadi numerik

   Pada proyek ini masih mempertahankan kolom kategorikal yaitu Brand dan OS. Sebab pada saat ingin mempredikasi harga smartphone, calon pembeli tentunya akan memilih Brand dan OS dalam bentuk kategori bukan numerik. Oleh karena itu kita ubah data kategorik menjadi numberik menggunkan teknik OneHotEncoding. Tapi sebelum dilakukan teknik `OneHotEncoding` dilakukan harus menampilkan indeks dari masing-masing kolom menggunakan fungsi `enumerate()`. Brand berada di indeks 0, dan OS berada di index 9. Selanjutkan dilakukan proses `ColumnTransformer`.

3. Membuat pipeline untuk menggabungkan data numerik dan kategorik

   Hasil penggunakan teknik `ColumnTransformer` disimpan dalam objek feature. Selanjutnya dilakukan proses pipeline untuk menggabungkan dan meng-optimasi kolom numerikal dan kategorikan agar dapat di proses oleh algoritma machine learning. 

4. Memilih algoritma dengan performa terbaik untuk di evaluasi

   Setelah dilakukan proses pelatihan oleh Lazy Predict, diperoleh 3 algoritma dengan performa terbaik yaitu :

   - **ExtraTreesRegressor**

     ExtraTreesRegressor adalah algoritma regresi yang digunakan dalam machine learning. Ini adalah variasi dari algoritma Random Forest yang menggabungkan beberapa pohon keputusan acak untuk membuat prediksi. Pohon keputusan acak dalam ExtraTreesRegressor dibangun dengan membagi dataset menjadi subset yang acak dan menggunakan subset tersebut untuk menghitung pembagian terbaik pada setiap langkah. Dalam setiap pohon keputusan, prediksi akhir diperoleh dengan mengambil rata-rata dari prediksi semua pohon.

5. Menambahkan parameter tunning untuk mengingkatkan performa model

   Penambahan parameter menggunakan **Teknik Grid Search**. Sehingga diperoleh hyperparameter dari masing-masing algoritma adalah sebagai berikut.

   - Parameter ExtraTreesRegressor

     - n_estimator = 90
     - max_depth = 5
     - min_samples_split = 10
     - min_samples_leaf = 4
     - max_features = 4
       

## Evaluation

- Metrik evaluasi yang digunakan adalah *Mean Square Error* (MSE), *Root Mean Square Error* (RMSE), dan *R Square* (R2 Score)

- MSE melakukan pengurangan nilai data aktual dengan data peramalan dan hasilnya dikuadratkan (*squared*) kemudian dijumlahkan secara keseluruhan dan membaginya dengan banyaknya data yang ada. Rumus dari MSE adalah sebagai berikut 
  $$
  MSE = \frac{1}{n} \Sigma_{i=1}^n({y}-\hat{y})^2
  $$
  Diketahui:

  - n = Jumlah Data
  - yi = *Actual Value* / Nilai Sebenarnya
  - ŷi = *Predicted Value* / Nilai Prediksi

- RMSE adalah jumlah dari kesalahan kuadrat atau selisih antara nilai sebenarnya dengan nilai prediksi yang telah ditentukan. Cara menghitungnya tinggal mengakar kan mse menggunakan fungsi *np.sqrt*. Rumus dari RMSE adalah sebagai berikut.
  $$
  RMSE = \sqrt{(\frac{1}{n})\sum_{i=1}^{n}(y_{i} - x_{i})^{2}}
  $$
  Diketahui:

  - n = Jumlah Data
  - yi = *Actual Value* / Nilai Sebenarnya
  - ŷi = *Predicted Value* / Nilai Prediksi

- R2 Score dijadikan sebagai pengukuran seberapa baik garis regresi mendekati nilai data asli yang dibuat melalui model. Rumus dari R2 Score adalah sebagai berikut.
  $$
  R^2 = 1 - {SS_R \over SS_T} =  1 - {\sum_{i} (y_i - ŷ_p) ^ 2 \over \sum_{i} (y_i - ȳ) ^ 2}
  $$

  - SSR : Kuadrat dari selisih nilai Y prediksi dengan nilai rata-rata Y = ∑ (Ypred – Yrata-rata)²
  - SST : Kuadrat dari selisih nilai Y aktual dengan nilai rata-rata Y = ∑ (Yaktual – Yrata-rata)²

- Setelah melalui tahap pelatihan dan evaluasi menggunakan MSE, RMSE, dan R Square, diperoleh hasil bahwa algoritma **GradienBoosterRegressor** memiliki performa yang paling baik seperti ditunjukan Tabel 3. Maksud performa yang paling baik adalah memiliki nilai MSE dan RMSE yang mendekati nilai 0, serta memiliki nilai R2 Score yang mendekati nilai 1.

  <div style="text-align:center">Tabel 3. Hasil Pengujian Algoritma </div>

  | id   | Model_Name | MSE       | R2 Score  | RMSE      |
  | ---- | ---------- | --------- | --------- | --------- |
  | 0    | ExtraTrees | 0.5185144 | 0.3548695 | 0.7200795 |

- Membandingkan data sebenarnya dengan hasil prediksi. Hasil perbandingan dapat dilihat pada Tabel 4.

  <div style="text-align:center">Tabel 4. Hasil Perbandingan Data Sebenarnya dengan Hasil Prediksi</div>

  | Id   | y_true     | prediksi_ET |
  | :--- | :--------- | :---------- |
  | 1131 | 10.2960025 | 9.6000000   |
  | 529  | 9.7290151  | 9.5000000   |
  | 392  | 8.3250637  | 9.5000000   |
  | 41   | 8.5623577  | 8.6000000   |
  | 681  | 8.8637572  | 8.6000000   |
  | ...  | ...        | ...         |
  | 582  | 8.2230906  | 8.6000000   |
  | 632  | 8.5338536  | 8.6000000   |
  | 557  | 8.5812941  | 8.6000000   |
  | 2    | 7.4972072  | 8.6000000   |
  | 1215 | 10.0363562 | 9.6000000   |

## Conclussion

1. Berdasarkan hasil pengukuran, terdapat 10 kolom atau fitur yang mempengaruhi *Prices* yaitu Brand, Battery, Screen_Size, RAM, Internal_Storage, OS.
2. Proses preprocessing yang dilakukan adalah dengan melakukan manipulasi data seperti mengabungkan lowest_price dan highest_price untuk menghasilkan fitur baru yaitu Prices. Menghapus data yang tidak memiliki korelasi yang signifikan dengan *Prices*, dan mengubah format tipe data pada setiap kolom yang memiliki korelasi.
3. Berdasarkan hasil pengujian model, diperoleh hasil bahwa algoritma Extra memiliki performa yang paling baik yaitu memiliki nilai RMSE paling kecil dan R2 Score paling besar.
4. Meningkatkan performa model dapat dilakukan dengan menambahkan hyperparameter.  Pemilihan hyperparameter yang menghasilkan performa terbaik dapat dilakukan menggunakan teknik Grid Search.
5. Dataset yang digunakan memiliki rentang jangkauan yang berbeda (imbalace), oleh sebab itu agar performa model lebih baik maka perlu dilakukan teknik SMOTE untuk menangani imbalance dataset.

## Referensi

[1]   S. Subhiksha, S. Thota, and J. Sangeetha, “Prediction of Phone Prices Using machine learning,” 2020, doi: [10.1007/978-981-15-1097-7_65](https://doi.org/10.1007/978-981-15-1097-7_65).

[2]   A. Kalmaz and O. Akin, “Estimation of Mobile Phone Prices with machine learning,” 2022, doi: [10.1109/ICEET56468.2022.10007128](https://doi.org/10.1109/ICEET56468.2022.10007128).

[3]   M. Çetın and Y. Koç, “Mobile Phone Price Class Prediction Using Different Classification Algorithms with Feature Selection and Parameter Optimization,” 2021, doi: [10.1109/ISMSIT52890.2021.9604550](https://doi.org/10.1109/ISMSIT52890.2021.9604550).

[4]  M. Saulo, N. Felipe "Online Extra Trees Regressor," 2019, doi: [https://ieeexplore.ieee.org/abstract/document/9926750]


**---Ini adalah bagian akhir laporan---**
