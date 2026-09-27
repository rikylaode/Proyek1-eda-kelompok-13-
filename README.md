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

## 3 Temuan Utama
1. **Ketidakseimbangan Sebaran Panjang URL (Right-Skewed):** Baik panjang total URL (`length_url`) maupun panjang nama domain (`length_hostname`) memiliki distribusi miring ke kanan. Nilai rata-rata jauh lebih besar daripada median akibat adanya pencilan (*outliers*) bernilai ekstrem pada URL tertentu.
2. **Karakteristik URL Phishing:** URL kategori *phishing* cenderung memiliki variasi panjang karakter yang jauh lebih tinggi dan jumlah titik (`nb_dots`) yang lebih banyak dibandingkan URL *legitimate*.
3. **Keseimbangan Kelas Data:** Dataset ini memiliki jumlah data yang seimbang sempurna (50% *legitimate* dan 50% *phishing*), sehingga siap digunakan untuk pemodelan tanpa membutuhkan teknik *resampling*.

## Kesimpulan
Bisa dilihat dari hasil temuan utama dataset phising ini bahwa URL dari situs *phising* memiliki banyak karakteristik menonjol yang sangat membedakannya dengan URL situs *legitimate*, seperti halnya panjang URL, nama domain, jumlah titik yang lebih banyak, karakter yang bervariasi dan panjang, serta yang lain. 

## Kesimpulan
Berdasarkan hasil analisis statistik deskriptif terhadap dataset phishing yang terdiri dari 11.430 URL, dapat disimpulkan beberapa poin penting yang membedakan secara signifikan antara URL situs phishing dan legitimate:

1. Distribusi Panjang URL dan Hostname yang Miring ke Kanan (Right-Skewed)
Analisis terhadap variabel length_url dan length_hostname menunjukkan bahwa distribusinya tidak normal, melainkan miring ke kanan. Hal ini dibuktikan dengan nilai Mean yang jauh lebih besar daripada Median (contoh: Mean length_url = 61.13, Median = 47.0). Ini mengindikasikan adanya sejumlah besar data dengan nilai ekstrem (outliers) atau URL yang sangat panjang. URL dengan panjang yang ekstrem ini adalah ciri khas dari situs phishing, di mana pelaku kejahatan siber sering kali menambahkan banyak karakter, subdomain, atau parameter palsu untuk mengelabui pengguna dan sistem deteksi otomatis.
Karakteristik Unik pada URL Phishing
Situs phishing cenderung memiliki karakteristik yang lebih kompleks dan tidak wajar dibandingkan situs legitimate. Hal ini terlihat dari:

2. Panjang URL dan Hostname: URL phishing memiliki rata-rata dan variasi panjang karakter yang lebih tinggi. Situs legitimate umumnya menggunakan URL yang pendek, jelas, dan mudah diingat, sedangkan phishing seringkali menggunakan URL yang panjang dan rumit untuk menyembunyikan domain asli atau meniru situs resmi.
Jumlah Titik (.): Variabel nb_dots juga menunjukkan bahwa URL phishing memiliki jumlah titik yang lebih banyak. Jumlah titik yang berlebihan (seperti pada http://www.netflix.com.akun-update.login-bantuan.id/) adalah indikasi kuat adanya subdomain bertingkat yang tidak wajar, yang sering digunakan untuk membuat URL terlihat seolah-olah merupakan bagian dari situs resmi.
3. Keseimbangan Kelas Data yang Sempurna
Dataset ini memiliki distribusi kelas yang sangat seimbang, dengan 50% data merupakan URL legitimate dan 50% lainnya adalah URL phishing (masing-masing 5.715 data). Keseimbangan ini merupakan keuntungan besar untuk tahap pemodelan klasifikasi selanjutnya, karena model tidak akan bias terhadap salah satu kelas dan tidak memerlukan teknik resampling (seperti oversampling atau undersampling) untuk menangani ketidakseimbangan data.
4. Kualitas Data yang Baik
Proses pemeriksaan data menunjukkan bahwa dataset ini tidak memiliki nilai yang kosong (missing value) maupun data duplikat. Hal ini menandakan bahwa dataset sudah bersih dan siap digunakan untuk analisis lebih lanjut tanpa memerlukan tahap pembersihan data yang kompleks.
5. Implikasi untuk Deteksi Phishing
Secara keseluruhan, analisis ini berhasil mengidentifikasi fitur-fitur statistik yang sangat relevan untuk membedakan URL phishing dan legitimate. Fitur-fitur seperti length_url, length_hostname, dan nb_dots dapat menjadi prediktor yang kuat dalam membangun model machine learning untuk deteksi phishing. Pemahaman mendalam tentang pola-pola ini menjadi fondasi penting dalam pengembangan sistem keamanan siber yang lebih proaktif dan akurat dalam mengidentifikasi ancaman phishing sebelum korban terjebak.

