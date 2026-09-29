# Plan — Harga & Skema Penjualan ERP ke Pridata Jaya

> **Revisi 2** — diperbarui setelah peta fitur ERP Pridata masuk dan catatan bahwa sistem ini sulit menyelesaikan human error. Diagnosisnya saya verifikasi langsung ke kode (`SMD-Pridata-BE`), bukan tebakan dari nama fitur.

## Tujuan

Punya **angka harga dan skema penjualan yang siap ditawarkan ke Pridata Jaya** (distributor, Mataram), lengkap dengan posisi yang jujur dan bisa dipertahankan soal **human error di pencatatan barang masuk**.

Selesai = ada dokumen penawaran berisi: harga normal (pasar NTB), harga Pridata setelah diskon 50% mitra riset, isi paket, termin pembayaran, timbal balik dari Pridata, dan penanganan Fase 2 barang masuk.

## Temuan yang mengubah rencana ini

### 1. Sistemnya jauh lebih besar dari asumsi revisi 1

47 fitur: **8 Easy, 12 Mid, 14 High, 13 Advance**. 27 dari 47 menyentuh uang/stok atau infrastruktur inti (stock ledger, invoice ledger, RBAC, StoreScope, antrian job, realtime, analitik SQL). Ini bukan "aplikasi pencatatan". Ini dasar harga yang kuat dan harus jadi tulang punggung argumen nilai — bukan sekadar lampiran.

### 2. Modul terima barang SUDAH ada — asumsi revisi 1 salah

Revisi 1 menulis "modul barang masuk belum dibangun". Salah. `stockAdjustment` sudah punya tipe `RECEIPT` dan alurnya jalan lewat stock movement ledger. Yang tidak ada bukan modulnya, tapi **kontrolnya**.

### 3. Akar masalah human error: tidak ada dokumen pembanding

Hasil verifikasi di `prisma/schema.prisma` dan `src/routes`:

- **Tidak ada Purchase Order ke supplier.** Yang ada `Supplier` (master data saja: nama, alamat, kontak) dan "Purchase Order dari toko" — itu PO dari *pelanggan*, bukan *ke supplier*. Tidak ada model `PurchaseOrder` maupun `GoodsReceipt` di schema.
- **Tidak ada angka ekspektasi.** `StockAdjustment.quantity` adalah `Int` polos yang diketik operator. Tidak ada `expectedQuantity`, tidak ada referensi ke baris dokumen sumber. Berapa pun yang diketik dianggap sah oleh sistem.
- **Tidak ada dokumen penerimaan per pengiriman.** Satu `StockAdjustmentRecord` = satu produk. Surat jalan supplier 40 baris = 40 entri terpisah, tanpa header yang mengikatnya jadi satu penerimaan yang totalnya bisa dicek.
- **Tidak ada approval selisih.** Tidak ada status, tidak ada field verifikasi. Entri langsung final.
- **Tidak ada scan.** Tidak ada barcode/QR di seluruh backend. Semua input diketik manual.
- **Tidak ada satuan (UOM).** `quantity` hanya `Int`. Karton vs pcs dikonversi di kepala operator — sumber salah hitung klasik di distribusi.
- **Jejak pelaku lemah.** `StockAdjustmentRecord` tidak menyimpan siapa yang membuat; hanya `reason` bebas teks. Penelusuran bergantung `AuditLog` umum.

Kesimpulan: **menambah validasi di layar terima barang tidak akan menutup masalah ini.** Tidak ada yang bisa divalidasi karena tidak ada angka ekspektasi. Ini masalah *dokumen yang hilang*, bukan masalah *form*.

### 4. Perbaikannya menyentuh zona paling berisiko

Stock movement ledger adalah satu-satunya penulis kuantitas stok (level Advance). Modul penerimaan baru wajib lewat ledger itu, bukan di sampingnya. Jadi effort-nya nyata dan berbayar — bukan tambal cepat yang bisa diberikan gratis sebagai bonus penutup rasa bersalah.

### 5. Posisi jualan: jujur, bukan diskon tambahan

Tidak ada ERP yang menghilangkan human error. Yang bisa dilakukan software hanya tiga hal:

| Kemampuan | Status sistem sekarang |
|---|---|
| (a) Kurangi peluang salah input — scan, bukan ketik | **belum ada** |
| (b) Tangkap salah lebih awal — cocokkan dokumen, blind count | **belum ada** |
| (c) Buat salah terlacak & murah dikoreksi — ledger, audit log, stock opname | **sudah kuat** |

Jadi klaim ke Pridata dibalik. Dari "kami menyelesaikan human error" (tidak bisa dibuktikan, dan mereka sudah tahu itu tidak benar) menjadi:

> Sistem ini tidak menghilangkan salah catat. Yang berubah: selisih ketemu dalam hitungan hari dan bisa ditelusuri ke transaksinya, bukan baru ketahuan saat opname tanpa ada yang tahu asalnya. Untuk mencegahnya di sumber — PO supplier, scan, blind count — itu Fase 2, dan kami scope terpisah dengan harga terpisah.

