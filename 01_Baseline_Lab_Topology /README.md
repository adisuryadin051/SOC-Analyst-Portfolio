# Laporan Baseline SOC Home Lab

## 1. Pendahuluan

Laporan ini menyajikan dokumentasi kondisi awal (baseline) dari SOC Home Lab yang dirancang sebagai lingkungan simulasi untuk pengujian deteksi dan respons insiden keamanan siber. Tahap baseline ini bertujuan untuk memberikan gambaran menyeluruh mengenai arsitektur sistem, topologi jaringan, alur data log, serta peran masing-masing komponen sebelum dilakukan pengujian serangan dan penerapan skenario keamanan.

Dokumentasi baseline sangat penting agar hasil pengujian pada tahap selanjutnya dapat dianalisis secara objektif dan terukur.

---

## 2. Gambaran Umum Lingkungan SOC Home Lab

SOC Home Lab dibangun pada lingkungan virtual (VMware) dengan pendekatan modular. Arsitektur sistem dibagi menjadi beberapa domain fungsional yang merepresentasikan alur kerja SOC secara nyata, mulai dari fase serangan, pengumpulan log, analisis, hingga pelaporan.

Secara umum, sistem terdiri dari komponen berikut:

* Mesin virtual penyerang (Attacker)
* Mesin virtual target (Target Server)
* Mekanisme pengumpulan dan penyimpanan log
* Platform analisis keamanan (SIEM dan Network Analysis)
* Proses investigasi dan pelaporan insiden

---

## 3. Desain Arsitektur Sistem

### 3.1 Arsitektur Konseptual SOC Home Lab

Arsitektur SOC Home Lab dirancang secara hierarkis dengan pendekatan *layered architecture*. Setiap lapisan memiliki fungsi dan tanggung jawab yang jelas.

Lapisan utama dalam arsitektur ini meliputi:

1. Threat & Attack Layer
2. Target & Assets Layer
3. Log Collection Layer
4. Analysis & Response Layer
5. Reporting Layer

Pendekatan ini memungkinkan pemisahan peran (separation of concern) sehingga proses analisis dan investigasi dapat dilakukan secara sistematis.

---

### 3.2 Threat & Attack Layer

Lapisan ini merepresentasikan sumber ancaman dan aktivitas serangan yang disimulasikan dalam lingkungan lab.

Jenis serangan yang direncanakan dalam lab meliputi:

* Brute Force Attack (terhadap layanan SSH)
* SQL Injection (terhadap aplikasi web)
* Simulasi traffic berbahaya (malware atau anomali jaringan)

Pada tahap baseline, lapisan ini belum dijalankan sebagai serangan aktif, melainkan hanya didefinisikan sebagai komponen arsitektur.

---

### 3.3 Target & Assets Layer

Lapisan target berfungsi sebagai sistem korban yang menerima aktivitas serangan dan menghasilkan data log.

Komponen utama pada lapisan ini adalah:

* Layanan SSH (SSH Service)
* Aplikasi Web (Web Application)
* Antarmuka jaringan (Network Interface)

Setiap aktivitas yang terjadi pada layanan ini akan menghasilkan artefak log yang menjadi bahan analisis pada tahap berikutnya.

---

### 3.4 Log Collection Layer

Lapisan ini bertanggung jawab terhadap pengumpulan dan penyimpanan data log yang dihasilkan oleh sistem target.

Jenis log yang dikumpulkan antara lain:

* auth.log (aktivitas autentikasi SSH)
* access.log (aktivitas HTTP/HTTPS pada web server)
* PCAP / Traffic Capture (hasil perekaman lalu lintas jaringan)

Log-log ini dikonfigurasi untuk dapat diteruskan ke sistem analisis secara terpusat.

---

### 3.5 Analysis & Response Layer

Lapisan analisis merupakan inti dari SOC Home Lab. Pada lapisan ini, data log yang telah dikumpulkan dianalisis untuk mendeteksi indikasi serangan.

Komponen utama:

* Splunk SIEM: digunakan untuk indexing, pencarian, dan penerapan detection rules
* Wireshark: digunakan untuk analisis forensik lalu lintas jaringan berbasis PCAP

Pada tahap baseline, sistem analisis belum menjalankan rule deteksi aktif, namun infrastruktur dan alur data telah disiapkan.

---

### 3.6 Reporting Layer

Lapisan ini berfungsi sebagai tahap akhir dari siklus SOC, yaitu dokumentasi dan pelaporan hasil analisis.

Output yang direncanakan meliputi:

* Laporan insiden dalam format PDF
* Daftar Indicator of Compromise (IOC)
* Rekomendasi mitigasi dan perbaikan sistem

Pada kondisi baseline, lapisan ini belum menghasilkan laporan insiden karena belum ada serangan yang dieksekusi.

---

## 4. Topologi Jaringan Lab

Topologi jaringan SOC Home Lab menggunakan satu virtual switch sebagai pusat konektivitas antar mesin virtual. Seluruh VM berada dalam satu segmen jaringan terisolasi untuk memastikan keamanan dan kemudahan observasi.

Karakteristik topologi:

* Model star / hub-and-spoke
* Virtual switch sebagai core network
* Isolasi dari jaringan produksi

Topologi ini dipilih untuk mempermudah pemantauan lalu lintas dan korelasi log pada tahap analisis.

---

## 5. Alur Data dan Informasi (Baseline)

Pada kondisi sebelum pengujian, alur data sistem dapat dijelaskan sebagai berikut:

1. Aktivitas sistem terjadi pada target server
2. Sistem target menulis aktivitas ke log lokal (auth.log dan access.log)
3. Log disiapkan untuk diteruskan ke sistem SIEM
4. Data PCAP disiapkan untuk dianalisis menggunakan tools forensik jaringan

Belum terdapat traffic serangan atau alert aktif pada tahap ini.

---

## 6. Tujuan Penetapan Baseline

Penetapan baseline dilakukan untuk:

* Mendefinisikan kondisi normal sistem
* Menjadi pembanding hasil pengujian serangan
* Memastikan setiap komponen SOC berfungsi sesuai peran
* Memudahkan analisis dampak serangan pada tahap berikutnya

---

## 7. Kesimpulan Tahap Baseline

Berdasarkan hasil dokumentasi baseline, dapat disimpulkan bahwa:

* Arsitektur SOC Home Lab telah dirancang secara terstruktur
* Seluruh komponen utama SOC telah tersedia dan terintegrasi
* Sistem siap digunakan untuk pengujian serangan dan evaluasi deteksi

Tahap selanjutnya akan difokuskan pada eksekusi skenario serangan dan analisis kemampuan deteksi sistem SOC.

---

