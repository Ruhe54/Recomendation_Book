# Laporan Proyek Machine Learning - Dicky Ary Setiawan

## Project Overview

Dataset "Best Books 10k Multi-Genre Data" merupakan kumpulan data yang berisi informasi tentang 10.000 buku populer dari berbagai genre. Dataset ini mencakup berbagai atribut penting yang dapat digunakan untuk analisis dan pembuatan sistem rekomendasi, seperti judul buku, genre, deskripsi, penulis, rating, dan lainnya. Informasi ini dirancang untuk memberikan wawasan yang komprehensif tentang buku-buku yang tersedia, sekaligus memungkinkan pengembangan sistem berbasis machine learning untuk merekomendasikan buku kepada pembaca. Oleh karena itu dibutalah rekomendasi sistem Content-based Filtering.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Apakah genre paling populer ?
- Siapakah penulis buku dengan jumlah terbanyak? dan buku apa yang paling populer berdasarkan Num_Ratingnya ?
- Buku apa yang memiliki Avg_Rating paling tinggi dengan Num_Rating diatas 2.000.000? dan buku apa yang memiliki cosine_similarity yang paling tinggi dengan buku Avg_rating tertinggi tersebut ?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Mengetahui apa genre paling populer pada buku.
- Mengetahui penulis dengan jumlah buku paling banyak.
- Mengetahui rekomendasi buku yang sesuai dengan nilai rating paling tinggi.


