# Putaran 3: Fakta baru, Pridata sudah memakai Ketoko.co.id (Rp 50 rb/bln)

**Fakta yang dibawa moderator ke meja** (dari halaman publik ketoko.co.id via hasil pencarian, Oktober 2026; situsnya tidak bisa dibuka langsung dari lingkungan kerja ini, jadi belum diverifikasi):

- Paket **Unlimited Omset Rp 50.000/bln** (min. 6 bulan): 8.000 barang, **15 user, 5 gudang**, support standar. Paket Silver Rp 110.000/bln: 20.000 barang, 50 user, 15 gudang.
- Fitur yang **sudah dimiliki Ketoko** dan **belum dimiliki sistem kita**: pesanan pembelian (PO) ke supplier, pembelian/penerimaan yang menambah stok, retur pembelian, hutang supplier, **barcode per satuan, konversi s.d. 4 satuan**, level harga, laporan neraca, integrasi Tokopedia/Shopee, aplikasi Android/iOS/desktop, import Excel (barang, supplier, pelanggan).
- Fitur Ketoko yang **tumpang tindih** dengan sistem kita: penjualan, piutang, data sales + komisi, multi gudang + mutasi, kartu stok, penyesuaian stok/opname.
- Yang **hanya ada di sistem kita**: penugasan sales↔toko, grade toko, KPI sales, alur DO pick→pack→ship, piutang aging per toko/sales, verifikasi pembayaran, audit log, peran dashboard berjenjang. **Fase 2** (blind count, pencocokan 3 arah, approval selisih) belum dibangun, dan tidak ada indikasi Ketoko memilikinya.
- Tidak ditemukan panduan import transaksi pembelian/PO ke Ketoko, juga tidak ada API publik. Jembatan otomatis ke Ketoko belum terbukti mungkin.

Pembanding: skema Pridata hasil putaran 2 (Rp 0 di muka, Rp 1,5 jt → 2 jt/bln) = Tahun 1 ±Rp 19,5 jt, atau **±32× biaya Ketoko per tahun** (Rp 600 rb). Total 3 tahun Rp 67,5 jt vs Ketoko Rp 1,8 jt.

Peserta: lima peserta putaran 1–2, ditambah **Admin Gudang Pridata** (pengguna harian Ketoko), karena sekarang pertanyaannya juga soal pemakaian sehari-hari, bukan hanya harga.

---

## 3A. Posisi awal

# POSISI PEMILIK PRIDATA (Putaran 3) — ringkas
- "Saya bayar Rp 50 rb dan sistem saya jalan. Penjualan, pembelian, hutang-piutang, stok, laporan, semua ada. Rp 1,5–2 jt/bln itu 30–40 kali lipat untuk sistem yang malah **belum punya PO dan pembelian**."
- Alternatif saya yang sebenarnya **bukan pindah ke Accurate** seperti di putaran 1, tapi **tidak melakukan apa-apa**: tetap di Ketoko, paling jauh naik ke Silver Rp 110 rb.
- Saya hanya mau membayar untuk satu hal yang Ketoko tidak bisa: **barang masuk yang salah catat berhenti terjadi.** Fitur sales↔toko, grade, DO itu bagus, tapi tim saya sudah jalan tanpa itu.
- **Menolak menjalankan dua sistem dengan input ganda.** Kalau input ganda, admin saya justru menambah kesalahan.
- Tawaran: Rp 0 selama Fase 2 dibangun dan diuji di gudang saya (tetap memberi K2 data agregat dan K5 20 sesi). Setelah lulus T1/T3/T4/T5: **maks Rp 250 rb/bln** bila hanya modul penerimaan berdampingan dengan Ketoko, **maks Rp 500 rb/bln** bila sistem kalian bisa menggantikan Ketoko sepenuhnya.

