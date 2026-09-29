# Penawaran Sistem Distribusi & ERP

**Untuk: CV Pridata Jaya · Mataram, Nusa Tenggara Barat**

| | |
|---|---|
| **Nomor penawaran** | {{NOMOR_PENAWARAN}} |
| **Tanggal penawaran** | {{TANGGAL_PENAWARAN}} |
| **Masa berlaku penawaran** | 30 hari kalender sejak tanggal penawaran |
| **Dasar harga** | Daftar Harga Resmi **NTB-PL-2026-09**, terbit 29 September 2026 (Lampiran 2) |
| **Penerbit** | Ato-team |
| **Bahasa / mata uang** | Indonesia / Rupiah. Semua harga **belum termasuk PPN** |

---

## 1. Ringkasan

Anda membeli sebuah sistem distribusi dan ERP yang sudah berjalan: dari pesanan toko, invoice, pengiriman, dan piutang, sampai pergerakan stok antar gudang dan laporan untuk pemilik. Setiap pergerakan uang dan stok meninggalkan catatan yang bisa ditelusuri: siapa, kapan, dari nilai berapa ke nilai berapa. Invoice yang sudah terbit tidak bisa diubah diam-diam, dan setiap pengguna hanya melihat toko dan gudang yang menjadi tanggung jawabnya.

Yang berubah di operasional harian: pencatatan yang sekarang tersebar menjadi satu alur yang saling terhubung, dan selisih, baik di piutang maupun di stok, bisa ditelusuri ke transaksi asalnya. **Yang tidak berubah dengan sendirinya adalah ketepatan orang yang menghitung dan mengetik barang masuk.** Bagian itu kami jelaskan lebih dulu di §1A, sebelum harga, karena itu yang paling menentukan apakah sistem ini cocok untuk Anda.

Yang Anda terima:

- Sistem berisi **47 fitur** yang sudah berjalan, dikelompokkan dalam 8 fungsi bisnis (Lampiran 1).
- Implementasi sampai go-live: **40 orang-hari** kerja, termasuk migrasi data master, penyesuaian dokumen dan laporan, pelatihan **3 batch**, UAT, dan pendampingan 2 minggu setelah go-live.
- **Garansi cacat 6 bulan** sejak go-live: perbaikan cacat tanpa biaya, dan Kontrak Dukungan Tahunan belum berjalan selama masa itu.
- Kontrak Dukungan Tahunan (ASC) mulai bulan ke-7 setelah go-live, dengan waktu respons pertama yang dijamin tertulis.

Lingkup kontrak ini: **CV Pridata Jaya**, satu instance produksi, **{{JUMLAH_GUDANG}}** gudang, **{{JUMLAH_PENGGUNA}}** pengguna. Sistem berjalan di server milik Anda; Ato-team mengelola aplikasinya.

---

## 1A. Yang perlu Anda ketahui lebih dulu: human error di penerimaan barang

**Sistem ini tidak menghilangkan kesalahan manusia, dan penawaran ini tidak menjanjikannya.** Tidak ada ERP yang bisa. Yang bisa dilakukan software hanya tiga hal, dan kondisi sistem ini untuk masing-masing kami sampaikan apa adanya:

| Yang bisa dilakukan software | Kondisi sistem sekarang | Setelah Fase 2 |
|---|---|---|
| **Mengurangi peluang salah input** (scan, bukan ketik) | **Belum ada.** Setiap angka dan produk di penerimaan barang diketik atau dicari manual. Tidak ada scan barcode. Konversi karton ke pcs dilakukan di kepala operator | Turun, **tidak nol**. Scan menghilangkan salah pilih produk, tetapi jumlah fisik tetap dihitung manusia |
| **Menangkap salah lebih awal** | **Belum ada saat barang masuk.** Tidak ada angka pembanding (PO atau surat jalan) untuk angka yang diketik operator. Selisih baru terlihat saat stock opname, sering lama setelah kejadiannya | Selisih terlihat **pada hari penerimaan**, saat barang masih di depan gudang, untuk penerimaan yang punya dokumen pembanding |
| **Membuat salah terlacak dan murah dikoreksi** | **Sudah kuat** untuk buku besar stok: setiap pergerakan punya sebab yang bisa ditelusuri, ada audit log, ada stock opname. **Belum** untuk pengubahan catatan penerimaan yang sudah tersimpan: perubahannya belum tercatat siapa dan kapan | Setiap perubahan punya pelaku, waktu, alasan, dan dokumen induk |

