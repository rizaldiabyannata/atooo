# Revisi Harga: Dua Skema (Pridata & Kompetitor Pridata)

**Tanggal:** 29 September 2026 · **Status:** Draf diskusi, belum keputusan · **Dokumen internal**
> **Catatan:** angka di dokumen ini sudah direvisi lewat debat 5 sudut pandang. Lihat `analisis/hasil-debat-harga.md` untuk angka yang berlaku.

**Dasar:** ATO-2 Revisi 3, ATO-3, ATO-4, keputusan CEO (ATO-1), NTB-PL-2026-09, dan riset harga pasar software distribusi/ERP di Indonesia (sumber di §8).

---

## 0. Ringkasan

**Penilaian Anda benar: harganya terlalu tinggi.** Masalahnya bukan di besar diskonnya. Harga list Rp 175.000.000 dihitung dari **biaya bangun yang harus dipulihkan** (Rp 239,4 juta dibagi 3–4 pembeli), bukan dari **harga yang sanggup dan mau dibayar pasar**. Setelah dibandingkan dengan pasar:

| | Penawaran lama | **Usulan baru** |
|---|---:|---:|
| Harga list sistem (pembeli biasa, paket setara Pridata) | Rp 175.000.000 | **Rp 60.000.000** (beli putus) atau **Rp 2.500.000/bulan** (sewa) |
| Pridata: dibayar Tahun 1 (termasuk server) | Rp 116.550.000 | **Rp 24–40,5 juta** |
| Pridata: total 3 tahun (termasuk server) | Rp 212.350.000 | **Rp 63–70,5 juta** (turun ±67–70%) |
| Pridata: biaya berjalan per tahun | Rp 47.900.000 (2,4% omzet) | **Rp 15.000.000** (0,75% omzet) |

**Konsekuensi yang harus diterima:** dengan harga baru, biaya bangun **tidak bisa pulih dari 2–3 pembeli**. Butuh **±5–8 pelanggan** dalam 3–5 tahun. Menurut saya itu tetap lebih realistis daripada rencana lama, karena peluang menjual Rp 175 juta ke distributor NTB sangat kecil ketika Odoo bisa diimplementasikan Rp 30–60 juta dan SaaS distribusi hanya Rp 1,5–3 juta/bulan (§1).

---

## 1. Analisis pasar: kita dibandingkan dengan apa?

Distributor yang menilai sistem ini tidak membandingkannya dengan biaya bangun kita. Yang mereka bandingkan adalah alternatif berikut (harga publik 2025–2026, belum diverifikasi lewat kuotasi langsung):

| Alternatif | Harga | Kekuatan vs sistem kita | Kelemahan vs sistem kita |
|---|---|---|---|
| **Accurate Online** | Rp 333.000/bulan (1 user) + Rp 20.000/user, multi-cabang Rp 90.000/cabang | Akuntansi penuh sampai neraca, **ada PO ke supplier & penerimaan barang**, e-faktur | Bukan DMS: tidak ada penugasan sales↔toko, KPI sales, alur DO lengkap |
| **Mekari Jurnal** | Rp 399.000–1.169.000/bulan + Rp 99.000/user | Akuntansi, merek besar | Sama seperti Accurate |
| **SimpliDOTS (DMS FMCG)** | Rp 150.000–250.000/user/bulan (min. 10 user, kontrak 1 th) → **Rp 1,5–2,5 juta/bulan** | Aplikasi mobile sales, khusus distributor | Harga per user: mahal bila sales banyak |
| **ScaleOcean Distri Pro** | Mulai Rp 250.000/user/bulan (min. 5 user) | ERP lengkap | Vendor Jakarta, implementasi mahal |
| **Ukirama** | ±Rp 260.000–1.000.000/bulan | Murah, lokal | Fitur distribusi lebih umum |
| **Odoo** | Rp 137.500–212.500/user/bulan (Enterprise) + implementasi Rp 30–60 juta (UKM, 3–5 modul) | Sangat lengkap, ekosistem besar | Implementasi berat, butuh partner |
| **SAP Business One** | Ratusan juta rupiah | Kelas atas | Tidak proporsional untuk UKM |

