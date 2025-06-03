# Laporan Proyek Machine Learning - Muhammad Farhan

## Domain Proyek
#### Tujuan Proyek

Proyek ini bertujuan untuk membangun model prediktif yang dapat memperkirakan kualitas wine berdasarkan data kimiawi yang ada, seperti kadar alkohol, keasaman, kadar gula, dan lainnya. Dengan menggunakan dataset yang terdiri dari berbagai fitur kimia, kita akan mencoba untuk membangun model yang dapat memberikan prediksi yang lebih akurat mengenai kualitas wine, baik untuk keperluan produksi maupun pemasaran.

#### Keuntungan Penerapan Predictive Analysis dalam Industri Wine

Penerapan **predictive analysis** dalam industri wine menawarkan berbagai keuntungan, antara lain:
1. **Efisiensi dalam Penilaian Kualitas**
Dengan menggunakan model machine learning, proses penilaian kualitas wine dapat dilakukan lebih cepat dan dengan hasil yang lebih konsisten, mengurangi ketergantungan pada penilaian manusia yang mungkin dipengaruhi oleh subjektivitas.
2. **Pemahaman yang Lebih Mendalam tentang Faktor-faktor yang Mempengaruhi Kualitas**
Proyek ini akan mengidentifikasi hubungan antara berbagai faktor kimiawi dan kualitas wine, memberikan wawasan berharga bagi produsen untuk memahami lebih baik bagaimana elemen-elemen tertentu mempengaruhi rasa dan kualitas wine.
3. **Peningkatan Kualitas Produk**
Dengan adanya prediksi yang lebih akurat mengenai kualitas wine, produsen dapat lebih tepat dalam mengatur proses produksi mereka, mulai dari pemilihan anggur hingga pengolahan dan pematangan wine. Ini dapat membantu meningkatkan kualitas produk secara keseluruhan dan meminimalkan produk yang tidak memenuhi standar kualitas.
4. **Peluang untuk Pengembangan Industri Wine**
Di pasar yang semakin kompetitif, produsen wine yang mampu mengandalkan data dan teknologi untuk meningkatkan kualitas produk mereka memiliki keunggulan besar. Penggunaan machine learning untuk analisis kualitas wine bisa menjadi nilai jual yang menarik di pasar global.

## Business Understanding

#### 1. **Pendahuluan**
Dalam industri minuman, khususnya produksi wine, kualitas produk sangat penting untuk memenuhi harapan konsumen. Salah satu cara untuk menilai kualitas wine adalah dengan menggunakan penilaian subjektif, yang sering kali dipengaruhi oleh preferensi individu. Oleh karena itu, proyek ini bertujuan untuk mengembangkan model prediktif yang dapat memberikan prediksi objektif tentang kualitas wine berdasarkan data kimiawi yang ada. Model ini akan membantu produsen dalam meningkatkan kualitas produk secara konsisten dan efisien.

#### 2. **Pernyataan Masalah (Problem Statement)**
Meskipun kualitas wine dapat dinilai oleh ahli sommelier dan pengamat lainnya, penilaian ini sering kali bersifat subjektif dan bervariasi antara satu individu dengan individu lainnya. Oleh karena itu, masalah utama yang dihadapi adalah:
- **Keterbatasan dalam penilaian kualitas yang konsisten**: Penilaian kualitas yang bersifat subjektif sulit untuk diandalkan dalam konteks produksi massal dan pengendalian kualitas.
- **Kurangnya sistem prediktif yang dapat mengidentifikasi kualitas berdasarkan parameter kimiawi**: Proses penilaian kualitas sering kali tidak memanfaatkan data objektif yang tersedia dari analisis kimia dan sifat fisik wine.

Model prediktif yang dikembangkan dalam proyek ini bertujuan untuk memecahkan masalah ini dengan memberikan estimasi kualitas wine secara otomatis menggunakan data kimiawi yang tersedia.