Artinya, untuk **penerimaan barang**, sistem ini hari ini mencatat dan menelusuri dengan baik, tetapi **belum mencegah** dan **belum menangkap lebih awal**. Kalau kekhawatiran utama Anda adalah salah hitung barang masuk, itu belum terselesaikan oleh paket di penawaran ini. Menambah validasi di layar penerimaan juga tidak akan menyelesaikannya, karena tidak ada angka pembanding untuk divalidasi.

### Fase 2: modul penerimaan barang tahap lanjut

Fase 2 dirancang khusus untuk dua kemampuan yang belum ada di atas:

- **Dokumen penerimaan per surat jalan**: satu dokumen untuk satu pengiriman supplier, bukan satu entri lepas per produk. Penerimaan tidak bisa terposting sebagian atau ganda.
- **Pencocokan** antara dokumen pembanding (PO ke supplier, atau surat jalan supplier) dan hitungan fisik.
- **Hitung buta**: angka di dokumen disembunyikan dari operator, supaya ia benar-benar menghitung dan tidak menyalin.
- **Persetujuan selisih** di atas ambang tertentu, lewat ponsel supervisor.
- **Pencatatan pelaku** dan jejak audit pada penerimaan dan pengubahannya.
- **Scan barcode** dan input dari ponsel gudang, bila barang Anda berbarcode.

**Target yang diukur pada data produksi Anda sendiri**, bukan janji umum:

| Target | Cara ukur |
|---|---|
| Selisih terhadap dokumen pembanding terdeteksi **pada hari penerimaan** | Selisih waktu antara penerimaan dan posting untuk dokumen bervarian |
| **100%** penerimaan baru terhubung ke supplier | Jumlah penerimaan baru tanpa supplier = 0 |
| **100%** pengubahan catatan stok punya entri audit | Rekonsiliasi berkala antara mutasi dan entri audit |
| **Nol** penerimaan terposting sebagian, **nol** dokumen ganda dari satu surat jalan | Jumlah dokumen draf yang punya pergerakan stok = 0 |

Bila barang Anda berbarcode dan fitur scan masuk lingkup, target tambahannya: sebagian besar baris penerimaan terisi lewat scan. Angkanya ditetapkan setelah survei barcode di gudang Anda.

**Yang tidak kami janjikan**, dan tidak bisa diselesaikan software mana pun:

1. **Salah hitung fisik tetap bisa terjadi.** Bila operator menghitung 11 padahal isinya 12, sistem yang punya dokumen pembanding akan menandai selisih 1. Itu deteksi, bukan pencegahan.
2. **Kekurangan orang di jam puncak bongkar muat.** Bila tiga truk datang bersamaan dan hanya ada dua orang, kontrol apa pun akan diakali. Itu soal staf dan penjadwalan kedatangan supplier.
3. **Kebiasaan memesan tanpa dokumen.** Bila pesanan ke supplier dilakukan lewat telepon atau WhatsApp tanpa PO, pencocokan bertumpu pada surat jalan supplier (2 arah), yang lebih lemah karena angka pembandingnya berasal dari supplier.
4. **Kemauan menindaklanjuti.** Jejak audit hanya berguna kalau ada yang membacanya dan ada konsekuensinya.
5. **Data master yang berantakan.** Bila satu barang fisik punya dua entri produk, selisih akan muncul terus dan peringatan mulai diabaikan.
6. **Penurunan selisih stock opname sebesar angka tertentu.** Selisih opname punya banyak sebab, dan Fase 2 hanya menyentuh sebagian. Kami akan mengukur dan melaporkannya, tetapi tidak menjanjikan angkanya.

