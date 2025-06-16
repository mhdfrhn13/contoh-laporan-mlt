# Laporan Proyek Machine Learning - Rafi Nanda Edtrian

## Domain Proyek
Sektor ritel sangat kompetitif, dan memahami penjualan sangat penting untuk kesuksesan bisnis. Kemampuan memprediksi tren penjualan, mengidentifikasi produk populer, dan memahami pola pembelian pelanggan adalah kunci pengambilan keputusan strategis. Tanpa analisis, perusahaan menghadapi tantangan seperti manajemen inventaris yang tidak efisien dan pemasaran yang tidak efektif.

Proyek ini menggunakan dataset transaksi penjualan historis (nomor transaksi, tanggal, detail produk, harga, kuantitas, pelanggan, negara) untuk mendapatkan wawasan. Tujuannya adalah mengidentifikasi tren penjualan, mengevaluasi kinerja produk, dan memahami pola pembelian pelanggan.

Dengan menggunakan analisis prediktif, khususnya model regresi linier, kami akan memprediksi total penjualan berdasarkan harga dan kuantitas. Prediksi yang akurat akan membantu perusahaan ritel mengoptimalkan inventaris, merencanakan promosi yang efektif, meningkatkan kepuasan pelanggan, dan membuat keputusan bisnis berbasis data. Secara keseluruhan, proyek ini menunjukkan bagaimana data penjualan dapat digunakan untuk keunggulan kompetitif dan pertumbuhan bisnis.

## Business Understanding

### Klarifikasi Masalah

Tahap **Business Understanding** adalah fondasi dari setiap proyek analisis data, yang memastikan bahwa tim analitik memiliki pemahaman yang jelas dan komprehensif tentang tujuan bisnis dan masalah yang perlu dipecahkan. Proses klarifikasi masalah melibatkan identifikasi tantangan spesifik yang dihadapi bisnis, merumuskan pertanyaan yang tepat, dan menentukan bagaimana solusi berbasis data dapat memberikan nilai.

### Problem Statements (Pernyataan Masalah)

Berdasarkan analisis awal data penjualan dan kebutuhan umum dalam sektor ritel, kami mengidentifikasi pernyataan masalah berikut:

1. **Volatilitas Penjualan yang Tidak Terprediksi**  
   Perusahaan ritel sering kali kesulitan memprediksi fluktuasi permintaan produk. Ketidakmampuan untuk memperkirakan volume penjualan di masa depan menyebabkan:
   - **Overstocking (kelebihan stok)**: Penumpukan inventaris yang tidak terjual, mengakibatkan biaya penyimpanan tinggi, risiko kerusakan atau kadaluwarsa produk, dan penurunan margin keuntungan.
   - **Understocking (kekurangan stok)**: Kehabisan stok produk yang diminati, menyebabkan hilangnya potensi penjualan, ketidakpuasan pelanggan, dan kerusakan reputasi merek.

2. **Kurangnya Wawasan Spesifik Produk**  
   Manajer produk tidak memiliki visibilitas yang cukup mengenai produk mana yang benar-benar mendorong pendapatan signifikan atau produk mana yang berkinerja buruk. Ini menghambat pengambilan keputusan terkait pengembangan produk, promosi, atau penghapusan produk.

3. **Inefisiensi Strategi Pemasaran dan Promosi**  
   Tanpa pemahaman yang jelas tentang kapan dan bagaimana penjualan paling mungkin terjadi, upaya pemasaran dan promosi seringkali bersifat generik dan kurang efektif. Hal ini dapat menyebabkan pemborosan anggaran pemasaran pada kampanye yang tidak memberikan return on investment (ROI) yang optimal.

### Goals (Tujuan)

Untuk mengatasi pernyataan masalah di atas, proyek analisis prediktif ini menetapkan tujuan-tujuan berikut:

1. **Membangun Model Prediksi Penjualan yang Akurat**  
   Mengembangkan model pembelajaran mesin (regresi linier) yang mampu memprediksi **'TotalSales'** dengan tingkat akurasi yang tinggi berdasarkan fitur-fitur yang relevan seperti **'Price'** dan **'Quantity'**. Model ini akan memberikan perkiraan penjualan yang andal untuk membantu dalam perencanaan inventaris.

2. **Mengidentifikasi Faktor-faktor Pendorong Penjualan**  
   Menganalisis fitur-fitur dalam dataset untuk memahami bagaimana masing-masing fitur (misalnya, harga dan kuantitas) berkorelasi dengan total penjualan. Wawasan ini akan membantu dalam merumuskan strategi penetapan harga dan pengelolaan inventaris yang lebih baik.

