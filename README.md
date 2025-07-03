# Analisis Spasial dan Prediksi Emisi Karbon di Purbalingga Menggunakan Machine Learning

Repositori ini berisi kode sumber dan analisis untuk tugas besar mata kuliah Strategi Algoritma, dengan studi kasus prediksi tingkat emisi karbon berbasis data geospasial di Kabupaten Purbalingga, Jawa Tengah.

## 1. Latar Belakang & Tujuan Proyek

Urbanisasi dan pembangunan infrastruktur yang pesat dapat berdampak signifikan terhadap lingkungan, salah satunya adalah peningkatan emisi karbon. Analisis berbasis data geospasial dapat memberikan wawasan mendalam mengenai area mana yang berisiko tinggi dan memerlukan perhatian khusus dalam perencanaan tata kota yang berkelanjutan.

### Tujuan Utama Proyek:

1. **Ekstraksi Fitur Perkotaan:** Mengambil dan mengolah data geospasial dari OpenStreetMap (OSM) untuk mengekstrak fitur-fitur kunci seperti kepadatan jalan, kepadatan bangunan, dan persentase ruang terbuka hijau.
2. **Implementasi Model Machine Learning:** Menerapkan dan membandingkan kinerja dua algoritma klasifikasi, **Random Forest** dan **XGBoost**, untuk memprediksi tingkat potensi emisi karbon (Normal vs. Tinggi).
3. **Analisis Spasial:** Memvisualisasikan hasil prediksi dalam bentuk peta tematik untuk mengidentifikasi distribusi spasial tingkat emisi di area studi.

### Area Studi:

Proyek ini berfokus pada tiga kecamatan asri di Purbalingga: **Pengadegan**, **Kaligondang**, dan **Bojongsari**.

## 2. Alur Kerja Proyek (Workflow)

Proyek ini dilaksanakan melalui beberapa tahapan utama yang sistematis:
<details>
  <summary>Klik untuk melihat gambar (opsional)</summary>
  <img src="https://github.com/user-attachments/assets/cf6e6ecf-da0a-4126-a8f6-20f062ef2063" />
</details>

## 3. Dataset dan Fitur

- **Sumber Data:** Data geospasial publik yang diakses secara dinamis dari **OpenStreetMap (OSM)** menggunakan pustaka Python `OSMNx`.
- **Fitur Utama:**  
  a. `kepadatan_jalan`: Total panjang jalan per kilometer persegi (km/km²).  
  b. `kepadatan_bangunan`: Jumlah bangunan per kilometer persegi (bangunan/km²).  
  c. `persentase_hijau`: Persentase luas area hijau dari total luas area (%).
- **Variabel Target (Label):**  
Label emisi dibuat berdasarkan kriteria yang telah ditentukan, menghasilkan dua kategori:
  - **Normal:** Area dengan RTH yang cukup dan kepadatan yang terkendali.
  - **Tinggi:** Area padat dengan RTH terbatas, berpotensi menghasilkan emisi lebih tinggi.

## 4. Hasil dan Evaluasi

Kedua model, Random Forest dan XGBoost, dilatih menggunakan data yang telah melalui proses _undersampling_ untuk menyeimbangkan kelas. Hasil evaluasi pada data uji menunjukkan performa yang sangat tinggi.

### Perbandingan Kinerja Model
| **Metrik**              | **Random Forest** | **XGBoost** |
|-------------------------|-------------------|-------------|
| Akurasi                | 1.000             | 1.000       |
| Presisi (Tinggi)       | 1.000             | 1.000       |
| Recall (Tinggi)        | 1.000             | 1.000       |
| F1-Score (Tinggi)      | 1.000             | 1.000       |
| ROC-AUC                | 1.000             | 1.000       |

Meskipun kedua model mencapai performa sempurna pada set data uji ini, analisis lebih lanjut pada data yang lebih bervariasi mungkin diperlukan. Untuk proyek ini, kedua model dianggap sangat efektif.

### Visualisasi Hasil Prediksi

Peta di bawah ini menunjukkan hasil prediksi tingkat emisi karbon di tiga kecamatan menggunakan model XGBoost. Area berwarna **merah** menunjukkan prediksi emisi **Tinggi**, sedangkan warna **hijau** menunjukkan **Normal**.

![Peta Prediksi](/assets/peta_prediksi.png)

### Interpretasi per Kecamatan

| **Kecamatan** | **Prediksi Area "Normal"** | **Rata-rata % Hijau** | **Interpretasi** |
|---------------|-----------------------------|------------------------|-------------------|
| Pengadegan    | 3.91%                       | 82.05%                | Perlu perhatian. Mayoritas area padat, RTH terbatas, berpotensi emisi tinggi. |
| Kaligondang   | 57.52%                      | 15598263.27%          | Kondisi campuran. Terdapat keseimbangan antara area padat dan area hijau.     |
| Bojongsari    | 11.19%                      | 6104.17%              | Perlu perhatian. Mayoritas area padat, RTH terbatas, berpotensi emisi tinggi. |

## 5. Cara Menjalankan Proyek

### Prasyarat

Pastikan Anda memiliki Python 3.9 atau versi lebih baru.

### Instalasi

1. **Clone Repositori**  
   ```bash
   git clone https://github.com/RozhakXD/CarbonML-Purbalingga.git
   cd CarbonML-Purbalingga
   ```

2. **Buat dan aktifkan virtual environment (opsional tapi direkomendasikan):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Untuk Windows: venv\Scripts\activate
   ```

3. **Instal semua pustaka yang dibutuhkan:**
   ```bash
   pip install -r requirements.txt
   ```

### **Jalankan Kode**

Buka dan jalankan file `Prediksi_Emisi_Karbon_Purbalingga_OSM_ML.ipynb` menggunakan Jupyter Notebook atau Jupyter Lab.
```
jupyter notebook Prediksi_Emisi_Karbon_Purbalingga_OSM_ML.ipynb
```

> **Catatan:** Pastikan koneksi internet stabil karena beberapa data geospasial diunduh secara dinamis dari OpenStreetMap.

## 6. Struktur Repositori
```
../CarbonML-Purbalingga
├── 25_sample_prediksi_emisi_purbalingga.csv
├── assets
│   └── peta_prediksi.png
├── cached_osm
├── LICENSE
├── Prediksi_Emisi_Karbon_Purbalingga_OSM_ML.ipynb
├── README.md
└── requirements.txt
```

## 7. Terima Kasih
Proyek ini tidak lepas dari bimbingan dan dukungan dosen pengampu mata kuliah **Strategi Algoritma**, `Bapak Sudianto, S.PD., M.KOM.`, yang telah memberikan arahan dan masukan berharga selama proses pengerjaan tugas besar ini. Semoga kontribusi ini dapat memberikan manfaat bagi perkembangan ilmu pengetahuan dan masyarakat.