**Harga dan jadwal Fase 2.** Fase 2 dijual **terpisah**, dengan harga terpisah, kriteria penerimaan terpisah, dan jadwal terpisah. **Fase 2 tidak termasuk dalam harga di §3 dan tidak dijanjikan gratis.** Harga dan jadwalnya belum diterbitkan; keduanya baru dapat ditetapkan setelah kami mengetahui beberapa hal dari gudang Anda (lihat di bawah) dan akan disampaikan **tertulis, sebelum pekerjaan Fase 2 dimulai**. Peran Anda sebagai mitra uji coba Fase 2 dijelaskan di §3.3.

**Pertanyaan yang jawabannya menentukan rancangan Fase 2**, mohon disiapkan:

1. Apakah Anda membuat Purchase Order resmi ke supplier, atau memesan lewat telepon atau WhatsApp?
2. Berapa penerimaan per hari, dan berapa baris per surat jalan?
3. Apakah barang Anda berbarcode, dan apakah konsisten antar supplier?
4. Apakah ada produk dengan tanggal kedaluwarsa?
5. Berapa orang menangani penerimaan di jam puncak, dan apakah ada supervisor di lokasi?
6. Seberapa sering stock opname dilakukan sekarang?
7. Apakah barang diterima dalam karton lalu dijual dalam pcs?

---

## 2. Isi Paket

47 fitur terkirim, dikelompokkan per fungsi bisnis:

| Fungsi bisnis | Jumlah fitur |
|---|---:|
| Data induk & referensi | 6 |
| Penjualan & pelanggan | 7 |
| Penagihan, piutang & kas | 7 |
| Gudang, pengiriman & persediaan | 8 |
| Laporan & analitik | 6 |
| Pengguna, peran & keamanan akses | 6 |
| Integrasi & otomasi | 4 |
| Platform & keandalan | 3 |
| **Total** | **47** |

Rincian tiap fitur ada di **Lampiran 1**. Seluruh fitur tersebut termasuk dalam harga di §3 tanpa biaya tambahan. Termasuk juga: pengelolaan aplikasi di server Anda selama ASC berjalan, backup harian, uji pemulihan backup 2× per tahun, dan dokumentasi pengguna.

**Batas ruang lingkup di §4 sama pentingnya dengan daftar di atas.** Mohon dibaca sebelum menandatangani, terutama bila Anda pernah membandingkan dengan ERP lain yang berbayar.

---

## 3. Harga

Seluruh harga dalam Rupiah dan **belum termasuk PPN** serta pajak lain yang berlaku.

### 3.1 Harga list: Lisensi perpetual + Kontrak Dukungan Tahunan (Opsi A)

| Komponen | **Harga list** |
|---|---:|
| Lisensi perpetual: satu badan usaha, satu instance produksi | Rp 105.000.000 |
| Implementasi & go-live: 40 orang-hari | Rp 70.000.000 |
| **Total Tahun 1 (sekali bayar)** | **Rp 175.000.000** |
| Kontrak Dukungan Tahunan (ASC) **SLA Dasar, server milik pembeli** | Rp 27.500.000/tahun |

Lisensi dimiliki selamanya. Bila ASC dihentikan, sistem tetap berjalan di server Anda, tetapi patch keamanan, pengelolaan, dan dukungan berhenti; Anda mengambil alih pengelolaan aplikasinya sendiri.

### 3.2 Program Mitra Riset 2026/2027

CV Pridata Jaya diundang sebagai mitra dalam **Program Mitra Riset 2026/2027**: program tertutup, atas undangan, maksimum satu mitra per kategori usaha per pasar, berakhir **31 Desember 2027**.