#### 3. **Tujuan Proyek**
Untuk menjawab pernyataan masalah di atas, proyek ini memiliki tujuan utama sebagai berikut:
- **Membangun Model Prediktif**: Mengembangkan model prediktif yang dapat memperkirakan kualitas wine berdasarkan fitur kimiawi seperti kadar alkohol, pH, asam volatil, dan lainnya.
- **Meningkatkan Konsistensi Penilaian Kualitas**: Menerapkan teknik machine learning untuk menghasilkan prediksi kualitas yang konsisten, yang tidak dipengaruhi oleh subjektivitas manusia.
- **Meningkatkan Pengendalian Kualitas Produksi**: Membantu produsen wine untuk lebih memahami bagaimana faktor kimiawi mempengaruhi kualitas wine, sehingga dapat meningkatkan proses produksi secara lebih efektif.
- **Memberikan Insight Mendalam tentang Faktor-Faktor yang Mempengaruhi Kualitas Wine**: Mengidentifikasi hubungan antara berbagai faktor kimia dan kualitas wine, yang dapat menjadi bahan pertimbangan dalam penelitian atau inovasi produk baru.

#### 4. **Solusi yang Diharapkan**
Dengan membangun model prediktif yang memanfaatkan data kimiawi yang ada, diharapkan model ini dapat memberikan hasil yang akurat dan dapat diandalkan untuk memprediksi kualitas wine. Dengan demikian, produsen dapat:
- Mengurangi ketergantungan pada penilaian subjektif.
- Menjamin kualitas wine yang lebih stabil dan konsisten di setiap batch produksi.
- Mengoptimalkan proses produksi untuk mencapai kualitas yang lebih baik dengan biaya yang lebih efisien.
  
## Data Understanding

### 1. **Informasi Umum Dataset**
Dataset yang digunakan dalam proyek ini adalah dataset mengenai kualitas wine merah yang mencakup berbagai parameter kimiawi dan kualitas produk akhir. Dataset ini memiliki sejumlah baris dan kolom yang berisi informasi yang relevan untuk tujuan prediksi kualitas wine. Berikut adalah informasi umum mengenai dataset:

- **Jumlah Data**: Dataset ini terdiri dari 1599 sampel (baris) dan 12 fitur (kolom).
- **Sumber Data**: Dataset diambil dari kumpulan data yang tersedia secara publik di UCI Machine Learning Repository, yang digunakan untuk analisis kualitas wine merah.

### 2. **Kondisi Data**
Setelah melakukan pemeriksaan awal, kami menemukan bahwa dataset tidak mengandung nilai yang hilang atau missing values, yang berarti data telah siap digunakan tanpa memerlukan imputation. Semua nilai dalam dataset sudah terisi dengan lengkap dan konsisten.

### 3. **Penjelasan Fitur**

Dataset ini terdiri dari beberapa fitur yang menggambarkan sifat kimiawi dari wine serta kualitas wine sebagai target prediksi. Berikut adalah penjelasan rinci mengenai setiap fitur dalam dataset.

1. **Fixed Acidity (Asiditas Tetap)**
- **Tipe**: Numerik
- **Deskripsi**: Kadar asam tetap dalam wine yang tidak mudah menguap. Asam tetap ini berperan penting dalam rasa dan stabilitas wine. Asiditas tetap yang tinggi dapat memberikan rasa segar dan stabil pada wine.
  
2. **Volatile Acidity (Asiditas Volatil)**
- **Tipe**: Numerik
- **Deskripsi**: Kadar asam asetik dalam wine yang berperan dalam pengaruh rasa asam. Asiditas volatil yang tinggi dapat menyebabkan wine terasa asam, dan jika terlalu tinggi, wine akan terasa tidak enak.

3. **Citric Acid (Asam Sitrus)**
- **Tipe**: Numerik
- **Deskripsi**: Kadar asam sitrat dalam wine. Asam sitrat memberikan rasa asam segar yang sering ditemukan pada wine putih. Meskipun kontribusinya tidak sebesar asam tetap atau asam volatil, asam sitrus memberikan kesegaran pada wine.

4. **Residual Sugar (Gula Sisa)**
- **Tipe**: Numerik
- **Deskripsi**: Jumlah gula yang tersisa dalam wine setelah proses fermentasi. Gula ini mempengaruhi rasa manis atau kering pada wine. Wine dengan kandungan gula sisa tinggi cenderung lebih manis.

5. **Chlorides (Klorida)**
- **Tipe**: Numerik
- **Deskripsi**: Kandungan klorida (garam) dalam wine. Meskipun tidak memiliki pengaruh langsung pada rasa, kandungan klorida yang terlalu tinggi dapat memberikan rasa masin atau mengubah profil rasa wine secara keseluruhan.

