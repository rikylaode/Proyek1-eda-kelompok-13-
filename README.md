# Proyek1-eda-kelompok-13
# Analisis Statistik Deskriptif Karakteristik URL pada Dataset Phishing

## Identitas Kelompok
* **Nomor Kelompok:** Kelompok 13
* **Anggota Kelompok:**
1.  La Ode Muh. Baharizqi Ma'rufi - 5027261086
2.  Marsha Daruningtyas - 5027261056
3.  Farras Hazim Ramadhan - 5027261132

---

## Topik & Sumber Dataset
* **Topik:** Keamanan Siber / Klasifikasi URL Phishing vs Legitimate
* **Sumber Dataset:** Kaggle - Web Phishing Detection Dataset
* **Link Dataset:** https://www.kaggle.com/datasets/shashwatwork/web-page-phishing-detection-dataset
* **Lisensi:** Open Data Commons Attribution License (ODC-By)
* **Kontributor data:** Abdelhakim Hannousse, Salima Yahiouche
* **Tanggal publish:** 26 Juni 2021 (V3)
* **Sumber data yang di ekstrak:**
a. 56 from structure and syntax of URLs
b. 24 from the content of their correspondent pages
c. 7 from querying external services

| | Arti | Jenis Variabel | Skala | Contoh |
|---|---|---|---|---|
| **length_url** | Panjang karakter URL | Kuantitatif | Rasio | 37 |
| **length_hostname** | Panjang host URL |Kuantitatif | Rasio | 19 |
| **nb_dots** | Jumlah karakter titik di URL | Kuantitatif | Rasio | 3 |

## Latar Belakang & Pertanyaan Analisis

### Latar Belakang
Dataset ini sangat menarik untuk dianalisis karena ancaman kejahatan siber berbasis *phishing* kian marak dan makin sulit dideteksi secara kasat mata. Dataset ini merangkum **11.430 baris data URL** yang diekstraksi ke dalam **89 fitur teknis**, mencakup atribut struktur URL (seperti panjang nama domain dan jumlah karakter khusus), karakteristik HTML/halaman web, hingga indikator pihak ketiga seperti indeks Google dan nilai PageRank. Mempelajari pola statistik dari atribut-atribut tersebut memungkinkan kita untuk memahami perbedaan mendasar antara situs web resmi (*legitimate*) dan situs kejahatan (*phishing*), yang menjadi pijakan awal penting sebelum membangun model klasifikasi otomatis.

### Pertanyaan Analisis (Statistik Deskriptif)
1. Bagaimana karakteristik sebaran (pemusatan dan penyebaran) dari variabel numerik utama seperti panjang URL (`length_url`), panjang hostname (`length_hostname`), dan jumlah titik (`nb_dots`) pada dataset ini?
2. Apakah URL dari situs *phishing* cenderung memiliki ukuran karakter (`length_url`) yang lebih panjang dan variasi yang lebih tinggi dibandingkan dengan URL situs aman (`legitimate`)?
3. Bagaimana distribusi dan proporsi keseimbangan kelas antara URL *phishing* dan URL *legitimate* pada variabel target (`status`)?

---
## Cara Instalasi 
Gunakan environment mata kuliah:
```bash
conda create -n statprob python=3.11 -y
conda activate statprob
conda install -c conda-forge jupyter pandas matplotlib seaborn -y
```
Jalankan :
```bash
jupyter notebook
```
Jika ingin membukanya lagi, maka cara aktifkan kembali Jupyter Notebook yaitu:
```bash
conda activate statprob
jupyter notebook
```
Kemudian buat Folder Baru: `proyek1-eda-kelompok-13`

Jangan lupa download library yang dibutuhkan
* pandas
* matplotlib
* seaborn

Cara mendownload library
```bash
conda install library
```
Setelah prosesnya selesai, akan muncul perintah:
```bash
Proceed ([y]/n)? 
```
Ketik "y", lalu akan muncul tulisan:
```bash
Downloading and Extracting Packages:

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
WARNING conda.conda_pypi.main:notify_externally_managed_future(156):
  Did you know? You can install many PyPI packages with conda
  using the conda-pypi beta. Get started:
    https://docs.conda.io/projects/conda/en/stable/new-features.html
```
Ini menandakan kalau library pythonnya sudah terinstall. Jangan lupa lakukan hal yang sama ke library lainnya.