| | |
|---|---:|
| Harga list Tahun 1 (§3.1) | Rp 175.000.000 |
| Potongan Mitra Riset 2026/2027 | −Rp 87.500.000 |
| **Harga sistem Tahun 1 setelah potongan** | **Rp 87.500.000** |
| Harga list ASC SLA Dasar, server milik pembeli, per tahun | Rp 27.500.000 |
| Potongan Mitra Riset atas ASC | −Rp 0 |
| **ASC per tahun setelah potongan** | **Rp 27.500.000** |

**Potongan ini bukan harga.** Nilainya setara dengan kewajiban timbal balik yang disepakati tertulis di §3.3. **Jika satu kewajiban dicoret saat negosiasi, potongan berkurang persis sebesar nilai kewajiban tersebut.** Potongan hanya berlaku atas harga sistem, **tidak** atas ASC (ditampilkan Rp 0 supaya tidak menimbulkan kesalahpahaman di kemudian hari), komponen hosting, modul penerimaan barang tahap lanjut, perluasan lisensi, dan integrasi pihak ketiga.

**Yang Ato-team berikan sebagai bagian dari program**, sekali dan tidak diperpanjang:

- **Garansi cacat 6 bulan** (bukan 3), sehingga ASC baru mulai bulan ke-7 setelah go-live.
- **Bank 10 orang-hari** permintaan perubahan, berlaku 3 tahun, tidak dapat dialihkan atau diuangkan, hangus bila tidak terpakai.
- **ASC terkunci tanpa indeksasi selama 3 tahun.**
- Kerahasiaan dua arah: nama dan angka Anda tidak dipublikasikan tanpa persetujuan tertulis Anda atas naskahnya.

Harga mitra riset **bukan preseden** untuk perpanjangan, perluasan, modul baru, pembeli lain, maupun perusahaan satu grup. Perpanjangan setelah tahun ketiga kembali ke harga list yang berlaku saat itu, dikurangi maksimum 10% potongan loyalitas. Syarat komersial ini tunduk klausul kerahasiaan dua arah: yang boleh disebut publik oleh kedua pihak hanya harga list dalam NTB-PL-2026-09.

### 3.3 Kewajiban timbal balik CV Pridata Jaya

Nilai tiap kewajiban dicantumkan di lampiran kontrak. **Tidak ada komitmen ASC minimum**: Anda dapat menghentikan ASC pada akhir periode yang sudah dibayar.

| # | Kewajiban | Bila tidak dipenuhi |
|---|---|---|
| **K1** | **Studi kasus dan referensi penjualan di NTB.** Ato-team boleh menyebut nama CV Pridata Jaya dan memakainya sebagai referensi. Naskah studi kasus disetujui tertulis oleh Anda sebelum terbit. Anda menyediakan 1 narahubung, maksimum 4 kontak calon pembeli per tahun | Ato-team berhak menagih kembali bagian potongan senilai kewajiban ini, pro rata sisa masa 36 bulan |
| **K2** | **Akses data operasional untuk riset, 3 tahun.** Akses baca ke data transaksi (order, invoice, pergerakan stok, piutang), dengan NDA dua arah: hanya dalam bentuk teragregasi atau teranonimkan, tidak dipindahkan ke pihak ketiga, nama Anda tidak dipublikasikan | Sama seperti K1; Ato-team juga dapat mengakhiri status mitra riset |
| **K3** | **Testimoni dan lokasi demo.** Testimoni tertulis dan video dalam 6 bulan sejak tanda tangan. Kunjungan demo calon pembeli maksimum 6× per tahun, 2 jam, dijadwalkan minimal 5 hari kerja sebelumnya | Pro rata bagian yang belum dipenuhi, setelah pemberitahuan tertulis 60 hari |
| **K5** | **Peran co-development Fase 2.** Akses gudang dan waktu operator untuk minimal 20 sesi uji coba modul penerimaan barang, masing-masing ±3 jam dengan 1 operator gudang dan 1 supervisor, umpan balik terdokumentasi 5 hari kerja per sesi | Per sesi yang tidak dipenuhi setelah pemberitahuan 10 hari |

Penagihan kembali dilakukan **proporsional terhadap bagian yang dilanggar**, bukan sebagai denda. Rumusan lengkapnya ada di kontrak.