6. **Free Sulfur Dioxide (Sulfida Bebas)**
- **Tipe**: Numerik
- **Deskripsi**: Kandungan sulfur dioksida bebas dalam wine. Sulfur dioksida digunakan untuk mencegah pertumbuhan mikroorganisme yang tidak diinginkan dan untuk menjaga stabilitas wine. Kadar sulfur dioksida bebas yang cukup penting untuk pengawetan dan perlindungan kualitas wine.

7. **Total Sulfur Dioxide (Sulfida Total)**
- **Tipe**: Numerik
- **Deskripsi**: Total kandungan sulfur dioksida, termasuk baik yang terikat maupun yang bebas. Kadar sulfur dioksida ini membantu melindungi wine dari oksidasi dan mempertahankan kualitas rasa selama penyimpanan.

8. **Density (Kepadatan)**
- **Tipe**: Numerik
- **Deskripsi**: Kepadatan wine pada suhu tertentu. Kepadatan ini dapat digunakan untuk menentukan kandungan alkohol dan air dalam wine. Wine dengan kepadatan lebih tinggi biasanya memiliki kandungan alkohol lebih rendah, sedangkan wine dengan kepadatan lebih rendah memiliki alkohol yang lebih tinggi.

9. **pH**
- **Tipe**: Numerik
- **Deskripsi**: pH wine yang menggambarkan tingkat keasaman. pH wine berperan penting dalam rasa dan stabilitas wine. Wine dengan pH lebih rendah cenderung lebih asam, sementara pH lebih tinggi menunjukkan sifat wine yang lebih lembut dan sedikit lebih manis.

10. **Sulphates (Sulfat)**
- **Tipe**: Numerik
- **Deskripsi**: Kadar sulfat dalam wine yang berfungsi sebagai pengawet dan dapat mempengaruhi rasa wine. Sulfat yang tinggi dapat memberikan rasa tertentu pada wine dan mempengaruhi keseimbangan antara rasa manis dan asam.

11. **Alcohol (Alkohol)**
- **Tipe**: Numerik
- **Deskripsi**: Kandungan alkohol dalam wine yang berperan dalam rasa, aroma, dan kekuatan wine. Semakin tinggi kandungan alkohol, wine cenderung memiliki rasa yang lebih kuat dan lebih berat.

12. **Quality (Kualitas)**
- **Tipe**: Kategorikal (Integer)
- **Deskripsi**: Nilai kualitas wine yang dinilai berdasarkan parameter rasa dan kimiawi. Nilai kualitas ini merupakan target variabel yang akan diprediksi oleh model. Nilainya berkisar antara 0 (terendah) hingga 10 (tertinggi), dengan 6-7 sebagai kualitas standar yang sering ditemui pada dataset ini.

### 4. **Sumber Dataset**
https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009/code

## Data Preparation

### 1. **Penerapan Data Preparation**
Data preparation adalah langkah penting dalam proyek ini untuk memastikan bahwa dataset yang digunakan siap untuk pelatihan model prediktif. Proses ini mencakup beberapa tahapan yang bertujuan untuk membersihkan data, mengubah skala fitur, dan membagi data menjadi subset yang tepat untuk pelatihan, validasi, dan pengujian model.

### 2. **Teknik Data Preparation yang Dilakukan**

#### a. **Pemeriksaan Nilai yang Hilang (Missing Values)**
- Sebelum melanjutkan ke tahapan model training, langkah pertama yang dilakukan adalah memeriksa apakah terdapat nilai yang hilang (missing values) dalam dataset. Hasil pemeriksaan menunjukkan bahwa dataset **tidak memiliki nilai yang hilang**, sehingga tidak diperlukan penanganan lebih lanjut terhadap data yang hilang.

#### b. **Pemisahan Fitur dan Target Variabel**
- **Fitur (Features)**: Semua kolom dalam dataset kecuali kolom **quality** digunakan sebagai fitur yang menggambarkan karakteristik kimiawi wine.
- **Target (Target Variable)**: Kolom **quality** digunakan sebagai target variabel yang ingin diprediksi, yang menunjukkan kualitas wine berdasarkan penilaian.

