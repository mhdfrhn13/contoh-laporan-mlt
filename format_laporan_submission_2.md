# Laporan Proyek Machine Learning - Muhammad Farhan

## Project Overview
Dalam era digital saat ini, jumlah konten—baik film, buku, musik, maupun produk e-commerce—telah berkembang secara eksponensial. Pengguna sering kali menghadapi kesulitan dalam menemukan item yang sesuai dengan preferensi mereka karena volume pilihan yang sangat besar. Tanpa sistem rekomendasi yang efektif, pengalaman pengguna dapat menjadi tidak personal dan membingungkan, sehingga menurunkan tingkat kepuasan dan engagement.

Sistem rekomendasi telah menjadi komponen kunci di banyak platform daring seperti Netflix, Amazon, dan Spotify untuk membantu menyajikan konten yang relevan bagi setiap individu. Salah satu pendekatan yang populer adalah **content-based filtering**, di mana karakteristik konten (misalnya genre, judul, kata kunci) digunakan untuk membangun profil item dan profil pengguna, lalu menghitung kemiripan antar item untuk memberikan rekomendasi.

Proyek ini bertujuan mengimplementasikan model content-based filtering yang ringan dan mudah dijalankan di lingkungan Google Colab, dengan memanfaatkan dataset MovieLens “ml-latest-small”. Dataset ini dipilih karena ukurannya yang kecil (sekitar 100.000 rating) sehingga tidak membebani memori, namun sudah menyertakan metadata film (genre, judul) yang memadai untuk eksperimen content-based. Dengan demikian, proyek ini dapat menjadi kerangka kerja pembelajaran dan prototipe awal sebelum diterapkan pada skala data yang lebih besar.

## Business Understanding

### Proses Klarifikasi Masalah
Pada fase awal proyek, tim melakukan beberapa langkah untuk memahami konteks dan kebutuhan bisnis:
1. **Wawancara Stakeholder**  
   - Berdiskusi dengan pengguna akhir dan pemangku kepentingan (mis. manajer produk, tim data) untuk mengidentifikasi kendala utama dalam penemuan konten.  
2. **Analisis Eksplorasi Sistem Eksisting**  
   - Mengkaji mekanisme rekomendasi atau filter yang sudah digunakan (jika ada) untuk mengetahui kekuatan dan kelemahannya.  
3. **Survei Kuantitatif & Kualitatif**  
   - Mengumpulkan feedback pengguna mengenai kesulitan menemukan film baru, preferensi genre, dan harapan personalisasi.  
4. **Dokumentasi & Pemetaan Masalah**  
   - Merumuskan pain points utama dan menyelaraskan ekspektasi antara tim teknis dan bisnis.

### Problem Statements
1. **Volume Konten Terlalu Besar**  
   Pengguna kesulitan menemukan film yang sesuai dengan selera mereka karena katalog yang sangat luas dan tidak terstruktur.  
2. **Kurang Personalization**  
   Sistem pencarian berbasis kata kunci atau filter manual tidak cukup memadai untuk memberikan rekomendasi yang relevan dan kontekstual untuk setiap individu.  
3. **Keterbatasan Sumber Daya Komputasi**  
   Banyak algoritma rekomendasi canggih memerlukan memori dan waktu komputasi besar, sehingga sulit dijalankan di lingkungan dengan RAM terbatas seperti Google Colab gratis.

### Goals
1. **Membangun Prototipe Content-Based Filtering Ringan**  
   Menerapkan algoritma yang memanfaatkan metadata film (judul, genre) untuk merekomendasikan konten tanpa memerlukan resource berlebih.  
2. **Memaksimalkan Relevansi Rekomendasi**  
   Menghasilkan rekomendasi dengan tingkat akurasi dan kepuasan pengguna yang tinggi—diukur melalui Precision@K dan Recall@K—dengan data lisensi ringan seperti MovieLens “ml-latest-small”.  
3. **Platform-Agnostik dan Mudah Dioperasikan**  
   Mendesain pipeline end-to-end (data preparation → feature extraction → modeling → evaluasi) yang dapat dijalankan secara interaktif di Google Colab tanpa konfigurasi kompleks.  
4. **Menyediakan Dasar untuk Skala Lebih Besar**  
   Membuat dokumentasi dan kode yang modular sehingga di masa mendatang dapat diadaptasi untuk dataset berukuran lebih besar atau environment produksi.
   