### 3.4 Biaya kepemilikan 3 tahun

| Dibayar ke Ato-team | Tahun 1 | Tahun 2 | Tahun 3 | **Total 3 tahun** |
|---|---:|---:|---:|---:|
| Harga list sistem | Rp 175.000.000 | | | Rp 175.000.000 |
| Potongan Mitra Riset | −Rp 87.500.000 | | | −Rp 87.500.000 |
| ASC SLA Dasar (Tahun 1: 6 bulan, mulai bulan ke-7; terkunci tanpa indeksasi) | Rp 13.750.000 | Rp 27.500.000 | Rp 27.500.000 | Rp 68.750.000 |
| **Total** | **Rp 101.250.000** | **Rp 27.500.000** | **Rp 27.500.000** | **Rp 156.250.000** |

### 3.5 Biaya berjalan yang perlu Anda perhitungkan

| | Per tahun |
|---|---:|
| ASC SLA Dasar | Rp 27.500.000 |
| Server milik Anda (perkiraan ± Rp 1.700.000/bulan, **bukan harga Ato-team**; bergantung penyedia dan spesifikasi) | ± Rp 20.400.000 |
| **Total biaya berjalan (perkiraan)** | **± Rp 47.900.000** |

Biaya ini berjalan setiap tahun. **Kami tidak menjanjikan penghematan dalam jumlah tertentu.** Nilai utama sistem ini adalah kendali dan keterlacakan atas piutang, stok, dan hak akses, bukan pengurangan biaya yang bisa kami jamin. Kami menyarankan Anda menilai kecocokannya terhadap angka usaha Anda sendiri sebelum menandatangani.

### 3.6 Jasa di luar lingkup paket

| Item | **Harga list** |
|---|---:|
| Pengembangan modul, laporan, atau penyesuaian di luar 47 fitur | Rp 1.750.000/orang-hari, minimum 5 orang-hari |
| Migrasi data historis di luar saldo awal | Rp 1.750.000/orang-hari |
| Batch pelatihan tambahan di luar 3 batch bawaan | Rp 1.750.000/orang-hari |

---

## 4. Batas Ruang Lingkup dan Kewajiban Pembeli

Yang **tidak** termasuk dalam harga §3, dan cara masing-masing dihargai:

| Item | Cara dihargai |
|---|---|
| **Modul penerimaan barang (receiving) tahap lanjut (Fase 2)** | Dalam pengembangan. Belum tersedia dan **harganya belum diterbitkan**. Ditawarkan terpisah dengan kriteria penerimaan dan jadwal sendiri (§1A) |
| **Infrastruktur: server, database, storage, bandwidth** | **Ditanggung Anda langsung** kepada penyedia pilihan Anda |
| Badan usaha kedua atau instance produksi tambahan | Lisensi penuh sesuai harga list |
| Gudang atau cabang di luar yang tercantum dalam kontrak | Harga list, sebagai perluasan lisensi |
| Pengguna di atas kuota kontrak | Harga list, sebagai perluasan lisensi |
| Integrasi pihak ketiga (e-faktur, bank, marketplace, payment gateway) | Proyek terpisah; perlu scoping sebelum harga dapat diberikan |
| Modul atau laporan kustom di luar 47 fitur | Rp 1.750.000/orang-hari, minimum 5 orang-hari |
| Fitur yang lazim di ERP besar: multi-mata-uang, manufaktur, konsolidasi antar badan usaha, akuntansi penuh sampai neraca | **Tidak ada** di 47 fitur |
| Aplikasi mobile native | Tidak tersedia; bukan bagian dari paket |
| Perangkat keras (server fisik, barcode scanner, printer, jaringan) | Di luar lingkup; disediakan pembeli |

**Kewajiban pembeli yang menjadi prasyarat harga ini:**

