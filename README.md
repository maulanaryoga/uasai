# Laporan Akhir Kecerdasan Buatan - Kelompok 3

**Anggota Kelompok :**

1. JAgustinus Ricad Simbolon - NIM. 3.34.21.3.03
2. Maulana Arya Yoga J. - NIM. 3.34.21.3.14

## Domain Proyek

*Smartphone* di era digital saat ini menjadi barang yang sangat esensial untuk menunjang pembelajaran dan pekerjaan. Menurut data dari Asosiasi Penyelenggara Jasa Internet Indonesia (APJII) tahun 2022 menunjukan bahwa 89,03% penduduk Indonesia memiliki smartphone [1]. Bahkan lebih dari 70% penduduk memiliki *smartphone* lebih dari dua. Harga *smartphone* menjadi parameter yang paling berpengaruh terhadap kecenderungan seseorang membeli *smartphone*. Oleh karena itu kemampuan *machine learning* dalam memprediksi harga *smartphone* menjadi sangat penting untuk masyarakat yang ingin mencari *smartphone* sesuai kebutuhannya.

Terdapat beberapa parameter untuk memprediksi harga *smartphone*. Salah satu parameter tersebut adalah ukuran RAM, ukuran Layar, Prosesor, ukuran memori internal, kapasitas baterai dan sebagainya [2]. Salah satu bidang penelitian machine learning yang didapat digunakan untuk melakukan predikasi adalah regresi. Algoritma regresi dapat memprediksi nilai dari sebuah variabel target berdasarkan nilai dari beberapa variabel input (atau fitur). Terdapat beberapa penelitian terkait prediksi harga *smartphone*. Salah satu diantaranya adalah penelitian yang dilakukan oleh [3] yang memprediksi harga *smartphone* menggunakan beberapa algoritma *machine learning* seperti Random Forest, Logistic Regression, Decision Tree, Linear Discriminant Analysis, K-Nearest Neighbor and SVC. Hasilnya algoritma SVC memiliki akurasi paling baik.

Selanjutnya penelitian yang dilakukan oleh [4] yang melakukan prediksi harga *smartphone* menggunakan 25 jenis algoritma *machine learning*. Hasil pengujian menunjukan algoritma SVM memiliki akurasi paling besar yaitu 0.9470. Pada proyek ini dilakukan prediksi harga smartphone menggunakan beberapa algoritma machine learning. Sebelum pelatihan model dan evaluasi, terlebih dahulu dilakukan manipulasi data, dan pembersihan data agar model *machine learning* yang dihasilkan memiliki akurasi yang tinggi.

## Business Understanding

Setiap tahun terdapat berbagai jenis tipe *smartphone* dengan fitur yang bermacam-macam. Umumnya *smartphone* tipe tertentu meng-*upgrade* perangkatnya dari segi penambahan ukuran kamera, kapasitas RAM dan memori internal, serta kecepatan prosesor. Penambahan fitur pada *smartphone* akan mempengaruhi kenaikan harga *smartphone* tersebut. Oleh karena itu calon konsumen harus memahami spesifikasi *smartphone* yang akan dibeli disesuaikan dengan budget yang dimiliki. Diperlukan sebuah model *machine learning* yang dapat memprediksi harga *smartphone* dengan akurat. Sehingga calon konsumen dapat menyiapkan budget yang digunakan untuk membeli *smartphone* dengan spesifikasi yang dia diinginkan.

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

