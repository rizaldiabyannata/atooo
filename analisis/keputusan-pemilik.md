# Keputusan Pemilik & Dampaknya ke Harga

**Tanggal:** 29 September 2026 · **Dokumen internal** · Menjawab §6 `analisis/revisi-harga-dua-skema.md`, dan menyesuaikan `analisis/hasil-debat-harga.md`.

## 1. Jawaban pemilik

| # | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Omzet Pridata | **Rp 2 miliar per tahun** (terkonfirmasi) |
| 2 | Kepemilikan IP | **Milik Ato-team.** Pridata tidak berkontribusi langsung dalam pembangunan |
| 3 | Apakah Pridata diberi tahu sistem dijual ke pesaingnya | **Tidak diumumkan.** Sistem ini hanya *base*; setiap pembeli lain akan mendapat kustomisasi sesuai bisnisnya |
| 4 | Tawaran utama Pridata | **P-A (beli putus)**, karena Ato-team tidak punya modal sama sekali dan beranggotakan **4 orang** |
| 5 | Fase 2 didanai Ato-team | **Tidak ada dana.** Semua modal berasal dari anggota tim masing-masing |
| 6 | Daftar harga NTB-PL-2026-09 | **Belum pernah dikirim/dipublikasikan** ke pihak mana pun |
| 7 | Status sistem di Pridata | **Belum produksi.** Akan masuk tahap trial |
| 8 | Rate internal & kuotasi server | *Belum dijawab* |

## 2. Dampak tiap jawaban

**#1 Omzet Rp 2 M/tahun.** Semua cabang "kalau ternyata per bulan" dibuang. Batas yang mengikat untuk Pridata adalah **kemampuan bayar**: laba bersih diperkirakan Rp 60–100 jt/tahun.

**#2 IP milik Ato-team.** Menjual ke pihak lain sah. Tetapi kontrak Pridata **wajib menyebut tegas**:
- lisensi yang diberikan **non-eksklusif**;
- IP tetap milik Ato-team;
- kustomisasi yang dibayar Pridata tidak memberi hak kepemilikan atas produk.

Tanpa klausul ini, Pridata bisa mengklaim belakangan bahwa sistem "dibuat untuk kami". Escrow kode sumber (syarat kedua pembeli di debat) tetap bisa diberikan, karena escrow hanya memberi **hak pakai** bila Ato-team berhenti melayani, bukan kepemilikan.

**#3 Dirahasiakan dari Pridata.** Tidak mengumumkan itu sah. Tetapi ada tiga risiko yang harus dikelola:
1. **Mataram kecil.** Pesaing yang memakai sistem dengan tampilan dan alur yang sama akan terlihat. Kalau Pridata tahu dari orang lain, yang rusak adalah kepercayaan, bukan hanya harga. Apalagi Ato-team memegang data operasional Pridata (K2).
2. **Jangan pernah menyangkal kalau ditanya.** Menyembunyikan boleh, berbohong tidak. Kalimat aman: *"Lisensi Anda non-eksklusif, dan data serta konfigurasi Anda tidak pernah dipakai untuk pihak lain."*
3. **Klausul "akses lebih dulu Fase 2" dari debat dihapus.** Tanpa pengumuman, klausul itu tidak relevan. Gantinya klausul **firewall data** (database terpisah per pelanggan, akses tercatat) yang tetap wajib di kontrak Pridata.

**Konsekuensi teknis dari "base + kustomisasi":** dengan 4 orang, **jangan membuat salinan kode (fork) per pelanggan.** Kustomisasi harus berupa konfigurasi atau *feature flag* di satu kode yang sama. Setiap fork menggandakan beban patch, upgrade, dan escrow, dan inilah yang paling cepat menghabiskan kapasitas tim kecil.

**#4 + #5 P-A dan tidak ada modal.** Keduanya menunjuk ke kebutuhan yang sama: **kas masuk cepat.** Masalahnya, P-A juga paling berat bagi Pridata. Kompromi di §3: harga P-A tetap Rp 30 jt, tapi dibayar dalam **termin yang diikat ke milestone trial, go-live, dan Fase 2**. Ato-team mendapat kas di awal, dan Pridata membayar sesuai hasil yang terlihat.

Fase 2 inti (27 od) tidak didanai dengan uang, tetapi dengan **waktu tim**. Karena itu ia dimasukkan ke harga P-A sebagai **termin ke-3**, bukan digratiskan.

**4 orang, bukan 2.** Analisis CFO memakai asumsi 2 orang (±460 od/tahun):
- **Kapasitas praktis dua kali lipat** (±900 od/tahun). Melayani Pridata dan beberapa kompetitor sekaligus mengerjakan kustomisasi menjadi realistis.
- **Pendapatan produk dibagi 4 orang.** Karena tidak ada gaji tetap, rate Rp 950 rb/od adalah *biaya peluang*, bukan kas keluar. Kas keluar nyata hanya server, transport, dan operasional.
- **Sumber uang terbesar kemungkinan besar kustomisasi** (Rp 1,75 jt/od) untuk kompetitor, bukan sewa bulanan.