1. **Data master** (kode produk, daftar toko, daftar supplier, saldo awal piutang) diserahkan dalam format dan kelengkapan yang disepakati tertulis, dan saldo awal piutang sudah terekonsiliasi. Ini adalah **prasyarat termin pembayaran kedua**. Pembersihan data di luar kriteria tersebut dihargai Rp 1.750.000/orang-hari.
2. **Server memenuhi spesifikasi minimum, dinyatakan tertulis sebelum tanda tangan:** 4 vCPU, 8 GB RAM, SSD, database PostgreSQL terpisah atau terkelola, backup off-site dengan retensi 30 hari. Bila server di bawah spesifikasi ini, jaminan waktu respons ASC tidak berlaku, dan biaya peningkatan server (misalnya ke 8 vCPU / 16 GB) menjadi tagihan Anda.

---

## 5. Dukungan Setelah Go-Live

Garansi cacat **6 bulan** sejak go-live. Kontrak Dukungan Tahunan mulai berjalan bulan ke-7.

| | **Dasar** | **Standar** | **Prioritas** |
|---|---|---|---|
| **Harga per tahun, server milik pembeli** | **Rp 27.500.000** | Rp 51.500.000 | Rp 72.500.000 |
| Waktu respons pertama (hari kerja) | 8 jam kerja | 4 jam kerja | 2 jam kerja |
| Jam help desk | ±4 jam/bulan | ±12 jam/bulan | ±12 jam/bulan |
| Perbaikan bug | Hanya bug kritis (menghentikan operasional atau merusak data) | Penuh, termasuk non-kritis | Penuh, termasuk non-kritis |
| Pengelolaan aplikasi, backup harian, patch keamanan | ✅ | ✅ | ✅ |
| Jatah perubahan kecil | — | — | 12 orang-hari/tahun |
| Kunjungan on-site | — | — | Kuartalan |

Tingkat yang ditawarkan dalam penawaran ini: **SLA Dasar**. Peningkatan tingkat dapat dilakukan kapan saja dan berlaku prorata.

**Yang tidak dijamin di tingkat mana pun:** waktu penyelesaian (yang dijamin adalah waktu respons pertama), gangguan yang bersumber dari server, infrastruktur, atau jaringan milik Anda, dan permintaan fitur baru.

---

## 6. Termin Pembayaran

Pembayaran diikat ke milestone yang dapat diverifikasi, bukan ke tanggal kalender. Persentase termin dihitung atas nilai setelah potongan, dengan milestone yang sama.

| Termin | Milestone | Harga list | Potongan Mitra Riset | **Dibayar** |
|---|---|---:|---:|---:|
| 1 | Tanda tangan kontrak | Rp 52.500.000 | −Rp 26.250.000 | **Rp 26.250.000** |
| 2 | Environment siap + data master selesai dimigrasi dan diverifikasi | Rp 43.750.000 | −Rp 21.875.000 | **Rp 21.875.000** |
| 3 | Berita acara UAT diterima | Rp 43.750.000 | −Rp 21.875.000 | **Rp 21.875.000** |
| 4 | 30 hari setelah go-live tanpa insiden kritis | Rp 35.000.000 | −Rp 17.500.000 | **Rp 17.500.000** |
| | **Jumlah** | **Rp 175.000.000** | **−Rp 87.500.000** | **Rp 87.500.000** |

- ASC ditagih **tahunan di muka** (Rp 27.500.000), pada awal bulan ke-7 setelah go-live. Pembayaran kuartalan tersedia dengan biaya administrasi **+5%**.
- Jatuh tempo pembayaran **14 hari kalender** sejak tanggal invoice, kecuali disepakati lain tertulis.
- Invoice dan kontrak menampilkan harga list penuh, lalu baris potongan terpisah. Invoice ASC menampilkan `Potongan Program Mitra Riset: Rp 0`.

---

## 7. Masa Berlaku Harga dan Indeksasi