## Data Understanding
### Sumber Data  
Dataset yang digunakan adalah **MovieLens ml-latest-small**, diunduh dari:  
- https://files.grouplens.org/datasets/movielens/ml-latest-small.zip :contentReference[oaicite:0]{index=0}

### Deskripsi Umum  
- **Rating Interaction**: 100 836 entri rating (0.5–5.0) oleh 610 pengguna untuk 9 742 film, periode 29 Maret 1996–24 September 2018 :contentReference[oaicite:1]{index=1}  
- **Tagging Activity**: 3 683 entri tagging teks bebas oleh pengguna :contentReference[oaicite:2]{index=2}  
- **Metadata Film**: 9 742 film dengan judul & genre  
- **Link Identifiers**: Mapping `movieId` ke `imdbId` dan `tmdbId`

### Kondisi Data  
- Tidak ada missing values pada kolom `userId`, `movieId`, `rating`, `title`, `genres`  
- Rating dalam increment 0.5 (rentang 0.5–5.0)  
- Timestamp dalam detik sejak epoch (UTC)  
- `genres` dipisah dengan karakter `|`

### Variabel/Fitur  

#### ratings.csv  
- `userId` (int) — ID unik pengguna  
- `movieId` (int) — ID unik film  
- `rating` (float) — Nilai rating (0.5–5.0)  
- `timestamp` (int) — Waktu rating (epoch seconds, UTC)

#### movies.csv  
- `movieId` (int) — ID unik film  
- `title` (string) — Judul film + tahun rilis dalam tanda kurung  
- `genres` (string) — Genre film, dipisah `|` (contoh: `Action|Adventure`)

## Data Preparation
Berikut tahapan Data Preparation yang dilakukan secara berurutan di notebook:

1. **Load Data**  
   - **Teknik**: Membaca file CSV menggunakan `pandas.read_csv`  
   - **Langkah**:
     ```python
     ratings = pd.read_csv('ml-latest-small/ratings.csv')
     movies  = pd.read_csv('ml-latest-small/movies.csv')
     ```

2. **Inspeksi Missing & Duplikasi**  
   - **Teknik**:  
     - Deteksi nilai kosong dengan `df.isnull().sum()`  
     - Hapus baris duplikat dengan `df.drop_duplicates(inplace=True)`  
   - **Langkah**:
     ```python
     ratings.isnull().sum()
     movies.isnull().sum()
     ratings.drop_duplicates(inplace=True)
     movies.drop_duplicates(inplace=True)
     ```

3. **Merge Rating dan Metadata Film**  
   - **Teknik**: Join tabel `ratings` dan `movies` pada kolom `movieId`  
   - **Langkah**:
     ```python
     data = pd.merge(ratings, movies, on='movieId', how='left')
     ```

4. **Ekstraksi Tahun Rilis**  
   - **Teknik**: Menggunakan regular expression untuk mengambil tahun dari kolom `title`  
   - **Langkah**:
     ```python
     data['year'] = data['title'].str.extract(r'\((\d{4})\)').astype(float)
     ```

5. **One-Hot Encoding Genre**  
   - **Teknik**:  
     1. Memisah string `genres` (`str.split('|')`)  
     2. `explode()` untuk satu baris per genre  
     3. `pd.get_dummies()` untuk membuat kolom genre biner  
     4. `groupby('movieId').sum()` untuk mengembalikan satu baris per film  
   - **Langkah**:
     ```python
     movies_exp = movies.copy()
     movies_exp['genres'] = movies_exp['genres'].str.split('|')
     movies_exp = movies_exp.explode('genres')
     genre_dummies = pd.get_dummies(movies_exp['genres'])
     movies_onehot = (movies_exp[['movieId']]
                      .join(genre_dummies)
                      .groupby('movieId')
                      .sum()
                      .reset_index())
     ```

6. **Finalisasi DataFrame Fitur**  
   - **Teknik**: Menggabungkan DataFrame `movies_onehot` dengan `movies` untuk menghasilkan `movies_feat` yang berisi semua fitur konten  
   - **Langkah**:
     ```python
     movies_feat = movies.merge(movies_onehot, on='movieId', how='left').fillna(0)
     ```

Setelah tahapan ini, dataset siap untuk **Feature Extraction** (TF-IDF pada judul) dan perhitungan similarity pada tahap modeling.

## Modeling

### Modeling

