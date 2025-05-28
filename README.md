# Laporan Proyek Machine Learning - Juli Arsi Sabrina
## 📌 Project Overview
## 💼 Business Understanding
### Problem Statements
1. **Kebingungan pengguna dalam memilih drama Korea yang sesuai**  
   Banyaknya pilihan drama Korea yang tersedia membuat pengguna sering kesulitan menentukan tontonan yang sesuai dengan minat atau preferensi mereka.
2. **Kurangnya sistem rekomendasi berbasis isi yang relevan dan personal**  
   Sebagian besar rekomendasi hanya berdasarkan popularitas atau rating tanpa memperhatikan kesamaan konten dengan tontonan yang disukai pengguna sebelumnya.
3. **Kurangnya integrasi teknologi Machine Learning dalam sistem rekomendasi drama Korea** 
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
Pendekatan ini memberikan rekomendasi berdasarkan kemiripan konten antar drama Korea. Fitur-fitur seperti genre, sinopsis, pemeran, dan sutradara dianalisis menggunakan metode ekstraksi teks seperti TF-IDF, lalu dihitung kemiripannya menggunakan cosine similarity. Sistem ini bersifat personal, karena rekomendasi disesuaikan dengan konten drama yang telah dipilih pengguna.
2. **Popularity-Based Recommendation**  
Popularity-Based Recommendation adalah pendekatan sistem rekomendasi yang menyarankan item berdasarkan popularitasnya secara umum, tanpa mempertimbangkan preferensi atau riwayat pengguna secara personal. Sistem ini sederhana dan efektif ketika informasi pengguna tidak tersedia, atau saat ingin memberikan rekomendasi yang bersifat umum.

Dengan mengimplementasikan kedua pendekatan ini, sistem rekomendasi akan memberikan saran yang lebih personal releval, dan adaptif, sekaligus membandingkan efektivitas pendekatan berbasis konten dan kaloboratif dalam konteks penyaringan tontonan drama Korea.