## Data Understanding
Jumlah data yang dimiliki dataset ini sebanyak 10.000 data dengan 0 data duplicate dan 40 data kosong pada colom Description.
Sumber dataset (https://www.kaggle.com/datasets/ishikajohari/best-books-10k-multi-genre-data/data)

Variabel-variabel pada Best Books dataset adalah sebagai berikut:
- Book             : Nama buku.
- Author           : Nama penulis buku.
- Description      : Deskripsi buku yang di mention di goodreads.
- Genres           : Genre buku berdasarkan clasifikasi di goodreads.
- Average Rating   : Rating rata-rata yang diberikan user.
- Number of Rating : Jumlah user yang memberikan rating.
- Url              : Link untuk mengakses informasi lebih detail.

untuk memahami data terdapat langkah yang akan dilakukan :
1. Mencari tahu daftar colom apa saja yang terdapat pada dataframe.
2. Melihat jenis data yang terdapat pada colom.
3. Melihat statistik deskriptif pada dataframe.
4. Melakuakn pengecekan apakah terdapat nilai yang sama atau duplicated.
5. Melakukan drop nilai pada column genres yang memiliki nilai [].
6. Melakukan pengecekan apakah terdapat nilai Na.
7. Melakukan drop nilai Na.
8. Membuat plot dengan nilai X adalah rating dan Y adalah jumlah buku.

## Data Preparation

1. Membuat variable baru dengan merubah data menjadi list dari colom Book dan Genres.
2. Membuat dataframe baru dan merubah nama colom Book menjadi book_nam dan Genres menjadi genre.

## Modeling

1. Membuat variable dengan menggunakan TfidfVectorizer.
2. Selanjutnya melakuakn tokenisasi pada kolom Genres untuk dipecah menjadi token.
3. Mengeluarkan vocabulary dari colom genre dalam bentuk array.
4. Membuat variable baru dengan nama tfidf_matrix untuk merepresentasikan kata-kata unik (fitur/vocabulary) yang ditemukan di dalam colom genres.
5. Selanjutnya merubah hasil dari TfidfVectorizer menjadi dense matrix.Dense matrix adalah representasi penuh dari matriks dalam bentuk array 2D, di mana setiap elemen memiliki nilai eksplisit (bukan nol diisi dengan angka 0).
6. Selanjutnya membuat variable baru bernama cosine_sim yang berisi matriks kemiripan cosine, yang menunjukkan tingkat kesamaan antara setiap pasangan dokumen.
7. Membuat variable baru yang berisi Dataframe cosine_sim dan column yang berisi dataframe.Book .
8. Membuat variable dengan nama buku yang akan digunakan sebagai referensi untuk mencari buku-buku serupa.
9. Selanjunya mencari lokasi index dari nama buku.
10. Mencari baris yang sesuai dengan indeks buku (yaitu nilai cosine similarity antara buku yang dicari dan semua buku lainnya).

Berikut adalah hasil rekomendasi dari buku yang berjudul "Big Fish":


![image](https://github.com/user-attachments/assets/7e1513e8-55e2-4302-8765-d1dc8ea9d845)


## Evaluation

Cosine similarity adalah metrik evaluasi yang digunakan untuk mengukur kemiripan antara dua vektor dalam ruang vektor, yang sering diterapkan pada masalah pemrosesan bahasa alami, pencarian informasi, dan pembelajaran mesin.
Cara Kerja Cosine Similarity dengan mengukur seberapa dekat dua vektor arah (bukan panjangnya) dengan menghitung sudut antara keduanya. Nilai cosine similarity berkisar antara -1 hingga 1:
1: Vektor tersebut memiliki arah yang sama.
0: Vektor tersebut tidak memiliki korelasi atau tegak lurus satu sama lain.
-1: Vektor tersebut memiliki arah yang berlawanan.

Dari rekomendasi yang didapatkan oleh buku yang berjudul "Big Fish" buku yang memiliki score cosine similarity paling tinggi adalah buku berjudul "The Midnight Library" dengan score 0.82 .

Sistem rekomendasi buku berbasis machine learning yang dibuat dari dataset "Best Books 10k Multi-Genre Data" memiliki berbagai implikasi yang signifikan dalam berbagai aspek. Berikut adalah beberapa implikasinya:

1. Implikasi pada Pengguna (Pembaca)
- Meningkatkan Pengalaman Membaca: Sistem ini dapat membantu pengguna menemukan buku yang relevan dan sesuai dengan preferensi mereka, sehingga pengalaman membaca menjadi lebih menyenangkan.
- Efisiensi dalam Pemilihan Buku: Dengan rekomendasi yang terkurasi, pengguna tidak perlu menghabiskan waktu lama mencari buku yang sesuai di antara ribuan pilihan.
- Personalisasi: Sistem ini dapat disesuaikan untuk memberikan rekomendasi yang lebih spesifik berdasarkan minat unik pengguna.
2. Implikasi pada Industri Penerbitan dan Penjualan Buku
- Meningkatkan Penjualan: Dengan merekomendasikan buku berdasarkan preferensi pengguna, sistem ini dapat meningkatkan konversi penjualan pada platform e-commerce atau toko buku online.
- Promosi Buku Baru: Buku baru atau kurang populer dapat di-highlight ke pengguna yang kemungkinan besar tertarik, sehingga membantu distribusi yang lebih merata.

Apakah sudah menjawab problem statment?

- Apakah genre paling populer ?
  Genre yang paling populer berdasarkan dataset goodreads adalah Fiction disusul oleh Fantasy dan selanjutnya adalah Nonfiction.
- Siapakah penulis buku dengan jumlah terbanyak? dan buku apa yang paling populer berdasarkan Avg_Rating yang ditulis oleh penulis tersebut?
  Nama penulis buku terbanyak adalah Stepen King dengan jumlah buku sebanyak 57 dengam buku paling tinggi ratingnya adalah The Dark Tower Series: Books 1-7.
- Buku apa yang memiliki Avg_Rating paling tinggi dengan Num_Rating diatas 2.000.000? dan buku apa yang memiliki cosine_similarity yang paling tinggi dengan buku Avg_rating tertinggi tersebut?
  buku dengan kriteria jumlah user yang memberikan rating diatas 2.000.000 dan memiliki rating paling baik adalah buku yang berjudul "Harry Potter and the Deathly Hallows (Harry Potter, #7)" karya J.K. Rowling. buku ini memilki cosine similarity paling tinggi dengan buku yang berjudul "Harry Potter and the Half-Blood Prince (Harry Potter, #6)","Harry Potter and the Order of the Phoenix (Harry Potter, #5, Part 1)", dan "Harry Potter and the Deathly Hallows (Harry Potter, #7)" dengan memiliki cosine similarity bernilai 1

Apakah berhasil mencapai goals yang diharapkan?
- Goal pertama : Berhasil didapatkan bahwa genre Fiction adalah genre paling populer berdasarkan Goodreads.
- Goal Kedua   : Berhasil mengetahui bahwa Stepen king adalah author dengan buku terbanyak sebanyak 57 buku.
- Goal Ketiga  : Mengetahui bahwa the midnight library adalah buku yang paling direkomendasikan sesuai dengan buku dengan rating tinggi yaitu A Court of Mist and Fury (A Court of Thorns and Roses, #2).