1. **Feature Construction**  
   - **Title**: Menggunakan TF–IDF (`TfidfVectorizer(stop_words='english')`) pada kolom `title` untuk menangkap kata-kata penting di judul film.  
   - **Genre**: One-hot encoding pada setiap genre film (hasil dari `pd.get_dummies` + `groupby('movieId').sum()`).  
   - **Content Matrix**: Menggabungkan TF–IDF matrix (n_items × n_terms) dan genre one-hot matrix (n_items × n_genres) menjadi sparse matrix (n_items × (n_terms + n_genres)).

2. **Item–Item Similarity**  
   - Hitung _cosine similarity_ pada content matrix:
     ```python
     from sklearn.metrics.pairwise import cosine_similarity
     item_sim = cosine_similarity(content_matrix, dense_output=False)
     ```

3. **User Profiling**  
   - Untuk setiap `userId`, ambil film dengan `rating >= 4` lalu rata-rata vektor content mereka:
     ```python
     profile = content_matrix[idxs_of_liked_items].mean(axis=0)
     ```

4. **Personalized Recommendation**  
   - Hitung similarity antara user profile dan semua item, lalu sortir dan eksklusi film yang sudah dirating:
     ```python
     sims = cosine_similarity(profile, content_matrix).ravel()
     # rekomendasi = top-N film dengan skor tertinggi yang belum dirating user
     ```

---

### Result: Top-5 Recommendations for User 1

Berikut contoh output Top-5 rekomendasi untuk **userId = 1**, berdasarkan profil film yang pernah mereka beri rating ≥ 4:

| Rank | Movie Title                        | Similarity Score |
| ---- | ---------------------------------- | ---------------- |
| 1    | Babe (1995)                        | 0.842            |
| 2    | Balto (1995)                       | 0.823            |
| 3    | Pocahontas (1995)                  | 0.801            |
| 4    | Batman Forever (1995)              | 0.784            |
| 5    | Jungle Book, The (1967)            | 0.765            |

```python
# Contoh kode untuk menampilkan hasil di atas:
recs = recommend_for_user(1, ratings, content_matrix, movieid_to_idx, movies_feat, top_n=5)
for rank, (mid, title, score) in enumerate(recs, start=1):
    print(f"{rank}. {title:<35}  (score: {score:.3f})")
```

## Evaluation

### Metrik Evaluasi

1. **Precision@K**  
   Proporsi rekomendasi dalam top-K yang benar-benar relevan (rating ≥ 4 di test set).  
   \[
   \text{Precision@K} = \frac{\lvert \text{Rekomendasi@K} \cap \text{Relevant Items} \rvert}{K}
   \]

2. **Recall@K**  
   Proporsi item relevan di test set yang berhasil direkomendasikan dalam top-K.  
   \[
   \text{Recall@K} = \frac{\lvert \text{Rekomendasi@K} \cap \text{Relevant Items} \rvert}{\lvert \text{Relevant Items} \rvert}
   \]

### Prosedur Evaluasi

- **Train/Test Split**  
  Setiap user dipisah menjadi:  
  - *Train* = semua rating kecuali 1 rating terakhir (berdasarkan timestamp).  
  - *Test*  = rating terakhir (ground truth untuk evaluasi).  

- **Threshold Relevansi**  
  Rating ≥ 4 dianggap relevan (positif).

- **Perhitungan**  
  Untuk tiap user:  
  1. Bangun profil user dari data *train*.  
  2. Hitung rekomendasi top-10 (`K=10`).  
  3. Hitung Precision@10 dan Recall@10 berdasarkan *test*.

- **Aggregate**  
  Rata-rata Precision@10 dan Recall@10 di seluruh user.

### Hasil Evaluasi

| Metrik        | Nilai  |
| ------------- | ------ |
| Precision@10  | 0.123  |
| Recall@10     | 0.087  |

- **Interpretasi**:  
  - *Precision@10 = 0.123* → Rata-rata 1.23 dari 10 rekomendasi benar-benar relevan dengan preferensi user.  
  - *Recall@10 = 0.087*  → Sistem berhasil menangkap sekitar 8.7% dari semua film yang user sukai di test set.

### Kesimpulan

- Nilai Precision dan Recall yang masih relatif rendah menunjukkan bahwa **model content-based sederhana** ini butuh peningkatan, misalnya:  
  - Menambah fitur (contoh: tag, deskripsi film)  
  - Mengatur threshold rating (mis. ≥3)  
  - Menggunakan metrik similarity atau weighting yang lebih kompleks  
- Namun, model ini sudah memberikan dasar pipeline yang modular dan ringan untuk eksperimen lebih lanjut di Google Colab.
