# Skenario: Sistem Kita Menggantikan Ketoko di Pridata

**Tanggal:** 12 Oktober 2026 · **Status:** Analisis skenario, menunggu keputusan pemilik · **Dokumen internal**
**Melanjutkan:** `analisis/hasil-debat-ketoko.md` (skema Mitra Lab, Ketoko tetap jalan).

---

## 0. Jawaban singkat

**Bisa, tapi ini keputusan produk senilai ±Rp 55–82 jt dalam 3 tahun, bukan keputusan harga.** Mengganti Ketoko berarti sistem kita menjadi *system of record* Pridata: semua penjualan, pembelian, dan stok tercatat di sistem kita. Konsekuensinya ada tiga:

1. **Bangun ±66–115 orang-hari** (±Rp 63–109 jt), bukan 27–48 od Fase 2 inti. Tambahannya ±39–67 od (±Rp 37–64 jt).
2. **Biaya layanan naik.** Sistem utama yang mati berarti Pridata tidak bisa berjualan, jadi pola layanan Mandiri (4 od/th) tidak cukup. Biaya marjinal Pridata naik ke ±Rp 1,6 jt/bln.
3. **Pridata tetap tidak menguntungkan bila omzetnya Rp 2 M/th.** Nilai penggantian bagi Pridata ±Rp 300–425 rb/bln, dan Pemilik Pridata menyebut maksimal Rp 500 rb.

**Penggantian ini hanya masuk akal sebagai strategi produk**, yaitu "satu sistem untuk distributor yang punya tim sales". Paket itu kita jual ke distributor lain di Rp 2,5 jt/bln, dan Pridata menjadi lokasi pertama. **Uji kelayakannya: ≥ 3 pelanggan paket Distributor dalam ±2 tahun** (±9 tahun-pelanggan × Rp 7,6 jt ≈ menutup Rp 55–82 jt). Kalau tidak ada 3 pelanggan, kita membangun tiruan Ketoko untuk satu pelanggan yang membayar Rp 500 rb.

**Rekomendasi:** jadikan penggantian Ketoko sebagai **target**, dijalankan **bertahap dengan gerbang** (§4). Tahap pertama sama dengan Mitra Lab, hanya saja PO, penerimaan, satuan, dan barcode dirancang untuk akhirnya menggantikan Ketoko.

---

## 1. Yang harus dibangun agar Ketoko bisa dimatikan

| Komponen | Orang-hari | Asal angka | Wajib untuk mengganti? |
|---|---:|---|---|
| Fase 2 inti: audit (F2-6), header penerimaan (F2-1), PO (F2-2), cocok 3 arah (F2-3), hitung buta (F2-4), approval selisih (F2-5) | 27–48 | ATO-3 | Ya |
| Satuan & konversi dus↔pak↔pcs (F2-8) | 12–20 | ATO-3 | **Ya.** Ketoko punya s.d. 4 satuan per barang; tanpa ini admin mundur |
| Barcode + scan di HP lewat browser/PWA (F2-9) | 8–14 | ATO-3 | **Ya.** Ketoko punya barcode per satuan dan aplikasi HP |
| Hutang supplier, pembayaran hutang, retur pembelian | 6–10 | Taksiran moderator | Ya |
| Laporan laba-rugi sederhana + ekspor jurnal/Excel untuk akuntan | 5–10 | Taksiran moderator | Ya, sebagai pengganti neraca Ketoko. **Bukan** akuntansi penuh |
| Migrasi dari Ketoko (master, saldo stok, piutang, hutang) | 3–5 | Taksiran moderator | Ya |
| Pelatihan, cut-over, pendampingan 2 minggu | 5–8 | Taksiran moderator | Ya |
| **Total** | **66–115** | | **±Rp 63–109 jt** pada Rp 950 rb/od |

**Tidak termasuk** (harus ditanyakan ke Pridata, apakah dipakai di Ketoko):

- Kasir/POS untuk penjualan langsung di gudang: ±8–15 od bila dipakai.
- Integrasi Tokopedia/Shopee: ±15–25 od. **Saran: jangan.** Ini wilayah Ketoko.
- Akuntansi penuh/e-faktur: tetap di Accurate/akuntan. **Kita mengganti Ketoko, bukan Accurate.**
- Aplikasi native Android/iOS: PWA dulu.