# POSISI RANI (Putaran 3) — ringkas
- Rp 50 rb adalah harga produk massal tanpa implementasi, tanpa kunjungan, dan tanpa tim yang mengenal gudang Pridata. Itu bukan ukuran nilai, tapi **ukuran alternatif Pridata**, dan alternatif itu menentukan batas atas yang mau dibayar. Pada titik ini saya akui Pemilik benar.
- Hitung ulang model nilai ATO-2 §3.4 (omzet Rp 2 M/th) dengan **Ketoko sebagai baseline**, bukan pencatatan manual. Hampir semua penghematan waktu admin dan akuntan sudah didapat Pridata dari Ketoko. Sisa nilai tambah sistem kita ±**Rp 2,9–4,5 jt/th** (±Rp 240–375 rb/bln, keyakinan rendah; rincian di rangkuman §2). Harga Rp 1,5–2 jt/bln tidak bisa dibela di omzet itu.
- **Tapi bila omzet Rp 2 M itu per bulan, gambarnya lain**: nilai tambah ±Rp 17–27 jt/th (±Rp 1,4–2,25 jt/bln), dan skema putaran 2 tetap masuk akal. **Satuan omzet sekarang menentukan, bukan lagi catatan kaki.**
- Usul (bila omzet per tahun): **berhenti menganggap Pridata sumber pendapatan.** Pridata adalah lab riset. Tetap ada bayaran kecil sebagai tanda komitmen, ±Rp 250–300 rb/bln setelah Fase 2 lulus, supaya hubungan ini tetap jual-beli dan bukan hibah.
- Syarat keras: tarif Pridata **tidak dipublikasikan dan diberi label "tarif lab"**. Kalau tarif ini bocor menjadi jangkar pasar, paket Distributor Rp 2,5 jt tidak akan pernah laku. Tolak paket murah baru untuk umum: biaya layanan kita tidak akan pernah turun ke level Ketoko.

# POSISI PENANTANG PASAR (Putaran 3) — ringkas
- Inilah yang saya peringatkan di putaran 1 (iPos Rp 3,35 jt sekali bayar). Ketoko membuktikan **jangkar distributor kecil NTB untuk "toko + stok + hutang-piutang" adalah Rp 50–110 rb/bln**, bukan Rp 1,5–3 jt.
- Akibatnya bukan hanya untuk Pridata. **Kebanyakan calon pembeli di sensus pasar kemungkinan juga sudah memakai Ketoko/iPos/Accurate.** Paket Distributor Rp 2,5 jt hanya laku untuk distributor dengan tim sales lapangan dan banyak toko, yaitu kebutuhan yang memang tidak dilayani Ketoko.
- Posisikan sistem kita sebagai **pendamping Ketoko/Accurate, bukan pengganti**: kita tidak membangun akuntansi, kasir, atau marketplace. Kita jual DMS (sales↔toko, DO, aging) plus penerimaan terkontrol.
- Usul paket umum baru **"Mandiri" Rp 750 rb/bln**: 1 gudang, user tak terbatas, server bersama (DB terpisah per pelanggan di satu VPS), support tiket 2 hari kerja, setup Rp 3 jt (impor template dari Excel Ketoko).
- Pridata: Rp 0 sampai Fase 2 lulus, lalu **Rp 300 rb/bln**.
- Usulan baru: **modul Penerimaan berdiri sendiri untuk pengguna Ketoko/Accurate** (Rp 150–300 rb/bln) bisa menjadi produk yang pasarnya jauh lebih besar daripada DMS. Akui: ini hipotesis, butuh 10–15 pelanggan swalayan, dan tim 2 orang sudah di batas.

# POSISI CALON PEMBELI KOMPETITOR (Putaran 3) — ringkas
- "Saya juga pakai Ketoko di kasir dan stok." Yang membuat saya mau membayar Rp 2–2,5 jt: **12 user, 6 sales lapangan, ±300 toko**. Ketoko tidak bisa mengatur siapa mengunjungi toko mana, tidak ada DO bertahap, dan piutang per sales berantakan. Nilai saya masih sama.
- **Tapi kalau Pridata membayar Rp 300 rb dan saya Rp 2,5 jt untuk perangkat lunak yang sama, itu melanggar semangat klausul "pelanggan setara".** Saya baru terima selisihnya bila: (1) tarif Pridata adalah kompensasi kerja riset yang tertulis (data + 20 sesi + gudang jadi lab), (2) tarif itu berbatas waktu, (3) Pridata tidak mendapat SLA atau rilis lebih dulu > 30 hari.
- Kalau ada paket "Mandiri" untuk umum, **saya pun berhak memilihnya.** Itu wajar, asal batasannya nyata (1 gudang, tanpa SLA) dan bukan Distributor yang diberi label lain.
- Minta **alat impor dari Excel Ketoko** (barang, satuan, pelanggan, supplier) sebagai bagian setup. Itu yang paling mengurangi biaya pindah saya.