**Kesimpulan pasar:**

1. **Distributor UKM dengan 10–20 pengguna membayar ±Rp 1,5–3 juta/bulan** (Rp 18–36 juta/tahun) untuk sistem SaaS, dengan biaya awal Rp 0–60 juta.
2. Harga list Rp 175 juta + Rp 27,5 juta/tahun + server hanya bersaing dengan **SAP B1/Odoo besar**. Pembeli di kelas itu biasanya distributor ber-omzet puluhan miliar, dan jumlahnya di NTB belum diketahui (Q2 = c "3–4 pembeli" belum pernah diverifikasi).
3. **Keunggulan kita yang nyata:**
   - Dibuat khusus untuk alur distributor (toko, grade toko, sales↔toko, DO pick→pack→ship, piutang aging, ledger stok).
   - **Harga flat per perusahaan, bukan per pengguna.** Bagi distributor dengan banyak sales, ini menang telak atas SimpliDOTS/Odoo.
   - **Tim ada di Lombok**: bisa datang ke gudang, bicara bahasa yang sama, dan tidak harus menunggu tiket ke Jakarta.
4. **Kelemahan kita yang nyata**, dan harga harus mengakuinya:
   - Belum ada akuntansi penuh (buku besar/neraca) dan belum ada e-faktur.
   - Belum ada aplikasi mobile native.
   - **Belum ada PO ke supplier & penerimaan barang terkontrol.** Ini justru masalah utama Pridata, dan Accurate seharga Rp 333 ribu/bulan sudah memilikinya.
   - Belum ada rekam jejak selain Pridata.

**Satu temuan biaya yang ikut menurunkan harga:** ATO-2 mengasumsikan server Rp 1.700.000/bulan (Rp 20,4 juta/tahun). Harga VPS 4 vCPU / 8 GB di Indonesia sekarang ±Rp 85.000–200.000/bulan di penyedia murah, dan beberapa ratus ribu di penyedia besar. **Saya pakai Rp 500.000/bulan (Rp 6 juta/tahun) termasuk backup off-site**, cukup aman untuk distributor seukuran Pridata. Ini saja memangkas biaya berjalan Pridata ±Rp 14 juta/tahun. *Perlu dicek dengan kuotasi penyedia yang benar-benar akan dipakai.*

---

## 2. Prinsip harga baru

1. **Pasar menentukan batas atas, biaya menentukan batas bawah.** Biaya bangun Rp 239,4 juta sudah keluar (*sunk cost*). Ia menentukan *berapa pelanggan yang dibutuhkan* agar usaha ini layak, bukan *berapa harga per pelanggan*.
2. **Batas bawah = biaya marjinal per pelanggan:** implementasi, server, dan dukungan. Setiap harga di bawah ini harus berada di atasnya (kecuali Pridata, dengan alasan yang dinyatakan).
3. **Pridata selalu lebih murah daripada kompetitornya,** dan selisihnya dibayar dengan kontribusi yang nyata (data riset, co-development Fase 2), bukan hanya "karena yang pertama".
4. **Fase 2 (penerimaan barang) adalah investasi produk, bukan proyek kustom Pridata.** Masalah salah catat barang masuk dialami semua distributor. Modul itu menaikkan nilai jual ke seluruh pasar, jadi sebagian besar biayanya ditanggung Ato-team sebagai R&D.

**Asumsi biaya yang dipakai** (dari ATO-2, dengan koreksi):

