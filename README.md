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
## 🧹 Data Preparation
## 🤖 Model Development
### Content Based Filtering
## 📊 Evaluation
## Referensi
