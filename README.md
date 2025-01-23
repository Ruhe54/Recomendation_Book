# Laporan Proyek Machine Learning - Dicky Ary Setiawan

## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa proyek ini penting untuk diselesaikan.
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Judul Referensi](https://scholar.google.com/) 

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- apakah genre paling populer ?
- siapakah penulis buku dengan jumlah terbanyak? dan buku apa yang paling populer berdasarkan Num_Ratingnya?
- buku apa yang memiliki Avg_Rating paling tinggi dengan Num_Rating diatas 500.000? dan buku apa yang memiliki cosine_similarity yang paling tinggi dengan buku Avg_rating tertinggi tersebut?

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Mengetahui apa genre paling populer pada buku
- Mengetahui penulis dengan jumlah buku paling banyak
- Mengetahui rekomendasi buku yang sesuai dengan nilai rating paling tinggi


## Data Understanding
Jumlah data yang dimiliki dataset ini sebanyak 10.000 data dengan 0 data duplicate dan 40 data kosong pada colom Description.
sumber dataset (https://www.kaggle.com/datasets/ishikajohari/best-books-10k-multi-genre-data/data)

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Best Books dataset adalah sebagai berikut:
- Book             : Nama buku.
- Author           : Nama penulis buku.
- Description      : deskripsi buku yang di mention di goodreads.
- Genres           : genre buku berdasarkan clasifikasi di goodreads.
- Average Rating   : rating rata-rata yang diberikan user.
- Number of Rating : jumlah user yang memberikan rating.
- Url              : link untuk mengakses informasi lebih detail

untuk memahami data terdapat langkah yang akan dilakukan :
1. mencari tahu daftar colom apa saja yang terdapat pada dataframe.
2. melihat jenis data yang terdapat pada colom
3. melihat statistik deskriptif pada dataframe
4. melakuakn pengecekan apakah terdapat nilai yang sama atau duplicated
5. melakukan drop nilai pada column genres yang memiliki nilai []
6. melakukan pengecekan apakah terdapat nilai Na
7. melakukan drop nilai Na
8. membuat plot dengan nilai X adalah rating dan Y adalah jumlah buku

## Data Preparation

1. membuat variable baru dengan merubah data menjadi list dari colom Book dan Genres
2. Membuat dataframe baru dan merubah nama colom Book menjadi book_nam dan Genres menjadi genre

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

Implikasi rekomendasi buku antara lain:
1. memberikan rekomendasi buku sesuai dengan buku terakhir yang kita baca
2. mencari buku yang mempunyai genre yang sama dengan buku yang dibaca

Apakah sudah menjawab problem statment?
- apakah genre paling populer ?
  genre yang paling populer berdasarkan dataset goodreads adalah Fiction disusul oleh Fantasy dan selanjutnya adalah Nonfiction.
- siapakah penulis buku dengan jumlah terbanyak? dan buku apa yang paling populer berdasarkan Avg_Rating yang ditulis oleh penulis tersebut?
  Nama penulis buku terbanyak adalah Stepen King dengan jumlah buku sebanyak 57 dengam buku paling tinggi ratingnya adalah The Dark Tower Series: Books 1-7
- buku apa yang memiliki Avg_Rating paling tinggi dengan Num_Rating diatas 500.000? dan buku apa yang memiliki cosine_similarity yang paling tinggi dengan buku Avg_rating tertinggi tersebut?
  buku dengan rating paling tinggi dengan jumlah user yang memberikan rating diatas 500.000 adalah A Court of Mist and Fury (A Court of Thorns and Roses, #2) dan buku dengan cosine_similarity paling tinggi dengan A Court of Mist and Fury (A Court of Thorns and Roses, #2) adalah The midnight Library dengan nilai cosine similarity sebesar 0.82 .

Apakah berhasil mencapai goals yang diharapkan?
- Goal pertama : Berhasil didapatkan bahwa genre Fiction adalah genre paling populer berdasarkan Goodreads.
- Goal Kedua   : Berhasil mengetahui bahwa Stepen king adalah author dengan buku terbanyak sebanyak 57 buku.
- Goal Ketiga  : Mengetahui bahwa the midnight library adalah buku yang paling direkomendasikan sesuai dengan buku dengan rating tinggi yaitu A Court of Mist and Fury (A Court of Thorns and Roses, #2).
