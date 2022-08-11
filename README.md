# Laporan Proyek Machine Learning - Habib Azizul Haq

## Project Overview

Anime sebuah film animasi dari Jepang yang sangat populer dan mungkin banyak dari sebagian kalian yang merasa nostalgia ketika waktu kecil sering menontonnya di televisi. Sekarang untuk menontonnya banyak di antara kita yang sering mengunjungi situs-situs *streaming* seperti Bsite, iQIYI, atau bahkan di kanal Youtube seperti Ani-One, Muse Indonesia dan Muse Asia.

Kepopuleran Anime saat memang lagi tinggi-tingginya, hal ini disebabkan banyak judul-judul besar Anime yang sudah punya basis penggemar yang besar, di musim panas 2022 ini banyak yang mendapat lanjutan musim keduanya bahkan Anime dengan judul Overlord mendapat kelanjutan musim keempat, dimana kelanjutan series ini sangat di tunggu-tunggu, perilisan musim keempat ini juga di iringi dengan rilisnya volume terbaru dari Light Novel Overlord yaitu volume 15 dan 16, tentu ini makin menambah *hype* dari judul Anime ini.

![image](https://user-images.githubusercontent.com/43197282/182755994-e4e082a1-d997-4b59-bffd-f675c4973c1b.png)
![image](https://user-images.githubusercontent.com/43197282/182756138-d9a75610-75c8-4c5a-a645-f3c4694ab197.png)
![image](https://user-images.githubusercontent.com/43197282/182756296-1afc570b-09c7-456c-a2ce-12fa73adf741.png)

Melihat tingginya kepopuleran yang terjadi sekarang juga membawa berkah tersendiri bagi industri *streaming* untuk medulang cuan yang banyak. Dengan adanya situs-situs streaming seperti disebutkan diatas membantu kita sebagai orang yang sedang mencari Anime untuk menonton secara **Legal**. Lantas ketika Anda mengunjungi katakanlah kanal youtube Muse Indonesia dan meng-klik salah-satu judul Anime disana, Anda akan melihat tampilan video lain yang serupa ketika Anda menggeser kebawah. Pernahkan Anda berfikir bagaimana video dibawah tersebut bisa muncul? Apa mereka muncul secara acak? *Tentu tidak demikian ferguso*.

Video dibawah muncul melalui serangkaian algoritma yang sering di sebut dengan sistem rekomendasi, ia merekomendasikan sebuah video yang mungkin menarik bagi Anda, supaya Anda meng-klik video tersebut. Lantas sekarang bayangkan Anda orang di bagian marketing dari salah-satu situs *streming* diatas, tentu Anda ingin meningkatkan pengalaman pengguna ketika menggunakan situs Anda, supaya pengguna merasa nyaman dan ingin berlangganan tetap di situs *streaming* Anda.

Sekarang Anda mengajukan sebuah proposal kepada atasan Anda untuk membuat sistem rekomendasi dan menerapkannya di situs *streaming*, Anda mengatakan alasan penting mengapa perlu sistem rekomendasi di situs *streaming* saat ini:

- Untuk meningkatkan kepusaan pengguna, sehingga pengguna betah berlama-lama mengunjungi situs *streaming* Anime perusahaan.

Dengan harapan bahwa hal itu bisa meningkatkan keuntungan bagi perusahaan dan tentu saja jika ini sukses di implementasikan dan menarik lebih banyak pelanggan maka tentu gaji Anda akan di naikkana oleh perusahhana Anda, karena kontribusi Anda.

- [Pentingnya Sistem Rekomendasi](https://fib.bunghatta.ac.id/index.php/en/article/209-pentingnya-sistem-informasi-di-era-digital#:~:text=Dengan%20menerapkan%20sebuah%20sistem%20informasi,dalam%20pasar%20yang%20selalu%20berubah.)

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:

- Saat ini Anda belum memiliki model machine learning untuk memberikan rekomendasi Anime.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:

- Anda ingin menghasilkan model machine learning yang bisa memberikan rekomendasi Anime.

### Solution statements:

- Kita akan menggunkana pendekatan Sistem Rekomendasi: Content-based Filtering, untuk memberikan rekomendasi Anime.
- Kita akan menggunkana metrik `Precision` untuk menilai seberapa akurat hasil rekomendasi dari sistem rekomendasi yang kita buat.

## Data Understanding

Kita akan menggunkan dataset yang berisi 23 variabel yang sering muncul ketika Anda melihat deskripsi suatu Anime di situs MyAnimeList [1]. File dataset yang akan kita gunakan dalam proyek ini adalah anime_list.csv yang berisi 23 vaiabel dan 18.000 judul Anime.

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

1.  Kita akan mengubah nilai score yang -1 menjadi kosong supaya bisa kita hapus.
2.  Kita akan menghapus data yang kosong

**Langsung saja kita mulai dari yang pertama yaitu:**

**1.  Kita akan mengubah nilai score yang -1 menjadi kosong supaya bisa kita hapus.**

Penghapusan ini penting mengingat nilai -1 terjadi karena user menonton anime tersebut tapi tidak memberikan score, maka dari itu supaya nilai -1 ini tidak mempengaruhi sitem rekomendasi kita, kita akan menggantinya dengan nilai NaN / kosong supaya bisa kita hapus baris data yang mengandung nilai -1.

Sebelum itu kita lihat dulu nilai ada berapa jumlah nilai -1 nya.

Kita akan melihatnya dengan kode `data_anime.loc[(data_anime['score']==-1)]`. 
- `.loc[]` adalah akses grub baris dan kolom meurut label, dimana kita ingin mengakses kolom score dari data_anime.
- `==-1` adalah parameter untuk hanya menampilkan kolom score dengan nilai yang sama dengan -1.

![image](https://user-images.githubusercontent.com/43197282/183365451-fd965f7e-204f-406f-8ee1-0b2d008a7e5d.png)
![image](https://user-images.githubusercontent.com/43197282/183365575-5ade9c68-d1f8-4e8c-8c28-443655a807f3.png)

Dari hasil kode diatas kita bisa lihat bahwa:
- Ada 5.296 baris yang mengandung nilai -1 di kolom score.

Lanjut keproses mengubah nilai -1 menjadi Nan.

- Pertama kita buat variabel baru dengan nama `anime_clean` yang akan diisi dengan data_anime dengan kode `anime_clean = data_anime.copy()`.

- Setelah itu kita mengganti nilai -1 dengan fungsi `.replace({-1: np.nan}, inplace=True)`, nilai di dalam `{-1: np.nan}` berarti -1 diganti dengan nilai NaN dan `inplace=True` supaya jika kita berhasil mengganti nilai rating_user mengembalinkan nilai None / tidak ada.

- Setelah itu kita panggil variabel `anime_clean` untuk melihat apakah sudah berubah?

![image](https://user-images.githubusercontent.com/43197282/183369495-c059cfb1-5239-412a-b812-5dfe27814b26.png)

Hasil di atas menunjukkan bahwa kita berhasil merubah nilai yang tadinya -1 menjadi NaN atau kosong. Sebelum lanjut kita cek lagi apakah nilai -1 nya masih ada atau tidak dengan kode `anime_clean.loc[(anime_clean['score']==-1)]`

![image](https://user-images.githubusercontent.com/43197282/183370804-a58230b4-77c4-428b-916e-0c8c4a3bb87d.png)

Dari hasil diatas kita bisa yakin bahwa sudah tidak ada nilai -1 di kolom score. Selanjutnya kita akan melanjutkan ke proses selanjutnya.

**2.  Kita akan menghapus data yang kosong.**

Pertama kita cek lagi data yang kosong kita dengan kode `anime_clean.isnull().sum()`.

![image](https://user-images.githubusercontent.com/43197282/183380521-21fc78e6-fa55-450b-8a21-6557b0209fb1.png)

Dari hasil output diatas kita jadi tau bahwa ada tambahan data kosng yaitu pada kolom score sebanyak 5296.

Setelah berhasil kita hapus data kosong dengan kode `anime_clean = anime_clean.dropna(axis = 0, how ='any')`.

- Dimana `axis = 0` berarti hanya mengapus baris yang mengandung nilai kosong.
- Sedang `how = 'any'` berarti akan menghapus juga jika ada baris atau kolom yang nilainya kosong semua.

Setelah kita jalankan kode diatas kita cek lagi apakah datanya yang kosong sudah terhapus? Kita cek dengan kode `anime_clean.isnull().sum()`.

![image](https://user-images.githubusercontent.com/43197282/183386661-7f4c198d-5a77-4d65-aae3-b98137050c72.png)

Hasilnya sudah tidak ada lagi data kosong di variabel data_anime_clean.

Sebelum lanjut ke proses Modeling, kita akan menghapus beberapa fitur di variabel data_anime_clean.

Kita devinisikan variabel baru dulu dengan nama data_anime_cleaned yang akan menampung data dari data_anime_clean yang sudah di hapus beberapa kolomnya.

Kita akan menghapus kolom:
- duration.
- airing.
- aired.
- background.
- premiered.
- licensors.
- producers.
- status.

Setelah itu kita panggi lagi data_anime_cleaned untuk mengetahui apa isinya.

![image](https://user-images.githubusercontent.com/43197282/184055662-9bb772d7-4529-4c0b-8a94-b3c28f41e139.png)

Seperti yang kita lihat kolom yang tadi kita hapus sudah tidak ada, hanya menyisakan 12847 baris dan 15 kolom.

## Modeling

Pada tahap modeling kita akan menggunakan pendekatan Content-based Filtering, pendekatan ini memiliki beberapa kelebihan diantaranya:

- Pengguna tau bahwa ada Anime dengan fitur yang sama namun dengan judul yang berbeda.

Jika ada kelebihan tentu ada kekurangan ya, kekurangan dari pendekatan ini adalah:

- Hanya berfokus pada kemiripan kata kunci.

Baik, untuk menerapkan pendekatan Content-based Filtering kita akan melakuka:

1. Kita akan mencari representasi fitur synopsis menggunkana `TfidfVectorizer`

2. Mencari pasangan rekomendasi menggunkan metrik pairwise yang berfungsi untuk representasi koleksi vektor menggunakan `sigmoid_kernel`.

**Langsung saja kita mulai dari yang pertama yaitu:**

**1. Kita akan mencari representasi fitur synopsis menggunkana `TfidfVectorizer`**
 
Pertama kita import dulu `TfidfVectorizer` kemudian masukkan ke variabel tfv,
setelah itu kita set variabel dari `TfidfVectorizer`-nya dengan keterangan seperti ini:
- `min_df=5` : untuk mengabaikan kata/istilah yang jarang muncul.
- `max_feature=None` : supaya tidak membuat kosakata yang dengan berdasar frekuensi kemunculan teratas.
- `strip_accent='unicode'` : untuk menormalisasi karakter, kita memilih 'unicode' karena berkerja pada karakter apapun.
- `analyzer='word'` : untuk menggunkan ngram kita set analyzer ke word.
- `token_pattern=r'\w{1,}'` : Ekspresi reguler yang menunjukkan apa yang merupakan sebuah "token", hanya digunakan jika analyzer == 'word'.
- `ngram_range=(1, 3)` : Batas bawah dan batas atas kisaran nilai-n untuk n-gram berbeda yang akan diekstraksi.
- `stop_word='english'` : untuk mendeteksi kata akhiran dalam bahasa Inggris.

Setelah itu kita buat variabel dengan nama synopsis_str yang akan menampung fitur synopsis dari variabel anime_cleaned.

Selanjutnya kita lakukan proses fit, untuk mempelajari kosa kata dan Inverse Document Frequency.

Setelah itu kita lihat ukurannya dengan fungsi `.shape`.

![image](https://user-images.githubusercontent.com/43197282/184058588-810799f9-4137-4dc5-a730-346273addb67.png)

Dan hasilnya seperti diatas.

**2. Mencari pasangan rekomendasi menggunkan metrik pairwise yang berfungsi untuk representasi koleksi vektor menggunakan `sigmoid_kernel`.**

Kita import dulu metriknya, kita buat variabel sig untuk menampung hasil keluaran dari `sigmoid_kernel`, setelah itu kita masukkan variabel tfv_matrik yg berisi hasil dari proses fit_transform.

Setelah itu kita panggil untuk melihat seperti apa bentuknya.

![image](https://user-images.githubusercontent.com/43197282/184058683-1e930ab4-5e10-43fd-8b9c-1235223da57f.png)

`sigmoid_kernel` menghasilkan keluaran berupa array multi dimensi yang akan kita cocokan nanti saat proses memberikan rekomendasi.

Sekarang karena kita buat variabel baru bernama data_anime_index untuk menerapkan index pada 'title'.

Dan selanjutnya kita panggil variabel data_anime_index.

![image](https://user-images.githubusercontent.com/43197282/184058848-114cce8b-eb73-4a70-aea1-db5c80b61000.png)

Seperti yang kita lihat di atas angka di sebelah kanan adalah index dari title anime.

Lanjut kita buat fungsi yang akan memberikan rekomendasi dengan paramenter title. Dengan urutan
    1. Dapatkan indeks yang sesuai dengan title asli.
    2. Dapatkan skor kesamaan pairwsie.
    3. Urutkan keluaran film
    4. Pilih dari 5 Anime paling mirip
    5. Mengeluarkan indeks Anime
    6. Menampilkan 5 anime paling mirip
    
    

## Evaluation

Ditahap kita akan mengevaluasi model sistem rekomendasi kita dengan metrik `Precision`.

Pertama kita coba panggil fungsi rekomendasinya seperti kode di bawah, untuk menghasilkan rekomendasi dan setelah itu kita hitung menggunkaan metrik `Precision`.

Kita coba dulu untuk melihat hasil keluarannya.

![image](https://user-images.githubusercontent.com/43197282/184059142-a3d89e42-acfd-45da-9ecd-05365a3cd0ab.png)

![image](https://user-images.githubusercontent.com/43197282/184059182-e4cee13b-0d6c-41e0-941e-4e3a622accb9.png)


Dari dua hasil keluaran diatas kita akan menghitungnya dengan rumus Precision = jumlah Anime yang relevan dibagi jumlah Anime yang direkomendasikan[2]. Berikut rumusnya.

![image](https://user-images.githubusercontent.com/43197282/183836103-2789e957-e682-4e93-b714-2075160a4d33.png)

1. Hasil rekomendasi untuk 'Coboy Bebop' adalah:
    
    Precission = 4/5.

    Jadi presisinya = 80%

2. Hasil rekomendasi untuk 'Mobile Suit Gundam' adalah:

    Precission = 5/5.

    Jadi presisinya = 100%

## Conclusion

Akhirnya kita berhasil membuat sistem rekomendasi Anime dan mengujinya dengan hasil:
1. 80%.
2. 100%.

Jika kita rata-rata maka kita mendapat hasil akurasi 90%.

## Reference
[1](https://id.wikipedia.org/wiki/MyAnimeList)
[2](https://www.dicoding.com/academies/319/discussions/134402)






