# Toyota Price Explorer - Kelompok 10

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://younglord0.github.io/Kelompok_10/)
[![GitHub](https://img.shields.io/badge/github-repo-blue)](https://younglord0.github.io/Kelompok_10/)

> Interactive Exploratory Data Analysis (EDA) Dashboard untuk Analisis Data Harga Mobil Toyota

## Tentang Proyek

**Toyota Price Explorer** adalah dashboard visualisasi interaktif yang memungkinkan pengguna mengeksplorasi dataset harga mobil Toyota bekas. Dashboard ini dirancang untuk membantu calon pembeli memahami pola harga, depresiasi nilai, membandingkan efesiensi bahan bakar, dan korelasi antar variabel dalam data.

### Tujuan

- Menganalisis pola harga mobil Toyota berdasarkan model, tahun, dan jarak tempuh
- Memvisualisasikan depresiasi nilai kendaraan seiring waktu
- Membandingkan efisiensi dan harga berbagai jenis bahan bakar
- Mengidentifikasi korelasi antar variabel (price, mileage, year, MPG, dll.)

## Fitur Utama

### Visualisasi Multi-View

1. **Scatter Plot: Mileage vs Price**
   - Menampilkan pola korelasi dan outliers
   - Support untuk 20+ model dengan color palette berbeda
   - Color encoding per model untuk identifikasi mudah

2. **Line Chart: Tren Harga per Tahun**
   - Analisis depresiasi untuk top 4 model
   - Menunjukkan linear regression trend
   - Slope calculation untuk mengukur tingkat depresiasi

3. **Bar Chart: Harga per Fuel Type**
   - Visualisasi perbedaan harga Petrol, Diesel, Hybrid, dan Other
   - Perbandingan harga rata-rata yang jelas

4. **Heatmap: Correlation Matrix**
   - Identifikasi hubungan antar 6 variabel numerik
   - Red-Blue diverging colorscale untuk korelasi positif/negatif
   - Analisis korelasi terkuat dalam dataset

### Interaksi & Animasi

- **Dynamic Filtering**: Multi-select model dan fuel type
- **Year Range Selector**: Batasi analisis pada periode tertentu (1990-2025)
- **Dynamic Y-Axis**: Pilih metrik berbeda (Price, MPG, Mileage, Tax, Engine Size)
- **Zoom & Pan**: Eksplorasi detail pada subset data (Plotly built-in)
- **Brushing Selection**: Select multiple points untuk analisis cluster
- **Tooltips**: Details-on-demand dengan format custom
- **Highlight Mechanism**: Click untuk highlight dan lihat detail
- **Dark/Light Mode**: Toggle tema untuk kenyamanan visual
- **Real-time Update**: Semua chart update secara sinkron saat filter berubah

### Auto-Generated Insights

Setiap visualisasi dilengkapi dengan **narrative insights otomatis** yang menjelaskan:
- Rata-rata harga pada filter aktif
- Model paling populer dalam subset
- Pola korelasi (positif/negatif) antara mileage dan price
- Tren depresiasi dengan slope calculation
- Fuel type dengan harga tertinggi
- Korelasi terkuat antar variabel

## Tech Stack

| Kategori | Teknologi |
|----------|-----------|
| **Frontend** | Vanilla JavaScript, HTML5, CSS3 |
| **Visualization** | Plotly.js 2.27.0, D3.js v7 |
| **UI Framework** | Bootstrap 5.3.3 |
| **Data Processing** | PapaParse 5.4.1 (CSV parsing) |
| **Hosting** | GitHub Pages |

## Live Demo

**Akses dashboard:** [https://younglord0.github.io/Kelompok_10/](https://younglord0.github.io/Kelompok_10/)

## Dataset

Dataset berisi **6,738 data** mobil Toyota bekas dengan 9 variabel:

| Variabel | Deskripsi | Tipe | Range |
|----------|-----------|------|-------|
| **model** | Model mobil Toyota | Categorical | 20+ models |
| **year** | Tahun produksi | Numeric | 1998-2020 |
| **price** | Harga jual (£) | Numeric | £1,000 - £60,000 |
| **mileage** | Jarak tempuh (miles) | Numeric | 1 - 174,419 |
| **fuelType** | Jenis bahan bakar | Categorical | Petrol, Diesel, Hybrid, Other |
| **tax** | Pajak tahunan (£) | Numeric | £0 - £580 |
| **mpg** | Miles per gallon | Numeric | 2.8 - 235.4 |
| **engineSize** | Ukuran mesin (liter) | Numeric | 0.0 - 5.7 |
| **transmission** | Jenis transmisi | Categorical | Manual, Automatic, Semi-Auto |

**Sumber Data**:

## Keputusan Desain

### Visual Encoding

#### Pilihan yang Digunakan:

**Scatter Plot:**
- **Position encoding** (x=mileage, y=price) → efektif menunjukkan korelasi negatif
- **Color by model** dengan 20 distinct colors → membedakan kategori
- **Size uniform** (8px) → fokus pada position, tidak distract dengan size variation

**Line Chart:**
- **Temporal encoding** (x=year) → analisis tren waktu
- **Only top 4 models** → menghindari visual clutter
- **Lines + markers** → balance antara tren dan data points

**Bar Chart:**
- **Height encoding** untuk average price → perbandingan magnitude yang clear
- **Categorical x-axis** (fuel types) → grouping yang logis

**Heatmap:**
- **Diverging colorscale** (RdBu: Red-Blue) → intuitive untuk correlation
- **Zmid=0** → highlight positive/negative dengan jelas
- **Square cells** → konsisten dan mudah dibaca


### Interaksi & Animasi

#### Teknik yang Diimplementasikan:

**1. Zooming & Panning**
- **Kenapa?** Dataset besar (6,738 titik) memerlukan fokus pada subset
- **Implementasi:** Plotly built-in drag untuk smooth UX
- **Benefit:** Eksplorasi detail tanpa kehilangan context

**2. Brushing Selection**
- **Kenapa?** Enable analisis cluster - pilih grup mobil dalam range tertentu sekaligus
- **Implementasi:** Marquee select dengan Plotly `dragmode: 'select'`
- **Benefit:** Multi-point selection untuk comparative analysis

**3. Dynamic Query Filters**
- **Kenapa?** HomeFinder-inspired, immediate feedback untuk eksplorasi
- **Implementasi:** Multi-select dropdown + year range + metric selector
- **Benefit:** Reduce cognitive load dibanding manual filtering

**4. Tooltips (Details-on-Demand)**
- **Kenapa?** Menampilkan detail tanpa clutter visual permanent
- **Implementasi:** Custom format dengan model, year, price, mileage, fuel
- **Benefit:** Hover untuk info lengkap, click untuk highlight

**5. Highlight Mechanism**
- **Kenapa?** Focus attention pada data points tertentu
- **Implementasi:** Opacity changes (non-selected: 0.15, selected: 1.0)
- **Benefit:** Visual contrast yang kuat untuk analisis

**6. Smooth Transitions**
- **Kenapa?** Maintain context saat filter berubah
- **Implementasi:** Plotly animate, CSS transitions (0.3s ease)
- **Benefit:** Perubahan terasa natural, tidak jarring

**7. Multi-View Coordination**
- **Kenapa?** Filter global untuk eksplorasi koheren
- **Implementasi:** Single filter state untuk semua chart
- **Benefit:** Consistent analysis across different views

## Anggota - Kelompok 10

| Anggota | NIM | Role | Kontribusi |
|---------|-----|------|-----------|
| **Sandy Yopa Boangmanalu** | 2211102165 | Data Analyst | Mencari dan memilih dataset yang relevan dan menarik, melakukan eksplorasi awal (EDA), menentukan subset data yang akan divisualisasikan, membersihkan dan menyiapkan data (CSV/JSON) |
| **Fadlurrahman Al Abror** | 2211102144 | Front-End Developer | Mengimplementasikan visualisasi dengan D3.js atau library lain, menghubungkan data dengan elemen visual, mengatur interaksi dan animasi di kode, mengoptimalkan performa dan kompatibilitas |
| **Muhammad Fansha Fakhriza** | 2211102154 | Visual Designer | Menentukan encoding visual (warna, bentuk, ukuran), mendesain layout dan estetika visual, menambahkan animasi transisi atau naratif, menyesuaikan tampilan agar menarik dan informatif |
| **Muhammad Umar Yuda** | 2211102018 | Interaction Designer | Mendesain alur interaksi (filter, tooltip, zoom, dil.), menentukan teknik interaksi yang paling efektif, membuat wireframe/mockup interaktif, menguji kegunaan interaksi |
| **Ari Rohyto Ibrena Padang** | 2211102360 | Dokumentasi & Deployment | Menulis README.md dan dokumentasi proyek, mengunggah proyek ke GitHub Pages, menyusun laporan akhir dan memastikan semua sumber dikutip |


## Proses Pengembangan

### Timeline
- **Data Analyst**: 10 Jam
- **Interaction Designer**: 8 Jam
- **Visual Designer**: 8 Jam
- **Front-End Developer**: 18 Jam
- **Dokumentasi**: 5 Jam

### Aspek Paling Memakan Waktu

**Overall Top 3:**
1. **Chart Implementation (8 jam)** - Plotly configuration, custom styling, tooltips
2. **Exploratory Data Analysis (5 jam)** - Statistical analysis, correlation studies
3. **Interaction Handlers (5 jam)** - Brushing coordination, state management, edge cases

## Hasil Analisis & Kesimpulan

### Key Findings

**1. Faktor Nilai Jual**
- **Engine Size** adalah faktor tunggal terkuat dalam menentukan harga
- **Year** berkorelasi positif dengan price (mobil baru = harga tinggi)
- **Mileage** berkorelasi negatif kuat (r = -0.73) dengan year

**2. Tren Depresiasi**
-  Tren depresiasi terlihat jelas di seluruh dataset, dipengaruhi oleh Jarak Tempuh (Mileage) dan usia mobil. Tren ini konsisten di berbagai model.

**3. Segmen Bernilai Tinggi**
- Mobil dengan jenis bahan bakar Hybrid memiliki harga jual rata-rata tertinggi. Selain itu, model crossover seperti C-HR mempertahankan nilai jual kembali yang superior di pasar.

### Rekomendasi

**Untuk Fokus Pemodelan:**
- Fokus pada `engineSize` dan `fuelType` harus diberi bobot tertinggi

**Untuk Strategi Pasar:**
- Model kecil bervolume tinggi (Yaris, Aygo) perhatukan harga rata rata bahan bakar Petrol yang rendah sebagai baselin harga

**Untuk Analisis Lanjut:**
- Melakukan analisis regresi yang lebih dalam, memisahkan data berdasarkan jenis Bahan Bakar atau Model untuk mendapatkan prediksi harga yang lebih akirat per segmen

## Referensi & Inspirasi

- [Hans Rosling's Gapminder](https://www.gapminder.org/tools/) - Interactive exploration
- [Plotly Documentation](https://plotly.com/javascript/) - Chart implementation
- [Observable HQ](https://observablehq.com/) - D3.js examples
- [Edward Tufte's Principles](https://www.edwardtufte.com/) - Data visualization theory

## Lisensi

- **Dataset**:
- **Code**: 

## Acknowledgments

- **Mata Kuliah**: Visualisasi Data
- **Dosen Pengampu**: Affan Hilmy Natsir
- **Institusi**: Telkom University Purwokerto
  
</div>