| Asumsi | Nilai | Catatan |
|---|---|---|
| Biaya internal | Rp 950.000/orang-hari | ATO-2 A3, belum dicek ke penggajian |
| Server per pelanggan | Rp 500.000/bulan | Dikoreksi dari Rp 1.700.000 (§1) |
| Implementasi standar kompetitor | 10 / 16 / 25 orang-hari (Starter/Bisnis/Pro) | Lebih ramping dari 40 od ATO-2, karena produk sudah jadi dan implementasinya ditemplatkan (impor data master, konfigurasi, pelatihan, pendampingan go-live) |
| Dukungan khusus per pelanggan | 6 / 10 / 16 orang-hari/tahun | Help desk WhatsApp/telepon, uji restore, koordinasi server |
| Pemeliharaan produk bersama | 20 orang-hari/tahun dibagi semua pelanggan | Patch, upgrade, perbaikan bug. Satu kode untuk semua, jadi perbaikan tidak dihitung per pelanggan |

---

## 3. Skema B: Harga untuk kompetitor Pridata (daftar harga umum NTB)

Ini harga yang **dipublikasikan** dan menjadi jangkar. Semua paket berisi **47 fitur yang sama**. Pembedanya adalah kuota, jumlah gudang, dan tingkat layanan, supaya tidak perlu membangun *feature-flag* baru.

### 3.1 Paket

| | **Starter** | **Bisnis** | **Pro** |
|---|---|---|---|
| Cocok untuk | Distributor kecil, 1 gudang | Distributor menengah | Distributor besar / multi-cabang |
| Pengguna | s.d. 8 | s.d. 20 | Tak terbatas |
| Gudang | 1 | s.d. 3 | Tak terbatas |
| Waktu respons (hari kerja) | 1 hari kerja | 8 jam kerja | 4 jam kerja |
| Help desk | ±4 jam/bulan | ±8 jam/bulan | ±12 jam/bulan |
| Kunjungan on-site | — | 1× per semester | 1× per kuartal |
| Jatah perubahan kecil | — | — | 4 orang-hari/tahun |
| Modul Penerimaan Barang (Fase 2, setelah rilis) | Add-on Rp 250.000/bulan | **Termasuk** | **Termasuk** |

### 3.2 Harga: dua cara bayar

**Opsi SEWA (disarankan untuk kebanyakan distributor):** server disediakan dan dikelola Ato-team, kontrak minimum 12 bulan, data bisa diekspor penuh bila berhenti.

| | Starter | Bisnis | Pro |
|---|---:|---:|---:|
| Biaya setup & implementasi (sekali) | Rp 7.500.000 | Rp 15.000.000 | Rp 25.000.000 |
| Sewa per bulan (hak pakai + server + dukungan) | **Rp 1.500.000** | **Rp 2.500.000** | **Rp 4.000.000** |
| Tahun 1 | Rp 25.500.000 | Rp 45.000.000 | Rp 73.000.000 |
| Tahun 2 dan seterusnya | Rp 18.000.000 | Rp 30.000.000 | Rp 48.000.000 |
| **Total 3 tahun** | **Rp 61.500.000** | **Rp 105.000.000** | **Rp 169.000.000** |

**Opsi BELI PUTUS:** lisensi perpetual + implementasi, server milik pembeli, ASC mulai bulan ke-4 (garansi 3 bulan).

| | Starter | Bisnis | Pro |
|---|---:|---:|---:|
| Lisensi + implementasi (sekali) | **Rp 35.000.000** | **Rp 60.000.000** | **Rp 95.000.000** |
| ASC per bulan (tanpa server) | Rp 800.000 | Rp 1.250.000 | Rp 2.250.000 |
| Server milik pembeli (perkiraan) | ±Rp 500.000/bulan | ±Rp 500.000/bulan | ±Rp 500.000/bulan |
| **Total 3 tahun termasuk server** | **±Rp 79.400.000** | **±Rp 119.250.000** | **±Rp 187.250.000** |

Beli putus lebih mahal selama 3 tahun pertama. Titik impasnya dengan sewa sekitar tahun ke-4 sampai ke-5 (paket Bisnis). Yang dibeli adalah **kepemilikan dan kendali**, bukan penghematan, dan itu harus dikatakan jujur ke pembeli.

