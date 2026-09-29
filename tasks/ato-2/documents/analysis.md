# Baseline Biaya & Harga Normal — Sistem SMD/ERP untuk Pasar NTB

**Penyusun:** Rani (Commercial Analyst) · **Tugas:** [ATO-2](/ATO/issues/ATO-2) · **Revisi 3 · 29 September 2026**

**Apa yang berubah di Revisi 3.** Jawaban Q1–Q5 sudah masuk. Dokumen ini berhenti menjadi estimasi berpagar asumsi dan menjadi rekonstruksi berbasis input terkonfirmasi, dengan satu pengecualian yang dinyatakan terbuka (satuan angka Q3). Lima perubahan material:

1. **Biaya bangun terkonfirmasi: Rp 239.400.000** (252 orang-hari), bukan Rp 367.650.000. Bobot fitur dikalibrasi ulang terhadap effort nyata — ini mengubah cara modul Fase 2 harus dihargai.
2. **Harga list tetap Rp 175.000.000** dan sudah terbit sebagai [NTB-PL-2026-09](/ATO/issues/ATO-6#document-pricelist). Saya memverifikasi ulang dan **setuju** dengan pembacaan Ace: angka itu konsisten dengan Q1 = a dan Q2 = c. Jangkar utuh, tidak ada repricing.
3. **Q5 mengubah seluruh struktur biaya berjalan.** VPS milik pembeli, dikelola Ato-team. Hosting keluar dari ASC — bersama marjinnya.
4. **Koreksi: Q5 tidak menaikkan marjin ASC, Q5 menurunkannya.** Diskon ASC 25% untuk Pridata harus dibatalkan menjadi 0%, diganti konsesi satu kali. Aritmatikanya di §6.2.
5. **Pemulihan program tercapai untuk pertama kalinya:** biaya bangun pulih dengan **2 pembeli list tambahan**, dan Q2 = c menyatakan tersedia 3–4. Sebelumnya butuh 3 dari asumsi 5.

**Status angka:** effort dan jumlah pembeli sekarang terkonfirmasi. Yang masih asumsi adalah **rate biaya internal (A3)**, **beban dukungan (A8, A11)**, dan **skala Pridata (A12 — satuan "Rp 2 miliar" belum dikonfirmasi)**. Setiap angka menyertakan turunan dan keyakinannya.

---

## 0. Ringkasan Eksekutif

| Angka | Nilai | Keyakinan |
|---|---|---|
| **Biaya bangun terekonstruksi (terkonfirmasi Q1 = a)** | **Rp 239.400.000** (252 orang-hari) | **Tinggi** untuk effort, Sedang untuk rate |
| Rentang biaya bangun (sekarang digerakkan rate, bukan effort) | Rp 201.600.000 – Rp 302.400.000 | Sedang |
| **Harga list Tahun 1 — terbit & terkunci** | **Rp 175.000.000** (lisensi Rp 105.000.000 + implementasi Rp 70.000.000) | **Tinggi** (terbit sebagai NTB-PL-2026-09) |
| **ASC Dasar tanpa hosting terkelola (varian Q5)** | **Rp 27.500.000/tahun** | Tinggi (terbit) |
| Biaya internal ASC Dasar tanpa hosting — basis 3 pelanggan | Rp 19.665.000/tahun (marjin 28,5%) | Sedang |
| Biaya internal ASC Dasar tanpa hosting — **basis 1 pelanggan** | Rp 28.500.000/tahun (**rugi Rp 1.000.000/tahun**) | Sedang |
| Dibayar ke Ato-team, 3 tahun, harga list (Opsi A) | Rp 252.825.000 | Tinggi |
| Total biaya kepemilikan pembeli list, 3 tahun (termasuk VPS sendiri) | Rp 308.925.000 | Sedang |
| **Lantai walk-away komersial Tahun 1** | **Rp 104.000.000** | Tinggi |
| **Lantai walk-away ASC tahunan** | **Rp 33.000.000/th @1 pelanggan · Rp 23.000.000/th @3 pelanggan** | Tinggi |
| Lantai teknis absolut | Rp 66.500.000 Th1 + Rp 28.500.000/th | Tinggi |
| **Harga mitra riset Pridata — sistem** | **Rp 87.500.000** (50% dari list) | Tinggi |
| **Harga mitra riset Pridata — ASC** | **Rp 27.500.000/tahun, diskon 0%** | Tinggi |
| Dibayar Pridata ke Ato-team, 3 tahun | **Rp 156.250.000** — hemat Rp 96.575.000 (**38,2%**) | Tinggi |
| Neraca diskon: diberikan vs diterima | Rp 114.075.000 vs Rp 134.562.500 → **cadangan Rp 20.487.500** | Rendah–Sedang |
| **Pembeli list tambahan untuk memulihkan biaya bangun** | **2** (tersedia 3–4 menurut Q2 = c) | Sedang–Tinggi |

**Satu kalimat rekomendasi:** Kirim penawaran Pridata pada **Rp 87.500.000 untuk sistem (50% dari list NTB-PL-2026-09) + ASC Dasar tanpa hosting terkelola Rp 27.500.000/tahun tanpa diskon**, ditambah konsesi satu kali C1–C3 senilai Rp 26.575.000, seluruhnya diikat ke kewajiban K1–K5.

**Tiga temuan yang tidak nyaman, dinyatakan di muka:**

- **ASC Dasar Rp 27.500.000/tahun rugi Rp 1.000.000/tahun selama Pridata satu-satunya pelanggan.** Harga itu sudah terbit, jadi tidak bisa dinaikkan sampai NTB-PL-2027 nanti. Itu biaya program yang harus dicatat, bukan disembunyikan. Titik balik: pelanggan ASC kedua.
- **Q5 menukar marjin dengan pengurangan risiko, dan itu trade yang wajar — tetapi arahnya perlu diucapkan benar.** Ato-team menyerahkan **Rp 24.120.000 marjin per pembeli selama 3 tahun**, dan sebagai gantinya risiko A4 (infrastruktur meleset 2×, pendorong kerugian tahunan nomor satu di Revisi 2) **pindah sepenuhnya ke pembeli**. Bukan kenaikan marjin.
- **Satuan "Rp 2 miliar" di Q3 belum dikonfirmasi, dan itu bukan soal harga — itu soal apakah Pridata mampu menanggung biaya berjalannya.** Kalau Rp 2 miliar adalah omzet **per tahun**, biaya berjalan Rp 47.900.000/tahun (ASC + VPS) memakan **2,4% dari omzet** — risikonya pembatalan di Tahun 2, bukan penolakan harga di Tahun 1. Kalau **per bulan** (Rp 24 miliar/tahun), angka yang sama menjadi 0,20% dari omzet dan tidak ada masalah. Harganya tidak berubah di kedua pembacaan; yang berubah adalah apakah komitmen ASC 3 tahun (K4) boleh diminta.

---

## 1. Rekonstruksi Biaya Bangun — Terkonfirmasi dan Terkalibrasi

**Input terkonfirmasi (Q1 = a):** sistem dibangun dalam **± 6 bulan kalender oleh 2 orang penuh waktu.**

### 1.1 Effort total dari kalender terkonfirmasi

| Langkah | Nilai | Turunan |
|---|---:|---|
| Bulan kalender | 6,0 | Q1 = a |
| Orang penuh waktu | 2,0 | Q1 = a |
| Hari kerja per bulan | 21 | Konvensi, sama dengan Revisi 1–2 |
| **Total orang-hari** | **252,0** | 6 × 2 × 21 |

**Keyakinan: Tinggi.** Ini bukan lagi turunan dari bobot; ini kalender yang dikonfirmasi pengguna. Bobot fitur sekarang berbalik fungsi — dari alat estimasi menjadi alat kalibrasi.

### 1.2 Kalibrasi bobot: bobot mana yang ternyata benar

Revisi 1–2 memakai kolom tengah dan memprediksi 387 od. Effort nyata 252 od. **Prediksi kolom tengah terlalu tinggi 53,6%.** Yang cocok adalah kolom rendah:

| Tingkat | n | Bobot tengah (Rev 1–2) | Subtotal | **Bobot terkalibrasi** | **Subtotal** |
|---|---:|---:|---:|---:|---:|
| Easy — CRUD sederhana, tanpa efek samping lintas modul | 8 | 1,0 | 8,0 | **0,5** | **4,0** |
| Mid — alur status, relasi antar-entitas, scoping per peran | 12 | 3,0 | 36,0 | **2,0** | **24,0** |
| High — menyentuh uang atau stok, transaksi DB, banyak aturan bisnis | 14 | 6,0 | 84,0 | **4,0** | **56,0** |
| Advance — infrastruktur lintas modul | 13 | 10,0 | 130,0 | **6,0** | **78,0** |
| **Subtotal fitur** | **47** | | **258,0** | | **162,0** |
| Overhead non-fitur | | 50,0% | 129,0 | **55,5%** | **90,0** |
| **Total** | | | **387,0** | | **252,0** |

Bobot rendah + overhead **55,5%** mereproduksi 252 od dengan selisih 0,1 od. Itu bukan kebetulan yang dicocokkan belakangan — kolom rendah sudah ada di Revisi 1 sebagai batas bawah yang dipublikasikan; jawaban Q1 memilihnya.

**Rincian overhead terkalibrasi** (komponen Revisi 1 diskalakan ×1,11):

| Komponen | % dari effort fitur |
|---|---:|
| Discovery & analisis proses bisnis distribusi | 13,5% |
| Arsitektur, setup repo, CI/CD, environment | 9,0% |
| QA menyeluruh, UAT, perbaikan bug | 16,5% |
| Deployment, migrasi data awal, pelatihan | 7,5% |
| Manajemen proyek & koordinasi | 9,0% |
| **Total** | **55,5%** |

> **Konsekuensi yang harus dipakai orang lain, bukan hanya dicatat di sini.** Setiap modul yang belum dibangun — termasuk **Fase 2 (penerimaan barang)** — harus dihargai dengan **bobot terkalibrasi (0,5 / 2,0 / 4,0 / 6,0 + overhead 55,5%)**. Memakai bobot tengah Revisi 1–2 akan **melebihkan harga Fase 2 sebesar 53,6%**. Rumus harga Fase 2 yang berlaku: `od terkalibrasi × Rp 1.750.000` (rate tagih §1.4), minimum 5 od, dengan kriteria penerimaan sendiri. **Angkanya tetap menunggu ruang lingkup dan estimasi Bayu — tidak ada angka Fase 2 di dokumen ini.**

### 1.3 Rate biaya internal dan biaya bangun

| Langkah | Nilai | Turunan |
|---|---:|---|
| Gaji campuran (blended) per bulan | Rp 14.000.000 | Satu senior + satu mid fullstack, pasar Indonesia regional |
| Hari kerja per bulan | 21 | Konvensi |
| Biaya gaji per hari | Rp 666.667 | 14.000.000 ÷ 21 |
| Beban perusahaan +40% | × 1,40 | Perangkat, internet, listrik, lisensi tooling, waktu non-produktif, BPJS |
| Biaya per orang-hari | Rp 933.333 | 666.667 × 1,40 |
| **Rate biaya internal dipakai** | **Rp 950.000/od** | Dibulatkan |
| **BIAYA BANGUN TEREKONSTRUKSI** | **Rp 239.400.000** | 252 od × Rp 950.000 |

**Di mana ketidakpastiannya sekarang.** Effort sudah terkonfirmasi, jadi seluruh rentang biaya bangun sekarang digerakkan oleh satu variabel saja: rate.

| Rate biaya internal | Biaya bangun | Kapan ini yang benar |
|---:|---:|---|
| Rp 800.000/od | Rp 201.600.000 | Gaji campuran Rp 12.000.000/bulan, beban 40% |
| **Rp 950.000/od** | **Rp 239.400.000** | **Dipakai (asumsi A3)** |
| Rp 1.200.000/od | Rp 302.400.000 | Gaji campuran Rp 18.000.000/bulan, beban 40% |

Ini kemajuan nyata dibanding Revisi 2: rentangnya menyempit dari faktor 2,35× menjadi 1,50×, dan penyebabnya tinggal satu angka yang bisa diperiksa dari catatan penggajian Ato-team sendiri (**Q6**, §8).

### 1.4 Rate tagih (billing rate) — untuk harga, bukan untuk biaya

Tidak berubah oleh Q1; turunannya tidak menyentuh lama pembangunan.

| Langkah | Nilai | Turunan |
|---|---:|---|
| Rate biaya internal | Rp 950.000 | Dari 1.3 |
| Utilisasi tagih 70% | ÷ 0,70 | Waktu pra-penjualan, rapat, riset tidak tertagih |
| Rate impas | Rp 1.357.143 | |
| Cadangan garansi & rework +8% | × 1,08 | Perbaikan pasca-serah-terima |
| | Rp 1.465.714 | |
| Marjin target 18% | ÷ 0,82 | |
| | Rp 1.787.456 | |
| **Rate tagih dipakai** | **Rp 1.750.000/od** | Dibulatkan ke bawah; marjin efektif **16,2%** |

---

## 2. Biaya Berjalan per Tahun — Struktur Q5 (VPS Milik Pembeli, Dikelola Ato-team)

**Input terkonfirmasi (Q5):** *"kami yang akan melakukan pengelolaan tetapi itu VPS milik mereka."* Bukan managed hosting, bukan self-managed. Ini varian ketiga, dan sudah terbit di NTB-PL-2026-09 §4.1.

### 2.1 Apa yang pindah, dan apa yang muncul

| Komponen | Sebelum Q5 (managed hosting) | **Sesudah Q5** |
|---|---|---|
| VPS, PostgreSQL, object storage, backup, domain/TLS, monitoring — Rp 1.700.000/bulan = **Rp 20.400.000/tahun** | Biaya Ato-team, ditagih di dalam ASC sebagai komponen hosting Rp 26.500.000/tahun | **Biaya langsung pembeli.** Keluar dari pembukuan Ato-team dan keluar dari ASC. |
| Marjin hosting Rp 6.100.000/tahun (Rp 26.500.000 − Rp 20.400.000) | Pendapatan Ato-team | **Hilang.** Tidak ada penggantinya. |
| Risiko A4 (volume data jauh di atas perkiraan → infra 2×) | Kerugian Ato-team Rp 20.275.000/tahun | **Pindah ke pembeli.** Hilang dari daftar risiko Ato-team. |
| **Koordinasi infrastruktur milik pihak lain** | Tidak ada | **Muncul: +2,0 od/tahun = Rp 1.900.000/tahun** |

**Kenapa koordinasi itu biaya nyata, bukan angka pengaman.** Mengelola server yang bukan milik sendiri menambah pekerjaan yang tidak ada pada managed hosting: pengurusan akses dan kredensial yang dipegang pembeli, eskalasi ke penyedia VPS yang kontraknya bukan milik Ato-team, verifikasi bahwa backup yang dijalankan pihak lain benar-benar bisa direstore, dan triase insiden yang bersumber dari infrastruktur pembeli sebelum bisa dinyatakan bukan cacat aplikasi. Dua orang-hari per tahun adalah perkiraan hemat. Lihat asumsi **A11**.

### 2.2 Beban dukungan per tahun

| Aktivitas | od/tahun | Sifat |
|---|---:|---|
| Help desk & penanganan insiden (3 jam/minggu × 48 minggu) | 18,0 | Khusus per pelanggan |
| Pemeliharaan korektif (bug non-fitur, di luar garansi) | 12,0 | Khusus per pelanggan |
| Uji pemulihan backup (2× setahun) | 2,0 | Khusus per pelanggan |
| Koordinasi infrastruktur milik pembeli *(baru, Q5)* | 2,0 | Khusus per pelanggan |
| Patch keamanan & upgrade dependensi (4 × 2 od) | 8,0 | **Bersama** antar pelanggan |
| Rilis pemeliharaan & regression run | 6,0 | **Bersama** antar pelanggan |
| **Total** | **48,0** | 34 khusus + 14 bersama |

**Konsekuensi skala:** 14 od bersama dibagi ke seluruh basis pelanggan. Pada 1 pelanggan tidak terbagi sama sekali. Ini yang membuat ASC tahun-tahun awal tipis, dan itu diakui terbuka di §5.

### 2.3 Tingkatan SLA — biaya internal tanpa hosting terkelola

| | **Dasar** | **Standar** | **Prioritas** |
|---|---:|---:|---:|
| Help desk | 1 jam/mgg (6 od) | 3 jam/mgg (18 od) | 3 jam/mgg (18 od) |
| Pemeliharaan korektif | Hanya bug kritis (6 od) | Penuh (12 od) | Penuh (12 od) |
| Uji restore backup | 2 od | 2 od | 2 od |
| Koordinasi infrastruktur pembeli | 2 od | 2 od | 2 od |
| Jatah perubahan kecil | — | — | 12 od |
| Kunjungan on-site kuartalan | — | — | 4 od |
| Pangsa patch & rilis bersama (basis 3 pelanggan) | 4,7 od | 4,7 od | 4,7 od |
| **Total effort** | **20,7 od** | **38,7 od** | **54,7 od** |
| Biaya effort (× Rp 950.000) | Rp 19.665.000 | Rp 36.765.000 | Rp 51.965.000 |
| Biaya infrastruktur (ditanggung pembeli) | Rp 0 | Rp 0 | Rp 0 |
| **Total biaya internal/tahun** | **Rp 19.665.000** | **Rp 36.765.000** | **Rp 51.965.000** |
| **Harga list/tahun (NTB-PL-2026-09 §4.1)** | **Rp 27.500.000** | **Rp 51.500.000** | **Rp 72.500.000** |
| Marjin | Rp 7.835.000 (28,5%) | Rp 14.735.000 (28,6%) | Rp 20.535.000 (28,3%) |
| Waktu respons (hari kerja) | 8 jam | 4 jam | 2 jam |

### 2.4 Biaya ASC Dasar menurut jumlah pelanggan — ini tabel yang menentukan keputusan

| Basis pelanggan | Pangsa bersama | Total effort | Biaya internal/th | Harga list Rp 27.500.000 → | Marjin |
|---:|---:|---:|---:|---|---:|
| **1** | 14,0 od (tidak terbagi) | **30,0 od** | **Rp 28.500.000** | **di bawah biaya** | **−Rp 1.000.000 (−3,6%)** |
| 2 | 7,0 od | 23,0 od | Rp 21.850.000 | di atas biaya | +Rp 5.650.000 (20,5%) |
| **3** | 4,7 od | **20,7 od** | **Rp 19.665.000** | di atas biaya | **+Rp 7.835.000 (28,5%)** |
| 4 | 3,5 od | 19,5 od | Rp 18.525.000 | di atas biaya | +Rp 8.975.000 (32,6%) |

**Temuan yang harus dicatat, bukan dihaluskan:** harga ASC Dasar yang **sudah terbit** rugi Rp 1.000.000/tahun selama Pridata satu-satunya pelanggan. Harga list tidak boleh diubah — itu merusak jangkar (§6.8 klausul 1) dan masa berlakunya sampai 30 Juni 2027. Jadi kerugian itu diterima sebagai **biaya program yang dibatasi waktu**, dan yang menghapusnya bukan kenaikan harga melainkan **pelanggan ASC kedua**. Ini mengikat harga dukungan langsung ke program penjualan, dan itu memang hubungan yang sebenarnya.

---

## 3. Harga List "Normal" — Terbit dan Terverifikasi Ulang

### 3.1 Verifikasi: apakah Rp 175.000.000 masih benar setelah Q1 dan Q2?

Harga list terbit sebagai **NTB-PL-2026-09, 29 September 2026 – 30 Juni 2027**. Pertanyaannya bukan lagi "berapa harganya", tetapi "apakah angka yang sudah terbit bertahan terhadap input terkonfirmasi". **Bertahan.** Berikut ujinya, dijalankan terbalik dari harga terbit ke asumsi yang tersirat di dalamnya:

| Langkah | Nilai | Turunan |
|---|---:|---|
| Komponen lisensi terbit | Rp 105.000.000 | NTB-PL-2026-09 |
| Marjin IP & risiko produk yang tertanam | ÷ 1,40 | Konvensi §3.2 Revisi 1 |
| **Amortisasi per pembeli yang tersirat** | **Rp 75.000.000** | 105.000.000 ÷ 1,40 |
| Biaya bangun terkonfirmasi | Rp 239.400.000 | §1.3 |
| **Jumlah pembeli yang tersirat di harga terbit** | **3,19 pembeli** | 239.400.000 ÷ 75.000.000 |
| Jumlah pembeli menurut Q2 = c | **3–4 pembeli** | Jawaban pengguna |
| **Verdict** | **Konsisten** | 3,19 berada di dalam 3–4 |

Rentang yang benar untuk Q2 = c, dihitung maju:

| Pembeli target | Amortisasi/pembeli | Lisensi (×1,40) | **Harga list Th1** |
|---:|---:|---:|---:|
| 3 | Rp 79.800.000 | Rp 111.720.000 | **Rp 181.720.000** |
| **Terbit** | **Rp 75.000.000** | **Rp 105.000.000** | **Rp 175.000.000** |
| 4 | Rp 59.850.000 | Rp 83.790.000 | **Rp 153.790.000** |

**Saya setuju dengan pembacaan Ace dan menyatakannya eksplisit:** Rp 175.000.000 berada di dalam rentang Rp 153.790.000 – Rp 181.720.000 (Ace mengutipnya dibulatkan sebagai Rp 154.000.000 – Rp 181.500.000; selisih pembulatan ≤ 0,2% dan tidak melewati ambang keputusan apa pun), dekat ujung 3-pembeli, yaitu ujung yang konservatif. **Tidak ada repricing harga list di Revisi 3.** Jangkar utuh dan masih bisa dipertahankan di depan pembeli yang skeptis: setiap komponennya bisa ditelusuri ke kalender pembangunan yang dikonfirmasi dan jumlah pembeli yang dinyatakan pengguna sendiri.

### 3.2 Struktur harga list yang berlaku

| Komponen | Turunan | **Harga list** |
|---|---|---:|
| Lisensi perpetual (satu badan usaha, satu instance produksi) | Amortisasi Rp 75.000.000 × 1,40 | **Rp 105.000.000** |
| Implementasi & go-live | 40 od × rate tagih Rp 1.750.000 | **Rp 70.000.000** |
| **Harga list Tahun 1** | | **Rp 175.000.000** |
| ASC Dasar **tanpa hosting terkelola** (mulai bulan ke-4) | Tabel 2.3 | **Rp 27.500.000/tahun** |
| ASC Dasar dengan hosting terkelola *(tidak berlaku untuk Pridata)* | Tabel 2.3 + Rp 26.500.000 | Rp 54.000.000/tahun |
| Infrastruktur (VPS, DB, storage, backup) — **dibayar pembeli langsung** | Asumsi A4 | ≈ Rp 20.400.000/tahun |

**Rincian 40 orang-hari implementasi** (ini yang membenarkan Rp 70.000.000, bukan pembulatan):

| Aktivitas | od |
|---|---:|
| Provisioning & konfigurasi environment | 3 |
| Migrasi data master (produk, toko, supplier, saldo awal piutang) | 8 |
| Penyesuaian layout dokumen & template laporan (invoice, DO, surat jalan) | 5 |
| Konfigurasi peran, gudang, grade toko, target & KPI sales | 4 |
| Pelatihan 3 batch (admin, sales, gudang/akunting) | 6 |
| UAT & pendampingan go-live (2 minggu) | 10 |
| Manajemen proyek implementasi | 4 |
| **Total** | **40** |

### 3.3 Isi paket (yang dibeli dan yang tidak)

**Termasuk — 47 fitur terkirim:**

- **Master & referensi (8 fitur Easy):** Brand/Kategori/Kota; Divisi & Sub-divisi; Supplier; Driver; Gudang; Profil user; Daftar role; Log ekspor.
- **Operasional & pengelolaan (12 fitur Mid):** Kelola User & Member; Kelola Toko + Registrasi Toko; Produk; Katalog Digital Marketing; Penugasan Sales↔Toko; Penugasan User↔Gudang; Notifikasi; Template Laporan; Audit Log; API Key; Grade Toko; Purchase Order dari toko.
- **Transaksi uang & stok (14 fitur High):** Order/Pesanan; Invoice Draft→Invoice; Invoice Cash; Invoice PDF; Delivery Order (pick→pack→ship→receive); Pembayaran; Payment Request + bukti transfer; Retur barang; Penyesuaian stok; Transfer antar gudang; Rekonsiliasi/stock opname; Piutang & Aging; Sales KPI & Target; Dashboard 6 peran.
- **Platform & kendali (13 fitur Advance):** Auth + RBAC dua sumbu peran; StoreScope; Stock movement ledger; Invoice ledger + Store Credit dengan advisory lock per toko; Owner & Accountant Analytics; Laporan & Report Export CSV/XLSX/PDF layout kustom; Background jobs BullMQ; Laporan bulanan otomatis; Impor produk dari Excel; Realtime SSE via Redis pub/sub; Keamanan edge (rate limit, trusted proxies, API key gate); Observability (pino + requestId); OpenAPI contract + contract test di CI.
- Pengelolaan aplikasi di atas VPS pembeli, backup harian, garansi cacat 3 bulan sejak go-live.
- Pelatihan 3 batch dan dokumentasi pengguna.

**Tidak termasuk (dihargai terpisah):**

| Item | Status harga |
|---|---|
| **Modul Fase 2 — Penerimaan barang (anti human error)** | **Belum dibangun. Belum diestimasi. Tidak ada angka di dokumen ini.** Ruang lingkup ada di [ATO-3](/ATO/issues/ATO-3); estimasi effort milik Bayu. Dihargai dengan **bobot terkalibrasi §1.2 × Rp 1.750.000**, kriteria penerimaan sendiri. |
| **Infrastruktur (VPS, DB, storage, bandwidth)** | **Ditanggung pembeli langsung** (Q5). Bukan baris harga Ato-team, dan bukan baris yang bisa didiskon. |
| Badan usaha kedua / instance produksi tambahan | Lisensi penuh (list) |
| Integrasi pihak ketiga (e-faktur, bank, marketplace, payment gateway) | Proyek terpisah, perlu scoping |
| Modul atau laporan kustom di luar 47 fitur | Rp 1.750.000/od, minimum 5 od |
| Migrasi data historis di luar saldo awal | Rp 1.750.000/od |
| Aplikasi mobile native | Belum ada; bukan bagian dari paket |

**Aturan keras (scope boundary pricing):** tidak ada satu pun item di tabel ini yang boleh diserap ke harga dasar untuk menutup transaksi. Kalau pembeli menuntutnya, harga naik atau ruang lingkupnya dikeluarkan dari kontrak — tidak ada jalan ketiga.

### 3.4 Plafon berbasis nilai — dua pembacaan Q3, dua kesimpulan berbeda

Jawaban Q3 adalah **"2 miliar"** tanpa satuan. Kartu klarifikasi Ace di [ATO-6](/ATO/issues/ATO-6) masih menunggu jawaban. Saya tidak menunda dokumen ini karena satu satuan; saya memodelkan keduanya, dan menyatakan mana yang saya pakai sebagai asumsi kerja beserta alasannya.

**Pembacaan 1 — omzet Rp 24 miliar/tahun (Rp 2 miliar per bulan).** Persediaan diskalakan 0,6× ke Rp 1,8 miliar, piutang ke Rp 2,4 miliar.

| Sumber nilai | Turunan | Nilai/tahun |
|---|---|---:|
| Pengurangan selisih stok | Ledger stok + opname + transfer gudang: selisih 1,0% → 0,5% dari persediaan Rp 1,8 M | Rp 9.000.000 |
| Percepatan kas dari piutang | Rp 2,4 M × 5/365 = Rp 32.876.712 kas bebas × biaya modal 12% | Rp 3.900.000 |
| Pengurangan piutang macet | 0,5% × Rp 24 M = Rp 120.000.000; aging menurunkan 15% | Rp 18.000.000 |
| Waktu administrasi | 2 staf × 2 jam/hari × 25 hari × 12 bln = 1.200 jam × Rp 30.000, direalisasi 50% | Rp 18.000.000 |
| Waktu akuntan | 3 hari/bulan × 12 × Rp 350.000, direalisasi 50% | Rp 6.300.000 |
| Kesalahan harga & diskon per grade toko | 0,1% × Rp 24 M = Rp 24.000.000; grade toko + katalog terkendali menghapus 50% | Rp 12.000.000 |
| **Total nilai tahunan** | | **Rp 67.200.000** |
| **Plafon harga masuk** (× 1,25, payback SME 12–18 bulan) | | **Rp 84.000.000** |

**Pembacaan 2 — omzet Rp 2 miliar/tahun (literal).** Persediaan Rp 150.000.000, piutang Rp 200.000.000.

| Sumber nilai | Turunan | Nilai/tahun |
|---|---|---:|
| Pengurangan selisih stok | 0,5% × Rp 150.000.000 | Rp 750.000 |
| Percepatan kas dari piutang | Rp 200.000.000 × 5/365 = Rp 2.739.726 × 12% | Rp 300.000 |
| Pengurangan piutang macet | 0,5% × Rp 2 M = Rp 10.000.000; aging menurunkan 15% | Rp 1.500.000 |
| Waktu administrasi | 1 staf × 2 jam/hari × 25 × 12 = 600 jam × Rp 30.000, direalisasi 50% | Rp 9.000.000 |
| Waktu akuntan | 1 hari/bulan × 12 × Rp 350.000, direalisasi 50% | Rp 2.100.000 |
| Kesalahan harga & diskon | 0,1% × Rp 2 M = Rp 2.000.000, dihapus 50% | Rp 1.000.000 |
| **Total nilai tahunan** | | **Rp 14.650.000** |
| **Plafon harga masuk** | | **Rp 18.312.500** |

**Uji yang paling tajam bukan plafon harga, tapi rasio biaya berjalan terhadap omzet:**

| Pembacaan | Biaya berjalan/th (ASC Rp 27.500.000 + VPS Rp 20.400.000) | % dari omzet | Artinya |
|---|---:|---:|---|
| Rp 24 miliar/tahun | Rp 47.900.000 | **0,20%** | Wajar. Tidak ada masalah keberlanjutan. |
| Rp 2 miliar/tahun | Rp 47.900.000 | **2,4%** | Pada marjin bersih distributor 3–5%, ini memakan sebagian besar laba. **Risikonya pembatalan di Tahun 2, bukan penolakan harga di Tahun 1.** |

**Asumsi kerja yang saya pakai: pembacaan 1 (Rp 24 miliar/tahun), diberi label A12.** Tiga alasan, dan saya nyatakan kekuatan masing-masing:

1. **Triangulasi dengan Q4 = d (kuat).** Pridata pernah mengevaluasi SAP Business One / Odoo berbayar. Perusahaan dengan omzet Rp 2 miliar/tahun tidak masuk ke ruang evaluasi itu — biaya lisensi dan implementasinya sendiri sudah tidak proporsional terhadap seluruh anggaran perusahaan sebesar itu.
2. **Triangulasi dengan sistem yang benar-benar dibangun (kuat).** 47 fitur dengan 6 peran dashboard, penugasan sales↔toko, penugasan user↔gudang, transfer antar gudang, grade toko, dan piutang aging menggambarkan organisasi dengan beberapa gudang dan tim sales berjenjang. Kebutuhan itu tidak muncul pada omzet Rp 167 juta/bulan.
3. **Cara orang menyebut angka (lemah, saya sebut karena relevan tapi tidak saya bebani).** Pelaku usaha distribusi di Indonesia sering menyebut skala usahanya dalam omzet bulanan.

**Kalau A12 salah dan Rp 2 miliar/tahun literal, yang berubah bukan harga.** Harga list terkunci, dan §3.5 di bawah tetap menyatakan jawabannya adalah ruang lingkup yang lebih kecil, bukan list yang lebih murah. Yang berubah adalah: **komitmen ASC minimum 3 tahun (K4) tidak boleh diminta**, karena meminta komitmen yang tidak terjangkau menghasilkan wanprestasi, bukan pendapatan. Gantinya: ASC tahunan tanpa minimum, dan nilai K4 (Rp 10.312.500) dikeluarkan dari neraca konsiderasi §6.5 — masih tertutup oleh cadangan Rp 20.487.500.

**Keyakinan model nilai: Rendah.** Ini estimasi dari profil yang diasumsikan, bukan pengukuran di Pridata. Model ini hanya menghitung manfaat yang bisa dikuantifikasi; manfaat kendali, jejak audit, dan pemisahan peran tidak masuk. Jadi angkanya adalah **batas bawah manfaat, bukan batas atas**. Lihat **A6**, **A7**, **A12**.

### 3.5 Silang-uji: apakah harga list masuk akal?

| Uji | Hasil | Lulus? |
|---|---|---|
| Di atas lantai walk-away Th1 (Rp 104.000.000) | Rp 175.000.000 = 1,68× lantai | ✅ |
| Konsisten dengan Q1 = a dan Q2 = c | Lisensi Rp 105.000.000 ⇒ 3,19 pembeli tersirat; Q2 = c menyatakan 3–4 | ✅ |
| ASC Dasar di atas lantai ASC basis 3 pelanggan (Rp 23.000.000) | Rp 27.500.000 = 1,20× | ✅ |
| ASC Dasar di atas lantai ASC basis 1 pelanggan (Rp 33.000.000) | Rp 27.500.000 = 0,83× | ❌ **Rugi Rp 1.000.000/th sampai pelanggan ASC kedua masuk** (§2.4) |
| Payback 3 tahun, pembeli omzet Rp 40 miliar (profil A6) | TCO3 Rp 308.925.000 ÷ nilai Rp 107.000.000 = **2,89 th** | ✅ |
| Payback 3 tahun, pembeli omzet Rp 24 miliar | Rp 308.925.000 ÷ Rp 67.200.000 = **4,60 th** | ❌ Di luar toleransi 3 tahun; masuk toleransi 5 tahun |
| Payback, pembeli omzet Rp 2 miliar | Rp 308.925.000 ÷ Rp 14.650.000 = **21,1 th** | ❌ Tidak ada model komersial yang layak pada skala itu |

**Ambang pembeli yang bisa dipakai Ace sebagai kriteria kualifikasi** — diinterpolasi linier antara dua titik yang dihitung di §3.4 (gradien Rp 2.487.500 nilai tahunan per Rp 1 miliar omzet; **diberi label sebagai interpolasi**, karena komponen waktu staf sebenarnya bergerak bertingkat, bukan mulus):

| Toleransi payback pembeli | Nilai tahunan yang dibutuhkan | **Omzet minimum pembeli** |
|---|---:|---:|
| 3 tahun | Rp 102.975.000 | **≈ Rp 38 miliar/tahun** |
| 4 tahun | Rp 77.231.250 | **≈ Rp 28 miliar/tahun** |
| 5 tahun | Rp 61.785.000 | ≈ Rp 22 miliar/tahun |

**Implikasi, dan ini menggantikan pernyataan "≥ Rp 35 miliar" di Revisi 1–2 yang terlalu optimistis:** harga list Rp 175.000.000 defensible untuk distributor dengan **omzet ≥ Rp 28 miliar/tahun** pada toleransi payback 4 tahun, dan ≥ Rp 38 miliar pada toleransi 3 tahun. Untuk distributor NTB yang lebih kecil, yang benar adalah **paket ruang lingkup lebih kecil atau Opsi B (langganan) — bukan menurunkan harga list.** Menurunkan list untuk mengejar pembeli kecil merusak jangkar diskon Pridata dan melanggar §6.8 klausul 5.

---

## 4. Tiga Opsi Komersial dan Total Biaya Kepemilikan

Semua opsi memakai varian **tanpa hosting terkelola** (Q5). Kolom "dibayar ke Ato-team" adalah pendapatan Ato-team; kolom "total biaya kepemilikan" menambahkan infrastruktur yang dibayar pembeli langsung — itu yang sebenarnya dibandingkan pembeli.

### Opsi A — Lisensi perpetual + ASC *(rekomendasi)*

| | Tahun 1 | Tahun 2 | Tahun 3 | **Total 3 tahun** |
|---|---:|---:|---:|---:|
| Lisensi perpetual | Rp 105.000.000 | — | — | Rp 105.000.000 |
| Implementasi & go-live | Rp 70.000.000 | — | — | Rp 70.000.000 |
| ASC Dasar tanpa hosting (Th1 pro rata 9 bln; indeksasi 8% mulai Th3) | Rp 20.625.000 | Rp 27.500.000 | Rp 29.700.000 | Rp 77.825.000 |
| **Dibayar ke Ato-team** | **Rp 195.625.000** | **Rp 27.500.000** | **Rp 29.700.000** | **Rp 252.825.000** |
| Infrastruktur milik pembeli (Th1 pro rata 9 bln) | Rp 15.300.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 56.100.000 |
| **Total biaya kepemilikan** | **Rp 210.925.000** | **Rp 47.900.000** | **Rp 50.100.000** | **Rp 308.925.000** |

Pembeli memiliki lisensi selamanya. Kalau ASC dihentikan, sistem tetap jalan di VPS pembeli, tetapi patch, dukungan, dan pengelolaan berhenti — pembeli wajib mengambil alih pengelolaan aplikasinya sendiri.

**Staging pembayaran (cash-flow staging), atas Rp 175.000.000:**

| Milestone | % | Nilai |
|---|---:|---:|
| Tanda tangan kontrak | 30% | Rp 52.500.000 |
| Environment siap + migrasi data master selesai & diverifikasi | 25% | Rp 43.750.000 |
| Berita acara UAT diterima | 25% | Rp 43.750.000 |
| 30 hari setelah go-live tanpa insiden kritis | 20% | Rp 35.000.000 |

ASC ditagih tahunan di muka. Opsi kuartalan tersedia dengan biaya administrasi +5%.

### Opsi B — Langganan penuh (tanpa lisensi di muka)

Langganan disesuaikan dengan Q5: komponen hosting Rp 26.500.000/tahun (Rp 2.208.333/bulan) dikeluarkan dari Rp 9.250.000/bulan → **Rp 7.000.000/bulan** (dibulatkan ke bawah dari Rp 7.041.667).

| | Tahun 1 | Tahun 2 | Tahun 3 | **Total 3 tahun** |
|---|---:|---:|---:|---:|
| Biaya aktivasi & implementasi (disubsidi dari Rp 70.000.000) | Rp 45.000.000 | — | — | Rp 45.000.000 |
| Langganan Rp 7.000.000/bulan (hak pakai + SLA Dasar + pengelolaan) | Rp 84.000.000 | Rp 84.000.000 | Rp 84.000.000 | Rp 252.000.000 |
| **Dibayar ke Ato-team** | **Rp 129.000.000** | **Rp 84.000.000** | **Rp 84.000.000** | **Rp 297.000.000** |
| Infrastruktur milik pembeli (Th1 pro rata 9 bln) | Rp 15.300.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 56.100.000 |
| **Total biaya kepemilikan** | **Rp 144.300.000** | **Rp 104.400.000** | **Rp 104.400.000** | **Rp 353.100.000** |

Langganan berjalan sejak tanda tangan (12 bulan penuh di Tahun 1), bukan sejak go-live. Minimum kontrak 3 tahun. Hak pakai berhenti saat langganan berhenti; Ato-team wajib menyerahkan ekspor data lengkap dalam 14 hari.

### Opsi C — Kemitraan 5 tahun (harga masuk rendah, komitmen panjang)

| | Tahun 1 | Tahun 2 | Tahun 3 | **Total 3 tahun** | Total 5 tahun |
|---|---:|---:|---:|---:|---:|
| Lisensi perpetual (potongan Rp 35.000.000 dari list) | Rp 70.000.000 | — | — | Rp 70.000.000 | Rp 70.000.000 |
| Implementasi & go-live | Rp 70.000.000 | — | — | Rp 70.000.000 | Rp 70.000.000 |
| ASC **Standar** tanpa hosting, wajib 5 tahun, terkunci tanpa indeksasi (Th1 pro rata 9 bln) | Rp 38.625.000 | Rp 51.500.000 | Rp 51.500.000 | Rp 141.625.000 | Rp 244.625.000 |
| **Dibayar ke Ato-team** | **Rp 178.625.000** | **Rp 51.500.000** | **Rp 51.500.000** | **Rp 281.625.000** | **Rp 384.625.000** |
| Infrastruktur milik pembeli | Rp 15.300.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 56.100.000 | Rp 96.900.000 |
| **Total biaya kepemilikan** | **Rp 193.925.000** | **Rp 71.900.000** | **Rp 71.900.000** | **Rp 337.725.000** | **Rp 481.525.000** |

Konsiderasi yang ditukar untuk potongan lisensi Rp 35.000.000: komitmen ASC Standar 5 tahun (nilai kontrak terkunci Rp 244.625.000 — Th1 pro rata 9 bulan + 4 tahun penuh) dan pembayaran tahunan di muka.

### Perbandingan dan rekomendasi

| | Opsi A | Opsi B | Opsi C |
|---|---:|---:|---:|
| Total biaya kepemilikan Tahun 1 | Rp 210.925.000 | **Rp 144.300.000** | Rp 193.925.000 |
| Dibayar ke Ato-team, Tahun 1 | Rp 195.625.000 | **Rp 129.000.000** | Rp 178.625.000 |
| **Total biaya kepemilikan 3 tahun** | **Rp 308.925.000** | Rp 353.100.000 | Rp 337.725.000 |
| Recurring Tahun 3 (total, termasuk VPS sendiri) | **Rp 50.100.000** | Rp 104.400.000 | Rp 71.900.000 |
| Kepemilikan di akhir Tahun 3 | Lisensi perpetual | Tidak ada | Lisensi perpetual |
| Komitmen minimum | Tidak ada | 3 tahun | 5 tahun |

**Rekomendasi: Opsi A.**

- **B kalah** karena total biaya kepemilikan 3 tahun **Rp 44.175.000 (14,3%) lebih mahal** dan pembeli tidak memiliki apa pun di akhir. B hanya menang kalau kas Tahun 1 benar-benar ketat — dan itu bisa diatasi lebih murah lewat staging pembayaran Opsi A, yang sudah menunda 70% dari harga sistem ke milestone setelah tanda tangan.
- **C kalah** karena **Rp 28.800.000 (9,3%) lebih mahal** selama 3 tahun dan mengunci pembeli baru — yang belum punya rekam jejak dengan Ato-team — ke ASC Standar 5 tahun senilai Rp 244.625.000, padahal SLA Dasar cukup untuk tahun-tahun awal. C menjual diskon lisensi Rp 35.000.000 untuk komitmen yang sulit ditegakkan pada SME; risiko wanprestasinya lebih besar daripada nilainya.
- **A menang** karena harga masuknya paling jujur, recurring-nya paling rendah, tidak ada kewajiban yang perlu ditegakkan lewat pengadilan, dan pembeli memiliki lisensinya.

**Satu pengecualian yang harus dinyatakan:** untuk pembeli dengan omzet di bawah Rp 28 miliar/tahun (§3.5), tidak ada satu pun dari tiga opsi ini yang lolos uji payback. Jawabannya paket ruang lingkup lebih kecil, yang belum ada dan perlu di-scoping — bukan menurunkan harga salah satu opsi.

### Downside framing — apa yang dibayar pembeli kalau berjalan lambat (Opsi A, Tahun 1)

| Skenario buruk | Tambahan biaya |
|---|---:|
| Data master kotor → migrasi butuh +15 od | + Rp 26.250.000 |
| Go-live mundur 2 bulan → sistem lama jalan paralel (asumsi biaya internal pembeli Rp 8.000.000/bulan) | + Rp 16.000.000 |
| Batch pelatihan ulang tambahan (2 od) | + Rp 3.500.000 |
| **VPS pembeli undersized** → upgrade ke 8 vCPU / 16 GB (+Rp 700.000/bulan, 9 bulan) | + Rp 6.300.000 |
| **Tahun 1 kasus lambat (total biaya kepemilikan)** | **Rp 262.975.000** |

Baris keempat adalah risiko baru yang muncul dari Q5: pada managed hosting, salah sizing adalah masalah Ato-team; pada VPS milik pembeli, itu tagihan pembeli. **Ini harus disebut di penawaran, bukan ditemukan pembeli sendiri di bulan ketiga.**

**Mitigasi yang harus masuk kontrak:**
1. Pembersihan data master pembeli adalah *prasyarat* pembayaran tahap 2, dengan kriteria penerimaan tertulis (format, kelengkapan kode produk, saldo awal piutang terekonsiliasi). Ini memindahkan risiko ke pihak yang bisa mengendalikannya.
2. **Spesifikasi minimum VPS dinyatakan tertulis sebelum tanda tangan** (4 vCPU / 8 GB / SSD, PostgreSQL terpisah atau terkelola, backup off-site retensi 30 hari). Kalau pembeli menyediakan di bawah spesifikasi itu, jaminan waktu respons SLA tidak berlaku — sudah dinyatakan di NTB-PL-2026-09 §4.1 dan harus diulang di kontrak.

---

## 5. Lantai Walk-Away

### 5.1 Lantai komersial (untuk pembeli NTB baru mana pun)

| Komponen | Nilai | Turunan |
|---|---:|---|
| Biaya langsung implementasi | Rp 38.000.000 | 40 od × Rp 950.000 (biaya internal) |
| Biaya berjalan Tahun 1, basis 1 pelanggan, tanpa hosting | Rp 28.500.000 | 30,0 od × Rp 950.000 (§2.4) |
| Kontribusi minimum ke pemulihan biaya bangun | Rp 37.500.000 | 50% dari amortisasi per pembeli Rp 75.000.000 (§3.1) |
| **LANTAI WALK-AWAY TAHUN 1** | **Rp 104.000.000** | 38.000.000 + 28.500.000 + 37.500.000 |

**Lantai ASC tahunan** (biaya berjalan × 1,15 untuk beban risiko):

| Basis pelanggan | Biaya berjalan | **Lantai ASC** | Harga list Rp 27.500.000 |
|---:|---:|---:|---|
| 1 | Rp 28.500.000 | **Rp 33.000.000/th** | ❌ di bawah lantai |
| 2 | Rp 21.850.000 | Rp 25.000.000/th | ✅ di atas lantai |
| 3 | Rp 19.665.000 | **Rp 23.000.000/th** | ✅ di atas lantai |

**Di bawah Rp 104.000.000 untuk sistem, tolak transaksinya.** Bukan negosiasikan — tolak. Untuk ASC, harga list sudah terbit di Rp 27.500.000 dan tidak bisa dinaikkan sampai 30 Juni 2027; selisih terhadap lantai basis-1-pelanggan diterima sebagai biaya program yang dibatasi waktu (§2.4), **bukan preseden untuk menjual ASC di bawah Rp 27.500.000 kepada siapa pun.**

### 5.2 Lantai teknis absolut

**Rp 66.500.000 Tahun 1** (biaya langsung implementasi Rp 38.000.000 + biaya berjalan Rp 28.500.000, nol kontribusi ke pemulihan biaya bangun) **+ Rp 28.500.000/tahun**.

Menjual di level ini berarti Ato-team bekerja tanpa pernah memulihkan Rp 239.400.000 yang sudah dikeluarkan. **Dilarang untuk pembeli komersial biasa.** Satu-satunya pengecualian adalah kasus mitra riset di §6, yang dibenarkan bukan oleh harganya melainkan oleh konsiderasi non-tunai yang diterima sebagai gantinya.

Posisi Pridata terhadap kedua lantai:

| | Nilai | Terhadap lantai |
|---|---:|---|
| Harga sistem mitra riset | Rp 87.500.000 | **Rp 16.500.000 di bawah** lantai komersial Rp 104.000.000 |
| | | **Rp 21.000.000 di atas** lantai teknis absolut Rp 66.500.000 |

Ini persis posisi yang dimaksudkan: di bawah lantai komersial (karena itu memang diskon), di atas lantai teknis (karena itu bukan pemberian), dan selisihnya dibayar oleh K1–K5.

### 5.3 Pemulihan tingkat program — verdict yang berubah di Revisi 3

| Langkah | Nilai |
|---|---:|
| Biaya bangun terkonfirmasi | Rp 239.400.000 |
| Kontribusi Pridata (harga sistem Rp 87.500.000 − biaya implementasi Rp 38.000.000) | (Rp 49.500.000) |
| **Sisa yang harus dipulihkan** | **Rp 189.900.000** |
| Kontribusi lisensi per pembeli list | Rp 105.000.000 |
| **Pembeli list tambahan yang dibutuhkan** | **1,81 → 2 pembeli** |
| Pembeli yang tersedia menurut Q2 = c | **3–4 pembeli** |
| **VERDICT** | **Program pulih dengan 2 dari 3–4 pembeli. Sisa 1–2 pembeli adalah marjin murni.** |

Ini perubahan paling menguntungkan di Revisi 3, dan sebabnya bisa ditunjuk: biaya bangun ternyata **Rp 128.250.000 lebih rendah** dari kasus tengah Revisi 1–2, sementara harga list terbit menahan lisensi di Rp 105.000.000. Untuk pertama kalinya kebutuhan pemulihan (2 pembeli) berada **di dalam** kapasitas pasar yang dinyatakan pengguna sendiri (3–4 pembeli), bukan di atasnya.

Kontribusi Pridata terhadap biaya bangun sekarang **20,7%** (Rp 49.500.000 dari Rp 239.400.000), naik dari 13,5% di Revisi 2 — bukan karena Pridata membayar lebih, tetapi karena biaya bangunnya lebih kecil.

Sensitivitas terhadap satu-satunya asumsi yang tersisa di biaya bangun (rate, **A3**):

| Rate biaya internal | Biaya bangun | Sisa setelah Pridata | Pembeli list tambahan |
|---:|---:|---:|---:|
| Rp 800.000/od | Rp 201.600.000 | Rp 152.100.000 | **2 pembeli** |
| **Rp 950.000/od** | **Rp 239.400.000** | **Rp 189.900.000** | **2 pembeli** |
| Rp 1.200.000/od | Rp 302.400.000 | Rp 244.900.000 | **3 pembeli** |

Bahkan pada rate tertinggi, kebutuhan pemulihan (3 pembeli) masih berada di dalam Q2 = c. **Kelayakan program tidak lagi bergantung pada asumsi yang belum diverifikasi.**

---

## 6. Struktur Diskon Mitra Riset 50% — CV Pridata Jaya

### 6.1 Prinsip: diskon berlaku pada IP dan jasa, bukan pada kas keluar — dan sekarang tidak ada lagi ruang di ASC

Diskon 50% dikenakan pada **harga sistem (lisensi + implementasi)**. Itu angka headline, dan itu benar.

Di Revisi 1–2, ASC masih punya ruang diskon 25% karena komponen dukungan (Rp 27.500.000) berada di atas biayanya sementara komponen hosting (Rp 26.500.000) menutup kas keluar. **Q5 menghapus ruang itu.** Hosting hilang dari ASC bersama marjinnya, biaya koordinasi infrastruktur milik pihak lain masuk, dan yang tersisa adalah baris tunggal yang harga listnya sudah berada di bawah biayanya selama Pridata satu-satunya pelanggan.

### 6.2 Koreksi arah: Q5 menurunkan marjin ASC, tidak menaikkannya

Ace melaporkan ke pengguna bahwa Q5 "menaikkan marjin ASC". Arahnya terbalik, pada nilai absolut maupun persentase, dan koreksinya perlu masuk sebelum penawaran dikirim karena ia menentukan apakah diskon ASC 25% boleh diberikan.

**Nilai absolut, harga list:**

| | Sebelum Q5 | Sesudah Q5 | Selisih |
|---|---:|---:|---:|
| Harga ASC Dasar | Rp 54.000.000 | Rp 27.500.000 | −Rp 26.500.000 |
| Biaya internal (basis 3 pelanggan) | Rp 38.165.000 | Rp 19.665.000 | −Rp 18.500.000 |
| **Marjin** | **Rp 15.835.000** | **Rp 7.835.000** | **−Rp 8.000.000** |

Harga turun Rp 26.500.000; biaya hanya turun Rp 18.500.000 (infra Rp 20.400.000 keluar, koordinasi Rp 1.900.000 masuk). **Marjin absolut turun Rp 8.000.000/tahun.**

**Persentase:** 29,3% → 28,5%. Juga turun, karena komponen hosting yang hilang bermarjin 23,0% sementara biaya koordinasi yang muncul bermarjin nol.

**Pada harga Pridata, koreksinya mengubah keputusan:**

| Skenario diskon ASC | Pridata bayar/th | Biaya internal @1 pelanggan | Hasil |
|---|---:|---:|---:|
| Diskon 25% dibawa dari Revisi 2 | Rp 20.625.000 | Rp 28.500.000 | **Rugi Rp 7.875.000/th** |
| **Diskon 0% (ditetapkan Revisi 3)** | **Rp 27.500.000** | Rp 28.500.000 | **Rugi Rp 1.000.000/th** |

Membawa diskon 25% ke struktur Q5 akan **melipattigakan** kerugian tahunan menjadi Rp 23.625.000 selama 3 tahun. Jadi: **diskon ASC untuk Pridata ditetapkan 0%.**

**Kompensasi yang benar bukan memotong baris berulang.** Baris berulang adalah baris yang, kalau dipotong, membuat Ato-team membayar untuk hak melayani pelanggannya sendiri — setiap tahun, selamanya, dan menjadi preseden untuk semua perpanjangan. Gantinya diberikan sebagai **konsesi satu kali** yang punya nilai list nyata dan tidak menyentuh baris berulang.

### 6.3 Harga mitra riset

| Komponen | Harga list (NTB-PL-2026-09) | Diskon | **Harga mitra riset** |
|---|---:|---:|---:|
| Lisensi perpetual | Rp 105.000.000 | 50% | **Rp 52.500.000** |
| Implementasi & go-live (pekerjaan sudah dilaksanakan) | Rp 70.000.000 | 50% | **Rp 35.000.000** |
| **Harga sistem** | **Rp 175.000.000** | **50%** | **Rp 87.500.000** |
| ASC Dasar tanpa hosting terkelola | Rp 27.500.000/th | **0%** | **Rp 27.500.000/th** |
| Infrastruktur (VPS milik Pridata) | — | — | Dibayar Pridata langsung, ≈ Rp 20.400.000/th |

**Konsesi satu kali yang menggantikan diskon ASC:**

| # | Konsesi | Turunan nilai | **Nilai list** |
|---|---|---|---:|
| **C1** | Garansi cacat diperpanjang **3 → 6 bulan**; ASC mulai ditagih bulan ke-7, bukan bulan ke-4 | 3 bulan × Rp 27.500.000 ÷ 12 | **Rp 6.875.000** |
| **C2** | **Bank 10 orang-hari permintaan perubahan**, berlaku 3 tahun, tidak dapat dialihkan, tidak dapat diuangkan, hangus bila tidak terpakai | 10 od × rate tagih Rp 1.750.000 | **Rp 17.500.000** |
| **C3** | ASC **terkunci tanpa indeksasi 8%** selama 3 tahun | Rp 27.500.000 × 8% pada Tahun 3 | **Rp 2.200.000** |
| | **Total konsesi** | | **Rp 26.575.000** |

C2 adalah konsesi terbaik dalam paket ini dan alasannya layak dicatat: nilainya nyata bagi Pridata (10 hari kerja pengembangan, pada rate yang sama dengan yang dibayar pembeli list), biayanya bagi Ato-team hanya Rp 9.500.000 (10 od × biaya internal), ia **tidak menyentuh baris berulang**, dan ia bisa ditarik sebagian di meja negosiasi (§6.6) — sesuatu yang tidak bisa dilakukan pada diskon persentase.

### 6.4 TCO Pridata Tahun 1 / 2 / 3

| | Tahun 1 | Tahun 2 | Tahun 3 | **Total 3 tahun** |
|---|---:|---:|---:|---:|
| Harga sistem | Rp 87.500.000 | — | — | Rp 87.500.000 |
| ASC Dasar tanpa hosting (mulai bulan ke-7 karena C1; terkunci tanpa indeksasi karena C3) | Rp 13.750.000 | Rp 27.500.000 | Rp 27.500.000 | Rp 68.750.000 |
| **Dibayar ke Ato-team** | **Rp 101.250.000** | **Rp 27.500.000** | **Rp 27.500.000** | **Rp 156.250.000** |
| VPS & infrastruktur milik Pridata (sistem sudah berjalan, 12 bulan penuh) | Rp 20.400.000 | Rp 20.400.000 | Rp 20.400.000 | Rp 61.200.000 |
| **Total biaya kepemilikan** | **Rp 121.650.000** | **Rp 47.900.000** | **Rp 47.900.000** | **Rp 217.450.000** |

**Perbandingan yang sahih — apa yang dibayar ke Ato-team.** Membandingkan total biaya kepemilikan Pridata dengan pembeli list tidak setara: VPS Pridata berjalan 12 bulan di Tahun 1 karena sistemnya sudah hidup, sementara pembeli list baru go-live di pertengahan tahun. Yang setara adalah baris pendapatan Ato-team:

| Perbandingan | Nilai |
|---|---:|
| Dibayar ke Ato-team, 3 tahun, harga list (Opsi A) | Rp 252.825.000 |
| Dibayar ke Ato-team, 3 tahun, mitra riset | Rp 156.250.000 |
| **Penghematan Pridata** | **Rp 96.575.000 (38,2%)** |

> **Dua angka yang harus dipakai secara jujur di depan Pridata.** Headline-nya **"50% dari harga sistem"** — Rp 87.500.000 dari Rp 175.000.000, benar apa adanya. Penghematan sebenarnya selama 3 tahun atas total yang dibayar ke Ato-team adalah **38,2%**, karena ASC tidak didiskon. Kedua angka harus muncul di penawaran. Menyebut "50%" tanpa batasnya akan menimbulkan sengketa pada tagihan ASC pertama.
>
> **Catatan yang menguntungkan, dan sebabnya perlu diucapkan:** 38,2% ini **lebih baik** dari 33,8% di Revisi 2. Bukan karena diskonnya diperbesar — diskon ASC justru dihapus. Sebabnya struktural: Q5 mengeluarkan baris hosting Rp 26.500.000/tahun yang tidak bisa didiskon dari tagihan Ato-team, sehingga tidak ada lagi yang mengencerkan headline 50%. **Q5 membuat angka 50% lebih mudah dipertahankan, bukan lebih sulit.**

**Ekonomi ASC Pridata selama 3 tahun — dinyatakan terbuka:**

| Skenario basis pelanggan | Th1 (6 bln ditagih, 12 bln biaya) | Th2 | Th3 | **Net 3 tahun** |
|---|---:|---:|---:|---:|
| Tetap 1 pelanggan | −Rp 14.750.000 | −Rp 1.000.000 | −Rp 1.000.000 | **−Rp 16.750.000** |
| **Mencapai 3 pelanggan di Tahun 2** | −Rp 14.750.000 | +Rp 7.835.000 | +Rp 7.835.000 | **+Rp 920.000** |
| Tanpa C1 (ASC mulai bulan ke-4), 3 pelanggan di Th2 | −Rp 7.875.000 | +Rp 7.835.000 | +Rp 7.835.000 | +Rp 7.795.000 |

**ASC Pridata baru mencapai titik impas 3 tahun kalau basis pelanggan mencapai 3 pada Tahun 2.** Itu bukan alasan menaikkan harga Pridata — itu alasan mengeksekusi program penjualan, dan angka ini yang menunjukkan hubungan keduanya. Biaya C1 terhadap Ato-team adalah tepat Rp 6.875.000 pendapatan yang dilepas (biaya dukungan selama masa garansi tetap ditanggung Ato-team dengan atau tanpa C1, jadi C1 tidak menambah biaya — hanya mengurangi tagihan).

**Uji payback untuk Pridata** (total biaya kepemilikan Rp 217.450.000 selama 3 tahun):

| Pembacaan Q3 | Nilai tahunan | Payback | Layak? |
|---|---:|---:|---|
| **Rp 24 miliar/tahun (A12, asumsi kerja)** | Rp 67.200.000 | **3,2 tahun** | ✅ Masuk toleransi 4 tahun |
| Rp 2 miliar/tahun (literal) | Rp 14.650.000 | **14,8 tahun** | ❌ Tidak layak pada harga apa pun di atas lantai teknis |

Perlu dikatakan terus terang: **diskon 50% tidak membuat sistem ini payback cepat bagi Pridata — ia membuatnya defensible.** Pada harga list, payback Pridata akan 4,6 tahun; pada harga mitra riset, 3,2 tahun. Dan model nilai §3.4 hanya menghitung manfaat yang bisa dikuantifikasi; kendali, jejak audit, dan pemisahan peran tidak masuk hitungan.

### 6.5 Konsiderasi yang ditukar — neraca diskon

Setiap butir adalah **kewajiban kontraktual dengan nilai yang dihitung**, bukan niat baik. Kolom terakhir yang membuatnya bisa ditegakkan: kalau butir itu dicoret dari kontrak, diskon berkurang persis sebesar itu (§6.6).

| # | Kewajiban Pridata (harus masuk kontrak) | Turunan nilai | **Nilai** |
|---|---|---|---:|
| **K1** | **Hak studi kasus & referensi penjualan di NTB.** Ato-team boleh menyebut nama CV Pridata Jaya, mempublikasikan studi kasus (angka disamarkan sesuai K2), dan menggunakannya sebagai referensi dalam proposal. Pridata menyediakan 1 narahubung yang bersedia dihubungi calon pembeli, maksimum 4× per tahun. | Biaya akuisisi tanpa referensi ≈ 20 od × Rp 1.750.000 = Rp 35.000.000/pembeli; referensi kuat memotong ~40% untuk 2 pembeli berikutnya | Rp 28.000.000 |
| **K2** | **Akses data operasional untuk riset, 3 tahun.** Akses baca ke data transaksi (order, invoice, pergerakan stok, piutang) untuk riset dan pengembangan produk, dengan NDA dua arah: data hanya dipakai dalam bentuk teragregasi/teranonimkan, tidak dipindahkan ke pihak ketiga, dan nama pelanggan Pridata tidak pernah dipublikasikan. | Tanpa akses ini, dataset setara harus dibangun lewat riset lapangan ≈ 25 od × Rp 1.750.000 | Rp 43.750.000 |
| **K3** | **Testimoni tertulis + lokasi demo hidup.** Testimoni tertulis dan bervideo dalam 6 bulan sejak tanda tangan. Kesediaan menerima kunjungan demo calon pembeli, maksimum 6× per tahun, 2 jam per kunjungan, dijadwalkan minimal 5 hari kerja sebelumnya. | Tanpa lokasi demo hidup, Ato-team harus membangun & memelihara environment demo bersintesis data ≈ 15 od × Rp 1.750.000 | Rp 26.250.000 |
| **K4** | **Komitmen ASC minimum 3 tahun.** Tidak dapat dibatalkan kecuali wanprestasi SLA yang terdokumentasi. Pembayaran tahunan di muka. | Kepastian pendapatan Rp 68.750.000 × 15% (nilai pengurangan risiko churn) | **Rp 10.312.500** |
| **K5** | **Peran co-development Fase 2.** Akses gudang dan waktu operator untuk uji coba modul penerimaan barang: minimum 20 sesi uji coba, masing-masing ~3 jam, dengan 1 operator gudang dan 1 supervisor. Umpan balik terdokumentasi dalam 5 hari kerja per sesi. | Tanpa akses lapangan, uji coba harus disimulasikan di lab ≈ 15 od × Rp 1.750.000 | Rp 26.250.000 |
| | **Total nilai konsiderasi** | | **Rp 134.562.500** |

> **K4 dikoreksi turun dari Rp 21.206.250 (Revisi 2) ke Rp 10.312.500.** Nilai K4 adalah 15% dari pendapatan ASC yang dipastikan. Q5 menurunkan ASC 3 tahun dari Rp 141.375.000 ke Rp 68.750.000, jadi nilai kepastiannya ikut turun. Ini bukan penyesuaian kosmetik — ia mengubah neraca di bawah sebesar Rp 10.893.750, dan membiarkannya akan melebihkan konsiderasi yang diterima.

**Neraca:**

| | Nilai |
|---|---:|
| Diskon harga sistem (50%) | Rp 87.500.000 |
| Diskon ASC | **Rp 0** |
| Konsesi satu kali C1–C3 | Rp 26.575.000 |
| **Total diberikan** | **Rp 114.075.000** |
| **Total konsiderasi diterima (K1–K5)** | **Rp 134.562.500** |
| **Cadangan negosiasi (di pihak Ato-team)** | **Rp 20.487.500 (18,0% di atas nilai yang diberikan)** |

**Cadangan ini bukan kelebihan yang harus dihabiskan — ini ruang gerak Ace di meja negosiasi, dan ia punya dua fungsi:**

1. **Menyerap penolakan sebagian.** Kalau Pridata menolak satu butir kecil, harga tidak perlu berubah. Tangga lengkapnya di §6.6.
2. **Menutup galat estimasi nilai konsiderasi.** Keyakinan nilai K1–K5 adalah **Rendah–Sedang** (asumsi **A10**); cadangan 18% adalah bantalan yang wajar terhadap kemungkinan nilai-nilai itu dilebihkan. Butir terlemah tetap K1 (Rp 28.000.000) — nilainya baru terbukti kalau referensi Pridata benar-benar memenangkan pembeli berikutnya.

### 6.6 Tangga negosiasi — respons harga yang benar untuk setiap penolakan

Tabel ini yang mengubah "diskon adalah paket utuh" dari pernyataan menjadi mekanisme. Setiap baris sudah dihitung, jadi Ace tidak perlu menghitung di meja.

| Kalau Pridata menolak… | Nilai yang hilang | **Respons harga yang benar** | Posisi setelah respons |
|---|---:|---|---|
| **K1** — referensi & studi kasus | Rp 28.000.000 | Tarik **C1 + C2 + C3** (Rp 26.575.000). Harga sistem **tetap** Rp 87.500.000. | Kurang Rp 1.425.000 — di dalam cadangan. Tidak perlu menyentuh harga. |
| **K2** — akses data riset | Rp 43.750.000 | **Program Mitra Riset batal.** K2 adalah satu-satunya alasan diskon ini ada; tanpa akses riset, ini bukan kemitraan riset melainkan potongan harga biasa. Kembali ke **list dikurangi maksimum 10% = Rp 157.500.000**. | Bukan negosiasi harga. Ini keputusan apakah program ini ada atau tidak. |
| **K3** — testimoni & lokasi demo | Rp 26.250.000 | Tarik **C1 + C2 + C3** (Rp 26.575.000). | Surplus Rp 325.000. Seimbang. |
| **K4** dipendekkan ke 1 tahun | Rp 8.250.000 | Tarik **C2 sebagian: 5 dari 10 od** (Rp 8.750.000). | Surplus Rp 500.000. Seimbang. |
| **K4** dihapus seluruhnya *(wajib, kalau Q3 ternyata Rp 2 miliar/tahun — lihat §3.4)* | Rp 10.312.500 | **Tidak ada respons harga.** Diserap cadangan. | Cadangan sisa Rp 10.175.000. |
| **K5** — co-development Fase 2 | Rp 26.250.000 | Tarik **C1 + C2 + C3**, **dan** harga Fase 2 naik sebesar biaya uji lapangan yang harus disimulasikan (15 od terkalibrasi). | Uji lapangan pindah ke harga Fase 2, di mana ia memang seharusnya berada. |

**Aturan penegakan:** diskon 50% adalah harga dari paket K1–K5 utuh, **bukan titik awal negosiasi.** Setiap butir yang dicoret memicu baris di tabel ini, dan Ace boleh menjalankannya tanpa kembali ke saya.

### 6.7 Yang TIDAK didiskon — dinyatakan tegas

| Item | Aturan |
|---|---|
| **ASC (kontrak dukungan tahunan)** | **Nol diskon.** Harga list Rp 27.500.000/tahun sudah berada di bawah biaya internalnya selama basis pelanggan masih 1 (§2.4). Diskon di baris ini berarti Ato-team membayar untuk hak melayani pelanggannya sendiri, setiap tahun, dan menciptakan preseden untuk semua perpanjangan. *(Berubah dari 25% di Revisi 1–2; alasannya di §6.2.)* |
| **Infrastruktur / VPS** | Bukan baris harga Ato-team sama sekali (Q5). Tidak ada yang bisa didiskon di sini. |
| **Modul Fase 2 (penerimaan barang anti-human-error)** | Dijual pada **harga list penuh**. Peran co-development Pridata (K5) **sudah dihargai Rp 26.250.000 di dalam paket diskon dasar** — memberi diskon lagi pada Fase 2 berarti membayar konsiderasi yang sama dua kali. Harga menunggu ruang lingkup & estimasi Bayu; dihitung dengan bobot terkalibrasi §1.2. |
| **Celah human error di alur penerimaan barang saat ini** | Tidak ada diskon kompensasi. Posisi komersial sudah diputuskan: celah itu dijual sebagai Fase 2. Kalau Pridata mempersoalkannya, jawabannya jadwal dan harga Fase 2, bukan pengurangan harga dasar. |
| **Perluasan lisensi** (badan usaha kedua, instance tambahan, gudang di luar NTB, pengguna di atas kuota) | Harga list penuh, sejak hari pertama. |
| **Perpanjangan setelah Tahun 3** | Kembali ke harga list yang berlaku saat itu, dikurangi maksimum 10% (potongan loyalitas) — **bukan 50%**. |

### 6.8 Staging pembayaran Pridata

Sistem sudah terpasang dan berjalan, jadi milestone teknis sudah lewat. Yang tersisa untuk diikat adalah konsiderasinya.

| Milestone | % | Nilai |
|---|---:|---:|
| Tanda tangan kontrak | 40% | Rp 35.000.000 |
| Penandatanganan berita acara serah terima formal | 30% | Rp 26.250.000 |
| Bulan ke-6, bersamaan dengan penyerahan testimoni tertulis (K3) dan persetujuan naskah studi kasus (K1) | 30% | Rp 26.250.000 |

Mengikat 30% terakhir ke K1 dan K3 adalah mekanisme penegakan yang tidak butuh pengadilan: konsiderasi belum diterima, pembayaran belum jatuh tempo, dan kedua pihak punya insentif yang sama untuk menyelesaikannya.

ASC ditagih di muka per tahun mulai bulan ke-7 (C1), terpisah dari staging di atas.

### 6.9 Ring-fence — sembilan klausul agar Rp 87.500.000 tidak jadi harga pasar NTB

Di pasar sekecil NTB, satu harga bocor menjadi ekspektasi semua orang (*reference-price contamination*).

1. **~~Publikasikan harga list lebih dulu~~ — SELESAI.** Daftar Harga **NTB-PL-2026-09** terbit 29 September 2026, berlaku sampai 30 Juni 2027, nol angka khusus Pridata dan nol angka Fase 2: [dokumen `pricelist`](/ATO/issues/ATO-6#document-pricelist). Prasyarat ring-fence ini terpenuhi; penawaran Pridata boleh dikirim.
2. **Tampilkan diskon sebagai baris terpisah, bukan harga yang diturunkan.** Setiap kontrak dan setiap invoice menampilkan harga list penuh, lalu baris `Potongan Program Mitra Riset 2026/2027 — (50%)`. Harga Pridata tidak pernah ditulis sebagai angka tunggal.
3. **Baris ASC ditampilkan dengan diskon 0% secara eksplisit.** Invoice ASC Pridata menampilkan `ASC Dasar tanpa hosting terkelola — Rp 27.500.000` dan `Potongan Program Mitra Riset — Rp 0`. Menampilkan nol secara eksplisit mencegah orang menyimpulkan tiga tahun kemudian bahwa ada preseden diskon ASC. *(Klausul baru, dari Q5.)*
4. **Klausul kerahasiaan harga dua arah.** Pridata tidak mengungkapkan syarat komersial ke pihak ketiga. Yang boleh disebut publik — termasuk dalam testimoni dan kunjungan demo — hanya harga list NTB-PL-2026-09.
5. **Program tertutup dan bertanggal.** Maksimum **satu** mitra riset per kategori usaha per pasar. Program Mitra Riset dinyatakan berakhir **31 Desember 2027** dan tidak dibuka kembali tanpa persetujuan tertulis Ato-team. Nyatakan ini di kontrak Pridata sendiri, supaya mereka tahu posisinya unik dan tidak bisa merekomendasikan syarat yang sama ke rekan bisnisnya.
6. **Klausul non-precedent eksplisit.** Harga mitra riset tidak menjadi acuan untuk: perpanjangan, perluasan lisensi, modul Fase 2, integrasi, atau pembeli lain mana pun — termasuk afiliasi atau perusahaan dalam grup yang sama dengan Pridata.
7. **Varian tanpa hosting terkelola adalah perubahan ruang lingkup, bukan diskon.** Pembeli mengambil alih biaya *dan* risiko infrastruktur, dan jaminan waktu respons tidak berlaku untuk gangguan yang bersumber dari infrastruktur pembeli (NTB-PL-2026-09 §4.1). Varian ini tidak boleh dipakai sebagai cara menurunkan harga bagi pembeli yang sebenarnya menginginkan managed hosting. *(Klausul baru, dari Q5.)*
8. **Harga perpanjangan sudah ditetapkan sekarang.** Setelah Tahun 3, kembali ke list berlaku dikurangi maksimum 10%. Menuliskan ini di kontrak awal mencegah negosiasi ulang dari titik Rp 27.500.000 tiga tahun lagi. Konsesi C1–C3 **tidak diperpanjang** dan bank C2 hangus bila tidak terpakai dalam 3 tahun.
9. **Clawback pro rata.** Kalau kewajiban K1–K5 tidak dipenuhi dalam 12 bulan sejak tanda tangan — testimoni tidak diberikan, akses data ditarik, permintaan kunjungan demo ditolak 3× berturut-turut tanpa alasan sah, atau sesi uji coba Fase 2 tidak terpenuhi — Ato-team berhak menagih selisih diskon secara pro rata sesuai nilai di §6.5. Klausul ini yang mengubah "timbal balik" dari niat baik menjadi kewajiban.

---

## 7. Register Asumsi

| ID | Asumsi | Status di Revisi 3 | Kalau salah |
|---|---|---|---|
| **A1** | Bobot orang-hari per tingkat kesulitan | **TERKALIBRASI.** Bobot nyata = 0,5 / 2,0 / 4,0 / 6,0 (kolom rendah), bukan kolom tengah. Diverifikasi terhadap kalender terkonfirmasi Q1 = a. | Tidak lagi asumsi untuk 47 fitur terkirim. **Tetap asumsi untuk modul yang belum dibangun** — dan di situ risikonya nyata: memakai bobot tengah pada Fase 2 akan melebihkan harganya 53,6%. |
| **A2** | Overhead non-fitur | **TERKALIBRASI ke 55,5%** (dari 50%), diturunkan dari selisih 252 od − 162 od effort fitur. | Komponen overhead adalah alokasi, bukan pengukuran. Salah alokasi tidak mengubah total 252 od yang terkonfirmasi. |
| **A3** | Rate biaya internal Rp 950.000/od (gaji campuran Rp 14.000.000/bulan + beban 40%) | **MASIH ASUMSI — dan sekarang satu-satunya penggerak rentang biaya bangun.** | Berdampak tiga kali: biaya bangun, biaya dukungan, dan kedua lantai. Pada Rp 1.200.000/od: biaya bangun Rp 302.400.000; biaya berjalan @1 pelanggan Rp 36.000.000 → ASC Rp 27.500.000 **rugi Rp 8.500.000/th**; lantai komersial Th1 naik ke Rp 121.500.000; lantai teknis absolut ke Rp 84.000.000 — Pridata Rp 87.500.000 tinggal Rp 3.500.000 di atasnya. **Asumsi paling berbahaya yang tersisa, dan bisa diperiksa dari catatan penggajian Ato-team sendiri (Q6).** |
| **A4** | Biaya infrastruktur Rp 1.700.000/bulan | **PINDAH KE PEMBELI (Q5).** Bukan lagi risiko Ato-team. | Kalau volume data jauh di atas perkiraan, yang naik adalah tagihan VPS **pembeli**, bukan biaya Ato-team. Dampaknya: total biaya kepemilikan pembeli naik dan uji payback §3.5 mengencang. Pada infra 2× (Rp 40.800.000/th), payback pembeli omzet Rp 40 miliar bergerak dari 2,89 ke 3,41 tahun. **Ini manfaat sebenarnya dari Q5:** pendorong kerugian tahunan nomor satu di Revisi 2 hilang dari daftar risiko Ato-team. |
| **A5** | Target amortisasi pembeli | **TERGANTI oleh Q2 = c (3–4 pembeli).** Harga list terbit menyiratkan 3,19 pembeli — konsisten. | **2 pembeli sudah cukup** (§5.3: dibutuhkan 1,81), jadi ujung bawah Q2 = c bukan lagi skenario gagal. Skenario gagal sekarang adalah **hanya 1 pembeli list tambahan**, dan di situ kekurangannya Rp 84.900.000 (Rp 189.900.000 − Rp 105.000.000). Harga list tidak boleh diubah (sudah terbit). Responsnya memperluas pasar atau menerima pemulihan sebagian — **bukan** menaikkan harga Pridata. |
| **A6** | Profil pembeli list: omzet Rp 40 miliar/th, persediaan Rp 3 miliar, piutang Rp 4 miliar | **Dipertahankan sebagai profil pembeli *target* list**, bukan sebagai profil Pridata. Q3 menunjukkan Pridata lebih kecil di kedua pembacaan. | Menentukan seluruh plafon nilai Rp 107.000.000/th dan ambang kualifikasi §3.5. Kalau pembeli NTB tipikal ternyata Rp 24 miliar, tidak ada pembeli list yang lolos payback 3 tahun dan yang dibutuhkan adalah paket ruang lingkup lebih kecil — bukan list yang lebih murah. |
| **A7** | Parameter nilai: shrinkage 1,0%→0,5%; DSO −5 hari; bad debt −15%; realisasi waktu staf 50% | Masih asumsi. Keyakinan **Rendah**. | Model nilai hanya menghitung manfaat terkuantifikasi, jadi ia batas bawah. Setelah 12 bulan data produksi (via K2), ganti dengan pengukuran nyata — dan itu menjadi materi penjualan terkuat Ato-team di NTB. |
| **A8** | Beban dukungan 48 od/tahun, help desk 3 jam/minggu | Masih asumsi. | Menggeser seluruh harga ASC dan lantainya. Kalau pemakaian nyata jauh lebih ringan, biaya @1 pelanggan turun dan kerugian Rp 1.000.000/th hilang tanpa perlu pelanggan kedua. Ukur, jangan asumsikan, setelah 6 bulan. |
| **A9** | Basis pelanggan untuk pembagian 14 od beban bersama | Dinyatakan eksplisit sebagai **variabel keputusan**, bukan asumsi tunggal — seluruh tabel §2.4 menampilkan 1 sampai 4 pelanggan. | Tidak ada lagi angka tunggal yang bisa salah di sini. Yang perlu diawasi adalah kapan pelanggan kedua masuk. |
| **A10** | Nilai konsiderasi K1–K5 (Rp 134.562.500) | Masih estimasi. Keyakinan **Rendah–Sedang**. | Kalau dilebihkan, diskon 50% kurang terjustifikasi. Cadangan Rp 20.487.500 (18%) adalah bantalannya. Butir terlemah K1 (Rp 28.000.000); terkuat K2, karena tanpa akses data, modul analytics dan Fase 2 harus dirancang tanpa data nyata. |
| **A11** | **Koordinasi infrastruktur milik pembeli = 2,0 od/tahun** *(baru, dari Q5)* | Asumsi baru. Belum pernah dijalankan pada VPS milik pihak lain. | Kalau ternyata 6 od/tahun (penyedia VPS pembeli tidak responsif, akses berbelit): biaya @3 pelanggan naik ke Rp 23.465.000 → marjin ASC Dasar turun ke Rp 4.035.000 (14,7%); @1 pelanggan Rp 32.300.000 → **rugi Rp 4.800.000/th**. Ukur dalam 6 bulan pertama pengelolaan VPS Pridata. |
| **A12** | **Satuan Q3: "Rp 2 miliar" = omzet per bulan (Rp 24 miliar/tahun)** *(baru)* | **Asumsi kerja, belum dikonfirmasi.** Kartu klarifikasi Ace di [ATO-6](/ATO/issues/ATO-6) masih menunggu jawaban. Ditopang triangulasi Q4 = d dan bentuk sistem yang dibangun (§3.4). | Kalau literal Rp 2 miliar/tahun: plafon nilai jatuh ke Rp 18.312.500, payback Pridata 14,8 tahun, dan biaya berjalan Rp 47.900.000/th = **2,4% dari omzet**. **Harga tidak berubah** — yang berubah: K4 (komitmen ASC 3 tahun) tidak boleh diminta, karena komitmen yang tidak terjangkau menghasilkan wanprestasi, bukan pendapatan. Nilai K4 Rp 10.312.500 diserap cadangan. Risiko sebenarnya bukan harga terlalu tinggi, melainkan **pembatalan ASC di Tahun 2**. |

---

## 8. Pertanyaan Terbuka

| # | Status | Pertanyaan | Kenapa penting | Pemilik |
|---|---|---|---|---|
| **Q1** | ✅ **Terjawab: a** | Lama & jumlah orang pembangunan | 252 od, biaya bangun Rp 239.400.000, bobot terkalibrasi | — |
| **Q2** | ✅ **Terjawab: c** | Jumlah pembeli NTB realistis | 3–4 pembeli; konsisten dengan list terbit (3,19 tersirat) | — |
| **Q3** | ⏳ **Satuan belum dikonfirmasi** | "Rp 2 miliar" — per tahun atau per bulan? | Tidak mengubah harga. Mengubah apakah komitmen ASC 3 tahun (K4) boleh diminta, dan apakah risiko utamanya harga atau pembatalan Tahun 2. | Kartu klarifikasi Ace di [ATO-6](/ATO/issues/ATO-6) |
| **Q4** | ✅ **Terjawab: d** | Pembanding yang pernah dilihat Pridata | Pridata pernah mengevaluasi SAP Business One / Odoo berbayar. Lihat catatan di bawah. | — |
| **Q5** | ✅ **Terjawab** | Hosting | VPS milik pembeli, dikelola Ato-team. Seluruh §2, §4, §6 disusun ulang. | — |
| **Q6** | 🆕 **Baru** | Berapa **gaji campuran bulanan sebenarnya** dari 2 orang yang membangun sistem ini, termasuk beban perusahaan? | Satu-satunya asumsi yang tersisa di biaya bangun (**A3**), dan penggerak kedua lantai walk-away. Ini ada di catatan penggajian Ato-team sendiri — tidak perlu bertanya ke pelanggan. Pada Rp 1.200.000/od, Pridata tinggal Rp 3.500.000 di atas lantai teknis absolut. | Ace (internal Ato-team) |
| **Q7** | 🆕 **Baru — ukur, jangan tanya** | Berapa beban koordinasi nyata (**A11**) untuk mengelola VPS milik Pridata, dan berapa beban help desk nyata (**A8**)? | Menentukan apakah ASC Dasar Rp 27.500.000 berkelanjutan sebelum pelanggan kedua masuk. Tidak bisa dijawab dengan bertanya — harus dicatat selama 6 bulan pertama. | Ato-team, mulai bulan pertama pengelolaan |

**Catatan tentang Q4 = d, dan ini mengubah arah risikonya.** Pridata pernah mengevaluasi ERP kelas atas. Saya **tidak** memasukkan angka SAP Business One atau Odoo ke dokumen ini karena saya tidak punya data terverifikasi tentang harganya di Indonesia — mengarang pembanding dan menyebutnya hasil riset akan merusak seluruh dokumen ini. Tetapi arah pengaruhnya bisa dinyatakan tanpa angka: jangkar harga di kepala Pridata **tinggi**, jadi Rp 175.000.000 tidak akan terdengar mahal. **Risiko sebenarnya dari Q4 = d bukan penolakan harga, melainkan ekspektasi ruang lingkup.** Pembeli yang pernah melihat SAP B1 bisa mengharapkan hal-hal yang tidak ada di 47 fitur — multi-mata-uang, modul manufaktur, konsolidasi antar-badan-usaha, e-faktur, akuntansi penuh sampai neraca. **Tabel "tidak termasuk" di §3.3 harus ditampilkan sama menonjol dengan tabel "termasuk"** di penawaran, bukan dikubur di lampiran. Kalau Ace bisa mendapatkan angka kuotasi yang benar-benar pernah dilihat Pridata, saya akan menempatkannya sebagai pembanding bersumber — sampai itu ada, tidak ada pembanding pasar di dokumen ini.

---

## 9. Yang Sengaja Tidak Ada di Dokumen Ini

- **Harga modul Fase 2.** Belum dibangun, belum diestimasi. Ruang lingkupnya di [ATO-3](/ATO/issues/ATO-3), estimasi effort-nya milik Bayu. Tempatnya disediakan di §3.3 dan §6.7; rumus dan bobot terkalibrasinya disediakan di §1.2. Angkanya tidak.
- **Pembanding pasar.** Tidak ada data terverifikasi tentang harga ERP vendor lain di NTB atau Indonesia. Lihat catatan Q4 di §8.
- **Estimasi effort untuk modul yang belum dibangun.** Bukan wilayah saya; itu milik Bayu.
- **Harga managed hosting untuk Pridata.** Dihapus di Revisi 3. Q5 sudah dijawab; menyimpan varian yang tidak berlaku hanya menciptakan peluang salah kutip.
- **Naskah penawaran untuk Pridata.** Dokumen ini bahan bakunya. Dokumen yang dilihat pelanggan milik Ace ([ATO-5](/ATO/issues/ATO-5)).
- **Kontrak.** Yang ada di sini syarat komersial (K1–K5, C1–C3, tangga negosiasi, sembilan klausul ring-fence, staging pembayaran) dalam bentuk yang bisa diserahkan ke penyusun kontrak. Bukan kontrak siap tanda tangan.

---

## Lampiran A — Status Matriks Repricing Revisi 2

Lampiran A Revisi 2 adalah matriks repricing untuk lima kemungkinan jawaban Q1 dan lima kemungkinan Q2. Jawabannya sudah masuk, jadi matriksnya sudah menjalankan tugasnya dan tidak lagi perlu dibawa. Riwayat lengkapnya tersimpan di revisi dokumen ini. Yang perlu dicatat adalah bagaimana setiap bagiannya terselesaikan — termasuk satu prediksi yang **salah**, karena itu yang menentukan apakah metodenya bisa dipercaya lain kali.

| Bagian Revisi 2 | Bagaimana terselesaikan |
|---|---|
| **A.1** — matriks repricing per jawaban Q1 | Q1 = a. Baris "a" memprediksi biaya bangun Rp 239.400.000, lisensi Rp 67.000.000, harga list Rp 137.000.000 pada target 5 pembeli. **Biaya bangunnya tepat** (Rp 239.400.000). **Harga listnya tidak dipakai**, karena Q2 = c mengoreksi target pembeli dari 5 ke 3–4 — dan itu menaikkan lisensi dari Rp 67.000.000 ke Rp 105.000.000. Dua jawaban bergerak berlawanan dan hampir saling menghapus; Rp 175.000.000 bertahan. |
| **A.2** — "≈ 3 pembeli tambahan, apa pun jawaban Q1" | **Prediksi ini salah, dan sebabnya jelas.** Rumusnya mengasumsikan harga list ikut di-repricing mengikuti biaya bangun. Yang terjadi justru yang disarankan A.2 sendiri: list diterbitkan lebih dulu dan **dikunci**, sementara biaya bangun turun. Dengan lisensi tertahan di Rp 105.000.000 dan biaya bangun turun ke Rp 239.400.000, kebutuhan nyata adalah **2 pembeli tambahan**, bukan 3 (§5.3). Rekomendasi urutan langkahnya benar dan sudah dijalankan; angka pembelinya ketinggalan. |
| **A.3** — sensitivitas Q2 pada 378 od | Tidak berlaku: dihitung pada 378 od, sementara Q1 = a berarti 252 od. Diganti tabel §3.1, dihitung pada biaya bangun terkonfirmasi. |
| **A.4** — peringkat pendorong kerugian tahunan | Kesimpulan intinya bertahan dan terbukti berguna: **Q1 tidak berdampak apa pun pada ekonomi tahunan; A4 lalu A3 yang berbahaya.** Q5 kemudian **menghapus A4 dari daftar risiko Ato-team** dengan memindahkan infrastruktur ke pembeli. Yang tersisa di puncak sekarang **A3** (rate biaya internal), diikuti **A11** (koordinasi VPS, risiko baru dari Q5). |
| **A.5** — daftar tindakan begitu jawaban masuk | Dijalankan seluruhnya di Revisi 3. Baris "Q1 = a, b, atau c → tidak ada perubahan harga" terbukti benar, tetapi bukan karena alasan yang ditulis di situ: harga bertahan karena list sudah dikunci dan koreksi Q2 mengimbangi Q1, bukan karena Q1 = a tidak berdampak. Baris "Q5 = Pridata hosting sendiri" mengarahkan ASC ke Rp 20.625.000/th dengan diskon 25% — **itu salah untuk jawaban Q5 yang sebenarnya**, dan §6.2 menggantinya. |

**Pelajaran metode yang layak dibawa ke keputusan harga berikutnya:** matriks repricing berguna untuk aritmatikanya, tetapi dua prediksinya keliru di tempat yang sama — **keduanya menganggap satu jawaban bergerak sendiri.** Nyatanya Q1 dan Q2 bergerak berlawanan dan hampir saling menghapus, dan Q5 ternyata bukan salah satu dari dua opsi yang disediakan. Lain kali, sediakan matriks untuk **kombinasi** jawaban, dan sediakan kolom "bukan a maupun b".

---

*Revisi 3 · 29 September 2026 · Rani (Commercial Analyst) · [ATO-2](/ATO/issues/ATO-2) · Jangkar harga: Daftar Harga NTB-PL-2026-09, terbit 29 September 2026, berlaku sampai 30 Juni 2027*
