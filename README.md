# Laporan Proyek Machine Learning - Habib Azizul Haq

## Project Overview

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

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:

- Anda belum memiliki sistem rekomendasi, yang memberikan rekomendasi-rekomendasi Anime yang mungkin di sukai oleh pengguna di situs *streaming* Anda.
- Anda belum mengetahui preferensi dari pengguna situs *streaming* Anda.

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

**Langsung saja kita mulai dari yang pertama yaitu:**

**1. Kita akan melihat ada berapa jumlah baris dari data dalam tampilan tabel.**

Kita akan menggunakan menggunakan kode `data_anime`, `data_anime` adalah nama variabel yang kita ganakan saat meload dataset anime_list.csv.

![image](https://user-images.githubusercontent.com/43197282/183354940-0cb40f38-e25e-4b84-b7ad-d4e970ac6c38.png)
![image](https://user-images.githubusercontent.com/43197282/183355330-294e4d4f-7156-4a51-ac5a-e7a0c8a81663.png)

Dari kode `data_anime` kita mendapat informasi:

*   Ada 18.162 baris dataset anime_list.csv kita
*   Dan terdapat 23 kolom

**2. Kita akan melihat tipe data dari kedua dataset kita.**

Kita akan menggunakan `data_anime.info()`, `.info()` akan menampilkan informasi tipe data 7 kolom dataset anime.csv yang kita gunakan.

![image](https://user-images.githubusercontent.com/43197282/183356843-19b0c428-aab4-4a58-b04e-0c2b684b2bfc.png)

Dari *output* `data_anime.info()`, terlihat bahwa:

*   Terdapat 2 kolom dengan tipe data float64, yaitu: rank, score.
*   Terdapat 7 kolom dengan tipe data int64, yaitu: mal_id, airing, episodes, favorites, members, popularity, scored_by.
*   Terdapat 14 kolom dengan tipe data object, yaitu: title, synopsis, background, aired, duration, type, rating, premiered, genres, related, status, licensors, producers, studios.

**3. Kita akan mengecek deskripsi statistik data.**

Kita akan mengeceknya dengan fungsi `describe()`. Sehingga keseluruhan kodenya adalah `data_anime.describe()`, hasilnya seperti dibawah.

![image](https://user-images.githubusercontent.com/43197282/183360030-d52f78e9-7c16-4b14-bd87-e3a13d33913c.png)

Fungsi `describe()` memberikan informasi statistik pada masing-masing kolom, antara lain:

*   Count  adalah jumlah sampel pada data.
*   Mean adalah nilai rata-rata.
*   Std adalah standar deviasi.
*   Min yaitu nilai minimum setiap kolom.
*   25% adalah kuartil pertama. Kuartil adalah nilai yang menandai batas interval dalam empat bagian sebaran yang sama.
*   50% adalah kuartil kedua, atau biasa juga disebut median (nilai tengah).
*   75% adalah kuartil ketiga.
*   Max adalah nilai maksimum.

Perhatikan pada kolom `score` bisa kita lihat bahwa baris Max atau nilai maksimum yang diberikan oleh rata-rata user adalah 9.17 dan baris Min yaitu nilai terendahnya adalah -1. Niali -1 terjadi ketika user melihat Anime tersebut tapi tidak memberikan rating.

**4. Kita akan melihat apakah ada data yang kosong / tidak ada isinya.**

Kita akan mengeceknya dengan fungsi `.isnull().sum()`. Fungsi `.isnull()` akan mengecek apakah ada data kosng pada setiap baris pada semua kolom di dataset kita, kemudian kita gunakan juga fungsi `.sum()` untuk menjumlahnya sehingga hasilnya akan seperti berikut.

![image](https://user-images.githubusercontent.com/43197282/183362724-aee44298-a310-4a7e-9048-0e10dbaa449a.png)

Dari hasil di atas kita tau bahwa di kolom genres memiliki 67 data kosong.

## Data Preparation

Setelah kita melalui proses Data Understanding, kita menjadi lebih paham tentang seperti apa isi dataset kita.

Oleh karena itu di proses ini kita akan melakukan 2 proses yaitu:

1.  Kita akan menghapus nilai score yang -1.
2.  Kita akan melihat apakah ada data yang kosong / tidak ada isinya.

**Langsung saja kita mulai dari yang pertama yaitu:**

**1.  Kita akan menghapus nilai score yang -1.**

Penghapusan ini penting mengingat nilai -1 terjadi karena user menonton anime tersebut tapi tidak memberikan score, maka dari itu supaya nilai -1 ini tidak mempengaruhi sitem rekomendasi kita, kita akan menggantinya dengan nilai NaN / kosong supaya bisa kita hapus baris data yang mengandung nilai -1.

Sebelum itu kita lihat dulu nilai ada berapa jumlah nilai -1 nya.

Kita akan melihatnya dengan kode `data_anime.loc[(data_anime['score']==-1)]`. 
- `.loc[]` adalah akses grub baris dan kolom meurut label, dimana kita ingin mengakses kolom score dari data_anime.
- `==-1` adalah parameter untuk hanya menampilkan kolom score dengan nilai yang sama dengan -1.

![image](https://user-images.githubusercontent.com/43197282/183365451-fd965f7e-204f-406f-8ee1-0b2d008a7e5d.png)
![image](https://user-images.githubusercontent.com/43197282/183365575-5ade9c68-d1f8-4e8c-8c28-443655a807f3.png)

Dari hasil kode diatas kita bisa lihat bahwa:
- Ada 5.296 baris yang mengandung nilai -1 di kolom score.

Pertama kita buat variabel baru dengan nama `anime_clean` yang akan diisi dengan data_anime dengan kode `anime_clean = data_anime.copy()`.

Setelah itu kita mengganti nilai -1 dengan fungsi `.replace({-1: np.nan}, inplace=True)`, nilai di dalam `{-1: np.nan}` berarti -1 diganti dengan nilai NaN dan `inplace=True` supaya jika kita berhasil mengganti nilai rating_user mengembalinkan nilai None / tidak ada.

Setelah itu kita panggil variabel `anime_clean` untuk melihat apakah sudah berubah?

![image](https://user-images.githubusercontent.com/43197282/183369495-c059cfb1-5239-412a-b812-5dfe27814b26.png)

Hasil di atas menunjukkan bahwa kita berhasil merubah nilai yang tadinya -1 menjadi NaN.

![image](https://user-images.githubusercontent.com/43197282/183370804-a58230b4-77c4-428b-916e-0c8c4a3bb87d.png)


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