Dataset yang digunakan pada proyek ini diperoleh dari Kaggle. Silahkan kunjungi tautan berikut [Mobile Phone Specifications and Prices](https://www.kaggle.com/datasets/pratikgarai/mobile-phone-specifications-and-prices) untuk mengakses dataset yang dipakai. Adapun variabel-variabel yang terdapat pada dataset adalah sebagai berikut :

1. **Name**: Nama *Smarphone*
2. **Brand**: Nama Brand
3. **Model**: Model *Smarphone*
4. **Battery capacity (mAh)**: Kapasitas Baterai dalam mAh
5. **Screen size (inches)**: Ukuran layar dalam Inchi
6. **Touchscreen**: Informasi apakah *Smarphone* ada Touchscreen atau tidak
7. **Resolution x**: Resolusi lebar layar dari *Smarphone*
8. **Resolution y**: Resolusi panjang layar dari *Smarphone*
9. **Processor**: Jumlah core dari Prosesor
10. **RAM (MB)**: Jumlah RAM dari  *Smarphone* dalam MB
11. **Internal storage**: Kapasitas memori internal dalam GB
12. **Rear camera**: Resolusi kamera belakang dalam MP (0 jika tidak ada kamera belakang)
13. **Front camera**: Resolusi kamera depan dalam MP (0 jika tidak ada kamera belakang)
14. **Operation system**: OS yang digunakan pada *Smarphone*
15. **Wi-Fi**: Ketersediaan Wi-Fi dari *Smarphone*
16. **Bluetooth**: Ketersediaan Bluetooth dari *Smarphone*
17. **GPS**: Ketersediaan GPS dari *Smarphone*
18. **Number of SIMs**: Jumlah slot SIM card *Smarphone*
19. **3G**: Ketersediaan 3G dari *Smarphone*
20. **4G/LTE**: Ketersediaan 4G/LTE dari *Smarphone*
21. **Price:** Harga *Smarphone* dalam mata uang india (INR)

Pada dataset, terdapat 12 fitur numerikal dan 9 fitur kategorikal. Ringkasan statistik dari data-data numerikal dapat dilihat pada Tabel 1.

<div style="text-align:center">Tabel 1. Ringkasan Statistik Data-Data Numerikal Pada Dataset</div>

|       | Unnamed: 0  | Battery capacity (mAh) | Screen size (inches) | Resolution x | Resolution y | Processor   | RAM (MB)     | Internal storage (GB) | Rear camera | Front camera | Number of SIMs | Price         |
| ----- | ----------- | ---------------------- | -------------------- | ------------ | ------------ | ----------- | ------------ | --------------------- | ----------- | ------------ | -------------- | ------------- |
| count | 1359.000000 | 1359.000000            | 1359.000000          | 1359.000000  | 1359.000000  | 1359.000000 | 1359.000000  | 1359.000000           | 1359.000000 | 1359.000000  | 1359.000000    | 1359.000000   |
| mean  | 679.000000  | 2938.489330            | 5.291310             | 811.543046   | 1490.777778  | 5.551141    | 2488.777778  | 30.654864             | 12.070199   | 7.037969     | 1.833701       | 11465.825607  |
| std   | 392.453819  | 873.514133             | 0.671357             | 270.707271   | 557.780120   | 2.196562    | 1664.440386  | 36.950241             | 8.948337    | 6.295448     | 0.374457       | 13857.497077  |
| min   | 0.000000    | 1010.000000            | 2.400000             | 240.000000   | 320.000000   | 1.000000    | 64.000000    | 0.064000              | 0.000000    | 0.000000     | 1.000000       | 494.000000    |
| 25%   | 339.500000  | 2300.000000            | 5.000000             | 720.000000   | 1280.000000  | 4.000000    | 1000.000000  | 8.000000              | 8.000000    | 2.000000     | 2.000000       | 4763.500000   |
| 50%   | 679.000000  | 3000.000000            | 5.200000             | 720.000000   | 1280.000000  | 4.000000    | 2000.000000  | 16.000000             | 12.200000   | 5.000000     | 2.000000       | 6999.000000   |
| 75%   | 1018.500000 | 3500.000000            | 5.700000             | 1080.000000  | 1920.000000  | 8.000000    | 3000.000000  | 32.000000             | 13.000000   | 8.000000     | 2.000000       | 11999.000000  |
| max   | 1358.000000 | 6000.000000            | 7.300000             | 2160.000000  | 3840.000000  | 10.000000   | 12000.000000 | 512.000000            | 108.000000  | 48.000000    | 3.000000       | 174990.000000 |

Pada tahap *Data Understanding* dilakukan analisis data eksploratif untuk mendapatkan wawasan tentang karakteristik data, memahami struktur data, dan mengidentifikasi potensi masalah atau kesalahan yang mungkin terjadi. Kegiatan Data Understanding yang dilakukan pada Proyek ini antara lain :

- Memberikan informasi seperti jumlah data, *missing value*, duplikasi data, korelasi antar kolom, dan sebaran data.

- Melakukan manipulasi data untuk mendapatkan variabel atau fitur baru seperti menggabungkan kolom Resolution X dan Resolution Y untuk mendapatkan nilai PPI (*Pixel Per Inch*).

- Melakukan visualisasi data untuk mengetahui korelasi dan sebaran data. Visualisasi korelasi antar kolom digambarkan dalam heatmap seperti ditunjukan Gambar 1. Berdasarkan diagaram heatmap Gambar 1 diketahui bahawa terdapat beberapa kolom seperti Battery, Processor, RAM, dll yang berkorelasi dengan kolom 'Prize'.  Semakin mendekati nilai 1 maka korelasi semakin tinggi. Kemudian hasil visualisasi heatmap hanya menampilkan korelasi pada kolom yang memberikan data numerikal, sedangkan kolom yang memberikan hasil kategorikal tidak dapat diketahui korelasinya.

  <img src="https://afandistudio.net/prak_ai/korelasi.png" style="zoom:67%;" />
  
  <div style="text-align:center">Gambar 1. Visualisasi Korelasi Data dengan Heatmap</div>
  
  Sedangkan contoh visualisasi dari sebaran data ditunjukan pada Gambar 2. Visualisasi yang ditunjukan pada Gambar 2 menunjukan bahwa ada ketidakseimbangan data pada kolom Battery, Screen_Size, Processor, dan RAM.
  
  ![](https://afandistudio.net/prak_ai/sebaran_data_mlt1.png)

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
   | GradientBoostingRegressor     | 0.71               | 0.72      | 0.40 | 0.53       |
   | RandomForestRegressor         | 0.70               | 0.72      | 0.40 | 0.53       |
   | BaggingRegressor              | 0.69               | 0.71      | 0.41 | 0.07       |
   | SVR                           | 0.69               | 0.70      | 0.41 | 0.14       |
   | NuSVR                         | 0.69               | 0.70      | 0.41 | 0.26       |
   | LGBMRegressor                 | 0.68               | 0.70      | 0.42 | 0.10       |
   | HistGradientBoostingRegressor | 0.68               | 0.69      | 0.42 | 1.16       |
   | LassoLarsIC                   | 0.66               | 0.68      | 0.43 | 0.04       |
   | LassoCV                       | 0.66               | 0.68      | 0.43 | 0.17       |
   | LarsCV                        | 0.66               | 0.68      | 0.43 | 0.07       |
   | LassoLarsCV                   | 0.66               | 0.68      | 0.43 | 0.08       |
   | HuberRegressor                | 0.66               | 0.68      | 0.43 | 0.10       |
   | ElasticNetCV                  | 0.66               | 0.68      | 0.43 | 0.17       |
   | Lars                          | 0.66               | 0.67      | 0.43 | 0.03       |
   | LinearRegression              | 0.66               | 0.67      | 0.43 | 0.02       |
   | TransformedTargetRegressor    | 0.66               | 0.67      | 0.43 | 0.02       |
   | RidgeCV                       | 0.66               | 0.67      | 0.43 | 0.03       |
   | Ridge                         | 0.66               | 0.67      | 0.43 | 0.02       |
   | BayesianRidge                 | 0.66               | 0.67      | 0.43 | 0.04       |

   Algoritma dengan performa terbaik dilihat dari nilai R-Square dan RMSE. Semakin besar nilai R-Square (mendekati 1) maka model semakin akurat. Sedangkan pada RMSE, apabila nilai semain kecil (mendekati 0), maka akurasi model akan semakin tinggi. Berdasarkan hasil R-Square dan RMSE menggunakan Lazy Predict pada Tabel 1, disimpulkan bahwa 3 algoritma terbaik yang akan digunakan untuk mempredikasi harga adalah **GradientBoostingRegressor**, **RandomForestRegressor**, dan **BaggingRegressor**.

2. Menggunakan `ColumnTransformer` untuk mengubah data kategorik menjadi numerik

   Pada proyek ini masih mempertahankan kolom kategorikal yaitu Brand dan OS. Sebab pada saat ingin mempredikasi harga smartphone, calon pembeli tentunya akan memilih Brand dan OS dalam bentuk kategori bukan numerik. Oleh karena itu kita ubah data kategorik menjadi numberik menggunkan teknik OneHotEncoding. Tapi sebelum dilakukan teknik `OneHotEncoding` dilakukan harus menampilkan indeks dari masing-masing kolom menggunakan fungsi `enumerate()`. Brand berada di indeks 0, dan OS berada di index 9. Selanjutkan dilakukan proses `ColumnTransformer`.

3. Membuat pipeline untuk menggabungkan data numerik dan kategorik

   Hasil penggunakan teknik `ColumnTransformer` disimpan dalam objek feature. Selanjutnya dilakukan proses pipeline untuk menggabungkan dan meng-optimasi kolom numerikal dan kategorikan agar dapat di proses oleh algoritma machine learning. 

4. Memilih 3 (tiga) algoritma dengan performa terbaik untuk di evaluasi

   Setelah dilakukan proses pelatihan oleh Lazy Predict, diperoleh 3 algoritma dengan performa terbaik yaitu :

   - **GradientBoostingRegressor**

     GradientBoostingRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa pohon keputusan untuk membuat model yang lebih kuat. Algoritma GradientBoostingRegressor bekerja dengan menggabungkan banyak pohon keputusan sederhana. Setiap pohon yang ditambahkan ke model berusaha untuk memperbaiki kesalahan prediksi yang dihasilkan oleh pohon sebelumnya. Algoritma ini bekerja dengan cara mengoptimalkan gradien fungsi kerugian (misalnya, *Mean Squared Error*) menggunakan proses iteratif. Ilustrasi dari cara kerja GradienBoostingRegressor ditunjukan pada Gambar 2.

     ![](https://afandistudio.net/prak_ai/GradienRegression.png)

     <div style="text-align:center">Gambar 2. Ilustrasi GradienBoostingRegressor [5]</div>

   - **RandomForestRegressor**

     RandomForestRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa pohon keputusan acak (*random decision trees*) untuk membuat model yang lebih kuat. Pada dasarnya, algoritma RandomForestRegressor bekerja dengan menggabungkan hasil dari banyak pohon keputusan acak yang diberi bobot yang sama. Setiap pohon keputusan acak dibangun dengan menggunakan subset acak dari data pelatihan dan subset acak dari fitur (variabel independen). Proses ini dikenal sebagai bootstrap aggregating atau biasa disebut juga sebagai "bagging". Ilustrasi dari cara kerja RandomForestRegressor ditunjukan pada Gambar 3.

     <img src="https://afandistudio.net/prak_ai/RFRegression.jpg" style="zoom: 25%;" />

     <div style="text-align:center">Gambar 3. Ilustrasi RandomForestRegressor [6]</div>

   - **BaggingRegressor**

     BaggingRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa model regresi (misalnya, Regresi Linier, DecisionTreeRegressor) untuk membuat model yang lebih kuat. Pada dasarnya, algoritma BaggingRegressor bekerja dengan membuat beberapa model regresi yang berbeda menggunakan subset acak dari data pelatihan. Setiap model regresi dibangun secara independen dan tidak saling bergantung satu sama lain. Ketika melakukan prediksi, hasil dari semua model regresi digabungkan untuk menghasilkan prediksi akhir dengan menggunakan rata-rata atau mayoritas suara (tergantung pada jenis variabel target). Ilustrasi dari cara kerja BaggingRegressor ditunjukan pada Gambar 4.

     <img src="https://afandistudio.net/prak_ai/BaggingRegressor.png" style="zoom:50%;" />

     <div style="text-align:center">Gambar 4. Ilustrasi BaggingRegressor [7]</div>

     Namun, BaggingRegressor tidak memberikan interpretasi model yang langsung seperti Regresi Linier. Selain itu, dalam beberapa kasus, jika terdapat korelasi yang kuat antara fitur, BaggingRegressor mungkin tidak memberikan peningkatan yang signifikan dalam kinerja prediksi dibandingkan dengan model regresi tunggal.

5. Menambahkan parameter tunning untuk mengingkatkan performa model

   Penambahan parameter menggunakan **Teknik Grid Search**. Sehingga diperoleh hyperparameter dari masing-masing algoritma adalah sebagai berikut.

   - Parameter GradienBoostingRegressor
   
     - n_estimator = 90
     - max_depth = 5
     - min_samples_split = 10
     - min_samples_leaf = 4
     - max_features = 4
     
   - Parameter RandomForestRegressor
   
     - n_estimator = 90
   - max_samples = 0.4
     - max_features = 0.5
   
   - Parameter BaggingRegressor

     - n_estimators = 70
     - max_features = 0.7
     - max_samples = 0.6
  - warm_start= False
     - oob_score = False
  - bootstrap = False
    


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

  <div style="text-align:center">Tabel 3. Hasil Pengujian dari 3 Algoritma Teratas</div>

  | id   | Model_Name       | MSE       | R2 Score  | RMSE      |
  | ---- | ---------------- | --------- | --------- | --------- |
  | 0    | GradienBoosting  | 0.1588188 | 0.7238088 | 0.3985208 |
  | 1    | RandomForest     | 0.1639016 | 0.7149698 | 0.4048476 |
  | 2    | BaggingRegressor | 0.1595067 | 0.7226127 | 0.3993828 |

- Membandingkan data sebenarnya dengan hasil prediksi. Hasil perbandingan dapat dilihat pada Tabel 4.

  <div style="text-align:center">Tabel 4. Hasil Perbandingan Data Sebenarnya dengan Hasil Prediksi</div>
  
  | Id   | y_true     | prediksi_GB | prediksi_RF | prediksi_BG |
  | :--- | :--------- | :---------- | :---------- | :---------- |
  | 965  | 13.6112660 | 13.9000000  | 13.9000000  | 14.0000000  |
  | 657  | 13.4294333 | 13.6000000  | 13.6000000  | 13.7000000  |
  | 1002 | 13.7166489 | 13.5000000  | 13.4000000  | 13.4000000  |
  | 918  | 13.2056893 | 13.7000000  | 13.7000000  | 13.8000000  |
  | 798  | 14.3035242 | 13.9000000  | 14.0000000  | 14.0000000  |
  | ...  | ...        | ...         | ...         | ...         |
  | 53   | 15.1153689 | 14.9000000  | 15.0000000  | 15.0000000  |
  | 1027 | 13.5657933 | 13.8000000  | 13.8000000  | 14.0000000  |
  | 436  | 14.1867278 | 13.3000000  | 13.3000000  | 13.3000000  |
  | 161  | 14.9745150 | 15.9000000  | 15.9000000  | 15.8000000  |
  | 47   | 15.2850487 | 14.9000000  | 15.1000000  | 14.9000000  |

## Conclussion

1. Berdasarkan hasil pengukuran, terdapat 10 kolom atau fitur yang mempengaruhi *Price* yaitu Brand, Battery, Screen_Size, Processor, RAM, Internal_Storage, Rear_Camera, Front_Camera, OS, dan PPI.
2. Proses preprocessing yang dilakukan adalah dengan melakukan manipulasi data seperti mengabungkan Resolution X dan Resolution Y untuk menghasilkan fitur baru yaitu PPI. Menghapus data yang tidak memiliki korelasi yang signifikan dengan *Price*, dan mengubah format tipe data pada setiap kolom yang memiliki korelasi.
3. Berdasarkan hasil pengujian model, diperoleh hasil bahwa algoritma GradienBoosting memiliki performa yang paling baik yaitu memiliki nilai RMSE paling kecil dan R2 Score paling besar.
4. Meningkatkan performa model dapat dilakukan dengan menambahkan hyperparameter.  Pemilihan hyperparameter yang menghasilkan performa terbaik dapat dilakukan menggunakan teknik Grid Search.
5. Dataset yang digunakan memiliki rentang jangkauan yang berbeda (imbalace), oleh sebab itu agar performa model lebih baik maka perlu dilakukan teknik SMOTE untuk menangani imbalance dataset.

## Referensi

[1]   APJII, “Laporan Survei Internet APJII 2021 - 2021,” 2022. [Online]. Available: [https://apjii.or.id/survei](https://apjii.or.id/survei).

[2]   S. Subhiksha, S. Thota, and J. Sangeetha, “Prediction of Phone Prices Using machine learning,” 2020, doi: [10.1007/978-981-15-1097-7_65](https://doi.org/10.1007/978-981-15-1097-7_65).

[3]   M. Çetın and Y. Koç, “Mobile Phone Price Class Prediction Using Different Classification Algorithms with Feature Selection and Parameter Optimization,” 2021, doi: [10.1109/ISMSIT52890.2021.9604550](https://doi.org/10.1109/ISMSIT52890.2021.9604550).

[4]   A. Kalmaz and O. Akin, “Estimation of Mobile Phone Prices with machine learning,” 2022, doi: [10.1109/ICEET56468.2022.10007128](https://doi.org/10.1109/ICEET56468.2022.10007128).

[5]  V. Aliyev, “A hands-on explanation of Gradient Boosting Regression,” *medium.com*, 2020. https://vagifaliyev.medium.com/a-hands-on-explanation-of-gradient-boosting-regression-4cfe7cfdf9e (accessed Jun. 03, 2023).

[6]   J. H. Graw, W. T. Wood, and B. J. Phrampus, “Predicting Global Marine Sediment Density Using the Random Forest Regressor machine learning Algorithm,” *J. Geophys. Res. Solid Earth*, vol. 126, no. 1, pp. 1–14, 2021, doi: [10.1029/2020JB020135](https://doi.org/10.1029/2020JB020135).

[7]   A. Biswal, “Bagging in machine learning: Step to Perform And Its Advantages,” *simplilearn.com*, 2023. https://www.simplilearn.com/tutorials/machine-learning-tutorial/bagging-in-machine-learning (accessed Jun. 03, 2023).

**---Ini adalah bagian akhir laporan---**