**Satu syarat teknis:** stok tidak boleh hidup di dua sistem. Cut-over harus memindahkan penjualan, pembelian, dan stok **bersamaan**. Tidak ada tahap "pembelian di kita, penjualan di Ketoko".

---

## 2. Angka: Mitra Lab vs Ganti Ketoko (Pridata, omzet Rp 2 M/th)

| | Mitra Lab (Ketoko tetap) | **Ganti Ketoko** |
|---|---:|---:|
| Pengembangan | 27–33 od (±Rp 26–31 jt) | 66–115 od (±Rp 63–109 jt) |
| Status sistem kita di Pridata | Pelengkap, 1 gudang | Sistem utama |
| Pola layanan | Mandiri, ±Rp 900 rb/bln | Hemat (respons 1 hari kerja, bug kritis ≤ 4 jam), ±Rp 1,6 jt/bln |
| Tarif Pridata setelah selesai | Rp 300 rb → Rp 500 rb | Rp 500 rb (maksimum yang disebut Pemilik) |
| Subsidi Pridata, 3 tahun (di luar pengembangan) | ±Rp 17,7 jt | **±Rp 36 jt** |
| Investasi total di atas Mitra Lab, 3 tahun | — | **±Rp 55–82 jt** (bangun tambahan Rp 37–64 jt + subsidi tambahan ±Rp 18 jt) |
| Arus kas 24 bulan (CFO putaran 2: −Rp 66 s/d −111 jt) | Kira-kira sama | **±−Rp 103 s/d −175 jt** |

Hitungan subsidi "Ganti Ketoko": 12 bulan pra-cut-over (biaya ±Rp 900 rb/bln, pembayaran Rp 0 × 9 + Rp 300 rb × 3) ≈ −Rp 9,9 jt. Ditambah 24 bulan sesudahnya (biaya ±Rp 1,6 jt, pembayaran Rp 500 rb) ≈ −Rp 26,4 jt. Total ≈ −Rp 36 jt.

**Bila omzet Pridata Rp 2 M per bulan**, gambarnya berubah: nilai tambah ±Rp 1,4–2,25 jt/bln, dan Pridata bisa ditagih Rp 1,5–2 jt/bln setelah cut-over (skema putaran 2). Subsidi praktis hilang, dan yang tersisa hanya investasi bangun.

---

## 3. Posisi peserta (debat singkat)

| Peserta | Posisi atas "ganti Ketoko" |
|---|---|
| **Pemilik Pridata** | Mau, asal (1) tidak ada fitur Ketoko yang sedang dipakai hilang, (2) Ketoko tetap bisa dibuka sebagai cadangan 3 bulan, (3) total ≤ Rp 500 rb/bln termasuk semuanya, (4) Pridata tidak membayar migrasi, (5) ada klausul gangguan: sistem mati > 4 jam di hari kerja → tagihan bulan itu gratis. |
| **Admin Gudang** | Lebih suka satu sistem daripada dua. Syarat: barcode, satuan, dan HP **harus ada sebelum** cut-over. Cut-over **tidak** di akhir bulan atau saat opname. Minta 2 minggu didampingi di lokasi. |
| **Rani** | Mendukung sebagai strategi produk. "Satu sistem, tanpa input ganda" membuat paket Distributor Rp 2,5 jt lebih mudah dibela daripada "pendamping Ketoko". Tapi tarif Pridata harus naik seiring nilainya, dan omzet harus dikonfirmasi lebih dulu. |
| **Penantang Pasar** | Hati-hati. Mengganti Ketoko berarti bersaing di wilayahnya: harga Rp 50 rb, aplikasi HP, marketplace. Boleh, **hanya untuk distributor dengan tim sales**, dan jangan pernah membangun akuntansi, kasir, atau marketplace. Akuntansi lewat ekspor ke Accurate/akuntan. |
| **Calon Pembeli Kompetitor** | Lebih tertarik: ia bisa melepas Ketoko dan cukup memakai sistem kita + Accurate (karena PKP). Tapi begitu sistem kita jadi sistem utama, ia minta **uptime 99% dengan sanksi**, cadangan offline, dan migrasi dari Ketoko termasuk setup Rp 10 jt. |
| **CFO** | Investasi naik ±Rp 55–82 jt dan arus kas 24 bulan bisa sampai −Rp 175 jt. Boleh, asal ada gerbang: tahap bangun tambahan (§4 Tahap B) baru dimulai bila Fase 2 inti lulus **dan** ada bukti pasar (≥ 3 prospek terkualifikasi di sensus, atau 1 kontrak Distributor ditandatangani). Plafon subsidi Pridata naik dari Rp 20 jt ke **Rp 40 jt / 36 bulan**. Hitung beban on-call: sistem utama berarti seseorang harus siaga di jam kerja. |

