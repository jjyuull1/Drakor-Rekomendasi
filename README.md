# Laporan Proyek Machine Learning - Juli Arsi Sabrina
## 📌 Project Overview
![drakor](https://github.com/user-attachments/assets/60ca8bc4-9cf6-4a9b-aa22-5f372accb33a)

Dalam beberapa tahun terakhir, popularitas drama Korea (K-Drama) mengalami peningkatan signifikan, tidak hanya di Asia tetapi juga secara global. Platform streaming seperti Netflix, Viu, dan Disney+ telah memperluas jangkauan K-Drama ke pasar internasional, menciptakan lonjakan besar dalam konsumsi konten Korea. Berdasarkan laporan dari Korea Creative Content Agency (KOCCA), ekspor konten Korea, termasuk drama, meningkat lebih dari 13% pada tahun 2022, menunjukkan tren global yang terus berkembang.<sup>[1]</sup>

Dengan semakin banyaknya judul drama yang dirilis setiap tahun, penonton sering kali merasa kesulitan dalam memilih tontonan yang sesuai dengan preferensi pribadi mereka. Dalam konteks ini, sistem rekomendasi berperan penting dalam membantu pengguna menemukan tayangan yang relevan dan menarik. Sistem ini dapat meningkatkan kepuasan pengguna serta mendorong engagement yang lebih tinggi terhadap platform.

Salah satu pendekatan yang dapat digunakan adalah Content-Based Filtering. Pendekatan ini bekerja dengan menganalisis fitur-fitur dari setiap drama seperti sinopsis, genre, aktor, dan elemen naratif lainnya. Kemudian, sistem menghitung kemiripan antar item berdasarkan konten tersebut, sehingga dapat memberikan rekomendasi drama yang mirip dengan drama yang sebelumnya disukai oleh pengguna.<sup>[2]</sup> Pendekatan ini juga dapat membantu mengatasi masalah cold-start bagi pengguna baru, karena tidak memerlukan data dari pengguna lain untuk memberikan rekomendasi yang personal.

## 💼 Business Understanding
### Problem Statements
1. **Kebingungan pengguna dalam memilih drama Korea yang sesuai.**
   
   Banyaknya pilihan drama Korea yang tersedia membuat pengguna sering kesulitan menentukan tontonan yang sesuai dengan minat atau preferensi mereka.
2. **Kurangnya sistem rekomendasi berbasis isi yang relevan dan personal.**
   
   Sebagian besar rekomendasi hanya berdasarkan popularitas atau rating tanpa memperhatikan kesamaan konten dengan tontonan yang disukai pengguna sebelumnya.
3. **Kurangnya integrasi teknologi Machine Learning dalam sistem rekomendasi drama Korea**.
   
   Masih terbatasnya pemanfaatan teknik machine learning dalam sistem penyaringan konten membuat hasil rekomendasi kurang adaptif dan tidak sepenuhnya mencerminkan ketertarikan pengguna terhadap konten tertentu.

### Goals
1. **Menyediakan sistem rekomendasi drama Korea yang sesuai dengan preferensi pengguna**
   
   Dengan mengolah informasi seperti genre, sinopsis, aktor, dan sutradara, sistem akan memberikan saran tontonan yang mirip dengan drama yang pernah disukai oleh pengguna.
2. **Mengembangkan sistem rekomendasi berbasis konten yang relevan serta efisien**
   
   Sistem akan menyajikan rekomendasi berdasarkan fitur-fitur isi drama, bukan sekadar berdasarkan popularitas umum.
3. **Menerapkan metode machine learning sederhana yang dapat diinterpretasikan**
   
   Sistem rekomendasi ini akan menggunakan metode yang transparan dan mudah dipahami untuk menganalisis konten drama Korea, seperti TF-IDF dan Cosine Similarity.
   
### Solusi Approach
Untuk mencapai tujuan proyek ini, dua pendekatan utama dalam sistem rekomendasi akan digunakan dan dibandingkan:
1. **Content-Based Filtering**
   
   Pendekatan dalam sistem rekomendasi yang menyarankan item kepada pengguna berdasarkan kesamaan fitur antara item yang pernah disukai dengan item lainnya. Dalam konteks rekomendasi drama Korea, pendekatan ini bekerja dengan menganalisis atribut-atribut seperti genre, sinopsis, aktor, sutradara, dan elemen naratif lainnya. Fitur-fitur teks seperti sinopsis atau deskripsi dapat diolah menggunakan teknik ekstraksi fitur seperti TF-IDF (Term Frequency–Inverse Document Frequency), yang mengubah teks menjadi representasi numerik. Setelah itu, sistem menghitung kemiripan antar item menggunakan cosine similarity, yaitu teknik yang mengukur sudut antar vektor representasi teks. Rekomendasi kemudian diberikan berdasarkan item yang paling mirip dengan apa yang pernah ditonton atau disukai pengguna. Sistem ini bersifat personal, karena rekomendasi tidak bergantung pada perilaku pengguna lain, melainkan pada karakteristik konten dari drama yang telah disukai sebelumnya.<sup>[2]</sup>


2. **Popularity-Based Recommendation**

   Pendekatan sistem rekomendasi yang menyarankan item berdasarkan tingkat popularitasnya secara umum, seperti rating tertinggi atau jumlah penonton terbanyak. Pendekatan ini tidak mempertimbangkan preferensi pribadi pengguna, tetapi efektif digunakan saat informasi pengguna belum tersedia. Meskipun tidak bersifat personal, metode ini mudah diimplementasikan dan sering menghasilkan rekomendasi yang relevan secara luas. Dalam proyek ini, pendekatan popularitas digunakan sebagai pembanding terhadap pendekatan berbasis konten, untuk mengevaluasi efektivitas rekomendasi drama Korea.<sup>[3]</sup>

## 📊 Data Understanding
Dataset yang digunakan dalam proyek ini diperoleh dari Kaggle dengan judul: [Korean Dramas Dataset](https://www.kaggle.com/datasets/saikalbatyrbekova/korean-dramas-dataset-eda). Dataset ini berisi informasi tentang drama Korea yang diambil dari situs MyDramaList. Dataset tersedia dalam format CSV dan mencakup berbagai informasi dasar seputar 350 drama Korea (Jumlah data) dengan 9 fitur.
#### Tabel Data
| Rank | Title                                 | Year of Release | Number of Episodes | Rating | Description                                        | Genre                              | Tags                                                   | Actors                                   |
|------|---------------------------------------|------------------|---------------------|--------|----------------------------------------------------|------------------------------------|---------------------------------------------------------|------------------------------------------|
| #1   | Move to Heaven                        | 2021             | 10                  | 9.2    | Geu Roo is a young autistic man. He works for ... | Life, Drama, Family                | Autism, Uncle-Nephew Relationship, Death, Sava...       | Lee Je Hoon, Tang Jun Sang, Hong Seung Hee, Ju... |
| #2   | Twinkling Watermelon                 | 2023             | 16                  | 9.2    | In 2023, high school student Eun Gyeol, a CODA... | Romance, Youth, Drama, Fantasy    | Time Travel, Child From The Future, Sign Langu...       | Ha Eun-Gyeol, Ha Yi-Chan, Choi Se-Kyung, Yoon ... |
| #3   | Moving                                | 2023             | 20                  | 9.1    | Kim Bong Seok, Jang Hui Su, and Lee Gang Hun,... | Action, Thriller, Mystery, Supernatural | Graphic Violence, Supernatural Power, Multiple... | Ryu Seung Ryong, Han Hyo Joo, Zo In Sung             |
| #4   | The Trauma Code: Heroes on Call       | 2025             | 8                   | 9.1    | Baek Gang Hyeok, a genius trauma surgeon with... | Action, Comedy, Drama, Medical    | Surgeon Male Lead, Hospital Setting, Mentor-Me...       | Ju Ji Hoon, Choo Young Woo, Ha Young, Yoon Gyu...   |
| #5   | Flower of Evil                        | 2020             | 16                  | 9.1    | Although Baek Hee Sung is hiding a dark secret... | Thriller, Romance, Crime, Melodrama | Married Couple, Deception, Suspense, Family Se... | Lee Joon Gi, Moon Chae Won, Jang Hee Jin, Seo ...    |

### Deskripsi Variabel
Berikut adalah uraian dari masing-masing fitur dalam dataset:
| Fitur               | Tipe Data | Deskripsi                                                                 |
|---------------------|-----------|---------------------------------------------------------------------------|
| Rank                | object    | Peringkat drama berdasarkan popularitas atau rating.                      |
| Title               | object    | Judul drama Korea.                                                       |
| Year of release     | int64     | Tahun pertama kali drama dirilis.                                        |
| Number of Episodes  | int64     | Jumlah total episode dari masing-masing drama.                                       |
| Rating              | float64   | Rating yang diberikan oleh penonton (biasanya dalam skala 0 hingga 10).           |
| Description         | object    | Ringkasan cerita atau sinopsis.                                          |
| Genre               | object    | Genre utama drama, bisa lebih dari satu.                                 |
| Tags                | object    | Label tambahan, seperti tema, gaya cerita, dll.                          |
| Actors              | object    | Daftar pemeran utama.                                                    |
#### Kondisi Data
- Berdasarkan pengecekan menggunakan `df.isnull().sum()`, tidak ditemukan missing value pada dataset. Hal ini mengindikasikan bahwa data sudah lengkap dan tidak memerlukan imputasi atau pengisian nilai yang hilang.
- Hasil dari `df.duplicated().sum()` juga menunjukkan bahwa tidak terdapat data duplikat. Ini memastikan bahwa setiap drama direpresentasikan secara unik dalam dataset.

### Visualization & Analysis
1. Distribusi Jumlah Drama Berdasarkan Tahun Rilis
<p align="center">
  <img src="https://github.com/user-attachments/assets/364ac73b-159a-4215-adac-e19303f8faca" alt="piechart" width="400"/>
  <br>
  <em>Gambar 1. Distribusi Drama Berdasarkan Tahun Rilis</em>
</p>
Visualisasi ini menunjukkan tren jumlah drama Korea yang dirilis setiap tahunnya. Terlihat adanya peningkatan jumlah drama secara signifikan sejak tahun 2015, dengan puncak pada tahun 2021. Hal ini mencerminkan tren industri hiburan Korea yang semakin berkembang dan produktif dalam beberapa tahun terakhir.

**Insight:**
Produksi drama meningkat tajam sejak 2015, dan tahun 2021 menjadi tahun paling produktif dalam dataset.

- Distribusi Rating Drama Korea
<p align="center">
  <img src="https://github.com/user-attachments/assets/c5a995ea-92e1-450f-8805-0a366effe3b7" alt="piechart" width="400"/>
  <br>
  <em>Gambar 2. Distribusi Rating Drama Korea</em>
</p>
Distribusi rating menunjukkan bahwa sebagian besar drama memiliki nilai antara 8.0 hingga 9.0. Hal ini mengindikasikan bahwa drama-drama dalam dataset umumnya berkualitas tinggi menurut penilaian penonton.

**Insight:**
Rating drama Korea umumnya tinggi (di atas 8.0), dan hanya sedikit drama yang memiliki rating di bawah 7.0.

- Genre Drama Korea yang Paling Umum
<p align="center">
  <img src="https://github.com/user-attachments/assets/7f3665fb-1300-4145-95ae-b2dfeaebd4da" alt="piechart" width="400"/>
  <br>
  <em>Gambar 3. Genre Drama Korea yang Paling Sering Muncul</em>
</p>
Visualisasi ini menunjukkan 10 genre drama paling umum yang terdapat dalam dataset. Genre Romance dan Drama mendominasi, diikuti oleh genre seperti Thriller, Comedy, dan Mystery.

**Insight:**
Romance dan Drama adalah genre paling populer. Genre populer lainnya adalah **Thriller, Comedy**, dan **Mystery**.

## 🧹 Data Preparation
Tahapan ini bertujuan untuk menyiapkan data agar dapat digunakan dalam proses pemodelan sistem rekomendasi. Teknik-teknik _feature engineering_ dan normalisasi digunakan untuk meningkatkan kualitas dan relevansi fitur.
### Feature Engineering: Content-Based Filtering
- **Penggabungan Fitur Teks Penting**

Beberapa kolom teks yang relevan seperti `Genre`, `Tags`, `Actors`dan `Description` digabung menjadi satu fitur baru bernama `combined_features` untuk membentuk representasi konten setiap drama. Tujuannya adalah untuk mengekstrak informasi penting yang menggambarkan karakteristik drama secara keseluruhan.
>Contoh hasil gabungan fitur: _Life,  Drama,  Family  Autism, Uncle-Nephew Relationship, Death, Savant Syndrome, Mourning, Tearjerker, Father-Son Relationship, Life Lesson, Ex-convict, Cleaning And Organizing Lee Je Hoon, Tang Jun ..._

- **TF-IDF Vectorization**
  
Setelah membuat fitur `combined_features` yang berisi gabungan teks dari kolom `Genre`, `Tags`, `Actors`, dan `Description`, dilakukan transformasi teks menjadi representasi numerik menggunakan teknik **TF-IDF (Term Frequency–Inverse Document Frequency)** dengan bantuan pustaka `TfidfVectorizer` dari Scikit-learn.

TF-IDF mengubah teks menjadi vektor angka berdasarkan seberapa sering suatu kata muncul dalam satu dokumen. Teknik ini bertujuan untuk menekankan kata-kata unik dan mengurangi pengaruh kata-kata umum, sehingga menghasilkan representasi numerik yang lebih relevan untuk menghitung kemiripan antar drama. Hasil dari TF-IDF ini nantinya digunakan dalam sistem rekomendasi berbasis konten dengan teknik Cosine Similarity.

#### Berikut adalah implementasi kode TF-IDF menggunakan Scikit-learn:
```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf = TfidfVectorizer(stop_words='english')
tfidf_matrix = tfidf.fit_transform(df['combined_features'])
````

### Feature Engineering: Popularity-Based Filtering
   - **Normalisasi Rating**
     
Untuk memastikan setiap fitur berkontribusi secara seimbang dalam perhitungan _popularity score_, dilakukan normalisasi terhadap nilai `rating` menggunakan teknik **Min-Max Scaling**. Rating awal (rentang 0 hingga 10) diubah ke rentang 0 hingga 1.
#### Inisialisasi

   ```python
  scaler = MinMaxScaler()
   ```

Normalisasi diperlukan karena skala asli fitur berbeda-beda. Dengan menyamakan skala, setiap fitur memiliki bobot kontribusi yang adil dalam model rekomendasi berbasis popularitas.
     
   - **Year Recency Score**
     
Skor _recency_ dihitung untuk memberi bobot lebih tinggi pada drama yang dirilis lebih baru, berdasarkan:

$$
\text{Recency Score} = \frac{\text{Year of Release - min(year)}}{\text{max(year) - min(year)}}
$$

Drama yang dirilis lebih dekat ke tahun sekarang (dalam hal ini 2025) dianggap lebih relevan secara waktu dan skor ini penting dalam sistem popularity-based filtering, untuk menghindari bias terhadap drama lama yang mungkin memiliki rating tinggi, tetapi sudah tidak relevan secara tren.

   - **Normalisasi Jumlah Episode**

Fitur `Number of Episodes` dinormalisasi karena jumlah episode bisa sangat bervariasi. Tujuannya adalah agar drama berdurasi wajar tidak terpinggirkan karena outlier dengan episode ekstrem.

   - **Penggabugan Polurarity**

Seluruh fitur yang telah dinormalisasi (`rating`, `recency`, `jumlah episode`) digabungkan menjadi satu metrik bernama `Popularity Score`. Dengan menggabungkan beberapa aspek popularitas, skor ini memberikan representasi yang lebih komprehensif untuk mengukur seberapa menarik suatu drama bagi pengguna umum.
#### Statistik Deskriptif Fitur Skor
Berikut adalah ringkasan statistik deskriptif dan fitur-fitur skor yang telah dinormalisasi:
| Statistik | Rating | rating_score | year_score | episode_score | popularity_score |
|-----------|--------|--------------|------------|----------------|------------------|
| Count     | 350    | 350          | 350        | 350            | 350              |
| Mean      | 8.365  | 0.702        | 0.764      | 0.131          | 0.663            |
| Std       | 0.455  | 0.162        | 0.169      | 0.110          | 0.091            |
| Min       | 6.400  | 0.000        | 0.000      | 0.000          | 0.295            |
| 25%       | 8.300  | 0.679        | 0.682      | 0.083          | 0.621            |
| 50%       | 8.400  | 0.714        | 0.773      | 0.114          | 0.670            |
| 75%       | 8.600  | 0.786        | 0.909      | 0.114          | 0.717            |
| Max       | 9.200  | 1.000        | 1.000      | 1.000          | 0.884            |


## 🤖 Modeling & Result
Pada tahap ini, sistem rekomendasi dikembangkan untuk memberikan rekomendasi drama Korea berdasarkan dua pendekatan yang berbeda: _Content-Based Filtering_ dan _Popularity-Based Recommendation_. Kedua pendekatan ini dirancang untuk memberikan solusi atas masalah rekomendasi, baik berdasarkan kesamaan konten maupun berdasarkan tingkat popularitas umum.
### Content Based Filtering
- **Menghitung Cosine Similarity**
  
Kemiripan antar drama dihitung menggunakan **Cosine Similarity**, yang mengukur sudut antar vektor TF-IDF. Semakin kecil sudutnya, semakin mirip konten dua drama tersebut. Hasilnya disimpan dalam dataframe `cosine_sim_df` yang menyimpan skor kesamaan antar semua pasangan drama.
#### Tabel Cosine Similarity
| Title                               | Move to Heaven | Twinkling Watermelon | Moving  | The Trauma Code: Heroes on Call | Flower of Evil |
|------------------------------------|----------------|-----------------------|---------|----------------------------------|----------------|
| **Move to Heaven**                 | 1.000000       | 0.027158              | 0.041006| 0.015090                         | 0.038604       |
| **Twinkling Watermelon**           | 0.027158       | 1.000000              | 0.059964| 0.035651                         | 0.013721       |
| **Moving**                         | 0.041006       | 0.059964              | 1.000000| 0.068624                         | 0.044067       |
| **The Trauma Code: Heroes on Call**| 0.015090       | 0.035651              | 0.068624| 1.000000                         | 0.064347       |
| **Flower of Evil**                 | 0.038604       | 0.013721              | 0.044067| 0.064347                         | 1.000000       |

#### Testing Model
Setelah proses modeling selesai, tahap berikutnya adalah menguji bagaimana model memberikan rekomendasi berdasarkan drama tertentu yang dipilih sebagai input. Untuk pendekatan _Content-Based Filtering_, rekomendasi diberikan dengan menghitung kemiripan antar drama berdasarkan konten (genre, sinopsis, aktor, dll) menggunakan TF-IDF dan cosine similarity. Langkah pengujian diterapkan melalui potongan kode berikut ini:

```python
content_based_recommendations('Moving', k=5)
```
##### Output
| Title                | Genre                                      | Rating | Year of Release |
|----------------------|---------------------------------------------|--------|-----------------|
| Motel California     | Romance, Drama                              | 7.3    | 2025            |
| Memorist             | Action, Thriller, Mystery, Supernatural     | 8.4    | 2020            |
| My Father is Strange | Comedy, Romance, Drama, Family              | 8.6    | 2017            |
| Pyramid Game         | Action, Thriller, Psychological, Drama      | 8.5    | 2024            |
| Flex X Cop           | Action, Thriller, Mystery, Comedy           | 8.7    | 2024            |

Rekomendasi yang dihasilkan menunjukkan drama-drama dengan unsur genre  serupa seperti Thriller, Action, dan Drama yang juga muncul dalam konten "Moving". Ini menunjukkan bahwa sistem bekerja dengan baik dalam mengidentifikasi kemiripan konten berdasarkan teks fitur.

### Popularity-Based Recommendation
Langkah-langkah dalam pembuatan rekomendasi berbasis popularitas:
- **Menentukan Popularity Score**
  
`popularity_score` dibentuk dari kombinasi fitur yang telah dinormalisasi: `rating_score`, `year_score`, dan `episode_score`. Skor ini mewakili seberapa populer dan relevan suatu drama secara umum.

- **Rekomendasi Berdasarkan Rating**
  
Rekomendasi diberikan kepada pengguna berdasarkan drama-drama dengan rating tertinggi, tanpa mempertimbangkan preferensi personal atau genre. Pengujian:
```python
popularity_based_recommendations(k=5, min_rating=8.5)
```
##### Output
| Title                             | Genre                                     | Rating | Year of Release | Popularity Score |
|-----------------------------------|-------------------------------------------|--------|-----------------|------------------|
| Twinkling Watermelon              | Romance, Youth, Drama, Fantasy            | 9.2    | 2023            | 0.884091         |
| The Trauma Code: Heroes on Call   | Action, Comedy, Drama, Medical            | 9.1    | 2025            | 0.883874         |
| Moving                            | Action, Thriller, Mystery, Supernatural   | 9.1    | 2023            | 0.865693         |
| Study Group                       | Action, Thriller, Comedy, Youth           | 9.0    | 2025            | 0.863961         |
| Lovely Runner                     | Music, Comedy, Romance, Fantasy           | 9.0    | 2024            | 0.854870         |

- **Filter Berdasarkan Genre**
  
Rekomendasi ini disaring berdasarkan genre tertentu, misalnya "Romance", kemudian dipilih drama dengan rating dan skor popularitas tertinggi di genre tersebut. Langkah pengujian diterapkan melalui potongan kode berikut ini:
```python
popularity_based_recommendations(k=5, genre_filter='Romance')
```
##### Output
| Title                          | Genre                                       | Rating | Year of Release | Popularity Score |
|--------------------------------|---------------------------------------------|--------|-----------------|------------------|
| Twinkling Watermelon           | Romance, Youth, Drama, Fantasy              | 9.2    | 2023            | 0.884091         |
| Lovely Runner                  | Music, Comedy, Romance, Fantasy             | 9.0    | 2024            | 0.854870         |
| Hospital Playlist 2           | Friendship, Romance, Life, Medical          | 9.1    | 2021            | 0.832359         |
| Alchemy of Souls              | Action, Historical, Romance, Fantasy        | 9.0    | 2022            | 0.830628         |
| Extraordinary Attorney Woo    | Law, Romance, Life, Drama                   | 9.0    | 2022            | 0.827597         |

- **Gabungan Rating dan Genre**
  
Pendekatan gabungan ini mempertimbangkan rating tinggi dan genre tertentu, seperti drama bertema “Family”. Ini mendekati minat spesifik pengguna terhadap tipe konten tertentu. Langkah pengujian diterapkan melalui potongan kode berikut ini:
```python
popularity_based_recommendations(k=5, min_rating=8.5, genre_filter='Family')
```
##### Output
| Title               | Genre                                     | Rating | Year of Release | Popularity Score |
|---------------------|--------------------------------------------|--------|-----------------|------------------|
| Move to Heaven      | Life, Drama, Family                        | 9.2    | 2021            | 0.852273         |
| The Good Bad Mother | Comedy, Life, Drama, Family                | 8.9    | 2023            | 0.818290         |
| Navillera           | Friendship, Life, Drama, Family            | 9.0    | 2021            | 0.810931         |
| My Mister           | Psychological, Life, Drama, Family         | 9.1    | 2018            | 0.794481         |
| Once Again          | Comedy, Romance, Drama, Family             | 8.6    | 2020            | 0.778247         |


### Kelebihan dan Kekurangan
Dua pendekatan sistem rekomendasi yang telah diterapkan:
| Pendekatan             | Kelebihan                                              | Kekurangan                                 |
|------------------------|--------------------------------------------------------|--------------------------------------------|
| Content-Based Filtering| Rekomendasi personal berdasarkan preferensi pengguna   | Tidak bisa merekomendasikan item baru (cold start) |
| Popularity-Based       | Sederhana dan cocok untuk semua pengguna               | Tidak personal dan bias terhadap item populer atau lama |

## 📊 Evaluation
Untuk mengevaluasi sistem rekomendasi yang dibangun, digunakan pendekatan evaluasi yang sesuai dengan jenis algoritma yang diterapkan. Karena sistem rekomendasi tidak memiliki label ground-truth eksplisit seperti supervised learning, maka evaluasi dilakukan secara heuristik menggunakan metrik yang sesuai dengan masing-masing pendekatan.

### Content-Based FIltering
Pendekatan ini menggunakan top-N recommendation untuk mengukur kualitas rekomendasi berdasarkan kemiripan konten dengan item yang disukai pengguna.

**Contoh:**
- Input: `Twinkling Watermelon`
- Output Rekomendasi:
   - The Sound of Magic
   - High School Return of a Gangster
   - My Unfamiliar Family
   - The King's Affection
   - Reply 1997
     
Rekomendasi di atas menunjukkan kemiripan dalam genre (romance, youth, fantasy) dan tema emosional atau keluarga, menunjukkan bahwa sistem berhasil menangkap konten yang relevan.

#### Metrik Evaluasi 
##### 1. Precision@K

Precision@K mengukur seberapa banyak item yang relevan dari total K rekomendasi.
- Setiap 5 rekomendasi yang diberikan, rata-rata 2.4 di antaranya dianggap relevan (karena saling merekomendasikan kembali).
  
$$
\text{Precision@5} = \frac{2.4}{5} = 0.48
$$

> **Hasil**: Precision@5 = **0.48**

##### 2. Coverage
Coverage mengukur seberapa besar cakupan sistem dalam merekomendasikan item dari seluruh dataset. Semakin tinggi nilai coverage, semakin besar variasi item yang mampu direkomendasikan.
- Jumlah item unik yang muncul sebagai rekomendasi dari seluruh pengguna: **319**
- Jumlah total drama dalam dataset: **350**
  
$$
\text{Coverage} = \frac{319}{200} = 0.9114
$$

> **Hasil**: Coverage = **0.9114** atau 91.14%

### Popularity-Based Recommendation
Dilakukan dengan tiga skenario:
- Berdasarkan rating tertinggi (Menampilkan drama top dengan rating 9.0+).
- Berdasarkan genre  (Menampilkan drama populer dalam kategori tertentu).
- Gabungan rating dan genre (Rekomendasi populer tetapi sesuai preferensi genre pengguna).
  
Hasil menunjukkan rekomendasi umumnya relevan dan mencakup drama-drama terkenal serta berkualitas tinggi

#### Metrik Evaluasi
##### 1. Coverage
Karena hanya item dengan skor populer yang muncul, cakupan sistem ini rendah.
- Item unik yang pernah direkomendasikan: 26
- Total drama: 350
  
$$
\text{Coverage} = \frac{26}{200} = 0.0743
$$

> **Hasil**: Coverage = 0.0743 atau 7,43%

##### 2. Novelty
Novelty mengukur kebaruan rekomendasi. Sistem popularitas cenderung merekomendasikan item yang umum diketahui.

$$
\text{Novelty}(i) \propto \frac{1}{\log_2(1 + popularity(i))}
$$

> Estimasi Novelty (Rata-Rata) = **1.1510**

#### Kesimpulan Evaluasi
| Pendekatan              | Precision@5 | Coverage | Novelty  |
|------------------------|-------------|----------|----------|
| Content-Based Filtering | 0.48        | 0.9114   | -        |
| Popularity-Based        | -           | 0.0743   | 1.1510   |

- **Content-Based Filtering** memberikan keseimbangan antara akurasi rekomendasi (precision) dan cakupan item (coverage), sehingga cocok untuk personalisasi yang berfokus pada preferensi unik tiap pengguna. Sistem ini memungkinkan eksplorasi lebih luas karena hampir semua item dapat direkomendasikan.
  
- **Popularity-Based Recommendation** memiliki cakupan dan kemungkinan relevansi yang rendah, karena hanya merekomendasikan item yang banyak ditonton atau disukai secara global. Metode ini lebih sederhana dan cepat, cocok untuk pengguna baru atau saat data preferensi pengguna masih minim.

  
## Referensi
[1] Korea Creative Content Agency (KOCCA). (2023). _2022 Content Industry Statistics Report_.

[2] Ricci, F., Rokach, L., & Shapira, B. (2015). _Recommender Systems Handbook. Springer_.

[3] Aggarwal, C. C. (2016)._ Recommender Systems: The Textbook. Springer._