### 3.3 Posisi terhadap pasar (paket Bisnis, 15 pengguna)

| | Per bulan (setara) | Catatan |
|---|---:|---|
| SimpliDOTS 15 user | Rp 2.250.000–3.750.000 | Per user, tanpa akuntansi |
| Odoo Enterprise 15 user + implementasi Rp 30–60 juta | Rp 2.060.000–3.190.000 + implementasi | Butuh partner |
| **Ato-team Bisnis (sewa)** | **Rp 2.500.000 flat + setup Rp 15 juta** | Harga tetap walau pengguna bertambah, tim lokal |
| Accurate Online 15 user | ±Rp 610.000 | Jauh lebih murah, tapi bukan DMS. Ini kombinasi yang harus dilawan dengan fitur distribusi, bukan harga |

### 3.4 Ekonomi per pelanggan kompetitor (dengan asumsi 5 pelanggan aktif)

| Paket | Kontribusi 3 tahun (sewa) | Kontribusi 3 tahun (beli) | Kontribusi per tahun setelah Th3 (sewa) |
|---|---:|---:|---:|
| Starter | Rp 5.500.000 | Rp 23.400.000 | Rp 2.500.000 |
| Bisnis | Rp 31.900.000 | Rp 46.150.000 | Rp 10.700.000 |
| Pro | Rp 70.250.000 | Rp 88.500.000 | Rp 23.000.000 |

*Kontribusi = pendapatan − biaya implementasi − server − dukungan (termasuk pangsa pemeliharaan bersama).* Starter hampir impas dan berfungsi sebagai pintu masuk. Marjin ada di Bisnis dan Pro.

---

## 4. Skema A: Harga untuk Pridata (mitra riset & pengguna pertama)

Pridata setara paket **Bisnis**. Dasar harganya adalah paket Bisnis kompetitor, bukan list Rp 175 juta lagi.

### 4.1 Dua pilihan untuk Pridata

**P-A: Beli putus mitra.** Tetap "50% dari harga list", hanya saja list-nya sekarang realistis.

| Komponen | Harga Bisnis (kompetitor) | Potongan mitra | **Pridata** |
|---|---:|---:|---:|
| Lisensi perpetual + implementasi | Rp 60.000.000 | −Rp 30.000.000 | **Rp 30.000.000** |
| ASC per bulan (tanpa server) | Rp 1.250.000 | −Rp 500.000 | **Rp 750.000** |
| Garansi | 3 bulan | +3 bulan | **6 bulan** |
| Cara bayar | 4 termin | | **Boleh dicicil 6× Rp 5.000.000** atau 3 termin milestone |

| | Tahun 1 | Tahun 2 | Tahun 3 | **3 tahun** |
|---|---:|---:|---:|---:|
| Sistem | Rp 30.000.000 | — | — | Rp 30.000.000 |
| ASC (mulai bulan ke-7) | Rp 4.500.000 | Rp 9.000.000 | Rp 9.000.000 | Rp 22.500.000 |
| Server milik Pridata (±) | Rp 6.000.000 | Rp 6.000.000 | Rp 6.000.000 | Rp 18.000.000 |
| **Total Pridata** | **Rp 40.500.000** | **Rp 15.000.000** | **Rp 15.000.000** | **Rp 70.500.000** |

**P-B: Sewa-milik 24 bulan (menurut saya paling cocok untuk kas Pridata).** Tanpa uang muka besar. Setelah 24 bulan lisensi menjadi milik Pridata.

| | Tahun 1 | Tahun 2 | Tahun 3 | **3 tahun** |
|---|---:|---:|---:|---:|
| Sewa-milik Rp 2.000.000/bulan × 24 (termasuk server & dukungan) | Rp 24.000.000 | Rp 24.000.000 | — | Rp 48.000.000 |
| Setelah milik: ASC + server dikelola Rp 1.250.000/bulan | — | — | Rp 15.000.000 | Rp 15.000.000 |
| **Total Pridata** | **Rp 24.000.000** | **Rp 24.000.000** | **Rp 15.000.000** | **Rp 63.000.000** |

