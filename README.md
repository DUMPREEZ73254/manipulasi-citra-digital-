# Manipulasi Citra Digital Menggunakan OpenCV dan Python

Tugas Individu - Mata Kuliah Pengolahan Sinyal Digital (PSD)  
Program Studi Teknik Informatika, Universitas Darussalam Gontor

---

## 1. Identitas Mahasiswa
Nama : Adam Rizqi Aghnisyahputra
Semester/Kelas : 5 / Teknik Informatika
NIM : 452024611044

---

## 2. Deskripsi Singkat Project
Project ini berfokus pada eksperimen dan implementasi manipulasi citra digital tingkat dasar hingga menengah menggunakan Python dan pustaka OpenCV. Tujuan utama dari proyek ini adalah memahami bagaimana operasi matematis (baik point processing maupun operasi aritmatika matriks piksel) dapat mengubah karakteristik visual, nilai piksel, kecerahan (*brightness*), kontras (*contrast*), distribusi histogram, serta detail spasial dari sebuah citra digital.

---

## 3. Citra yang Digunakan
Eksperimen ini menggunakan dua buah citra digital yang berbeda untuk menguji karakteristik dan perilaku setiap teknik transformasi:
1. **`image1.jpg`**: Citra utama yang digunakan untuk pengujian teknik transformasi intensitas tunggal (Negatif, Logaritmik, Gamma).
2. **`image2.jpg`**: Citra sekunder yang memiliki dimensi asli berbeda, digunakan sebagai objek pendukung dalam eksperimen manipulasi ukuran (*resize*) dan pencampuran (*image blending*).

---

## 4. Library yang Digunakan
Proyek ini dibangun menggunakan ekosistem Python 3 dengan pustaka-pustaka berikut:
* **`opencv-python` (OpenCV)**: Library utama untuk membaca, mengubah ruang warna, mengubah ukuran, dan melakukan operasi manipulasi citra.
* **`numpy`**: Untuk komputasi matriks numerik secara efisien (operasi aljabar linear pada piksel citra).
* **`matplotlib`**: Untuk visualisasi citra (*rendering*) dan menampilkan diagram distribusi histogram warna.

---

## 5. Struktur Folder Project
Berikut adalah susunan direktori repositori proyek agar kode dapat dieksekusi dengan lancar:

```text
manipulasi-citra-digital/
│
├── notebook/
│   └── image_manipulation.ipynb   # Jupyter Notebook berisi kode eksperimen lengkap
│
├── images/
│   ├── image1.jpg                 # Citra uji pertama
│   └── image2.jpg                 # Citra uji kedua
│
├── report/
│   └── laporan_tugas_2.pdf        # Laporan analisis hasil eksperimen (Maks. 8 Halaman)
│
├── requirements.txt               # Daftar dependensi library python
└── README.md                      # Dokumentasi utama proyek (file ini)


## 6. Cara Menjalankan Notebook
git clone [https://github.com/DUMPREEZ73254/manipulasi-citra-digital-.git)

## 7. Ringkasan Hasil Eksperimen
1.Konversi Warna: OpenCV membaca file dengan format matriks BGR. Jika langsung diplot dengan Matplotlib (RGB), warna citra akan mengalami distorsi/tertukar (merah menjadi   biru). Oleh karena itu, diperlukan fungsi cv.cvtColor(img, cv.COLOR_BGR2RGB).

2.Resize Citra: Menyamakan dimensi kedua citra menjadi $600 \times 400$ piksel sukses dilakukan, mencegah terjadinya error dimension mismatch saat aljabar matriks dijalankan.

3.Image Blending: Menggunakan cv.addWeighted. Kombinasi bobot $\alpha=0.5$ dan $\beta=0.5$ menghasilkan perpaduan transparansi yang paling seimbang di antara kedua citra.

4.Image Negative: Membalikkan intensitas warna ($s = 255 - r$). Piksel terang menjadi gelap dan sebaliknya. Histogram mengalami pencerminan horizontal secara simetris.

5.Transformasi Logaritmik: Berhasil mengekspansi kontras piksel pada area gelap (low intensity) secara signifikan sehingga detail bayangan terlihat, namun mengkompresi area terang sehingga rentan overexposure.

6.Transformasi Gamma: Memberikan koreksi pencahayaan yang fleksibel secara non-linear. Nilai $\gamma < 1$ mencerahkan citra (underexposure correction), sedangkan $\gamma > 1$ menggelapkan citra (overexposure correction).

## 8. Kesimpulan Singkat
Manipulasi citra digital pada dasarnya adalah operasi matematika diskrit yang diterapkan langsung pada matriks piksel. Tidak ada satu teknik transformasi yang selalu konstan meningkatkan kualitas semua citra; pemilihan metode (seperti Logaritmik vs Gamma) harus didasarkan pada karakteristik kondisi pencahayaan awal citra masukan serta bagian detail informasi visual mana yang ingin ditonjolkan oleh pengguna.