# Keputusan Pemilik & Dampaknya ke Harga

**Tanggal:** 29 September 2026 · **Dokumen internal** · Menjawab §6 `analisis/revisi-harga-dua-skema.md` dan menyesuaikan `analisis/hasil-debat-harga.md`.

## 1. Jawaban pemilik

| # | Pertanyaan | Jawaban |
|---|---|---|
| 1 | Omzet Pridata | **Rp 2 miliar per tahun** (terkonfirmasi) |
| 2 | Kepemilikan IP | **Milik Ato-team.** Pridata tidak berkontribusi langsung dalam pembangunan |
| 3 | Apakah Pridata diberi tahu sistem dijual ke pesaingnya | **Tidak diumumkan.** Sistem ini hanya *base*; setiap pembeli lain akan mendapat kustomisasi sesuai bisnisnya |
| 4 | Tawaran utama Pridata | **P-A (beli putus)**, karena Ato-team tidak punya modal sama sekali |
| 5 | Fase 2 didanai Ato-team | **Tidak ada dana.** Semua modal berasal dari anggota tim masing-masing |
| 6 | Daftar harga NTB-PL-2026-09 | **Belum pernah dikirim/dipublikasikan** ke pihak mana pun |
| 7 | Status sistem di Pridata | **Belum produksi.** Akan masuk tahap trial |
| 8 | Server | **Hostinger VPS KVM 2** |
| 9 | Susunan tim (4 orang) | **2 orang penuh untuk sistem internal (ERP)**, 1 orang untuk layanan mobile & aplikasi, 1 orang marketing & pengarah |
| 10 | Model server | **VPS milik pembeli, dibayar dari harga pembelian awal** |
| 11 | Kapan server dibeli | **Setelah deal (selesai trial)**, dan dicantumkan di proposal |

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

**Konsekuensi teknis dari "base + kustomisasi":** **jangan membuat salinan kode (fork) per pelanggan.** Kustomisasi harus berupa konfigurasi atau *feature flag* di satu kode yang sama. Setiap fork menggandakan beban patch, upgrade, dan escrow, dan inilah yang paling cepat menghabiskan kapasitas 2 developer.

**#4 + #5 P-A dan tidak ada modal.** Keduanya menunjuk ke kebutuhan yang sama: **kas masuk cepat**, dan **Ato-team tidak bisa menalangi apa pun** (termasuk server). Masalahnya, P-A juga paling berat bagi Pridata. Kompromi di §4: harga P-A tetap Rp 30 jt, tapi dibayar dalam **termin yang diikat ke milestone trial, go-live, dan Fase 2**.

Fase 2 inti (27 od) tidak didanai dengan uang, tetapi dengan **waktu tim**. Karena itu ia dimasukkan ke harga P-A sebagai **termin ke-3**, bukan digratiskan.

**#9 Susunan tim.** Yang menangani ERP tetap **2 orang penuh**, jadi:
- Biaya bangun ATO-2 (252 od, 2 orang × 6 bulan) tetap berlaku.
- **Model kapasitas CFO (±460 od/tahun untuk ERP) juga tetap berlaku.** Klaim sebelumnya bahwa kapasitas "dua kali lipat" **salah dan dicabut**. Batas ±3 pelanggan baru per tahun tetap dipakai.
- Yang membaik: **penjualan dipegang orang marketing**, bukan developer. Waktu "kesiapan jual" di hitungan CFO tidak lagi memakan jam developer.
- Peluang: orang mobile bisa menutup kelemahan "tidak ada aplikasi mobile untuk sales" yang dikeluhkan calon pembeli kompetitor. Tempatkan sebagai roadmap/add-on berbayar, bukan janji di penawaran pertama.
- Karena tidak ada gaji tetap, rate Rp 950 rb/od adalah *biaya peluang*, bukan kas keluar. Sumber uang terbesar kemungkinan kustomisasi (Rp 1,75 jt/od) untuk kompetitor.

**#6 Daftar harga lama belum pernah keluar.** Bisa langsung diganti daftar harga baru (paket "Distributor" di `hasil-debat-harga.md` §3.1) **tanpa risiko jangkar**.

**#7 Belum produksi, masuk trial.** Implementasi di Pridata adalah pekerjaan nyata: migrasi data master, pelatihan, pendampingan. Pembayaran sistem **dimulai setelah trial dinyatakan layak**.

## 3. Server: Hostinger VPS KVM 2, milik pembeli (#8, #10)