#### c. **Normalisasi Data (Scaling)**
- Fitur-fitur dalam dataset memiliki skala yang berbeda-beda (misalnya, kadar alkohol dan kadar asam sitrat memiliki rentang nilai yang sangat berbeda). Untuk memastikan bahwa model tidak lebih menekankan pada fitur dengan skala yang lebih besar, dilakukan **normalisasi** pada fitur numerik menggunakan **StandardScaler** dari **scikit-learn**.
- **StandardScaler** mengubah setiap fitur menjadi distribusi dengan rata-rata 0 dan standar deviasi 1. Ini membantu memastikan bahwa semua fitur memiliki skala yang seragam saat digunakan dalam pelatihan model.

#### d. **Pembagian Data (Train, Validation, Test Split)**
- Data dibagi menjadi tiga bagian utama untuk memastikan pelatihan dan pengujian model yang efektif:
  1. **Train Set (60%)**: Digunakan untuk melatih model dan mengoptimalkan parameter.
  2. **Validation Set (20%)**: Digunakan untuk validasi selama pelatihan untuk memantau overfitting dan memilih parameter model terbaik.
  3. **Test Set (20%)**: Digunakan untuk menguji kinerja model setelah pelatihan selesai, dan memberikan gambaran seberapa baik model dapat menggeneralisasi pada data yang belum pernah dilihat sebelumnya.

#### e. **Penghapusan Data yang Tidak Relevan**
- Tidak ada fitur yang dihapus dalam proses ini karena semua fitur dalam dataset dianggap relevan untuk analisis kualitas wine. Setiap fitur kimiawi seperti pH, alkohol, kadar asam, dan lainnya memiliki kontribusi dalam menentukan kualitas wine.

### 3. **Ringkasan Proses Data Preparation**
Proses data preparation yang dilakukan bertujuan untuk:
- Menyiapkan dataset agar siap digunakan dalam pelatihan model.
- Menjamin bahwa data tidak mengandung nilai yang hilang dan setiap fitur memiliki skala yang konsisten.
- Memastikan bahwa model dapat dilatih dan diuji dengan data yang terbagi secara adil untuk menghindari overfitting dan memastikan generalisasi yang baik.

Dengan melakukan teknik-teknik tersebut, data yang digunakan dalam proyek ini siap untuk membangun model prediktif yang akurat dan dapat diandalkan.

## Modeling

### 1. **Pembuatan Model Machine Learning**
Pada tahap ini, kami menggunakan **Random Forest Regressor** sebagai model machine learning untuk memprediksi kualitas wine berdasarkan fitur-fitur kimiawi yang tersedia. **Random Forest** dipilih karena kemampuannya untuk menangani data numerik yang besar dan kompleks serta kemampuannya untuk mengurangi risiko overfitting melalui teknik ensemble learning.

Model ini dirancang untuk mengidentifikasi hubungan antara berbagai fitur kimiawi, seperti kadar alkohol, pH, asam volatil, dan gula sisa, dengan **variabel target** yang merupakan **kualitas** wine.

#### Mengapa Memilih Random Forest Regressor?
- **Random Forest** adalah metode **ensemble learning** yang membangun banyak pohon keputusan (decision trees) dan menghasilkan prediksi rata-rata dari semua pohon.
- Model ini dapat menangani baik **linear** maupun **non-linear** relationship antara fitur dan target variabel.
- Keunggulannya adalah **robustness** terhadap overfitting, terutama jika jumlah pohon yang digunakan cukup besar.

### 2. **Tahapan Proses Pemodelan**
Berikut adalah tahapan yang dilakukan dalam proses pemodelan:

#### a. **Pelatihan Model (Model Training)**
   - Data yang telah dibagi sebelumnya menjadi **train**, **validation**, dan **test** digunakan untuk melatih model. **Train set** digunakan untuk melatih model, sementara **validation set** digunakan untuk memantau kinerja model selama proses pelatihan untuk mencegah overfitting.
   - Model **Random Forest Regressor** dengan 100 pohon keputusan (estimators) dilatih pada data **train set**.