### 4.2 Beban terhadap skala Pridata (omzet ± Rp 2 miliar/tahun)

| | Lama | P-A | P-B |
|---|---:|---:|---:|
| Tahun 1, % omzet | 5,8% | 2,0% | **1,2%** |
| Tahun 1, % laba bersih (asumsi Rp 60–100 juta) | 117–194% | 41–68% | **24–40%** |
| Tahun 2+, per bulan | Rp 3.991.667 | **Rp 1.250.000** | Rp 2.000.000 → Rp 1.250.000 |
| Tahun 2+, % omzet | 2,4% | **0,75%** | 1,2% → 0,75% |

P-A pun masih berat di Tahun 1 bila omzet benar Rp 2 miliar/tahun. Karena itu P-B saya anggap pilihan utama, dan P-A untuk Pridata yang ingin langsung memiliki.

### 4.3 Apakah Ato-team rugi di harga Pridata?

| | P-A | P-B |
|---|---:|---:|
| Pendapatan 3 tahun ke Ato-team | Rp 52.500.000 | Rp 63.000.000 |
| Biaya marjinal 3 tahun (dukungan, server bila Ato yang host, sisa implementasi) | ±Rp 44.650.000 | ±Rp 57.900.000 |
| **Kontribusi bersih** | **±Rp 7.850.000** | **±Rp 5.100.000** |

**Tidak rugi secara marjinal, tapi hampir tidak menyumbang ke pemulihan biaya bangun.** Itu disengaja: nilai Pridata bagi Ato-team ada di data riset dan uji lapangan Fase 2, bukan di uangnya.

### 4.4 Timbal balik: yang harus diubah karena kita juga menjual ke kompetitor Pridata

Paket timbal balik lama (K1–K5) **tidak cocok lagi** begitu kita juga menjual ke pesaing Pridata. Tidak masuk akal meminta Pridata menjadi lokasi demo bagi pesaingnya atau merujuk pesaingnya sendiri.

| Butir lama | Usulan baru | Alasan |
|---|---|---|
| K1 Studi kasus & referensi bernama | **Opsional.** Studi kasus boleh anonim ("distributor di Mataram") | Pridata wajar keberatan namanya dipakai untuk menjual ke pesaing |
| K2 Akses data riset (anonim, NDA) | **Tetap, wajib.** Ini inti program riset | Tanpa K2, tidak ada alasan potongan mitra |
| K3 Testimoni + lokasi demo | **Lokasi demo dihapus.** Testimoni opsional. Ato-team membuat environment demo dengan data sintetis | Kunjungan pesaing ke gudang Pridata merugikan Pridata |
| K4 Komitmen ASC | Tetap dicabut (P-A). Di P-B, komitmen 24 bulan menjadi bagian dari sewa-milik | |
| K5 Co-development Fase 2 (20 sesi) | **Tetap, wajib** | Ini yang membuat Fase 2 bisa dijual ke pasar |
| Kredit Rujukan | **Hanya untuk rujukan non-pesaing** (mis. distributor kategori lain, Sumbawa/NTT) | Pridata tidak akan merujuk pesaingnya |

**Yang diberikan Ato-team sebagai gantinya (murah bagi kita, bernilai bagi Pridata):**

1. **Harga mitra terkunci 3 tahun**, tanpa indeksasi.
2. **Akses pertama Fase 2:** modul Penerimaan Barang dipakai Pridata **6 bulan sebelum** dijual ke distributor lain. Ini jawaban langsung atas "kenapa kami membantu kalian membuat produk untuk pesaing kami".
3. **Firewall kerahasiaan tertulis:** data, daftar toko, grade harga, dan konfigurasi Pridata tidak pernah dipakai, dilihat, atau dijadikan template untuk implementasi pelanggan lain. Data riset hanya dalam bentuk agregat anonim.
4. **Bank 5 orang-hari** permintaan perubahan (3 tahun) untuk menyesuaikan sistem dengan cara kerja Pridata. Dikurangi dari 10 od, karena harga dasar sudah turun jauh.

