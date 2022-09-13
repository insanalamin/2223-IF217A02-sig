# Digitization and Data Representation

## Digitization

Konsep:
- Konversi
- Data spasial dari dunia nyata
- Ke bentuk digital

Contoh:
- Mengkonversi data jogging ke dalam data tipe line terkait rute jogging
- Mengkonversi peta dari buku peta offline ke bentuk digital dengan informasi lokasi
- Mengkonversi foto udara dari kamera ke bentuk digital dengan informasi lokasi
- Mengkonversi data penduduk miskin, foto, beserta koordinat ke database

Alur Umum:
- Menentukan tipe data yang akan di digitalkan
  - Point (titik koordinat rumah, titik koordinat laporan)
  - Line (rute jogging, rute berkendara, sungai, jaringan jalan, jaringan kereta, listrik)
  - Area / Polygon / Multi Polygon (batas wilayah, batas kawasan, batas tanah)
- Merancang dan membangun basis data spasial
  - Membuat tabel representasi objek dunia nyata
    - Contoh tabel jaringan jalan berisi satuan ruas jalan
  - Melengkapi tabel dengan atribut spasial maupun non spasial
    - Aplikasi tracking jogging : Tabel jogging : 
      - id
      - user
      - waktu
      - jarak
      - titik awal (POINT)
      - titik akhir (POINT)
      - rute (LINE)
- Membuat map service, layanan bagi aplikasi untuk mengakses data di database
  - Teknologi
    - Menggunakan map server
      - Geoserver
    - Menggunakan web map service berbasis bahasa pemrograman
      - Python
      - PHP
  - Kebutuhan use case
    - Input / POST koordinat infrastruktur desa
    - Menampilkan / GET semua infrastruktur desa
- Membuat aplikasi
  - User interface
    - Form input
    - Visualisasi
      - Peta
      - Tabel
      - Chart
  - Konektivitas / integrasi data

## Data Representation

### Data Type

### Data Format

## Spatial Database Introduction