## Cara Menjalankan Notebook
1. Clone repositori ini ke komputer lokal:
   ```bash
   git clone [https://github.com/username/proyek1-eda-kelompok-13.git](https://github.com/username/proyek1-eda-kelompok-13.git)








## Catatan
**1. length_url (Panjang URL)**

length url artinya seberapa panjang url nya. situs web biasanya menggunakan url yang mudah diingat, sedangan pelaku phising menggunakan url yang lebih panjang karena memmuat sesuatu (berupa kata kata palsu atau kode unik untuk menipu korban). karena panjang url terlalu tinggi, sistem akan mendeteksinya sebagai ancaman (dalam kasus ini link phising). contoh: https://google.com vs http://com-security-update.xyz karena terlalu panjang, maka sistem akan mendeteksinya sebagai sebuah ancaman.

**2. length hostname**

length hostname artinya nama khusus di bagian hostname saja (domain utama + subdomain). Sama seperti URL, pelaku phising membuat length hostname yang panjang agar menyerupai perusahaan asli. Length hostname yang panjang juga mengindikasikan adanya penipuan (dalam kasus ini phising) contoh: ://tokopedia.com vs ://paypal-update-security-login-system.com link kedua memiliki length hostname yang terlalu panjang, oleh karena itu sistem mendeteksinya sebagai phising.

**3. nb_dots**

nb_dots artinya jumlah karakter titik (.) yang ada di url. website pada umumnya menggunakan 3 karakter titik saja (seperti ://domain.com). namun, pelaku phising menggunakan subdomain dengan banyak titik untuk mengelabuhi targetnya (misalnya: ://konfirmasi-data.com). Jika jumlah dots terlalu banyak, maka sistem akah mendeteksi bahwa link ini adalah phising

## Bagaimana cara menghitung url length, hostname length dam nb dots? gini caranya:

1. url length cukup dihitung semua karakternya (termasuk karakter khusus seperti (.), (/), (:), dll contoh: https://www.instagram.com/accounts/login -> totalnya ada 40 karakter https://instagram-security-verifications-panel.net/secure-login

2. hostname length sebelum menghitung, pisahkan nama domain utama dari struktur URL, kemudian hitung jumlah karakternya contoh: https://www.bi.go.id/id/default.aspx -> hapus "https://" dan "/id/default.aspx" dari url utama lalu hitung (www.bi.go.id totalnya ada 12) https://login.facebook.com.akun-terverifikasi.id/masuk/aman.html -> pisahkan "https://" dan "/masuk/aman.html" dari url utama lalu hitung (login.facebook.com.akun-terverifikasi.id totalnya ada 40)

3. nb dots cukup hitung titiknya saya(bukan titik dua(:) ya) contoh: https://www.netflix.com -> ada 2 titik http://www.netflix.com.akun-update.login-bantuan.id/session/index.php -> ada 6 titik



## Data yang Kita Peroleh Untuk Pengecekan
Untuk dataset `dataset_phishing.csv`, Ringkasan statistik:
| | length_url | length_hostname | nb_dots |
|---|---|---|---|
| **Mean** | 61.126684 | 21.090289 | 2.480752 |
| **Median** | 47.000000 | 19.000000 | 2.000000 |
| **Mode** | 26.000000 | 16.000000 | 2.000000 |
| **Minimum** | 12.000000 | 4.000000 | 1.000000 |
| **Maximum** | 1641.000000 | 214.000000 | 24.000000 |
| **Range** | 1629.000000 | 210.000000 | 23.000000 |
| **Variance** | 3057.793382 | 116.147416 | 1.876040 |
| **Standar Deviasi** | 55.297318 | 10.777171 | 1.369686 |
| **Q1** | 33.000000 | 15.000000 | 2.000000 |
| **Q3** | 71.000000 | 24.000000 | 3.000000 |
| **IQR** | 38.000000 | 9.000000 | 1.000000 |

Dari 87 fitur yang tersedia, dipilih length_url, length_hostname, dan nb_dots karena ketiganya bersifat numerik kontinu sehingga langsung bisa dianalisis dengan statistik deskriptif seperti mean, median, dan variance. Ketiga variabel ini juga saling melengkapi, di mana length_url mewakili panjang keseluruhan URL, length_hostname mewakili panjang domain, dan nb_dots mewakili struktur titik/subdomain. Selain itu, ketiganya merupakan indikator klasik yang paling sering digunakan untuk membedakan URL phishing dan legitimate, mudah divisualisasikan dalam bentuk histogram maupun boxplot, serta menghindari fitur biner atau rasio yang kurang cocok untuk analisis deskriptif dasar.

## 3 Temuan Utama
1. **Ketidakseimbangan Sebaran Panjang URL (Right-Skewed):** Baik panjang total URL (`length_url`) maupun panjang nama domain (`length_hostname`) memiliki distribusi miring ke kanan. Nilai rata-rata jauh lebih besar daripada median akibat adanya pencilan (*outliers*) bernilai ekstrem pada URL tertentu.
2. **Karakteristik URL Phishing:** URL kategori *phishing* cenderung memiliki variasi panjang karakter yang jauh lebih tinggi dan jumlah titik (`nb_dots`) yang lebih banyak dibandingkan URL *legitimate*.
3. **Keseimbangan Kelas Data:** Dataset ini memiliki jumlah data yang seimbang sempurna (50% *legitimate* dan 50% *phishing*), sehingga siap digunakan untuk pemodelan tanpa membutuhkan teknik *resampling*.

## Kesimpulan
Dari analisis statistik deskriptif pada 11.430 URL, dapat disimpulkan:

1. **Distribusi miring ke kanan (right-skewed):** Nilai Mean length_url (61.13) jauh lebih besar dari Median (47.0), menandakan adanya outliers berupa URL yang sangat panjang bentuk ciri khas phishing.
2. **URL phishing lebih kompleks:** Memiliki panjang URL, hostname, dan jumlah titik (nb_dots) yang lebih tinggi dibanding situs legitimate. Contoh: https://login.facebook.com.akun-terverifikasi.id/masuk/aman.html. Ini digunakan untuk menyembunyikan domain asli atau meniru situs resmi.
3. **Data seimbang sempurna:** 50% legitimate dan 50% phishing (masing-masing 5.715 data). Tidak perlu teknik resampling untuk pemodelan.
4. **Data bersih:** Tidak ada missing value maupun duplikat, siap digunakan untuk analisis lanjutan.
5. **Implikasi:** Fitur length_url, length_hostname, dan nb_dots dapat menjadi prediktor kuat untuk membangun model machine learning deteksi phishing.
6. **Perbandingan panjang rata rata url antara legitimate dan phising:** 