# POSISI CFO (Putaran 3) — ringkas
- Lantai biaya marjinal per pelanggan (rate Rp 950 rb/od):
  - **Layanan Hemat, server sendiri:** server ≤Rp 600 rb + dukungan 16 od/th (Rp 1,27 jt/bln) = **±Rp 1,87 jt/bln**. Pada tarif impas Rp 1,36 jt/od: ±Rp 2,4 jt.
  - **Layanan Mandiri, server bersama:** server Rp 150–300 rb + dukungan 4 od/th (Rp 317 rb/bln) = **±Rp 470–620 rb/bln**. Pada tarif impas: ±Rp 600–750 rb.
  - Level Ketoko (Rp 50–110 rb) **mustahil bagi kita di skala berapa pun yang terjangkau tim 2 orang.** Jangan dikejar.
- **Nilai harapan, bukan nilai nominal.** Skema putaran 2 memberi kontribusi 3 tahun ±+Rp 10 jt (pendapatan Rp 67,5 jt − biaya ±Rp 57,6 jt), *bila diterima*. Dengan Ketoko sebagai alternatif, peluang diterima di omzet Rp 2 M/th saya taksir 10–20%. Nilai harapannya ≈ +Rp 1–2 jt, dan bila ditolak, lab riset ikut hilang.
- Skema lab (Rp 0 → Rp 300 rb → Rp 500 rb): pendapatan 3 th ±Rp 10,5 jt, biaya ±Rp 28 jt, **neto ±−Rp 17,7 jt dalam 3 tahun** (±19 od). Itu biaya riset dan harus disetujui sebagai biaya riset, dengan plafon.
- Syarat: plafon subsidi Pridata (biaya marjinal dikurangi pembayaran Pridata) **Rp 20 jt atau 24 bulan**, mana yang lebih dulu, di luar 27 od Fase 2. **Gerbang bulan ke-12:** bila belum ada 1 kontrak eksternal berbayar, pengembangan khusus Pridata berhenti, dan Pridata masuk mode pemeliharaan atau kembali ke Ketoko dengan ekspor data penuh.
- Paket Mandiri Rp 750 rb: **tolak dulu.** Margin di atas lantai hanya ±Rp 130–280 rb/bln, dan dukungan 4 od/th belum pernah terbukti. Pakai data dukungan Pridata (yang memang dilayani dengan pola Mandiri) sebagai bukti, lalu putuskan di tinjauan bulan ke-6.

# POSISI ADMIN GUDANG PRIDATA (Putaran 3, peserta baru) — ringkas
- Ketoko sudah saya pakai bertahun-tahun: cepat, ada di HP, barcode jalan, satuan dus↔pak↔pcs otomatis. **Sistem kalian sekarang malah lebih mundur di dua hal itu** (belum ada barcode, satuan hanya teks; ATO-3 §1.6–1.7).
- Salah catat barang masuk terjadi karena: surat jalan tidak cocok dengan pesanan, saya menyalin angka surat jalan alih-alih menghitung, salah pilih satuan, dan tidak ada yang memeriksa. Ketoko memang punya PO, tapi tidak memaksa saya menghitung atau minta persetujuan bila selisih.
- **Input ganda = saya akan berhenti memakai salah satunya dalam 3 bulan,** dan itu pasti sistem kalian.
- Saya mau memakai alat yang **hanya untuk penerimaan**: scan di HP, hitung buta, selisih minta persetujuan supervisor lewat HP. Hasilnya cukup saya salin ke Ketoko satu kali dari dokumen yang sudah disetujui, asal ≤15 menit/hari.
- **Blind count tanpa barcode akan lebih lambat daripada Ketoko sekarang.** ATO-3 sendiri menyebut barcode (F2-9) sebagai fitur yang "membiayai" friksi blind count. Kalau F2-9 dipotong dari paket inti, saya akan mengakalinya dengan menyalin angka surat jalan lagi.

