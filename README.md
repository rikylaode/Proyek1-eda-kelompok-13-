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

## Cara Menjalankan Notebook
1. Clone repositori ini ke komputer lokal:
   ```bash
   git clone [https://github.com/username/proyek1-eda-kelompok-13.git](https://github.com/username/proyek1-eda-kelompok-13.git)

## Catatan
**1. length_url (Panjang URL)**

Apa itu? Jumlah total karakter yang menyusun sebuah URL, dihitung dari awal (http:// atau https://) sampai karakter terakhir.
Contoh:

https://google.com → 18 karakter
http://shadetreetechnology.com/V4/validation/a111aedc8ae390eabcfa130e041a10a4 → 77 karakter

**2. length_hostname (Panjang Hostname)**

Apa itu? Jumlah karakter pada bagian hostname saja, yaitu nama domain utama + subdomain, tanpa http://, path, atau parameter.
Cara hitung: Ambil bagian setelah :// sampai sebelum / pertama.
Contoh:

https://www.bi.go.id/id/default.aspx → hostname = www.bi.go.id → 12 karakter
https://login.facebook.com.akun-terverifikasi.id/masuk/aman.html → hostname = login.facebook.com.akun-terverifikasi.id → 40 karakter

**3. nb_dots (Jumlah Titik)**

Apa itu? Jumlah karakter titik (.) yang ada di dalam URL. Titik di sini hanya titik pemisah domain, bukan titik dua (:) atau titik di path file.
Contoh:

https://www.netflix.com → 2 titik
http://www.netflix.com.akun-update.login-bantuan.id/session/index.php → 6 titik


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
2. **URL phishing lebih kompleks:** Memiliki panjang URL, hostname, dan jumlah titik (nb_dots) yang lebih tinggi dibanding situs legitimate. Contoh: http://shadetreetechnology.com/V4/... (baris ke-2 dataset). Ini digunakan untuk menyembunyikan domain asli atau meniru situs resmi.
3. **Data seimbang sempurna:** 50% legitimate dan 50% phishing (masing-masing 5.715 data). Tidak perlu teknik resampling untuk pemodelan.
4. **Data bersih:** Tidak ada missing value maupun duplikat, siap digunakan untuk analisis lanjutan.
5. **Implikasi:** Fitur length_url, length_hostname, dan nb_dots dapat menjadi prediktor kuat untuk membangun model machine learning deteksi phishing.
