# Laporan Proyek Machine Learning - Habib Azizul Haq

## Project Overview

Pada bagian ini, Kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.

Anime sebuah film animasi dari Jepang yang sangat populer dan mungkin banyak dari sebagian kalian yang merasa nostalgia ketika waktu kecil sering menontonnya di televisi. Sekarang untuk menontonnya banyak di antara kita yang sering mengunjungi situs-situs *streaming* seperti Bsite, IQiy, atau bahkan di kanal Youtube seperti Ani-One, Muse Indonesia dan Muse Asia.

Kepopuleran Anime saat memang lagi tinggi-tingginya, hal ini disebabkan banyak judul-judul besar Anime yang sudah punya basis penggemar yang besar, di musim panas 2022 ini banyak yang mendapat lanjutan musim keduanya bahkan Anime dengan judul Overlord mendapat kelanjutan musim keempat, dimana kelanjutan series ini sangat di tunggu-tunggu, perilisan musim keempat ini juga di iringi dengan rilisnya volume terbaru dari Light Novel Overlord yaitu volume 15 dan 16, tentu ini makin menambah *hype* dari judul Anime ini.

![image](https://user-images.githubusercontent.com/43197282/182755994-e4e082a1-d997-4b59-bffd-f675c4973c1b.png)
![image](https://user-images.githubusercontent.com/43197282/182756138-d9a75610-75c8-4c5a-a645-f3c4694ab197.png)
![image](https://user-images.githubusercontent.com/43197282/182756296-1afc570b-09c7-456c-a2ce-12fa73adf741.png)

Melihat tingginya kepopuleran yang terjadi sekarang juga membawa berkah tersendiri bagi industri *streaming* untuk medulang cuan yang banyak. Dengan adanya situs-situs streaming seperti disebutkan diatas membantu kita sebagai orang yang sedang mencari Anime untuk menonton secara **Legal**. Lantas ketika Anda mengunjungi katakanlah kanal youtube Muse Indonesia dan meng-klik salah-satu judul Anime disana, Anda akan melihat tampilan video lain yang serupa ketika Anda menggeser kebawah. Pernahkan Anda berfikir bagaimana video dibawah tersebut bisa muncul? Apa mereka muncul secara acak? *Tentu tidak demikian ferguso*.

Video dibawah muncul melalui serangkaian algoritma yang sering di sebut dengan sistem rekomendasi, ia merekomendasikan sebuah video yang mungkin menarik bagi Anda, supaya Anda meng-klik video tersebut. Lantas sekarang bayangkan Anda orang di bagian marketing dari salah-satu situs *streming* diatas, tentu Anda ingin meningkatkan pengalaman pengguna ketika menggunakan situs Anda, supaya pengguna merasa nyaman dan ingin berlangganan tetap di situs *streaming* Anda.

Sekarang Anda mengajukan sebuah proposal kepada atasan Anda untuk membuat sistem rekomendasi dan menerapkannya di situs *streaming*, Anda mengatakan alasan penting mengapa perlu sistem rekomendasi di situs *streaming* saat ini:

- Untuk meningkatkan kepusaan pengguna, mengingat setiap pengguna belum tentu tau banyak judul Anime.
- Untuk memahami yang lebih baik tentang preferensi pengguna.

Dengan harapan bahwa hal itu bisa meningkatkan keuntungan bagi perusahaan dan tentu saja jika ini sukses di implementasikan dan menarik lebih banyak pelanggan maka tentu gaji Anda akan di naikkana oleh perusahhana Anda, karena kontribusi Anda.

- [Referensi]()




**Rubrik/Kriteria Tambahan (Opsional):**

- Jelaskan mengapa proyek ini penting untuk diselesaikan.
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
- Referensi

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:

- Anda belum memiliki sistem rekomendasi, yang memberikan rekomendasi-rekomendasi Anime yang mungkin di sukai oleh pengguna di situs *streaming* Anda.
- Anda belum mengetahui preferensi dari pengguna situs *streaming* Anda.
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:

- Anda ingin meningkatkan pengalaman pengguna dengan memberikan rekomendasi-rekomendasi Anime yang mungkin di sukai oleh pengguna di situs *streaming* Anda.
- Anda ingin mengetahui preferensi dari pengguna situs *streaming* Anda.

### Solution statements:

- Kita akan menggunkana pendekatan Sistem Rekomendasi: Content-based Filtering, untuk memberikan rekomendasi Anime.
- Kita akan menggunakan model dengan metrik `cosine_similarity` untuk menentukan kemiripan dari suatu judul Anime dalam memberikan suatu hasil rekomendasi.
- Kita akan menggunkana metrik `Precision` untuk menilai seberapa akurat hasil rekomendasi dari sistem rekomendasi yang kita buat.

## Data Understanding

Kita akan menggunkan dataset yang berisi 23 variabel yang sering muncul ketika Anda melihat deskripsi suatu Anime di situs MyAnimeList[1]. File dataset yang akan kita gunakan dalam proyek ini adalah anime_list.csv yang berisi 23 vaiabel dan 18.000 judul Anime.

Sumber dataset yang akan kita gunakan berasal dari [Kaggle](https://www.kaggle.com/datasets/snehaanbhawal/anime-list-for-recommendation-system-june-2021). Yang di publis oleh [SNEHAAN BHAWAL](https://www.kaggle.com/snehaanbhawal).

**Variabel-variabel pada *Anime List for Recommendation System* dataset adalah sebagai berikut:**

- mal_id : id unik dari situs myanimelist.net yang mengidentifikasi Anime.
- title : Judul dari Anime
- synopsis : Sinopsis, ringkasan singkat yang memberikan gambaran tentang suatu karya.
- background : Latar belakang.
- aired : Rentang waktu anime ditayangkan. contoh format: "30 Sep 2004 sampai 29 Sep 2005".
- airing : Apakah saat ini sedang ditayangkan atau tidak. 0 jika anime telah berakhir 1 jika sedang berlangsung
- duration : Durasi per-episode.
- episodes : Jumlah episode dari suatu judul Anime.
- type : Jenis Anime seperti: ['TV', 'Movie', 'OVA', 'Special', 'ONA', 'Music', 'Unknown']
- favorites : Jumlah orang yang memfavoritkan anime ini.
- members : Jumlah anggota.
- rank : Peringkat per Juni 2021.
- popularity : Peringkat Popularitas per Juni 2021.
- score : Skor rata-rata yang diberikan oleh pengguna.
- scored_by : Jumlah orang yang merating Anime.
- rating : Peringkat diberikan untuk anime.['PG - Anak', 'PG-13 - Remaja 13 tahun ke atas', 'G - Semua Usia', 'R+ - Ketelanjangan Ringan', 'R - 17+','Rx - Hentai' ]
- premiered : Tahun dan musim pemutaran perdana.
- genres : Genre Anime.
- related : Anime terkait.
- status : Status Anime apakah sedang tayang saat ini atau tidak.
- licensors : Nama Pemberi Lisensi.
- producers : Nama Produser.
- studios : Nama studio yang menggerjakan.

Kita akan melakukan sedikit analisis untuk mengethui beberapa hal tentang variabel diatas diantaranya :

1. Kita akan melihat ada berapa jumlah baris dari data dalam tampilan tabel.
2. Kita akan melihat tipe data dari 21 kolom di dataset.
3. Kita akan mengecek deskripsi statistik data.
4. Kita akan melihat apakah ada data yang kosong / tidak ada isinya.
5. Kita akan melihat apakah data kita memiliki outliers.
6. Kita akan melihat variabel apa saja yang memiliki hubungan yang kuat atas klasifikasi harga suatu hp.

Langsung saja kita mulai dari yang pertama yaitu:

**1. Kita akan melihat ada berapa jumlah baris dari data dalam tampilan tabel.**

## Data Preparation

Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional):**

- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling

Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional):**

- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation

Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional):**

- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

## Conclusion


## Reference