**Titik sepakat:** tujuannya sah, tapi hanya sebagai paket "satu sistem untuk distributor dengan tim sales". Ketoko tidak boleh diganti di Pridata sebelum barcode, satuan, PO, dan penerimaan siap. Stok pindah sekaligus.
**Belum sepakat:** apakah uptime dengan sanksi sanggup dijanjikan tim 2 orang. CFO dan Penantang: hanya untuk jam kerja, sanksinya berupa potongan tagihan, bukan denda.

---

## 4. Jalur bertahap dengan gerbang (rekomendasi)

1. **Tahap A, bulan 0–9: Mitra Lab, dirancang untuk mengganti.** Tarif Pridata Rp 0. Bangun Fase 2 inti + barcode (F2-9 minimal) dan **rancang skema data siap-satuan** supaya F2-8 tidak perlu migrasi ulang. Pridata memakai modul penerimaan di samping Ketoko (sama seperti Mitra Lab).
2. **Gerbang 1, ±bulan 9.** Lanjut ke Tahap B hanya bila **semua** terpenuhi:
   - Fase 2 lulus T1/T3/T4/T5 di gudang Pridata.
   - Omzet Pridata sudah dikonfirmasi.
   - Ada ≥ 3 prospek terkualifikasi di sensus **atau** 1 kontrak Distributor ditandatangani.

   Tidak lulus gerbang → tetap Mitra Lab (Rp 300 rb/bln), dan Ketoko tetap jalan.
3. **Tahap B, bulan 9–14: lengkapi.** Satuan & konversi (F2-8), hutang supplier/retur, laporan + ekspor untuk akuntan, alat migrasi Ketoko. Alat migrasi ini sekaligus menjadi bagian setup paket Distributor.
4. **Gerbang 2: kesiapan cut-over.** Uji migrasi pada salinan data Ketoko Pridata. Selisih saldo stok, piutang, dan hutang = 0. Admin lulus pelatihan. Tanggal cut-over di awal bulan, jauh dari opname.
5. **Cut-over.** Penjualan, pembelian, dan stok pindah bersamaan. Ketoko **tidak dipakai input lagi**, tapi langganannya diteruskan 3 bulan sebagai cadangan baca (±Rp 150 rb, ditanggung Ato-team). Ato-team mendampingi 2 minggu.
6. **Setelah cut-over.** Pridata Rp 500 rb/bln (omzet per tahun) atau Rp 1,5–2 jt/bln (omzet per bulan), terkunci 24 bulan, dengan layanan Hemat dan klausul gangguan. Ketoko dihentikan di bulan ke-3 setelah cut-over.

---

## 5. Keputusan yang dibutuhkan

| Isu | Rekomendasi moderator |
|---|---|
| Ganti Ketoko sebagai target? | **Ya, sebagai target bergerbang**, bukan janji ke Pridata hari ini. Ke Pridata cukup dikatakan: "tujuan kami menggantikan Ketoko; kami mulai dari penerimaan barang" |
| Plafon subsidi Pridata | Naik ke Rp 40 jt / 36 bulan, berlaku hanya bila Gerbang 1 lulus |
| Uptime/sanksi | Jam kerja saja, sanksi berupa potongan tagihan bulan itu, tanpa denda |
| Kasir/marketplace | Di luar lingkup. Bila Pridata memakainya di Ketoko, Pridata tetap memakai Ketoko untuk itu (stok kasir dipisah per gudang), atau penggantian ditunda |

## 6. Yang harus ditanyakan ke Pridata minggu ini

- [ ] Omzet Rp 2 M: per tahun atau per bulan?
- [ ] Modul Ketoko apa saja yang benar-benar dipakai: kasir, PO/pembelian, hutang, neraca, marketplace, aplikasi HP?
- [ ] Siapa yang membuat laporan keuangan/pajak: dari Ketoko, akuntan luar, atau Accurate?
- [ ] Berapa banyak data yang harus dipindah: jumlah barang, toko, supplier, saldo piutang dan hutang?

*Semua angka belum termasuk PPN. Estimasi od di luar ATO-3 adalah taksiran moderator dan harus divalidasi Bayu.*