#### b. **Penentuan Parameter Model**
   Pada proses pelatihan, beberapa parameter utama yang digunakan untuk model adalah:
   - **n_estimators**: Menentukan jumlah pohon keputusan yang akan dibangun dalam random forest. Pada proyek ini, kami menggunakan **100 pohon** untuk model.
   - **random_state**: Digunakan untuk memastikan hasil yang dapat direproduksi. Dengan nilai **42**, setiap eksperimen akan memberikan hasil yang konsisten.

#### c. **Optimasi Model**
   - Kami menggunakan data **train set** untuk melatih model dan memanfaatkan data **validation set** untuk mengevaluasi kinerja model selama proses pelatihan.
   - Hasil prediksi pada data **validation set** digunakan untuk memantau kinerja model dan menyesuaikan parameter jika diperlukan.

#### d. **Evaluasi Model**
   Setelah model selesai dilatih, kami mengevaluasi model dengan menggunakan **test set** untuk mendapatkan hasil yang lebih objektif tentang kinerja model yang belum pernah dilihat sebelumnya.
   
### 3. **Penjelasan Parameter Model**
Berikut adalah penjelasan mengenai parameter yang digunakan pada **Random Forest Regressor** dalam proyek ini:

- **n_estimators**: 
  - Parameter ini mengontrol jumlah pohon keputusan dalam random forest. Semakin banyak pohon yang digunakan, semakin stabil hasil prediksi, namun juga membutuhkan waktu lebih lama untuk pelatihan.
  - Dalam proyek ini, kami menggunakan **100 pohon** untuk mendapatkan keseimbangan antara kecepatan pelatihan dan akurasi.
  
- **random_state**: 
  - Parameter ini digunakan untuk memastikan bahwa hasil pelatihan dapat direproduksi. Dengan nilai yang sama, model akan menghasilkan hasil yang konsisten meskipun dijalankan beberapa kali.
  
- **max_features (default "auto")**:
  - Menentukan jumlah fitur yang akan dipertimbangkan untuk pemecahan setiap simpul dalam pohon keputusan. Pengaturan "auto" secara otomatis memilih jumlah fitur yang optimal.
  
- **min_samples_split (default 2)**:
  - Menentukan jumlah minimum sampel yang diperlukan untuk membagi simpul. Mengatur nilai yang lebih besar akan menghasilkan pohon yang lebih sederhana dan lebih sedikit kompleksitas.
  
- **min_samples_leaf (default 1)**:
  - Menentukan jumlah minimum sampel yang harus ada di setiap daun. Mengatur nilai ini lebih tinggi dapat mengurangi overfitting.

### 4. **Pembuatan Model dan Pelatihan**
Setelah parameter ditentukan, model dibangun dan dilatih menggunakan **train set**. Selama pelatihan, model mempelajari hubungan antara fitur kimiawi dan kualitas wine, serta mengoptimalkan pohon-pohon keputusan untuk menghasilkan prediksi yang lebih akurat.

#### Kode Implementasi:
```python
from sklearn.ensemble import RandomForestRegressor

# Inisialisasi model dengan 100 estimators
model = RandomForestRegressor(n_estimators=100, random_state=42)

# Latih model menggunakan data train
model.fit(X_train, y_train)
```

## Evaluation

### 1. **Metrik Evaluasi yang Digunakan**

Dalam proyek ini, kami menggunakan beberapa **metrik evaluasi** untuk menilai kinerja model prediktif yang dibangun. Metrik ini dipilih berdasarkan konteks dataset, masalah yang dihadapi, dan solusi yang diinginkan.

#### a. **Mean Absolute Error (MAE)**
   - **Deskripsi**: MAE mengukur rata-rata perbedaan absolut antara nilai prediksi dan nilai sebenarnya (ground truth). Nilai MAE yang lebih kecil menunjukkan bahwa model lebih akurat dalam memprediksi kualitas wine.
   - **Mengapa digunakan?**: MAE memberikan gambaran yang jelas tentang seberapa besar kesalahan prediksi rata-rata yang dihasilkan oleh model. Ini sangat relevan dalam konteks kualitas wine karena kita ingin meminimalkan kesalahan prediksi dan menghasilkan perkiraan yang mendekati kualitas sesungguhnya.