1. Penawaran ini berlaku **30 hari kalender** sejak {{TANGGAL_PENAWARAN}}.
2. Dasar harganya adalah Daftar Harga **NTB-PL-2026-09**, berlaku 29 September 2026 – 30 Juni 2027 (Lampiran 2).
3. **Harga terkunci sejak tanda tangan.** Harga lisensi dan implementasi dalam kontrak yang sudah ditandatangani tidak berubah oleh revisi daftar harga berikutnya.
4. **ASC terkunci tanpa indeksasi selama 3 tahun** pertama. Perpanjangan setelahnya kembali ke harga list yang berlaku saat itu, dikurangi maksimum 10%. Penyesuaian diberitahukan tertulis paling lambat **60 hari** sebelum periode berikutnya. Tidak ada indeksasi retroaktif.
5. Penurunan tingkat SLA hanya berlaku pada perpanjangan berikutnya, tidak di tengah periode.

---

## 8. Langkah Berikutnya

1. Penawaran ditinjau, dan pertanyaan Fase 2 di §1A dijawab bila memungkinkan. Pertanyaan dikirim dengan menyebut nomor penawaran {{NOMOR_PENAWARAN}}.
2. Kontrak dan lampiran teknis disusun; kriteria kelengkapan data master dan spesifikasi minimum server disepakati tertulis.
3. Kontrak ditandatangani, Termin 1 dibayar, environment disiapkan.
4. Migrasi data master, penyesuaian dokumen dan laporan, konfigurasi peran dan gudang.
5. Pelatihan 3 batch, UAT, berita acara.
6. Go-live dengan pendampingan 2 minggu, dilanjutkan garansi cacat 6 bulan.

---

## Lampiran

| | |
|---|---|
| **Lampiran 1** | Rincian 47 fitur per fungsi bisnis (di bawah) |
| **Lampiran 2** | **Daftar Harga Resmi NTB-PL-2026-09 (29 September 2026), utuh tanpa perubahan** (dilampirkan sebagai dokumen terpisah) |
| **Lampiran 3** | Lampiran kontrak: nilai kewajiban timbal balik K1–K3 dan K5, kriteria data master, spesifikasi minimum server |

---

## Lampiran 1: Rincian 47 Fitur

### 1.1 Data induk & referensi — 6 fitur

| Fitur | Fungsinya |
|---|---|
| Brand, Kategori, Kota | Klasifikasi produk dan wilayah sebagai dasar seluruh pelaporan |
| Divisi & Sub-divisi | Struktur lini produk mengikuti cara tim penjualan dibagi |
| Supplier | Data pemasok dan kaitannya dengan produk |
| Gudang | Definisi lokasi penyimpanan, termasuk multi-gudang |
| Produk | Data produk: kode, satuan, kemasan, harga dasar |
| Impor produk dari Excel | Unggah massal data produk, dengan validasi baris per baris |

### 1.2 Penjualan & pelanggan — 7 fitur

| Fitur | Fungsinya |
|---|---|
| Kelola Toko + Registrasi Toko | Data pelanggan/toko beserta alur pendaftaran toko baru |
| Grade Toko | Tingkatan pelanggan yang menentukan harga dan diskon otomatis |
| Penugasan Sales ↔ Toko | Pemetaan sales ke wilayah/toko, dasar KPI dan pembatasan akses |
| Katalog Digital Marketing | Katalog produk terkendali untuk dipakai sales di lapangan |
| Order / Pesanan | Pencatatan pesanan sampai siap diproses gudang |
| Purchase Order dari toko | Toko mengajukan pesanan sendiri, masuk sebagai order terverifikasi |
| Sales KPI & Target | Penetapan target dan pemantauan pencapaian per sales |

### 1.3 Penagihan, piutang & kas — 7 fitur

| Fitur | Fungsinya |
|---|---|
| Invoice Draft → Invoice | Alur dua tahap: draft dapat dikoreksi, invoice terbit tidak bisa diubah diam-diam |
| Invoice Cash | Penjualan tunai langsung |
| Invoice PDF | Cetak invoice sesuai layout perusahaan |
| Pembayaran | Pencatatan pelunasan, sebagian maupun penuh |
| Payment Request + bukti transfer | Pengajuan pembayaran disertai unggahan bukti transfer untuk verifikasi |
| Piutang & Aging | Posisi piutang per toko dengan pengelompokan umur |
| Invoice ledger + Store Credit | Buku besar invoice per toko dan saldo kredit toko, dengan penguncian per toko agar dua transaksi bersamaan tidak merusak saldo |