3. **Mendukung Pengambilan Keputusan Strategis Berbasis Data**  
   Menyediakan alat dan wawasan bagi manajemen untuk membuat keputusan yang lebih tepat terkait:
   - **Manajemen Inventaris**: Optimasi level stok untuk menghindari overstocking dan understocking.
   - **Strategi Pemasaran**: Penargetan promosi yang lebih cerdas dan alokasi anggaran yang efisien.
   - **Pengembangan Produk**: Pemahaman tentang produk yang diminati untuk panduan keputusan inovasi atau diversifikasi produk.
  
## Data Understanding

Bagian ini bertujuan untuk memberikan pemahaman mendalam tentang data yang digunakan dalam proyek ini, termasuk karakteristik, kondisi, dan deskripsi setiap variabel atau fitur.

### Sumber Data
Dataset yang digunakan dalam proyek ini adalah **Sales Transaction v.4a.csv**.  
Tautan unduh data: https://www.kaggle.com/datasets/gabrielramos87/an-online-shop-business

### Informasi Umum Dataset
Dataset ini berisi informasi transaksi penjualan ritel.

- **Jumlah Baris (Observasi)**: Dataset asli memiliki 471.094 baris. Setelah pra-pemrosesan data (penghapusan baris dengan nilai null pada kolom 'Date' dan 'Country', serta penghapusan duplikat), jumlah baris menjadi 466.587.
- **Jumlah Kolom (Fitur)**: Dataset memiliki 9 kolom.
- **Tipe Data**:
  - **datetime64[ns]** (1 kolom): untuk informasi waktu.
  - **float64** (3 kolom): untuk nilai numerik dengan desimal.
  - **object** (5 kolom): untuk nilai teks atau kategori.
- **Missing Values (Nilai Hilang)**:
  - Sebelum pembersihan: Kolom 'Quantity', 'Country', dan 'TotalSales' masing-masing memiliki 1 nilai null.
  - Setelah pembersihan: Tidak ada nilai null di kolom manapun.
- **Duplikasi Data**: Tidak ada baris duplikat setelah tahap pembersihan data.

### Deskripsi Variabel (Fitur)
Berikut adalah uraian dari setiap kolom (variabel/fitur) yang terdapat dalam dataset:

1. **TransactionNo**
   - **Tipe Data**: Object (String)
   - **Deskripsi**: Nomor unik untuk setiap transaksi atau faktur. Ini dapat berisi kombinasi angka dan huruf.

2. **Date**
   - **Tipe Data**: datetime64[ns]
   - **Deskripsi**: Tanggal dan waktu ketika transaksi terjadi.

3. **ProductNo**
   - **Tipe Data**: Object (String)
   - **Deskripsi**: Nomor identifikasi unik untuk setiap produk.

4. **ProductName**
   - **Tipe Data**: Object (String)
   - **Deskripsi**: Nama deskriptif dari produk yang terjual.  
   - **Contoh Nilai Unik**: 'Set Of 2 Wooden Market Crates', 'Christmas Star Wish List Chalkboard', 'Storage Tin Vintage Leaf', dll.

5. **Price**
   - **Tipe Data**: float64
   - **Deskripsi**: Harga jual per unit dari produk.  
   - **Statistik**:
     - Minimum: 5.13
     - Maksimum: 660.62
     - Rata-rata: sekitar 12.49

6. **Quantity**
   - **Tipe Data**: float64
   - **Deskripsi**: Jumlah produk yang terjual dalam satu transaksi. Perlu dicatat bahwa terdapat nilai negatif yang mungkin mengindikasikan retur barang.  
   - **Statistik**:
     - Minimum: -80995.00
     - Maksimum: 80995.00
     - Rata-rata: sekitar 10.18

7. **CustomerNo**
   - **Tipe Data**: Object (String)
   - **Deskripsi**: Nomor identifikasi unik untuk setiap pelanggan.

8. **Country**
   - **Tipe Data**: Object (String)
   - **Deskripsi**: Negara tempat transaksi dilakukan.  
   - **Contoh Nilai Unik**: 'United Kingdom', 'Norway', 'Belgium', 'Germany', 'France', dll.

9. **TotalSales (Fitur yang Dibuat)**
   - **Tipe Data**: float64
   - **Deskripsi**: Total pendapatan dari satu baris item transaksi, dihitung sebagai Price * Quantity.  
   - **Statistik**:
     - Minimum: -501359.05
     - Maksimum: 1002718.10
     - Rata-rata: sekitar 114.42