---

## 3B. Saling bantah, lalu posisi akhir

**Rani → Penantang:** "Pendamping Ketoko" menyerahkan kasir, pembelian, dan akuntansi ke pihak lain untuk selamanya. Itu sah, tapi berarti kita tidak akan pernah menjual "sistem lengkap". **Penantang:** memang tidak perlu. Dua orang tidak akan menang melawan Ketoko di akuntansi atau kasir. Menang di yang sempit lebih baik. *Rani menerima untuk segmen kecil, menolak untuk paket Distributor.*

**CFO → Penantang (paket Mandiri):** server bersama bisa dijalankan **tanpa ubah kode**: beberapa instance, satu VPS, database terpisah per pelanggan. Firewall data yang diminta Kompetitor tetap terpenuhi. Yang belum terbukti adalah dukungan 4 od/th. **Penantang:** setuju menunda publikasi sampai bulan ke-6, asal Pridata dilayani dengan pola Mandiri sejak hari pertama supaya datanya ada.

**Kompetitor → Pemilik Pridata:** "Rp 300 rb tanpa batas waktu tidak bisa saya terima." **Pemilik:** "Saya terima batas 24 bulan, asal setelah itu tarifnya tidak melompat ke Rp 2 jt." Disepakati: setelah bulan ke-24, Pridata membayar **Rp 500 rb/bln atau tarif Mandiri publik dikurangi 50%, mana yang lebih rendah**, dan tidak pernah di bawah lantai marjinal Mandiri. *CFO menerima karena Rp 500 rb ≈ lantai marjinal Mandiri pada rate Rp 950 rb/od.*

**Admin Gudang → semua (cakupan lab):** sepakat bahwa Pridata **tidak** mengganti Ketoko selama lab. Lingkup lab: modul penerimaan di 1 gudang. Master barang/supplier diambil dari ekspor Excel Ketoko. Pembelian yang sudah disetujui disalin ke Ketoko (diukur; bila > 15 menit/hari, Ato-team membuat lembar ekspor yang mengikuti format Ketoko, bila Ketoko ternyata menerima impor pembelian).

**Admin Gudang ↔ CFO (barcode):** CFO mempertahankan plafon 27 od inti. Admin menolak blind count tanpa scan. **Belum sepakat.** Jalan tengah dari Penantang: F2-9 versi minimal, yaitu scan kamera HP lewat browser terhadap barcode yang sudah ada di master Ketoko, tanpa aplikasi native (±4–6 od dari rentang 8–14 od). Plafon naik ke ±33 od. CFO hanya setuju bila F2-5 (approval selisih) memakai alur paling sederhana. → **Keputusan pemilik.**

**Rani ↔ Penantang (modul Penerimaan berdiri sendiri):** Rani: itu produk baru, bukan skema harga. Penantang: justru lab Pridata adalah ujinya, karena Pridata akan memakai persis bentuk itu (penerimaan saja, di samping Ketoko). *Disepakati sebagai hipotesis yang diuji lewat sensus pasar, bukan keputusan sekarang.*

### Posisi akhir

| Peserta | Pridata | Kompetitor / pasar |
|---|---|---|
| Pemilik Pridata | Rp 0 sampai lulus → **Rp 300 rb** s.d. bln 24 → Rp 500 rb. Ketoko tetap jalan. Tanpa input ganda penuh | — |
| Rani | Setuju **bila omzet per tahun**. Bila per bulan, kembali ke skema putaran 2 | Distributor Rp 2,5 jt tetap. Mandiri: ragu (kanibalisasi) |
| Penantang | Setuju | Distributor tetap untuk segmen DMS + **Mandiri Rp 750 rb** setelah bln 6 |
| Kompetitor | Terima, karena tarif lab berbatas waktu dan tertulis sebagai kompensasi riset | Tetap Rp 2–2,5 jt; minta impor Excel Ketoko di setup |
| CFO | Terima sebagai biaya riset, **plafon Rp 20 jt/24 bln + gerbang bln 12** | Mandiri ditunda sampai data dukungan bln 6 |
| Admin Gudang | Mau memakai bila penerimaan saja + ada scan HP | — |