### 1.4 Gudang, pengiriman & persediaan — 8 fitur

| Fitur | Fungsinya |
|---|---|
| Delivery Order (pick → pack → ship → receive) | Alur pengiriman berstatus dari pengambilan sampai diterima toko |
| Driver | Data pengemudi dan penugasan pengiriman |
| Penugasan User ↔ Gudang | Pembatasan pengguna pada gudang yang menjadi tanggung jawabnya |
| Transfer antar gudang | Perpindahan stok antar lokasi dengan pencatatan dua sisi |
| Penyesuaian stok | Koreksi stok dengan alasan tercatat dan jejak audit |
| Rekonsiliasi / stock opname | Perhitungan fisik dan pencocokan terhadap catatan sistem |
| Retur barang | Pengembalian barang dari toko, terhubung ke saldo kredit toko |
| Stock movement ledger | Buku besar pergerakan stok: setiap perubahan punya sebab yang bisa ditelusuri |

### 1.5 Laporan & analitik — 6 fitur

| Fitur | Fungsinya |
|---|---|
| Dashboard 6 peran | Tampilan awal berbeda untuk owner, akuntan, admin, sales, gudang, dan supervisor |
| Owner & Accountant Analytics | Analitik penjualan, marjin, dan piutang untuk pemilik dan akuntan |
| Laporan & Report Export (CSV/XLSX/PDF) | Ekspor laporan dengan layout yang dapat disesuaikan |
| Template Laporan | Simpan format laporan yang sering dipakai |
| Laporan bulanan otomatis | Laporan periodik terbit sendiri tanpa diminta |
| Log ekspor | Catatan siapa mengekspor data apa dan kapan |

### 1.6 Pengguna, peran & keamanan akses — 6 fitur

| Fitur | Fungsinya |
|---|---|
| Auth + RBAC dua sumbu peran | Hak akses ditentukan oleh kombinasi jabatan dan lingkup kerja, bukan satu daftar peran datar |
| Kelola User & Member | Pembuatan dan penonaktifan akun pengguna |
| Daftar role | Definisi peran dan izin yang melekat padanya |
| Profil user | Data dan preferensi pengguna |
| StoreScope | Pembatasan otomatis: pengguna hanya melihat toko yang menjadi tanggung jawabnya |
| Audit Log | Jejak perubahan data penting: siapa, kapan, dari nilai apa ke nilai apa |

### 1.7 Integrasi & otomasi — 4 fitur

| Fitur | Fungsinya |
|---|---|
| API Key | Kunci akses terkendali untuk integrasi sistem lain |
| Notifikasi | Pemberitahuan peristiwa penting ke pengguna terkait |
| Realtime | Perubahan data tampil seketika di layar pengguna lain tanpa refresh |
| Background jobs | Pekerjaan berat (ekspor besar, laporan, kiriman terjadwal) berjalan di latar tanpa mengunci layar |

### 1.8 Platform & keandalan — 3 fitur

| Fitur | Fungsinya |
|---|---|
| Keamanan edge | Pembatasan laju permintaan, proxy tepercaya, dan gerbang API key |
| Observability | Log terstruktur dengan penanda permintaan, sehingga insiden dapat ditelusuri sampai baris kejadiannya |
| Kontrak OpenAPI + contract test di CI | Spesifikasi API diuji otomatis setiap perubahan; integrasi pihak lain tidak patah diam-diam |

**Total: 47 fitur** (6 + 7 + 7 + 8 + 6 + 6 + 4 + 3).


*Penawaran disusun berdasarkan Template Proposal Standar PROP-TPL-NTB-2026-09 dan Daftar Harga NTB-PL-2026-09 · Ato-team*