#### b. **Mean Squared Error (MSE)**
   - **Deskripsi**: MSE menghitung rata-rata kuadrat selisih antara nilai prediksi dan nilai sebenarnya. MSE memberi penalti yang lebih besar pada kesalahan prediksi yang lebih besar, sehingga model akan lebih terdorong untuk menghindari kesalahan besar.
   - **Mengapa digunakan?**: MSE membantu untuk menilai seberapa besar kesalahan model pada tingkat yang lebih sensitif, memberikan gambaran yang lebih kuat tentang seberapa buruk model dalam memprediksi kualitas wine jika ada kesalahan yang signifikan.

#### c. **R-squared (R²)**
   - **Deskripsi**: R-squared mengukur seberapa baik model dapat menjelaskan variansi dalam data target. Nilai R² berkisar antara 0 hingga 1, di mana nilai yang lebih tinggi menunjukkan model yang lebih baik dalam menjelaskan variansi data.
   - **Mengapa digunakan?**: R² sangat relevan dalam konteks regresi karena memberikan gambaran seberapa baik model dalam mengadaptasi dan menjelaskan pola-pola yang ada dalam data. Semakin tinggi nilai R², semakin baik model dalam memprediksi kualitas wine berdasarkan fitur yang ada.

### 2. **Hasil Proyek Berdasarkan Metrik Evaluasi**

Berikut adalah hasil evaluasi model menggunakan metrik yang telah disebutkan di atas:

#### a. **Hasil Evaluasi pada Data Validation**
- **Mean Absolute Error (MAE)**: 0.43
  - Hasil ini menunjukkan bahwa rata-rata kesalahan prediksi antara kualitas wine yang sebenarnya dengan yang diprediksi oleh model adalah 0.43.
- **Mean Squared Error (MSE)**: 0.37
  - MSE yang lebih tinggi ini mengindikasikan bahwa ada beberapa kesalahan prediksi yang cukup besar. Namun, ini tidak terlalu mengganggu karena MAE relatif rendah.
- **R-squared (R²)**: 0.41
  - Nilai R² sebesar 0.41 menunjukkan bahwa model dapat menjelaskan sekitar 41% variansi dalam kualitas wine pada data validation. Meskipun ini tidak terlalu tinggi, ini menunjukkan bahwa model mulai belajar hubungan yang signifikan antara fitur kimiawi dan kualitas wine.

#### b. **Hasil Evaluasi pada Data Test**
- **Mean Absolute Error (MAE)**: 0.44
  - Hasil pada data test menunjukkan sedikit peningkatan dalam kesalahan prediksi dibandingkan dengan data validation, tetapi tetap berada dalam rentang yang dapat diterima.
- **Mean Squared Error (MSE)**: 0.33
  - MSE pada data test lebih rendah dibandingkan dengan data validation, yang menunjukkan bahwa model mungkin lebih baik dalam menggeneralisasi pada data yang belum pernah dilihat sebelumnya.
- **R-squared (R²)**: 0.50
  - Nilai R² sebesar 0.50 pada data test menunjukkan bahwa model dapat menjelaskan sekitar 50% variansi dalam kualitas wine. Ini merupakan indikasi yang baik bahwa model cukup efektif dalam mengadaptasi dan memprediksi kualitas wine pada data yang baru.

### 3. **Kesimpulan Berdasarkan Hasil Evaluasi**
- Model **Random Forest Regressor** yang dibangun memberikan hasil yang cukup baik dengan **R-squared** sekitar 50% pada data test, yang menunjukkan kemampuan model dalam menggeneralisasi pada data yang belum dilihat sebelumnya.
- **MAE** dan **MSE** menunjukkan bahwa model memiliki kesalahan prediksi yang relatif rendah, meskipun ada beberapa prediksi yang agak melenceng, terutama pada data validation.
- Secara keseluruhan, model ini memberikan solusi yang efektif untuk memprediksi kualitas wine berdasarkan fitur kimiawi yang ada, namun masih ada potensi untuk **peningkatan lebih lanjut** dalam hal akurasi dan kemampuan menjelaskan variasi kualitas wine.

Berdasarkan hasil evaluasi, model ini dapat diterapkan dalam industri wine untuk meningkatkan kontrol kualitas dan menghasilkan prediksi yang lebih konsisten dan akurat.

**---Ini adalah bagian akhir laporan---**