**#6 Daftar harga lama belum pernah keluar.** Bisa langsung diganti daftar harga baru (paket "Distributor" di `hasil-debat-harga.md` §3.1) **tanpa risiko jangkar**.

**#7 Belum produksi, masuk trial.** Implementasi di Pridata adalah pekerjaan nyata: migrasi data master, pelatihan, pendampingan. Pembayaran **dimulai setelah trial dinyatakan layak**, bukan sebelumnya.

## 3. Skema Pridata yang direvisi: P-A dengan termin milestone

| Termin | Milestone | Bayar |
|---|---|---:|
| — | **Trial** 30–60 hari: sistem dipakai paralel dengan cara lama, data master dimigrasi | Rp 0 (atau tanda jadi kecil) |
| 1 | Tanda tangan kontrak **setelah trial dinyatakan layak** | **Rp 10.000.000** |
| 2 | Go-live: semua transaksi harian lewat sistem, pelatihan selesai | **Rp 10.000.000** |
| 3 | **Fase 2 inti lulus** kriteria T1, T3, T4, T5 di gudang Pridata | **Rp 10.000.000** |
| | **Harga sistem (lisensi perpetual non-eksklusif + implementasi + Fase 2 inti)** | **Rp 30.000.000** |
| ASC | Mulai bulan ke-4 setelah go-live (garansi 3 bulan). Paket layanan Hemat (`hasil-debat-harga.md` §3.3) | **Rp 1.250.000/bln** |
| Server | Milik Pridata, perkiraan (belum dikuotasi) | ±Rp 500.000/bln |

Termin 2 dan 3 boleh dipecah menjadi 2 × Rp 5 jt per bulan bila kas Pridata ketat. Harga total tidak berubah.

**Beban Pridata** (asumsi go-live bulan ke-2, Fase 2 lulus bulan ke-6):

| | Tahun 1 | Tahun 2 | Tahun 3 | 3 tahun |
|---|---:|---:|---:|---:|
| Sistem | Rp 30.000.000 | — | — | Rp 30.000.000 |
| ASC | Rp 10.000.000 | Rp 15.000.000 | Rp 15.000.000 | Rp 40.000.000 |
| Server milik Pridata (±) | Rp 5.500.000 | Rp 6.000.000 | Rp 6.000.000 | Rp 17.500.000 |
| **Total** | **Rp 45.500.000** | **Rp 21.000.000** | **Rp 21.000.000** | **Rp 87.500.000** |
| % omzet | 2,3% | 1,05% | 1,05% | |
| % laba bersih (asumsi Rp 60–100 jt) | 46–76% | 21–35% | 21–35% | |

**Kas masuk Ato-team Tahun 1: Rp 40 jt** (Rp 30 jt sistem + Rp 10 jt ASC), dibanding ±Rp 19,5 jt di skema sewa-milik hasil debat.

**Risiko yang harus diakui:** Tahun 1 memakan sekitar separuh laba bersih Pridata. Di debat, peran Pridata menyatakan akan pindah ke Accurate bila uang muka > Rp 10 jt. Karena itu termin 1 dibuat tepat Rp 10 jt, dan sisanya baru dibayar setelah ada hasil (go-live, Fase 2). **Bila Pridata tetap menolak, cadangan: skema sewa-milik** (`hasil-debat-harga.md` §3.2). Kas awalnya lebih kecil, tapi pelanggannya tidak hilang.

## 4. Skema kompetitor: tambahan dari jawaban #3

Harga dasar tetap paket "Distributor" (`hasil-debat-harga.md` §3.1: Rp 1,75 jt/bln gudang pertama + Rp 750 rb per gudang tambahan, setup Rp 10 jt, kontrak 24 bulan). Tambahannya:

- **Kustomisasi per pelanggan:** Rp 1.750.000/od, minimum 5 od, di-scope dan disetujui tertulis sebelum dikerjakan. Selalu dibangun sebagai konfigurasi/feature flag di kode yang sama.
- **Setup Rp 10 jt** mencakup konfigurasi standar saja, bukan kustomisasi.
- **Tidak menyebut Pridata** dalam materi penjualan mana pun, konsisten dengan keputusan #3.

## 5. Yang masih perlu dijawab

1. **Rate internal & kuotasi server (#8).** Tanpa gaji tetap, angka ini menentukan berapa penghasilan per orang, bukan apakah perusahaan rugi kas. Kuotasi server tetap diperlukan, karena biaya itu ditanggung Pridata (P-A) atau Ato-team (sewa kompetitor).
2. **Siapa yang benar-benar membangun sistem ini:** 2 orang penuh waktu selama 6 bulan (asumsi ATO-2), atau 4 orang? Ini hanya mengubah angka biaya bangun (sunk cost), tidak mengubah harga yang direkomendasikan.
3. **Model server kompetitor:** Ato-team host (satu server, database terpisah per pelanggan) atau VPS milik pembeli? (`hasil-debat-harga.md` §5)