**Jangan potong harga lagi untuk menutupi celah ini.** Celahnya dijual sebagai pekerjaan berikutnya, dan Pridata jadi mitra co-development-nya. Itu sekaligus timbal balik yang masuk akal untuk diskon 50%.

## Cara kerja

1. **Baseline biaya & harga normal** (Rani). Pakai peta fitur sebagai dasar hitungan: 47 fitur dibobot per level kesulitan → estimasi orang-hari → biaya. Tambah infra, riset, dan support tahunan. Hasilkan harga list "normal" untuk distributor lain di NTB. Wajib duluan — diskon 50% hanya masuk akal kalau harga normalnya punya dasar.
2. **Diagnosis human error & spesifikasi Fase 2** (Bayu). Verifikasi ulang temuan di atas langsung ke repo, petakan alur terima barang Pridata yang sebenarnya, tegaskan apa yang bisa dan tidak bisa diselesaikan software, lalu spesifikasi Fase 2 dengan estimasi effort dan target terukur.
3. **Skema penjualan & timbal balik** (Rani). Bandingkan 3 model: (a) lisensi sekali bayar + maintenance tahunan, (b) langganan, (c) kemitraan jangka panjang (harga masuk rendah + komitmen multi-tahun). Rekomendasikan satu, dengan termin bertahap dan posisi Fase 2 di dalamnya.
4. **Dokumen penawaran final** (Ace).

## Isi Fase 2 (kandidat — Bayu yang finalkan)

- `PurchaseOrder` ke supplier + `GoodsReceipt` header per surat jalan — sumber angka ekspektasi.
- Pencocokan 3 arah: PO vs surat jalan supplier vs hitungan fisik.
- Blind count — qty ekspektasi disembunyikan supaya operator tidak sekadar menyalin dokumen.
- Approval selisih wajib di atas ambang tertentu.
- Scan barcode/QR + input mobile untuk gudang.
- UOM & konversi karton ↔ pcs.
- Batch/expiry bila relevan untuk produk Pridata.
- `createdByUserId` pada penerimaan, supaya akuntabel.

Target yang dijanjikan harus terukur — misalnya waktu penemuan selisih turun dari bulanan (saat opname) ke harian, atau jumlah baris penerimaan yang diketik manual turun sekian persen. Angka finalnya Bayu yang tetapkan setelah melihat data Pridata.

## Timbal balik 2 arah (ditukar dengan diskon 50%)

- Izin pakai sebagai studi kasus & referensi penjualan di NTB.
- Akses data operasional untuk riset, dengan batasan kerahasiaan tertulis.
- Testimoni, dan kesediaan jadi lokasi demo untuk calon pembeli lain.
- Komitmen kontrak minimum / maintenance multi-tahun.
- Peran co-development Fase 2: Pridata menyediakan akses gudang dan waktu operator untuk uji coba.

## Tim (2 orang)

- **Rani — Commercial Analyst** — baseline biaya, harga normal pasar NTB, struktur diskon mitra riset, model & termin penjualan, syarat timbal balik.
- **Bayu — ERP Product Analyst** — diagnosis human error di alur barang masuk, spesifikasi & estimasi Fase 2, target terukur.

Penulisan penawaran final saya (Ace) yang pegang, jadi tim tetap dua orang.

## Tugas lanjutan

| # | Tugas | Pemilik | Status awal | Blocker | Kenapa harus tugas terpisah |
|---|---|---|---|---|---|
| 1 | Baseline biaya & harga normal ERP (pasar NTB) | Rani | todo | — | Spesialis komersial; deliverable mandiri, bisa jalan paralel dengan #2 sejak awal |
| 2 | Diagnosis human error & spesifikasi Fase 2 barang masuk | Bayu | todo | — | Spesialis produk/teknis; deliverable mandiri, paralel dengan #1 |
| 3 | Skema penjualan & syarat kemitraan untuk Pridata | Rani | blocked | #1, #2 | Butuh angka dari keduanya sebelum bisa disusun |
| 4 | Dokumen penawaran final Pridata Jaya | Ace | blocked | #3 | Penulisan akhir dan hubungan ke user ada di saya |

## Risiko

- **Pridata menolak bayar untuk sistem yang tidak menutup masalah utama mereka.** Mitigasi: posisi (c) di atas, plus Fase 2 sudah di-scope di dalam penawaran — bukan dijanjikan belakangan.
- **Diskon 50% jadi acuan harga di pasar NTB.** Mitigasi: diskon diikat eksplisit ke status mitra riset dan timbal balik tertulis, dengan harga list tetap terpampang di dokumen.
- **Estimasi biaya tanpa catatan jam kerja historis.** Mitigasi: Rani pakai bobot per level fitur dan minta konfirmasi rentang waktu pengerjaan dari kalian.

## Asumsi yang perlu dikoreksi kalau salah

- Pridata Jaya (CV/UD) adalah perusahaan calon pembeli, bukan badan usaha kalian.
- Fase 2 belum dikerjakan; di sini yang dinilai baru spesifikasi dan harganya.
- Repo rujukan ada di `/home/acedixy/Documents/Code/Pridata System` (`SMD-Pridata-BE`, `FE_Pridata_Jaya`).