## 📊 Data Understanding
Dataset yang digunakan dalam proyek ini diperoleh dari Kaggle dengan judul: [Korean Dramas Dataset](https://www.kaggle.com/datasets/saikalbatyrbekova/korean-dramas-dataset-eda). Dataset ini berisi informasi tentang drama Korea yang diambil dari situs MyDramaList. Dataset tersedia dalam format CSV dan mencakup berbagai informasi dasar seputar 350 drama Korea (Jumlah baris data) dengan 9 fitur.
#### Tabel Data
| Rank | Title                                 | Year of Release | Number of Episodes | Rating | Description                                        | Genre                              | Tags                                                   | Actors                                   |
|------|---------------------------------------|------------------|---------------------|--------|----------------------------------------------------|------------------------------------|---------------------------------------------------------|------------------------------------------|
| #1   | Move to Heaven                        | 2021             | 10                  | 9.2    | Geu Roo is a young autistic man. He works for ... | Life, Drama, Family                | Autism, Uncle-Nephew Relationship, Death, Sava...       | Lee Je Hoon, Tang Jun Sang, Hong Seung Hee, Ju... |
| #2   | Twinkling Watermelon                 | 2023             | 16                  | 9.2    | In 2023, high school student Eun Gyeol, a CODA... | Romance, Youth, Drama, Fantasy    | Time Travel, Child From The Future, Sign Langu...       | Ha Eun-Gyeol, Ha Yi-Chan, Choi Se-Kyung, Yoon ... |
| #3   | Moving                                | 2023             | 20                  | 9.1    | Kim Bong Seok, Jang Hui Su, and Lee Gang Hun,... | Action, Thriller, Mystery, Supernatural | Graphic Violence, Supernatural Power, Multiple... | Ryu Seung Ryong, Han Hyo Joo, Zo In Sung             |
| #4   | The Trauma Code: Heroes on Call       | 2025             | 8                   | 9.1    | Baek Gang Hyeok, a genius trauma surgeon with... | Action, Comedy, Drama, Medical    | Surgeon Male Lead, Hospital Setting, Mentor-Me...       | Ju Ji Hoon, Choo Young Woo, Ha Young, Yoon Gyu...   |
| #5   | Flower of Evil                        | 2020             | 16                  | 9.1    | Although Baek Hee Sung is hiding a dark secret... | Thriller, Romance, Crime, Melodrama | Married Couple, Deception, Suspense, Family Se... | Lee Joon Gi, Moon Chae Won, Jang Hee Jin, Seo ...    |

### Deskripsi Variable
Berikut adalah uraian dari masing-masing fitur dalam dataset:
| Fitur               | Tipe Data | Deskripsi                                                                 |
|---------------------|-----------|---------------------------------------------------------------------------|
| Rank                | object    | Peringkat drama berdasarkan popularitas atau rating.                      |
| Title               | object    | Judul drama Korea.                                                       |
| Year of release     | int64     | Tahun pertama kali drama dirilis.                                        |
| Number of Episodes  | int64     | Total episode dari drama tersebut.                                       |
| Rating              | float64   | Nilai rating dari penonton (biasanya dalam skala 0 hingga 10).           |
| Description         | object    | Ringkasan cerita atau sinopsis.                                          |
| Genre               | object    | Genre utama drama, bisa lebih dari satu.                                 |
| Tags                | object    | Label tambahan, seperti tema, gaya cerita, dll.                          |
| Actors              | object    | Daftar pemeran utama.                                                    |

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
  <em>Gambar 2. Distribusi Rating DramaKorea</em>
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
Romance dan Drama adalah genre paling populer. Genre populer lainnya adalah *Thriller, Comedy*, dan *Mystery*.

## 🧹 Data Preparation
Tahapan ini bertujuan untuk menyiapkan data agar dapat digunakan dalam proses pemodelan sistem rekomendasi. Teknik-teknik feature engineering dan normalisasi digunakan untuk meningkatkan kualitas dan relevansi fitur.
### Feature Engineering: Content-Based Filtering
- **Penggabungan Fitur Teks Penting**

Beberapa kolom teks yang relevan seperti `Genre`, `Tags`, `Actors`dan `Description` digabung menjadi satu fitur baru bernama `combined_features` untuk membentuk representasi konten setiap drama. Tujuannya adalah untuk mengekstrak informasi penting yang menggambarkan karakteristik drama secara keseluruhan.
>Combined features sample: Life,  Drama,  Family  Autism, Uncle-Nephew Relationship, Death, Savant Syndrome, Mourning, Tearjerker, Father-Son Relationship, Life Lesson, Ex-convict, Cleaning And Organizing Lee Je Hoon, Tang Jun ...

Penggabungan fitur ini penting untuk membentuk input yang bermakna dalam sistem rekomendasi berbasis konten. Algoritma seperti TF-IDF dan cosine similarity akan menggunakan teks gabungan ini untuk menghitung kedekatan antar drama.


### Feature Engineering: Popularity-Based Filtering
   - **Normalisasi Rating Score**
     
Untuk memastikan setiap fitur berkontribusi secara seimbang dalam perhitungan popularity score, dilakukan normalisasi terhadap nilai rating menggunakan teknik Min-Max Scaling. Nilai rating awal yang berada dalam rentang 0 hingga 10 diubah menjadi rentang 0 hingga 1.
#### Inisialisasi

   ```python
  scaler = MinMaxScaler()
   ```

Normalisasi diperlukan karena skala asli fitur berbeda-beda. Dengan menyamakan skala, setiap fitur memiliki bobot kontribusi yang adil dalam model rekomendasi berbasis popularitas.
     
   - **Year Recency Score**
     
Skor recency dihitung untuk memberi bobot lebih tinggi pada drama yang dirilis lebih baru, berdasarkan:

$$
\text{Recency Score} = \frac{\text{Year of Release - min year}}{\text{max year - min year}}
$$

Drama yang dirilis lebih dekat ke tahun sekarang (dalam hal ini 2025) dianggap lebih relevan secara waktu dan skor ini penting dalam sistem popularity-based filtering, untuk menghindari bias terhadap drama lama yang mungkin memiliki rating tinggi, tetapi sudah tidak relevan secara tren.

   - **Normalisasi Jumlah Episode**

Fitur `Number of Episodes` dinormalisasi karena jumlah episode bisa sangat bervariasi. Tujuannya adalah agar drama berdurasi wajar tidak terpinggirkan karena outlier dengan episode ekstrem.

   - **Penggabugan Polurarity**

Seluruh fitur yang telah dinormalisasi (`rating`, `recency`, `jumlah episode`) digabungkan menjadi satu metrik bernama `Popularity Score`. Dengan menggabungkan beberapa aspek popularitas, skor ini memberikan representasi yang lebih komprehensif untuk mengukur seberapa menarik suatu drama bagi pengguna umum.
#### Statistik Deskriptif Fitur-Fitur Skor
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


## 🤖 Model Development
Pada tahap ini, sistem rekomendasi dikembangkan untuk memberikan rekomendasi drama Korea berdasarkan dua pendekatan yang berbeda: Content-Based Filtering dan Popularity-Based Recommendation. Kedua pendekatan ini dirancang untuk memberikan solusi atas masalah rekomendasi, baik berdasarkan kesamaan konten maupun berdasarkan tingkat popularitas umum.
### Content Based Filtering

Content-Based Filtering merekomendasikan item berdasarkan kemiripan fitur dengan item yang disukai atau dipilih sebelumnya. Dalam proyek ini, fitur-fitur seperti `Genre`, `Tags`, `Actors` dan `Description` digunakan untuk mewakili konten setiap drama.

-  **TF-IDF Vectorization**
  
Untuk mengubah teks menjadi vektor numerik, digunakan teknik TF-IDF (Term Frequency-Inverse Document Frequency) pada fitur gabungan `combined_features`. Teknik ini menekankan kata-kata penting yang unik pada setiap drama dan mengurangi pengaruh kata-kata umum.

- Menghitung Cosine Similarity
Kemiripan antar drama dihitung menggunakan **Cosine Similarity**, yang mengukur sudut antar vektor TF-IDF. Semakin kecil sudutnya, semakin mirip konten dua drama tersebut. Hasilnya disimpan dalam dataframe `cosine_sim_df` yang menyimpan skor kesamaan antar semua pasangan drama.
#### Tabel Cosine Silimarity
| Title                               | Move to Heaven | Twinkling Watermelon | Moving  | The Trauma Code: Heroes on Call | Flower of Evil |
|------------------------------------|----------------|-----------------------|---------|----------------------------------|----------------|
| **Move to Heaven**                 | 1.000000       | 0.027158              | 0.041006| 0.015090                         | 0.038604       |
| **Twinkling Watermelon**           | 0.027158       | 1.000000              | 0.059964| 0.035651                         | 0.013721       |
| **Moving**                         | 0.041006       | 0.059964              | 1.000000| 0.068624                         | 0.044067       |
| **The Trauma Code: Heroes on Call**| 0.015090       | 0.035651              | 0.068624| 1.000000                         | 0.064347       |
| **Flower of Evil**                 | 0.038604       | 0.013721              | 0.044067| 0.064347                         | 1.000000       |


## 📊 Evaluation
## Referensi