### 4.5 Fase 2 (penerimaan barang anti human-error) untuk Pridata

- Effort paket inti (Bayu, ATO-3): **27–48 orang-hari**. Biaya internal: **Rp 25,7–45,6 juta**.
- **Usulan:** Ato-team mendanai Fase 2 sebagai R&D produk. Pridata membayar **kontribusi tetap Rp 10.000.000** (boleh dicicil) plus K5 (20 sesi uji coba).
- Distributor lain mendapat modul ini **termasuk di paket Bisnis/Pro** (add-on di Starter). Ini yang membenarkan harga Bisnis/Pro di atas Accurate.
- Kriteria penerimaan tetap T1, T3, T4, T5 (ATO-3). **T6 tidak dijanjikan.**

Menurut saya ini perubahan terpenting. Penawaran lama meminta Pridata membayar Rp 87,5 juta untuk sistem yang **belum menyelesaikan masalah utamanya**, lalu meminta bayaran lagi (±Rp 47–84 juta) untuk solusinya. Usulan baru membalik urutannya: harga dasar yang wajar, dan solusi masalah utamanya ikut dibangun bersama dengan biaya kecil.

---

## 5. Apakah bisnis ini masih layak dengan harga baru?

| | Rencana lama | Rencana baru |
|---|---|---|
| Yang harus dipulihkan | Rp 189,9 juta (biaya bangun − kontribusi Pridata) | **±Rp 257 juta** (biaya bangun Rp 239,4 juta + Fase 2 ±Rp 35,6 juta − kontribusi Pridata ±Rp 17,9 juta) |
| Kontribusi per pelanggan | Rp 105 juta (lisensi list) | Rp 32–46 juta (Bisnis, 3 tahun) · Rp 50–53 juta (Bisnis, 5 tahun) |
| **Pelanggan yang dibutuhkan** | **2–3** di harga Rp 175 juta | **±5–6 pelanggan dalam 5 tahun**, atau ±6–8 dalam 3 tahun (campuran paket Bisnis) |
| Peluang terjual | Rendah: harga 3–5× pasar UKM, hanya cocok untuk distributor ber-omzet ≥ Rp 28 miliar | Lebih tinggi: harga setara SaaS distribusi, dengan keunggulan tim lokal dan harga flat |

**Pertanyaan yang sebenarnya:** apakah ada **5–8 distributor** di NTB (atau NTB + Bali/NTT) yang mau membayar ±Rp 2,5 juta/bulan? Menurut saya jauh lebih mungkin daripada **3–4 distributor** yang mau membayar Rp 175 juta. Tapi angka ini tetap harus diuji dengan **sensus pasar** (daftar distributor, kategori produk, perkiraan skala). Itu sudah ada di rencana CEO dan belum dikerjakan.

---

## 6. Yang perlu diputuskan / dikonfirmasi (bahan diskusi)