| | Nilai |
|---|---|
| Spesifikasi | 2 vCPU, 8 GB RAM, 100 GB NVMe, bandwidth 8 TB |
| Harga promo kontrak 24 bulan | **Rp 151.900/bln → Rp 3.645.600 dibayar di muka** |
| Kontrak 12 bulan / bulanan | Rp 180.900/bln / Rp 252.900/bln |
| **Perpanjangan** (siklus 24 bulan) | **±Rp 232.900/bln → ±Rp 5.589.600 per 2 tahun** (±Rp 2,8 jt/tahun) |
| Backup bawaan | Mingguan gratis. Harian add-on ±Rp 104.900/bln |
| Lokasi | Tersedia data center Indonesia dan Malaysia |

*Angka diambil dari ringkasan hasil pencarian (§7). Halaman Hostinger diblokir proxy, jadi belum dicek langsung. Harga kemungkinan belum termasuk PPN: cek di halaman checkout sebelum membeli.*

**Dibanding asumsi sebelumnya (Rp 500 rb/bln), biaya server turun ±70%.** Tiga catatan:

1. **KVM 2 cukup untuk distributor kecil–menengah** (≤ ±20 pengguna, 1–3 gudang), termasuk Pridata. ATO-2 dulu menulis spesifikasi minimum 4 vCPU. Untuk pembeli besar (Pro), gunakan KVM 4 dengan kuotasi tersendiri.
2. **Backup mingguan tidak cukup untuk data uang dan stok.** Kalau server rusak di hari ke-6, transaksi 6 hari hilang. Pakai salah satu:
   - (a) add-on backup harian Hostinger ±Rp 104.900/bln; atau
   - (b) **disarankan:** dump database otomatis tiap malam ke penyimpanan di luar Hostinger (mis. object storage dengan free tier). Biaya ±Rp 0, dan backup benar-benar *off-site*. Dikerjakan sekali sebagai stack standar untuk semua pelanggan.
3. **Harga perpanjangan ±53% lebih mahal dari promo.** Pembeli harus tahu ini **sebelum tanda tangan**, bukan di bulan ke-24. VPS yang lupa diperpanjang berarti sistem mati dan data bisa dihapus penyedia. Karena itu:
   - akun VPS **atas nama dan metode bayar pembeli**, dengan perpanjangan otomatis;
   - Ato-team diberi akses kelola;
   - **pemantauan tanggal kedaluwarsa masuk tugas ASC.**

## 4. Skema Pridata yang direvisi: P-A dengan termin milestone + VPS

| Termin | Milestone | Bayar |
|---|---|---:|
| — | **Trial 30–60 hari** di environment Ato-team yang sudah ada (staging/dev), dipakai paralel dengan cara lama, data master dimigrasi. **Tidak ada server yang dibeli di tahap ini** | Rp 0 |
| 1 | **Deal:** tanda tangan kontrak setelah trial dinyatakan layak. Dari pembayaran ini **VPS KVM 2 24 bulan (±Rp 3,65 jt) dibeli atas nama Pridata**, lalu data trial dipindahkan ke VPS produksi | **Rp 10.000.000** |
| 2 | Go-live: semua transaksi harian lewat sistem, pelatihan selesai | **Rp 10.000.000** |
| 3 | **Fase 2 inti lulus** kriteria T1, T3, T4, T5 di gudang Pridata | **Rp 10.000.000** |
| | **Harga sistem: lisensi perpetual non-eksklusif + implementasi + Fase 2 inti + VPS 24 bulan** | **Rp 30.000.000** |
| ASC | Mulai bulan ke-4 setelah go-live (garansi 3 bulan). Paket layanan Hemat (`hasil-debat-harga.md` §3.3), termasuk pemantauan VPS & backup off-site | **Rp 1.250.000/bln** |
| Perpanjangan VPS (mulai Tahun 3) | Dibayar Pridata langsung ke Hostinger | ±Rp 2,8 jt/tahun |

**Keputusan pemilik: server baru dibeli setelah deal**, dari pembayaran termin 1. Ato-team tidak menalangi server, dan Pridata tidak mengeluarkan uang sama sekali selama trial. Konsekuensinya:
- Trial memakai environment Ato-team yang sudah ada. Pastikan environment itu **terpisah dari data pelanggan lain** dan punya backup, karena data master Pridata sudah masuk sejak trial.
- Setelah deal ada **pemindahan dari environment trial ke VPS produksi Pridata** (±0,5–1 od, termasuk dalam implementasi). Jadwalkan di luar jam operasional.
- Bila trial gagal, data trial Pridata **dihapus dari environment Ato-team** dan konfirmasi penghapusan diberikan tertulis.

Termin 2 dan 3 boleh dipecah menjadi 2 × Rp 5 jt per bulan bila kas Pridata ketat. Harga total tidak berubah.

**Beban Pridata** (asumsi go-live bulan ke-2, Fase 2 lulus bulan ke-6):