## Data Preparation

Tahap **Data Preparation** adalah langkah krusial dalam siklus hidup proyek analisis data, di mana data mentah diubah menjadi format yang bersih dan terstruktur, siap untuk dianalisis dan dimodelkan. Proses ini melibatkan serangkaian teknik untuk menangani nilai yang hilang, mengoreksi tipe data, merekayasa fitur baru, dan menghilangkan duplikasi.

### Penerapan dan Teknik Data Preparation

Berikut adalah teknik-teknik persiapan data yang diterapkan pada dataset ini, diuraikan secara berurutan:

#### 1. Konversi Tipe Data Kolom 'Date'
- **Teknik**: Konversi Tipe Data (Type Casting) dan Penanganan Kesalahan.
- **Penerapan**: Kolom 'Date' awalnya mungkin memiliki tipe data object atau string. Untuk memungkinkan analisis berbasis waktu dan ekstraksi fitur waktu, kolom ini dikonversi menjadi tipe data `datetime64[ns]` menggunakan `pd.to_datetime()`. Argumen `format='mixed'` digunakan untuk menangani berbagai format tanggal yang mungkin ada, dan `errors='coerce'` akan mengubah nilai tanggal yang tidak dapat diurai menjadi NaT (Not a Time).

#### 2. Penanganan Nilai Hilang (Missing Values)
- **Teknik**: Penghapusan Baris (Row Deletion) dan Imputasi Nilai Rata-Rata (Mean Imputation).
- **Penerapan**:
  - **Penghapusan Baris NaT pada 'Date'**: Setelah konversi tipe data, setiap baris di mana 'Date' menghasilkan NaT (karena format yang tidak valid) dihapus dari dataset menggunakan `df.dropna(subset=['Date'])`.
  - **Penghapusan Baris Null pada 'Country'**: Baris yang memiliki nilai null di kolom 'Country' dihapus menggunakan `df.dropna(subset=['Country'])`.
  - **Imputasi 'Price'**: Nilai-nilai yang hilang di kolom 'Price' diisi dengan nilai rata-rata dari kolom 'Price' itu sendiri menggunakan `df['Price'].fillna(df['Price'].mean(), inplace=True)`. Ini adalah metode imputasi sederhana yang cocok untuk distribusi data yang kurang memiliki outlier ekstrem.
  - **Imputasi 'Quantity'**: Demikian pula, nilai-nilai yang hilang di kolom 'Quantity' diisi dengan nilai rata-rata dari kolom tersebut menggunakan `df['Quantity'].fillna(df['Quantity'].mean(), inplace=True)`.

#### 3. Rekayasa Fitur 'TotalSales'
- **Teknik**: Penciptaan Fitur Baru (Feature Creation).
- **Penerapan**: Untuk mendapatkan metrik penjualan agregat per baris transaksi, kolom 'TotalSales' baru dibuat. Kolom ini dihitung dengan mengalikan nilai di kolom 'Price' dengan nilai di kolom 'Quantity' (`df['TotalSales'] = df['Price'] * df['Quantity']`). Fitur ini penting karena 'TotalSales' adalah target utama untuk model prediktif.

#### 4. Konversi Tipe Data Kolom 'CustomerNo'
- **Teknik**: Konversi Tipe Data (Type Casting).
- **Penerapan**: Meskipun 'CustomerNo' mungkin terlihat seperti angka, itu berfungsi sebagai pengenal unik daripada nilai numerik yang dapat dioperasikan secara matematis. Oleh karena itu, kolom ini dikonversi menjadi tipe data string (object) menggunakan `df['CustomerNo'].astype(str)` untuk memastikan penanganannya sebagai variabel kategorikal atau ID.

#### 5. Penghapusan Duplikat
- **Teknik**: Penghapusan Duplikasi (Duplicate Removal).
- **Penerapan**: Untuk memastikan integritas data dan mencegah bias dalam analisis dan pemodelan, semua baris yang merupakan duplikat sempurna di seluruh kolom dihapus menggunakan `df = df.drop_duplicates()`.

## Modelling

Untuk mengatasi masalah volatilitas penjualan dan memprediksi 'TotalSales', model **Regresi Linier (Linear Regression)** digunakan. Regresi Linier adalah algoritma machine learning yang banyak digunakan untuk memodelkan hubungan linier antara satu atau lebih variabel independen (fitur) dan variabel dependen (target). Dalam konteks ini, model akan belajar bagaimana 'Price' dan 'Quantity' memengaruhi 'TotalSales'.