1. **Omzet Pridata.** Rp 2 miliar per **tahun** atau per **bulan**? Bila per bulan (Rp 24 miliar/tahun), Pridata lebih cocok di paket Pro, dan harga mitra bisa naik ke ±Rp 45–50 juta (tetap jauh di bawah penawaran lama).
2. **Kepemilikan IP.** Sistem dibangun "untuk Pridata". Apakah ada perjanjian bahwa Pridata ikut memiliki kode, atau pernah membayar pembangunannya? Bila ya, **menjual ke kompetitornya butuh persetujuan Pridata**. Ini harus beres sebelum Skema B dijalankan.
3. **Apakah Pridata tahu kita akan menjual ke pesaingnya?** Saran saya, katakan terbuka sejak awal dan tawarkan akses pertama Fase 2 + firewall kerahasiaan (§4.4). Opsi tambahan yang bisa dipertimbangkan: **eksklusivitas terbatas**, misalnya tidak menjual ke distributor dengan *principal*/merek yang sama di Lombok selama 12 bulan. Opsi ini mengorbankan pasar, jadi keputusannya di Anda.
4. **Pridata: P-A atau P-B sebagai tawaran utama?** Saya condong ke **P-B (sewa-milik Rp 2 juta/bulan)**.
5. **Fase 2 didanai Ato-team** (Pridata hanya kontribusi Rp 10 juta)? Ini investasi ±Rp 26–46 juta dari kas/waktu tim.
6. **Tarik NTB-PL-2026-09.** Daftar harga lama belum pernah dikirim ke pembeli (penawaran Pridata belum terkirim), jadi masih aman diganti dengan daftar harga baru bernomor baru. Setelah daftar harga baru terbit dan dipakai, jangan diubah-ubah lagi.
7. **Status sistem di Pridata:** sudah dipakai produksi atau belum? Bila sudah, biaya implementasi Pridata praktis nol dan P-A bisa turun lagi ±Rp 5 juta.
8. **Verifikasi dua angka biaya:** rate internal Rp 950.000/od (penggajian nyata) dan harga server (kuotasi penyedia).

---

## 7. Yang tidak berubah dari analisis agent sebelumnya

- Bagian **human error ditulis jujur di depan**: sistem sekarang kuat di keterlacakan, belum di pencegahan. Fase 2 jawabannya.
- **Tidak ada klaim penghematan/ROI** di materi penjualan untuk distributor kecil.
- **Termin terikat milestone**, bukan tanggal.
- **Harga mitra ditulis sebagai harga list − potongan** (baris terpisah), dengan klausul kerahasiaan dan non-preseden.
- **Scope boundary:** integrasi e-faktur/bank/marketplace, aplikasi mobile native, dan akuntansi penuh tetap di luar paket (Rp 1.750.000/od, atau dijadikan roadmap bila banyak pelanggan meminta).

---

## 8. Sumber harga pasar

- Accurate Online: [penjualanonline.id](https://penjualanonline.id/accurate-online/harga-accurate-online/), [softwareonline.id](https://softwareonline.id/harga-accurate-online/)
- Mekari Jurnal: [jurnal.id pricing](https://www.jurnal.id/en/pricing-plans/), [gosumbar.com](https://www.gosumbar.com/berita/baca/2026/03/25/analisis-harga-dan-keunggulan-layanan-aplikasi-akuntansi-mekari-jurnal-yang-terjangkau)
- Odoo: [oec.sh Indonesia](https://oec.sh/odoo-pricing/indonesia), [odoo.com/pricing](https://www.odoo.com/pricing); implementasi: [digisolf.com](https://www.digisolf.com/en/blog/odoo-13/biaya-implementasi-odoo-di-indonesia-rincian-harga-dan-faktor-penentunya-138), [hash.id](https://hash.id/berapa-harga-odoo-erp-dan-biaya-implementasinya/)
- SimpliDOTS: [simplidots.com/harga](https://www.simplidots.com/harga/), [FAQ SimpliDOTS](https://simplidots.gitbook.io/faq/frequently-asked-questions/memulai-dengan-simplidots/distribution-management-system-dms/berapa-harga-berlangganan-dms)
- ScaleOcean & Ukirama: [scaleocean.com](https://scaleocean.com/id/blog/rekomendasi/software-distributor-terbaik), [ukirama.com](https://ukirama.com/blogs/software-distributor)
- VPS Indonesia: [awanservers.com](https://www.awanservers.com/benchmark-vps-orangevps-4-core-8gb-ram-cuma-rp-107-000-worth-it/), [biznetgio.com](https://www.biznetgio.com/product/vps-murah-indonesia), [rumahweb.com](https://www.rumahweb.com/vps-murah/)

*Harga pihak ketiga diambil dari halaman publik dan artikel per September 2026, bisa berubah, dan belum diverifikasi lewat kuotasi langsung. Semua harga Ato-team belum termasuk PPN.*
