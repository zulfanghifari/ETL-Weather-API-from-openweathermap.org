# ETL-Weather-API-from-openweathermap.org


## 📋 Deskripsi Project

Project ini melakukan proses ETL untuk data cuaca dari 15 kota besar di seluruh dunia. Data cuaca yang diambil mencakup informasi seperti suhu, kelembaban, tekanan udara, kecepatan angin, dan deskripsi cuaca.

### Fitur Utama
- **Extract**: Mengambil data cuaca real-time dari OpenWeatherMap API
- **Transform**: Membersihkan dan mengolah data JSON menjadi format tabel yang terstruktur
- **Load**: Menyimpan data ke Google BigQuery untuk analisis lebih lanjut

> **Note**: Project ini berjalan secara manual dan belum otomatis terupdate. Untuk mendapatkan data terbaru, script perlu dijalankan ulang secara manual.

## 🌍 Kota yang Dipantau

Project ini mengumpulkan data cuaca dari 15 kota:
- Jakarta, Indonesia
- New York, USA
- London, UK
- Tokyo, Japan
- Paris, France
- Sydney, Australia
- Mumbai, India
- Beijing, China
- Cairo, Egypt
- Moscow, Russia
- Rio de Janeiro, Brazil
- Toronto, Canada
- Berlin, Germany
- Madrid, Spain
- Rome, Italy

## 🛠️ Tech Stack

- **Python 3.8+**
- **Libraries**:
  - `requests` - HTTP requests ke OpenWeatherMap API
  - `pandas` - Data manipulation dan transformation
  - `google-cloud-bigquery` - Koneksi ke Google BigQuery
- **API**: OpenWeatherMap API
- **Data Warehouse**: Google BigQuery

## 📊 Data Schema

Data yang dikumpulkan mencakup kolom-kolom berikut:

| Kolom | Tipe Data | Deskripsi |
|-------|-----------|-----------|
| city | string | Nama kota |
| country | string | Kode negara |
| date | datetime | Timestamp pengambilan data |
| temperature_celsius | float | Suhu dalam Celsius |
| feels_like_celsius | float | Suhu yang terasa |
| weather_description | string | Deskripsi kondisi cuaca |
| pressure_hpa | int | Tekanan udara (hPa) |
| humidity_percent | int | Kelembaban (%) |
| wind_speed_ms | float | Kecepatan angin (m/s) |

## ⚙️ Setup dan Instalasi

### Prerequisites
1. Python 3.8 atau lebih tinggi
2. OpenWeatherMap API Key (gratis di [openweathermap.org](https://openweathermap.org/api))
3. Google Cloud Platform Account dengan BigQuery enabled
4. Service Account JSON key dari GCP

### Langkah Instalasi

1. **Clone repository**
   ```bash
   git clone https://github.com/username/weather-etl-project.git
   cd weather-etl-project
   ```

2. **Install dependencies**
   ```bash
   pip install requests pandas google-cloud-bigquery
   ```

3. **Konfigurasi API Key**
   
   Edit file script dan ganti `API_KEY` dengan API key Anda dari OpenWeatherMap:
   ```python
   API_KEY = "your_openweathermap_api_key_here"
   ```

4. **Konfigurasi Google Cloud**
   
   - Download Service Account JSON key dari GCP
   - Update konfigurasi BigQuery di script:
   ```python
   project_id = "your-project-id"
   dataset_id = "your-dataset-id"
   table_id = "your-table-name"
   key_path = "path/to/your/service-account-key.json"
   ```

5. **Buat Dataset di BigQuery**
   
   Pastikan Anda sudah membuat dataset di BigQuery sebelum menjalankan script.

## 🚀 Cara Menjalankan

Jalankan script Python atau notebook:

```bash
python weather_etl.py
```

atau buka dan jalankan file Jupyter Notebook:

```bash
jupyter notebook weather_etl.ipynb
```

Script akan:
1. Mengambil data cuaca dari 15 kota
2. Mentransformasi data menjadi format yang terstruktur
3. Mengunggah data ke BigQuery

## 📁 Struktur Project

```
weather-etl-project/
│
├── weather_etl.ipynb          # Jupyter notebook utama
├── weather_etl.pdf            # Dokumentasi dalam PDF
├── README.md                  # File ini
├── requirements.txt           # Dependencies Python
└── .gitignore                # File yang diabaikan Git
```

## ⚠️ Catatan Penting

- **Rate Limiting**: API gratis OpenWeatherMap memiliki limit 60 calls/menit. Script menggunakan `time.sleep(1)` untuk menghormati limit ini.
- **API Key Security**: Jangan commit API key atau service account JSON ke repository publik. Gunakan environment variables atau `.env` file.
- **Manual Update**: Data tidak otomatis terupdate. Untuk mendapatkan data terbaru, jalankan script secara manual.
- **Write Mode**: Script menggunakan `WRITE_TRUNCATE` yang akan menimpa data lama setiap kali dijalankan
  
## 🔮 Future Improvements

- [ ] Otomasi dengan Cloud Scheduler atau Airflow
- [ ] Tambahkan error handling yang lebih robust
- [ ] Implementasi logging yang lebih detail
- [ ] Tambahkan visualisasi data dengan Looker Studio atau Tableau
- [ ] Simpan historical data (append mode)
- [ ] Tambahkan unit tests
- [ ] Implementasi CI/CD pipeline

## 📝 License

Project ini dibuat untuk keperluan pembelajaran dan portfolio.

## 👤 Author

**Muhammad Zulfan Alghifari**

## 🙏 Acknowledgments

- [OpenWeatherMap](https://openweathermap.org/) untuk API cuaca gratis
- [Google Cloud Platform](https://cloud.google.com/) untuk BigQuery
- Purwadhika Digital Technology School untuk guidance dan support

---

⭐ Jika project ini membantu Anda, silakan berikan star!
