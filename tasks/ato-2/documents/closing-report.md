> **Catatan penyampaian.** Isi di bawah ini seharusnya menjadi komentar penutup ATO-2 pada 29 September 2026. Penulisan komentar dan perubahan status diblokir di heartbeat ini (`403 cross_issue_influence_run_context_required` — run ini kehilangan ikatan tugasnya setelah reconnect koneksi AI). Dokumen `analysis` Revisi 3 **berhasil terbit**. Status ATO-2 masih `in_progress` dan **perlu dipindahkan ke `done`**; sampai itu terjadi, [ATO-4](/ATO/issues/ATO-4) tetap terblokir. Isi laporan di bawah tetap berlaku apa adanya.

---

## Selesai — Revisi 3 terbit, seluruh jawaban Q1–Q5 sudah masuk ke angka

Dokumen: [ATO-2 · analysis](/ATO/issues/ATO-2#document-analysis) · jangkar harga: [NTB-PL-2026-09](/ATO/issues/ATO-6#document-pricelist)

### Angka headline

| | Nilai |
|---|---:|
| **Biaya bangun terkonfirmasi** (Q1 = a: 6 bln × 2 org = 252 od) | **Rp 239.400.000** |
| Harga list Th1 — **tidak berubah, tidak perlu berubah** | **Rp 175.000.000** |
| ASC Dasar tanpa hosting terkelola (varian Q5) | **Rp 27.500.000/tahun** |
| Dibayar pembeli list ke Ato-team, 3 tahun | Rp 252.825.000 |
| Total biaya kepemilikan pembeli list, 3 tahun (termasuk VPS sendiri) | Rp 308.925.000 |
| **Lantai walk-away Th1** | **Rp 104.000.000** |
| **Lantai walk-away ASC** | **Rp 33.000.000/th @1 pelanggan · Rp 23.000.000/th @3 pelanggan** |
| **Pridata — sistem** | **Rp 87.500.000** (50% dari list) |
| **Pridata — ASC** | **Rp 27.500.000/th, diskon 0%** *(berubah dari 25%)* |
| Dibayar Pridata ke Ato-team, 3 tahun | **Rp 156.250.000** — hemat Rp 96.575.000 (**38,2%**) |
| **Pembeli list tambahan untuk memulihkan biaya bangun** | **2** (Q2 = c menyatakan tersedia 3–4) |

**Rekomendasi dalam satu kalimat:** kirim penawaran Pridata pada **Rp 87.500.000 untuk sistem + ASC Dasar Rp 27.500.000/tahun tanpa diskon**, ditambah konsesi satu kali C1–C3 senilai Rp 26.575.000, seluruhnya diikat ke K1–K5.

---

### Empat hal yang mengubah apa yang kamu kirim, Ace

**1. Harga list Rp 175.000.000 lolos — dan sekarang ada uji yang bisa kamu pakai di depan pembeli.** Saya setuju dengan pembacaanmu, tapi lewat jalan yang lebih kuat daripada "ada di dalam rentang": lisensi Rp 105.000.000 ÷ 1,40 = amortisasi Rp 75.000.000/pembeli, dan Rp 239.400.000 ÷ Rp 75.000.000 = **3,19 pembeli tersirat** — persis di dalam Q2 = c (3–4). Harga terbit itu bisa diturunkan balik ke jawaban pengguna sendiri. Tidak ada repricing. *Catatan kecil: Q1 = a dan Q2 = c bergerak berlawanan dan hampir saling menghapus — Q1 menurunkan biaya bangun, Q2 menaikkan amortisasi per pembeli. Itu sebabnya angkanya bertahan, bukan karena Q1 tidak berdampak.*

**2. Koreksi: Q5 menurunkan marjin ASC, tidak menaikkannya — dan itu mengubah satu angka di penawaran.** Harga ASC turun Rp 26.500.000, tapi biaya hanya turun Rp 18.500.000 (infra Rp 20.400.000 keluar, koordinasi VPS milik pihak lain Rp 1.900.000 masuk). Marjin absolut **turun Rp 8.000.000/tahun**; persentasenya juga turun (29,3% → 28,5%).

Konsekuensinya konkret: **diskon ASC 25% harus dibatalkan menjadi 0%.**

| Skenario | Pridata bayar/th | Biaya internal @1 pelanggan | Hasil |
|---|---:|---:|---:|
| Diskon 25% dibawa dari Revisi 2 | Rp 20.625.000 | Rp 28.500.000 | **rugi Rp 7.875.000/th** |
| **Diskon 0% (Revisi 3)** | **Rp 27.500.000** | Rp 28.500.000 | rugi Rp 1.000.000/th |

Gantinya bukan potongan berulang, tapi **konsesi satu kali** yang nilai list-nya nyata dan bisa ditarik di meja negosiasi: garansi 3→6 bulan (Rp 6.875.000), bank 10 orang-hari permintaan perubahan (Rp 17.500.000), ASC terkunci tanpa indeksasi (Rp 2.200.000). Total Rp 26.575.000.

**Manfaat sebenarnya dari Q5 ada di tempat lain, dan itu trade yang wajar:** Ato-team menyerahkan Rp 24.120.000 marjin per pembeli selama 3 tahun, dan sebagai gantinya **risiko A4 — infrastruktur meleset 2×, pendorong kerugian tahunan nomor satu di Revisi 2 — pindah sepenuhnya ke pembeli.** Itu layak diucapkan sebagai pengurangan risiko, bukan sebagai kenaikan marjin.

**3. Headline 50% jadi lebih mudah dipertahankan, bukan lebih sulit.** Penghematan Pridata naik dari 33,8% (Revisi 2) ke **38,2%** — bukan karena diskon diperbesar, tapi karena Q5 mengeluarkan baris hosting Rp 26.500.000/th yang tidak bisa didiskon dari tagihan kita. Dua angka tetap harus disebut bersama: **"50% dari harga sistem"** dan **"38,2% dari total yang dibayar ke Ato-team selama 3 tahun."**

**4. Kamu tidak perlu kembali ke saya saat negosiasi — §6.6 sudah menghitungnya.** Tangga negosiasi untuk setiap butir K1–K5 yang ditolak, sudah jadi angka:

| Pridata menolak… | Respons harga yang benar |
|---|---|
| K1 (referensi/studi kasus, Rp 28.000.000) | Tarik C1+C2+C3. **Harga sistem tetap Rp 87.500.000.** |
| K2 (akses data riset, Rp 43.750.000) | **Program Mitra Riset batal** — ini satu-satunya alasan diskon ada. Kembali ke list −10% = Rp 157.500.000. Bukan negosiasi harga. |
| K3 (testimoni/demo, Rp 26.250.000) | Tarik C1+C2+C3. Seimbang. |
| K4 dipendekkan ke 1 tahun | Tarik 5 dari 10 od bank C2. Seimbang. |
| K5 (co-development Fase 2) | Tarik C1+C2+C3, dan harga Fase 2 naik sebesar biaya uji lapangan. |

Neraca: diberikan **Rp 114.075.000** vs diterima **Rp 134.562.500** → **cadangan negosiasi Rp 20.487.500 (18%)** di pihak kita. *(K4 saya koreksi turun dari Rp 21.206.250 ke Rp 10.312.500 — nilainya 15% dari pendapatan ASC yang dipastikan, dan Q5 memperkecil ASC.)*

---

### Dua temuan yang tidak nyaman, dinyatakan apa adanya

**ASC Dasar Rp 27.500.000/th rugi Rp 1.000.000/th selama Pridata satu-satunya pelanggan.** Harga itu sudah terbit dan berlaku sampai 30 Juni 2027, jadi tidak bisa dinaikkan. Titik baliknya bukan kenaikan harga, melainkan **pelanggan ASC kedua** — dan ini mengikat harga dukungan langsung ke program penjualan:

| Basis pelanggan | Biaya internal/th | Marjin atas Rp 27.500.000 |
|---:|---:|---:|
| 1 | Rp 28.500.000 | **−Rp 1.000.000** |
| 2 | Rp 21.850.000 | +Rp 5.650.000 |
| 3 | Rp 19.665.000 | +Rp 7.835.000 |

ASC Pridata baru impas selama 3 tahun **kalau basis pelanggan mencapai 3 di Tahun 2** (+Rp 920.000). Kalau tetap 1 pelanggan: −Rp 16.750.000.

**Kabar baiknya:** untuk pertama kalinya pemulihan biaya bangun berada **di dalam** kapasitas pasar yang dinyatakan pengguna. Butuh **2 pembeli list tambahan** (Rp 189.900.000 ÷ Rp 105.000.000 = 1,81), tersedia 3–4. Bahkan pada rate biaya internal tertinggi yang masuk akal (Rp 1.200.000/od) kebutuhannya masih 3 pembeli — **kelayakan program tidak lagi bergantung pada asumsi yang belum diverifikasi.**

---

### Asumsi yang paling menentukan hasil, dan satu pertanyaan yang masih terbuka

**A12 — satuan "Rp 2 miliar" (Q3), kartu klarifikasimu di [ATO-6](/ATO/issues/ATO-6) masih menunggu.** Saya tidak menahan dokumen untuk ini; saya memodelkan kedua pembacaan dan memakai **Rp 24 miliar/tahun (per bulan)** sebagai asumsi kerja, ditopang dua triangulasi: Q4 = d (perusahaan Rp 2 miliar/tahun tidak masuk ruang evaluasi SAP B1) dan bentuk sistem yang dibangun (6 peran dashboard, transfer antar gudang, penugasan sales↔toko — kebutuhan itu tidak muncul pada omzet Rp 167 juta/bulan).

**Yang penting: kalau pembacaan literal yang benar, harganya tidak berubah.** Yang berubah satu hal:

| Pembacaan | Biaya berjalan Rp 47.900.000/th (ASC + VPS) | % omzet | Konsekuensi |
|---|---:|---:|---|
| Rp 24 miliar/th | Rp 47.900.000 | 0,20% | Wajar. Payback Pridata 3,2 th. |
| Rp 2 miliar/th | Rp 47.900.000 | **2,4%** | **Komitmen ASC 3 tahun (K4) tidak boleh diminta.** Payback 14,8 th. Risikonya pembatalan di Tahun 2, bukan penolakan harga di Tahun 1. |

Nilai K4 (Rp 10.312.500) terserap cadangan Rp 20.487.500, jadi menghapusnya tidak menyentuh harga. **Konfirmasi satuan sebelum menandatangani minimum 3 tahun, bukan sebelum mengirim harga.**

**A3 — rate biaya internal Rp 950.000/od. Ini satu-satunya asumsi yang tersisa di biaya bangun, dan jawabannya ada di catatan penggajian Ato-team sendiri (Q6, §8).** Pada Rp 1.200.000/od: lantai teknis absolut naik ke Rp 84.000.000 dan Pridata Rp 87.500.000 tinggal Rp 3.500.000 di atasnya. Ini yang perlu diperiksa, bukan ditanyakan ke pelanggan.

**A11 — baru, dari Q5: koordinasi VPS milik pembeli 2,0 od/th.** Belum pernah dijalankan. Kalau ternyata 6 od/th, ASC Dasar rugi Rp 4.800.000/th @1 pelanggan. Harus **diukur** selama 6 bulan pertama, bukan diasumsikan (Q7).

---

### Satu hal yang perlu kamu rutekan, bukan aku putuskan

**Bobot effort di Revisi 1–2 terlalu tinggi 53,6%, dan itu akan melebihkan harga Fase 2 kalau dipakai lagi.** Effort nyata 252 od cocok dengan **kolom bobot rendah** (Easy 0,5 / Mid 2,0 / High 4,0 / Advance 6,0) + overhead **55,5%** — mereproduksi 252 od dengan selisih 0,1 od. Bobot tengah memprediksi 387 od.

Jadi: **harga Fase 2 harus dihitung dengan bobot terkalibrasi §1.2 × Rp 1.750.000**, bukan bobot tengah. Memakai bobot lama akan melebihkan harganya 53,6% — di modul yang justru paling perlu terjangkau karena Pridata sudah membayar akses lapangannya lewat K5. Tolong sampaikan kalibrasi ini ke Bayu saat ruang lingkup Fase 2 ([ATO-3](/ATO/issues/ATO-3)) masuk ke estimasi effort. **Angka Fase 2 tetap tidak ada di dokumen saya** — ruang lingkup dan estimasi milik Bayu, penetapan harganya milik saya begitu estimasi itu ada.

---

### Langkah berikutnya

- **Milikku:** [ATO-4](/ATO/issues/ATO-4) (skema penjualan & syarat kemitraan 2 arah) sekarang tidak terblokir — saya lanjutkan di heartbeat berikutnya dengan angka Revisi 3.
- **Milikmu:** dua hal — (i) keputusan penerbitan + satuan Q3 di kartu [ATO-6](/ATO/issues/ATO-6) yang masih menunggu pengguna, (ii) penawaran final [ATO-5](/ATO/issues/ATO-5) memakai Rp 87.500.000 + Rp 27.500.000/th diskon 0% + konsesi C1–C3, dengan tabel "tidak termasuk" §3.3 ditampilkan **sama menonjol** dengan tabel "termasuk" — itu mitigasi risiko Q4 = d, karena pembeli yang pernah melihat SAP B1 bisa mengharapkan e-faktur, multi-mata-uang, dan akuntansi penuh sampai neraca.
- **Tidak ada di dokumen ini:** pembanding pasar bersumber (saya tidak mengarang harga vendor lain) dan angka Fase 2. Kalau kamu bisa mendapatkan angka kuotasi yang benar-benar pernah dilihat Pridata, saya tempatkan sebagai pembanding bersumber.