### Tahapan dan Parameter Pemodelan

Proses pemodelan dilakukan melalui beberapa tahapan kunci:

#### 1. Pemilihan Fitur dan Target

- **Fitur (Variabel Independen)**: Berdasarkan tujuan proyek, fitur yang dipilih untuk memprediksi total penjualan adalah **Price** dan **Quantity**. Kedua variabel ini secara langsung memengaruhi nilai 'TotalSales'.
- **Target (Variabel Dependen)**: Variabel yang ingin diprediksi oleh model adalah **TotalSales**.

#### 2. Pembagian Data

- **Teknik**: Train-Test Split.
- **Penerapan**: Dataset dibagi menjadi dua subset utama:
  - **Data Pelatihan (Training Data)**: Digunakan untuk melatih model, di mana model belajar pola dan hubungan dari data. Sebesar 80% dari total data digunakan sebagai data pelatihan (**X_train**, **y_train**).
  - **Data Pengujian (Testing Data)**: Digunakan untuk mengevaluasi kinerja model pada data yang belum pernah dilihat sebelumnya, memastikan kemampuan generalisasi model. Sebesar 20% dari total data digunakan sebagai data pengujian (**X_test**, **y_test**).

- **Parameter**:
  - `test_size=0.2`: Menunjukkan bahwa 20% dari data akan dialokasikan untuk set pengujian.
  - `random_state=42`: Ini adalah seed untuk pengacakan yang digunakan dalam pembagian data. Penggunaan nilai `random_state` yang tetap memastikan bahwa pembagian data akan selalu sama setiap kali kode dijalankan, sehingga hasil dapat direproduksi.

#### 3. Inisialisasi dan Pelatihan Model

- **Teknik**: Inisialisasi Model dan Fitting.
- **Penerapan**: Model **LinearRegression()** diinisialisasi tanpa parameter khusus karena merupakan model dasar. Setelah inisialisasi, model dilatih menggunakan data pelatihan dengan memanggil metode `fit()` (`model.fit(X_train, y_train)`). Pada tahap ini, model menghitung koefisien (bobot) untuk setiap fitur yang meminimalkan error antara prediksi dan nilai aktual.

#### 4. Pembuatan Prediksi

- **Teknik**: Inferensi Model.
- **Penerapan**: Setelah model dilatih, model digunakan untuk membuat prediksi pada set pengujian yang belum pernah dilihat sebelumnya (`y_pred = model.predict(X_test)`). Prediksi ini kemudian akan dibandingkan dengan nilai 'TotalSales' aktual dari set pengujian untuk mengevaluasi kinerja model.

#### 5. Evaluasi Model

- **Teknik**: Metrik Evaluasi Regresi.
- **Penerapan**: Kinerja model dievaluasi menggunakan metrik berikut:
  - **Mean Absolute Error (MAE)**: Mengukur rata-rata magnitudo kesalahan dalam satu set prediksi, tanpa mempertimbangkan arahnya. MAE yang lebih rendah menunjukkan akurasi yang lebih tinggi.  
    - **Hasil**: 56.527
  - **Mean Squared Error (MSE)**: Mengukur rata-rata dari kuadrat kesalahan. Memberikan bobot lebih besar pada kesalahan yang lebih besar. MSE yang lebih rendah menunjukkan akurasi yang lebih tinggi.  
    - **Hasil**: 2,436,655.725
  - **R-squared (R²)**: Atau koefisien determinasi, menunjukkan proporsi varians dalam variabel dependen yang dapat diprediksi dari variabel independen. Nilai berkisar dari 0 hingga 1, di mana 1 menunjukkan model yang sangat cocok.  
    - **Hasil**: 0.777

## Evaluasi

Bagian evaluasi ini menyajikan metrik-metrik yang digunakan untuk menilai kinerja model machine learning yang telah dibangun, serta menjelaskan interpretasi hasil proyek berdasarkan metrik tersebut. Pemilihan metrik evaluasi disesuaikan dengan konteks data numerik, pernyataan masalah mengenai volatilitas penjualan, dan tujuan untuk memprediksi total penjualan.

### Metrik Evaluasi yang Digunakan

Untuk model regresi, seperti **Regresi Linier** yang digunakan dalam proyek ini, metrik evaluasi berikut adalah standar dan relevan:

#### 1. Mean Absolute Error (MAE)
- **Definisi**: MAE mengukur rata-rata dari selisih absolut antara nilai prediksi dan nilai aktual. Metrik ini memberikan gambaran tentang seberapa besar "rata-rata" kesalahan prediksi model, tanpa memperhatikan arah kesalahan (apakah prediksi terlalu tinggi atau terlalu rendah). MAE dinyatakan dalam unit yang sama dengan variabel target, sehingga mudah diinterpretasikan.
- **Relevansi Konteks**: Dalam konteks penjualan, MAE menunjukkan rata-rata jumlah kesalahan (dalam unit mata uang) dari setiap prediksi penjualan. Ini berguna bagi manajemen untuk memahami seberapa jauh perkiraan penjualan model dari angka sebenarnya.

#### 2. Mean Squared Error (MSE)
- **Definisi**: MSE menghitung rata-rata dari kuadrat selisih antara nilai prediksi dan nilai aktual. Dengan mengkuadratkan kesalahan, MSE memberikan bobot yang lebih besar pada kesalahan prediksi yang besar. Ini membuat MSE sangat sensitif terhadap outlier.
- **Relevansi Konteks**: MSE menyoroti dampak dari kesalahan prediksi yang signifikan. Jika ada beberapa prediksi yang sangat jauh dari nilai sebenarnya, MSE akan meningkat drastis, menunjukkan area di mana model perlu perbaikan.

#### 3. R-squared (R²)
- **Definisi**: R-squared, atau koefisien determinasi, adalah metrik yang menunjukkan proporsi varians dalam variabel dependen (target) yang dapat dijelaskan oleh variabel independen (fitur) dalam model. Nilainya berkisar antara 0 dan 1. Nilai 1 menunjukkan bahwa model dapat menjelaskan semua varians variabel target, sedangkan nilai 0 menunjukkan bahwa model tidak menjelaskan varians sama sekali.
- **Relevansi Konteks**: R² adalah indikator seberapa baik model "cocok" dengan data. Dalam konteks penjualan, R² menunjukkan seberapa besar variasi total penjualan dapat dijelaskan oleh variasi harga dan kuantitas. Semakin tinggi nilainya, semakin baik model dalam menangkap hubungan antara fitur dan penjualan.

### Hasil Proyek Berdasarkan Metrik Evaluasi

Setelah melatih model Regresi Linier dan membuat prediksi pada set pengujian, metrik evaluasi dihitung sebagai berikut:

#### 1. **Mean Absolute Error (MAE)**: 56.527106606486925
- **Interpretasi**: Secara rata-rata, prediksi 'TotalSales' oleh model kami meleset sekitar 56.53 unit mata uang dari nilai 'TotalSales' aktual. Ini memberikan gambaran langsung tentang rata-rata "kesalahan" model dalam prediksi penjualan.

#### 2. **Mean Squared Error (MSE)**: 2436655.725152318
- **Interpretasi**: Nilai MSE yang tinggi (sekitar 2.4 juta) menunjukkan bahwa ada beberapa kesalahan prediksi yang cukup besar (outlier) yang ditekankan oleh kuadratnya. Meskipun MAE terlihat moderat, MSE yang besar mengindikasikan bahwa model mungkin kurang baik dalam memprediksi beberapa transaksi dengan nilai penjualan yang sangat tinggi atau rendah. Ini adalah area yang perlu diperhatikan untuk perbaikan model lebih lanjut, mungkin dengan penanganan outlier yang lebih canggih atau fitur tambahan.

#### 3. **R-squared (R²)**: 0.7778156839784256
- **Interpretasi**: Nilai R² sebesar 0.7778 (sekitar 77.78%) menunjukkan bahwa sekitar 77.78% dari variabilitas dalam 'TotalSales' dapat dijelaskan oleh fitur 'Price' dan 'Quantity' dalam model Regresi Linier kami. Ini adalah hasil yang cukup baik, menunjukkan bahwa model memiliki kekuatan prediktif yang substansial dan berhasil menangkap sebagian besar hubungan linier antara fitur yang dipilih dan total penjualan.

### Kesimpulan

Secara keseluruhan, model **Regresi Linier** menunjukkan kinerja yang cukup baik dalam memprediksi total penjualan, dengan sebagian besar variasi penjualan dapat dijelaskan oleh harga dan kuantitas. Meskipun ada beberapa prediksi dengan kesalahan besar (ditunjukkan oleh MSE yang tinggi), MAE dan R² menunjukkan bahwa model secara umum dapat memberikan perkiraan yang wajar untuk tujuan perencanaan bisnis.