| | Tahun 1 | Tahun 2 | Tahun 3 | 3 tahun |
|---|---:|---:|---:|---:|
| Sistem (termasuk VPS 24 bulan) | Rp 30.000.000 | — | — | Rp 30.000.000 |
| ASC | Rp 10.000.000 | Rp 15.000.000 | Rp 15.000.000 | Rp 40.000.000 |
| Perpanjangan VPS | — | — | ±Rp 2.800.000 | ±Rp 2.800.000 |
| **Total** | **Rp 40.000.000** | **Rp 15.000.000** | **±Rp 17.800.000** | **±Rp 72.800.000** |
| % omzet | 2,0% | 0,75% | 0,9% | |
| % laba bersih (asumsi Rp 60–100 jt) | 40–67% | 15–25% | 18–30% | |

Dibanding versi sebelumnya (server Rp 500 rb/bln terpisah): Tahun 1 turun dari Rp 45,5 jt ke **Rp 40 jt**, dan total 3 tahun dari Rp 87,5 jt ke **±Rp 72,8 jt**.

**Kas masuk Ato-team Tahun 1: ±Rp 36,35 jt** (Rp 30 jt − VPS Rp 3,65 jt + ASC Rp 10 jt).

**Risiko yang harus diakui:** Tahun 1 masih memakan 40–67% laba bersih Pridata. Karena itu trial gratis, pembayaran pertama baru terjadi saat deal (Rp 10 jt), dan sisanya baru dibayar setelah ada hasil. **Bila Pridata tetap menolak, cadangannya skema sewa-milik** (`hasil-debat-harga.md` §3.2), dengan VPS tetap milik Pridata sehingga tarif bulanannya bisa turun ±Rp 150 rb.

## 5. Skema kompetitor: penyesuaian dari jawaban #3 dan #10

Harga dasar tetap paket "Distributor" (`hasil-debat-harga.md` §3.1). Penyesuaiannya:

- **Setup Rp 10 jt sudah termasuk VPS KVM 2 selama 24 bulan** (±Rp 3,65 jt) atas nama pembeli, ditambah konfigurasi standar. Kustomisasi tidak termasuk.
- **Sewa bulanan tetap Rp 1,75 jt (gudang pertama) + Rp 750 rb per gudang tambahan**, sekarang **tanpa biaya server di sisi Ato-team**. Dibanding model debat (server ±Rp 500 rb/bln ditanggung Ato-team), kontribusi per pelanggan naik ±Rp 6 jt/tahun, sehingga setup yang di bawah biaya implementasi tertutup lebih cepat.
- **Mulai Tahun 3**, pembeli membayar perpanjangan VPS langsung (±Rp 2,8 jt/tahun). Contoh 2 gudang, 3 tahun: Rp 10 jt + 9 × Rp 2 jt + 27 × Rp 2,5 jt + ±Rp 2,8 jt ≈ **Rp 98,3 jt**, masih di bawah plafon calon pembeli Rp 110 jt.
- **Kustomisasi per pelanggan:** Rp 1.750.000/od, minimum 5 od, di-scope dan disetujui tertulis sebelum dikerjakan. Selalu dibangun sebagai konfigurasi/feature flag di kode yang sama.
- **Sewa di server milik pembeli berarti kode ada di tangan pembeli.** Kontrak wajib mengatur bahwa bila sewa berhenti, data diekspor ke pembeli lalu aplikasi dihapus dari VPS. Secara teknis, pertimbangkan *license key* yang diperiksa aplikasi. Escrow tetap hanya dibuka bila Ato-team berhenti melayani.
- **Tidak menyebut Pridata** dalam materi penjualan mana pun, konsisten dengan keputusan #3.

## 6. Yang masih perlu dijawab

1. **Backup:** add-on harian Hostinger (±Rp 105 rb/bln per pelanggan) atau dump off-site buatan sendiri (disarankan)?
2. ~~VPS Pridata: tanda jadi trial atau dibeli setelah deal?~~ **Diputuskan: dibeli setelah deal, dari termin 1** (§4).
3. **Setup kompetitor Rp 10 jt yang sudah termasuk VPS:** setuju, atau VPS ditagih terpisah (setup Rp 10 jt + VPS at cost)?

## 7. Sumber harga Hostinger

- [id.hostadvice.com: harga VPS Hostinger & perpanjangan](https://id.hostadvice.com/hosting-company/hostinger-reviews/vps-pricing/)
- [id.hostadvice.com: review Hostinger VPS](https://id.hostadvice.com/hosting-company/hostinger-reviews/hostinger-vps-hosting-review/)
- [tasikhost.com: review KVM 2](https://tasikhost.com/info/teknologi/review-jujur-vps-hostinger-kvm-2-spek-dewa-2-core-8gb-ram-di-region-kuala-lumpur-masih-kencang)
- [hostinger.com: VPS hosting](https://www.hostinger.com/vps-hosting)
