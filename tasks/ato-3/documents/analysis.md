# Diagnosis Human Error Barang Masuk — SMD/ERP untuk CV Pridata Jaya

Analisis berbasis kode, read-only, atas `SMD-Pridata-BE` dan `FE_Pridata_Jaya` di `/home/acedixy/Documents/Code/Pridata System`.
Semua klaim di bawah punya kutipan `path:line`. Klaim ketiadaan sudah diverifikasi dua kali (grep skema + grep seluruh `src` + grep folder `prisma/migrations`).

---

## 1. Verifikasi 8 hipotesis Ace

### 1.1 "Tidak ada Purchase Order ke supplier" — **BENAR, dan lebih kuat dari dugaan**

- Tidak ada model `PurchaseOrder` maupun `GoodsReceipt` di seluruh skema. Daftar lengkap 60+ model/enum ada di `SMD-Pridata-BE/prisma/schema.prisma:14-1523`; tidak satupun bernama demikian.
- Pencarian ulang case-insensitive atas `purchaseorder|purchase_order|goodsreceipt|goods_receipt|receivingnote|purchaseRequisition` di `prisma/schema.prisma` → **0 hasil**.
- Pencarian yang sama atas seluruh `SMD-Pridata-BE/src` (di luar `__tests__` dan `src/generated`) → **0 hasil**.
- Pencarian yang sama atas seluruh `prisma/migrations` → **0 hasil**. Jadi modul ini tidak pernah ada dan tidak pernah dihapus.
- `Supplier` (`prisma/schema.prisma:252-275`) memang master data murni. Satu-satunya relasi transaksionalnya adalah `stockAdjustments StockAdjustmentRecord[]` (`:266`) — tidak ada relasi ke dokumen pembelian apa pun.
- "PO dari toko" yang dimaksud adalah model `Order` (`prisma/schema.prisma:604-637`): punya `storeId` (`:610`), `sourceWarehouseId` (`:611`), dan bermuara ke `Invoice` (`:626`). Ini **sales order dari pelanggan**, arah keluar. Tidak ada hubungannya dengan pembelian ke supplier.

### 1.2 "Penerimaan berjalan lewat `StockAdjustmentRecord` type=RECEIPT" — **BENAR**

- `enum StockAdjustmentType { RECEIPT, DAMAGE, CORRECTION, OUTBOUND }` di `prisma/schema.prisma:964-969`.
- `StockAdjustmentRecord` di `prisma/schema.prisma:429-454` dengan `supplierId String?` (`:436`, opsional) dan `reason String? @db.Text` (`:437`, teks bebas).
- Jalur tulisnya: `POST /stock-adjustments/receive` → `StockAdjustmentController.receiveStock` (`src/controllers/stockAdjustment.controller.ts:40`) → `StockAdjustmentService.receiveStock` (`src/services/stockAdjustment.service.ts:121-143`) → `StockAdjustmentRepository.receiveStock` (`src/repositories/stockAdjustment.repository.ts:226-230`) → `recordStockMovement` (`src/repositories/stockMovement.ts:120-154`).

**Koreksi penting atas hipotesis ini:** `supplierId` bukan sekadar "opsional" — **UI penerimaan barang tidak pernah mengirimkannya sama sekali**. Payload yang dikirim FE hanya `warehouseId`, `productId`, `receivedAt`, `reason`, `items` (`FE_Pridata_Jaya/app/(dashboard)/gudang/penerimaan-barang/input/page.tsx:226-232` dan `:237-243`). Nama supplier diambil dari input teks bebas `form.supplier` (`:172`) lalu dijejalkan ke dalam string `reason`. Artinya **relasi `Supplier` ↔ penerimaan secara praktis kosong 100%**: master data supplier tidak terhubung ke satupun transaksi barang masuk yang dibuat lewat layar ini.

### 1.3 "Tidak ada angka ekspektasi" — **BENAR, ini inti masalahnya**

- `StockAdjustment.quantity Int` polos di `prisma/schema.prisma:459`. Tidak ada `expectedQuantity`, tidak ada FK ke baris dokumen sumber (`:456-469`).
- Validasi satu-satunya di backend: `validateReceiveItems` (`src/services/stockAdjustment.service.ts:270-300`) hanya memeriksa (a) kondisi unik, (b) `quantity` integer positif, (c) total > 0. **Tidak ada satupun pembanding eksternal.**
- Skema request juga tidak punya tempat untuk angka ekspektasi: `stockAdjustmentReceiveBodySchema` (`src/validators/index.ts:583-593`) hanya menerima `warehouseId`, `productId`, `supplierId?`, `receivedAt?`, `reason?`, `items`.
- Grep `expected|variance|selisih|discrepan` di seluruh skema hanya mengembalikan `discrepancyQuantity` (`prisma/schema.prisma:942`) dan enum `DISCREPANCY` (`:1009`) — keduanya milik **`ReconciliationItem`, yaitu stock opname**, bukan penerimaan.

Konsekuensinya persis seperti dugaan: **berapapun yang diketik operator dianggap sah.** Satu-satunya deteksi selisih di seluruh sistem terjadi saat opname, yaitu setelah barang sudah lama masuk.

Perlu dicatat, ada "validasi" di FE yang mudah disalahpahami sebagai kontrol: `qtyGood + qtyDamaged harus sama dengan qtyReceived` (`.../input/page.tsx:202-205`). Ini **validasi operator terhadap dirinya sendiri** — ketiga angka itu sama-sama diketik orang yang sama. Ia tidak menangkap apa pun tentang kenyataan fisik di gudang.

### 1.4 "Satu record = satu produk, tidak ada header" — **BENAR, dan implementasinya lebih rapuh dari dugaan**

- `productId` memang ada di header record: `prisma/schema.prisma:434`. Anak `StockAdjustment[]` (`:445`, `:456-469`) hanya memecah per *kondisi barang* (`fromCondition`/`toCondition`), bukan per produk. Jadi satu record = satu produk, benar.
- **Temuan tambahan yang belum tercakup hipotesis:** "header surat jalan" sebenarnya *ada*, tapi hidup **hanya sebagai JSON yang di-serialize ke dalam kolom teks bebas `reason`**, dengan prefiks `[WAREHOUSE_RECEIPT]`:
  - penulisan: `buildWarehouseReceiptReason` (`FE_Pridata_Jaya/services/warehouse-receipts.ts:42-45`) — `JSON.stringify(meta)` digabung ke `reason`.
  - `meta` berisi `batchId`, `referenceNumber`, `supplier`, `warehouseId`, `receivedAt` (`services/warehouse-receipts.ts:3-9`), dengan `batchId` dibuat **di browser**: `` `rcv-${Date.now()}-${Math.random()...}` `` (`.../input/page.tsx:35`).
  - pembacaan kembali: `parseWarehouseReceiptReason` (`services/warehouse-receipts.ts:47-78`) dan `groupWarehouseReceiptBatches` (`:96-136`) — mengelompokkan ulang dengan **parsing string di sisi klien**.
- Akibat yang bisa dinyatakan pasti dari kode ini:
  - **Backend tidak tahu dokumen penerimaan itu ada.** Tidak ada query DB yang bisa mengelompokkan satu surat jalan, tidak ada `UNIQUE` pada nomor surat jalan, tidak ada laporan server-side per dokumen.
  - **Parsing bisa gagal diam-diam.** `parseWarehouseReceiptReason` mencari `}` pertama (`services/warehouse-receipts.ts:54`). Bila nilai `supplier` atau `referenceNumber` mengandung karakter `}`, parse gagal → `return null` → baris itu **dibuang dari daftar** (`:84-86`, `:94`). Stok tetap terlanjur masuk, tapi penerimaannya hilang dari layar riwayat.
  - **Satu surat jalan 40 baris = ~40–80 request HTTP terpisah.** FE melakukan fan-out `Promise.all` satu panggilan per produk per kondisi (`.../input/page.tsx:221-248`). Masing-masing adalah transaksi DB sendiri (`src/repositories/stockAdjustment.repository.ts:319`). **Tidak ada atomisitas dokumen**: bila panggilan ke-23 gagal, 22 baris sebelumnya sudah menambah stok permanen, dan operator hanya melihat satu pesan error generik (`.../input/page.tsx:259-261`). Menekan "Simpan" lagi akan **menggandakan** 22 baris yang sudah sukses.
  - **Tidak ada idempotency pada penerimaan.** `Order`, `Payment`, dan `PaymentRequest` punya `idempotencyKey` (`prisma/migrations/20260919090000_add_idempotency_keys/migration.sql`), `Order.idempotencyKey` di `prisma/schema.prisma:607`. `StockAdjustmentRecord` (`:429-454`) **tidak punya**. Double-submit = stok ganda.
  - Layar riwayat menarik **seluruh** record RECEIPT tanpa paginasi ke browser lalu mengelompokkan di klien (`app/(dashboard)/gudang/penerimaan-barang/page.tsx:36-41`). Ini akan melambat seiring waktu.

### 1.5 "Tidak ada approval selisih" — **BENAR**

- `StockAdjustmentRecord` (`prisma/schema.prisma:429-454`) tidak punya field `status`, `approvedBy`, `verifiedAt`, atau sejenisnya.
- `enum VerificationStatus { PENDING, VERIFIED, REJECTED }` memang ada (`prisma/schema.prisma:978-982`) tapi tidak dipakai oleh model penerimaan mana pun — ia milik alur pembayaran.
- Stok bergerak **seketika saat request diterima**, sebelum kontrol apa pun: `recordStockMovement` memanggil `moveStock` lebih dulu, baru menulis record (`src/repositories/stockMovement.ts:124-140`). Tidak ada state "menunggu persetujuan".

### 1.6 "Tidak ada barcode/QR di seluruh backend" — **BENAR, di kedua repo**

- `grep -rin "barcode|qrcode|gtin"` atas `SMD-Pridata-BE/src` → **0 hasil**.
- `grep -rin "barcode|qrcode|html5-qrcode|zxing|quagga"` atas `FE_Pridata_Jaya` (di luar `node_modules`/`.next`, termasuk `package.json`) → **0 hasil**.
- `Product` (`prisma/schema.prisma:196-236`) hanya punya `code String? @unique` (`:198`) yang merupakan kode internal "KD Item" berformat `YYMM + nomor urut`, bukan barcode supplier.
- Pemilihan produk di layar penerimaan dilakukan lewat pencarian teks + combobox (`.../input/page.tsx:402`). Seluruh input diketik/dipilih manual.

### 1.7 "Tidak ada UOM" — **SEBAGIAN BENAR, perlu dikoreksi**

- Benar bahwa tidak ada mekanisme konversi: grep `uom|conversionFactor|baseUnit|packSize|carton|karton|piecesPer` atas skema → **0 hasil**.
- Namun **bukan** benar bahwa tidak ada field satuan sama sekali. `Product.unit String?` ada di `prisma/schema.prisma:200` dengan komentar `// Satuan, mis. Pcs / Set / Meter`.
- Jadi diagnosis yang tepat: satuan tersimpan sebagai **label teks tanpa makna aritmetika**. Tidak ada faktor konversi, tidak ada satuan dasar, dan `quantity` di seluruh ledger adalah `Int` tanpa satuan (`prisma/schema.prisma:459`, `:416`, `:495`). Konversi karton↔pcs tetap terjadi di kepala operator — kesimpulan akhirnya sama, tapi alasannya harus dinyatakan benar.

### 1.8 "Tidak ada `createdByUserId`; cek apakah `AuditLog` menangkapnya" — **CAMPURAN. Sebagian salah, dan ada lubang yang lebih serius**

Tiga hal terpisah, jangan dicampur:

**(a) Kolom `createdByUserId` — memang tidak ada.** Grep `createdby|userId|actor` atas `prisma/schema.prisma:411-470` (model `WarehouseInventory`, `StockAdjustmentRecord`, `StockAdjustment`) → **0 hasil**. Modul ledger inti juga tidak menerima aktor: `RecordStockMovementInput` (`src/repositories/stockMovement.ts:26-36`) tidak punya field aktor sama sekali.

**(b) `AuditLog` MENANGKAP pembuatan penerimaan — hipotesis ini keliru.** `StockAdjustmentController.receiveStock` menulis audit log dengan aktor dari request: `getAuditActor(req)` → `createLog({...actor, action: 'STOCK_ADJUSTMENT_CREATED', entityType: 'STOCK_ADJUSTMENT', entityId: result.record.id, ...})` (`src/controllers/stockAdjustment.controller.ts:44-68`). Model `AuditLog` menyimpan `actorUserId` dan `actorEmail` (`prisma/schema.prisma:1183-1184`). Jadi **siapa yang membuat penerimaan bisa ditelusuri.**

**(c) Lubang yang sebenarnya, dan ini lebih buruk: PENGUBAHAN penerimaan tidak diaudit sama sekali.** `StockAdjustmentController.update` (`src/controllers/stockAdjustment.controller.ts:155-162`) memanggil service lalu langsung mengembalikan respons — **tidak ada `auditLogService.createLog`, tidak ada event, tidak ada notifikasi**, berbeda total dengan `receiveStock` (`:44-94`) dan `recordDamage` (`:103-150`). Padahal `update` benar-benar menulis ulang stok: ia menghapus seluruh item lama, membalik pergerakannya, lalu menulis yang baru (`src/repositories/stockAdjustment.repository.ts:244-314`, khususnya pembalikan di `:265-268` dan `moveStock` di `:298`). Dan untuk tipe RECEIPT, `reason` pun opsional saat update (`src/services/stockAdjustment.service.ts:218`, DTO `:59-65`).

> **Artinya: seseorang dapat mengubah kuantitas penerimaan yang sudah tercatat — mengubah stok riil — tanpa alasan wajib dan tanpa jejak audit apa pun.** Ini kerusakan pada *accountability trail* yang lebih tajam daripada absennya kolom `createdByUserId`, dan tidak tercakup dalam 8 hipotesis awal.

Catatan tambahan: penulisan audit log berada **di luar transaksi** dan dibungkus `try/catch` yang hanya mencatat `logger.warn` (`src/controllers/stockAdjustment.controller.ts:62-67`). Bila audit gagal, pergerakan stok tetap final. Jejak audit bersifat *best-effort*, bukan terjamin.

### Ringkasan verifikasi

| # | Hipotesis Ace | Putusan | Bukti utama |
|---|---|---|---|
| 1 | Tidak ada PO ke supplier | **Benar** | `schema.prisma:14-1523`; 0 hasil di src & migrations |
| 2 | Penerimaan lewat `StockAdjustmentRecord` RECEIPT | **Benar** (+ `supplierId` praktis tak pernah terisi) | `schema.prisma:429-454`, `.../input/page.tsx:226-243` |
| 3 | Tidak ada angka ekspektasi | **Benar** | `schema.prisma:459`, `stockAdjustment.service.ts:270-300` |
| 4 | 1 record = 1 produk, tak ada header | **Benar** (+ header palsu di `reason`, fan-out non-atomik) | `schema.prisma:434`, `warehouse-receipts.ts:42-78`, `.../input/page.tsx:221-248` |
| 5 | Tidak ada approval selisih | **Benar** | `schema.prisma:429-454`, `stockMovement.ts:124-140` |
| 6 | Tidak ada barcode/QR | **Benar**, di BE dan FE | 0 hasil grep kedua repo |
| 7 | Tidak ada UOM | **Sebagian** — `Product.unit` ada tapi tanpa konversi | `schema.prisma:200`; 0 hasil grep konversi |
| 8 | Tak ada `createdByUserId`; AuditLog? | **Campuran** — kolom tak ada (benar), tapi AuditLog **menangkap** pembuatan (hipotesis keliru); **`update` sama sekali tak diaudit** (lubang baru) | `stockMovement.ts:26-36`, `stockAdjustment.controller.ts:44-68` vs `:155-162` |

---

## 2. Akar masalah dalam satu kalimat

> **Sistem tidak punya dokumen ekspektasi apa pun untuk barang masuk — tidak ada PO ke supplier dan tidak ada header penerimaan yang tersimpan di database — sehingga angka yang diketik operator tidak pernah dibandingkan dengan angka manapun, dan satu-satunya mekanisme deteksi selisih yang ada (`ReconciliationSession`, `prisma/schema.prisma:919-954`) baru bekerja saat stock opname, yaitu berminggu-minggu setelah kesalahan terjadi.**

Hipotesis Ace **terbukti**: ini masalah *missing document*, bukan masalah form. Menambahkan validasi di layar penerimaan tidak akan menutup apa pun, karena tidak ada angka pembanding untuk divalidasi. Bukti paling telak justru ada di kode FE saat ini: validasi `qtyGood + qtyDamaged === qtyReceived` (`.../input/page.tsx:202-205`) adalah persis "validasi form tanpa dokumen" — ia terasa seperti kontrol, tapi hanya mencocokkan ketikan operator dengan ketikan operator itu sendiri.

Perlu ditambahkan satu lapis lagi pada diagnosis: **ledger-nya sendiri sehat, yang hilang adalah lapisan dokumen di atasnya.** `src/repositories/stockMovement.ts:1-154` adalah satu-satunya penulis kuantitas stok, transaksional, dan dipanggil oleh kelima jalur stok (`return.repository.ts:257`, `warehouseTransfer.repository.ts:283`, `warehouseInventory.repository.ts:250`, `stockAdjustment.repository.ts:320`, `deliveryOrder.repository.ts:711`). Ini kabar baik untuk Fase 2: fondasinya benar, yang perlu dibangun adalah dokumen dan kontrol di atas ledger — **bukan** membongkar ledger.

---

## 3. Pemisahan jujur: apa yang bisa dan tidak bisa diselesaikan software

Memakai lensa *error taxonomy*. Software hanya bisa melakukan tiga hal terhadap human error, dan **tidak satupun di antaranya adalah "menghilangkan"**.

### Posisi sistem saat ini

| Kemampuan | Nilai sekarang | Bukti |
|---|---|---|
| **(a) Mengurangi peluang salah input** | **Sangat rendah** | Setiap angka diketik manual; produk dicari dengan teks (`.../input/page.tsx:402`); supplier diketik bebas (`:172`); tidak ada scan (0 hasil grep); konversi satuan di kepala operator (`schema.prisma:200`) |
| **(b) Menangkap salah lebih awal** | **Nyaris nol pada saat penerimaan** | Tidak ada angka ekspektasi (`schema.prisma:456-469`); validasi hanya self-consistency (`.../input/page.tsx:202-205`). Deteksi baru terjadi di opname (`schema.prisma:935-954`) |
| **(c) Membuat salah terlacak & murah dikoreksi** | **Sedang untuk pembuatan, buruk untuk koreksi** | Pembuatan terekam beserta aktor (`stockAdjustment.controller.ts:44-68`); tapi **pengubahan tidak terekam sama sekali** (`:155-162`), header dokumen hanya string yang bisa gagal di-parse (`warehouse-receipts.ts:47-78`), dan tidak ada idempotency (`schema.prisma:429-454`) |

Jadi klaim "sistem ini sulit menyelesaikan masalah human error barang masuk" **valid apa adanya untuk kondisi saat ini.** Tidak perlu dibantah; yang perlu dijawab adalah apakah itu dapat diperbaiki dan dengan biaya berapa. Jawabannya: dapat, untuk (a), (b), dan (c) — dan (b) adalah yang paling besar peningkatannya.

### Yang realistis dijanjikan setelah Fase 2

- **(a)** turun signifikan, **tidak nol**. Scan menghilangkan salah pilih produk dan salah ketik kode, tapi jumlah fisik tetap dihitung manusia. Manusia tetap bisa salah hitung 11 vs 12 karton.
- **(b)** ini lompatan terbesar. Dari "selisih ketahuan saat opname" menjadi "selisih ketahuan sebelum truk supplier pergi". Ini yang paling layak dijual.
- **(c)** dari "tidak bisa dilacak siapa yang mengubah" menjadi "setiap perubahan punya pelaku, waktu, alasan, dan dokumen induk".

### Yang BUKAN masalah software — jangan dijanjikan, jangan dibuatkan fitur

Bagian ini harus disampaikan apa adanya ke Pridata:

1. **Salah hitung fisik tetap terjadi.** Kalau operator menghitung 11 padahal isinya 12, sistem dengan PO akan menandai selisih 1 — itu deteksi, bukan pencegahan. Tanpa timbangan atau hitung ganda, software tidak bisa tahu jumlah sebenarnya.
2. **Jam puncak bongkar muat.** Bila tiga truk datang bersamaan dan hanya ada dua orang, kontrol apa pun akan diakali: operator akan menghitung sekilas, meng-klik "sesuai", dan membereskannya nanti. Ini masalah *staffing dan penjadwalan kedatangan supplier*, bukan masalah fitur. Kontrol yang diusulkan di Fase 2 dirancang agar murah waktunya (lihat §6), tapi tidak ada desain yang selamat dari kekurangan orang.
3. **Budaya "tidak ada PO".** Ini risiko terbesar Fase 2. Bila Pridata memesan ke supplier lewat telepon/WhatsApp tanpa dokumen pesanan resmi, maka membangun modul `PurchaseOrder` hanya menghasilkan tabel kosong, dan pencocokan 3 arah tidak akan pernah aktif. **Pertanyaan terbuka untuk Ace — lihat §8.** Bila jawabannya "tidak ada PO", rancangannya harus berubah: bertumpu pada surat jalan supplier sebagai dokumen ekspektasi (pencocokan 2 arah), bukan pada PO.
4. **Insentif dan konsekuensi.** Jejak audit hanya berguna kalau ada yang membacanya dan ada konsekuensinya. Software menyediakan bukti; software tidak bisa menyediakan kemauan manajemen untuk menindaklanjuti.
5. **Kualitas data master.** Blind count dan scan bergantung pada master produk yang bersih. Bila satu barang fisik punya dua entri produk, selisih akan muncul terus dan operator akan belajar mengabaikan peringatan.
6. **Pelatihan.** Blind count secara sengaja membuat pekerjaan terasa lebih lambat di minggu pertama. Tanpa penjelasan mengapa, operator akan menganggapnya kemunduran dan mencari jalan pintas.

---

## 4. Spesifikasi Fase 2

Prinsip yang mengikat seluruh item:

> **Setiap perubahan kuantitas stok wajib lewat `src/repositories/stockMovement.ts` (`recordStockMovement`/`moveStock`).** Modul baru menulis dokumen dan kontrolnya sendiri, lalu memanggil ledger — tidak pernah menulis `warehouseInventory.quantity` atau `product.stockQuantity` langsung. Ini sudah menjadi kontrak eksplisit di `stockMovement.ts:4-9`.

Ada preseden arsitektur yang sangat dekat dan sebaiknya ditiru, bukan diciptakan ulang: **`ReconciliationSession`** sudah berupa *header + baris + angka sistem vs angka fisik + status DRAFT/CONFIRMED*, yang saat dikonfirmasi memposting `CORRECTION` lewat ledger (`prisma/schema.prisma:919-954`; `src/repositories/reconciliation.repository.ts:186-266`, pembuatan record di `:210-213`, sinkronisasi stok di `:254`). `GoodsReceipt` adalah pola yang sama diterapkan pada arah masuk. Ini menurunkan risiko dan biaya beberapa item di bawah.

**Tier effort** (hari-orang, 1 developer familier dengan repo):
S = 1–3 · M = 4–8 · L = 9–15 · XL = 16+

---

### F2-1 — `GoodsReceipt`: header penerimaan per surat jalan *(fondasi, prasyarat hampir semua item lain)*

**Delta data model**
```prisma
model GoodsReceipt {
  id                String   @id @default(uuid())
  receiptNumber     String   @unique          // digenerate server, pakai DocumentNumberCounter
  supplierDocNumber String                    // nomor surat jalan supplier
  supplierId        String                    // WAJIB, FK — bukan teks bebas lagi
  warehouseId       String
  purchaseOrderId   String?                   // diisi pada F2-2/F2-3
  receivedAt        DateTime
  status            GoodsReceiptStatus @default(DRAFT)
  notes             String?  @db.Text
  idempotencyKey    String?  @unique          // pola sama dgn migrations/20260919090000
  createdByUserId   String
  postedByUserId    String?
  postedAt          DateTime?
  // + relasi supplier, warehouse, lines, purchaseOrder
  @@unique([supplierId, supplierDocNumber])   // satu surat jalan tak bisa masuk dua kali
}

model GoodsReceiptLine {
  id                String   @id @default(uuid())
  goodsReceiptId    String
  productId         String
  expectedQuantity  Int?                      // dari PO; null bila tanpa PO
  countedQuantity   Int                       // hasil hitung fisik
  goodQuantity      Int
  damagedQuantity   Int
  varianceQuantity  Int                       // turunan: counted - expected
  @@unique([goodsReceiptId, productId])
}

enum GoodsReceiptStatus { DRAFT, PENDING_APPROVAL, POSTED, CANCELLED }
```
`StockAdjustmentRecord` mendapat `goodsReceiptId String?` agar setiap baris ledger bisa ditelusuri balik ke dokumennya.

**Alur & state**
`DRAFT` (operator mengisi, stok **belum** bergerak) → `POSTED` (satu transaksi tunggal: seluruh baris diposting lewat `recordStockMovement`, `goodsReceiptId` terisi, `postedByUserId`/`postedAt` terisi). `CANCELLED` hanya sah dari `DRAFT`. Dokumen yang sudah `POSTED` **tidak dapat diedit** — koreksi dibuat sebagai dokumen koreksi baru yang mereferensikan aslinya. Ini sekaligus menutup lubang §1.8(c).

**Edge case**
- Surat jalan sama dikirim dua kali → ditolak oleh `@@unique([supplierId, supplierDocNumber])`.
- Double-submit / retry jaringan → ditangani `idempotencyKey`.
- Posting gagal di tengah → satu transaksi, rollback penuh; tidak ada lagi kondisi "22 dari 40 baris terlanjur masuk" seperti sekarang (`.../input/page.tsx:221-248`).
- Produk muncul dua kali dalam satu dokumen → ditolak `@@unique([goodsReceiptId, productId])`.
- **Migrasi data lama:** record RECEIPT yang ada sekarang menyimpan header di string `reason` berprefiks `[WAREHOUSE_RECEIPT]` (`services/warehouse-receipts.ts:38-45`). Perlu skrip backfill yang mem-parse blob itu menjadi `GoodsReceipt`, termasuk penanganan baris yang gagal parse (harus dilaporkan, bukan dibuang diam-diam seperti `:84-86` sekarang). **Migrasi ini wajib dan tidak boleh disembunyikan dari estimasi.**

**Kriteria penerimaan**
1. Satu surat jalan 40 baris menghasilkan **1** `GoodsReceipt` + 40 `GoodsReceiptLine` + **1 transaksi DB**, terverifikasi lewat log query.
2. Mematikan koneksi DB di tengah posting meninggalkan stok **tidak berubah sama sekali** dan dokumen tetap `DRAFT`.
3. Mengirim ulang request dengan `idempotencyKey` sama mengembalikan dokumen yang sama, stok **tidak** bertambah dua kali.
4. Setiap `StockAdjustmentRecord` hasil posting punya `goodsReceiptId` terisi dan `supplierId` terisi (bukan null).
5. Laporan penerimaan per supplier dapat dihasilkan **dengan query SQL biasa**, tanpa parsing string.
6. Seluruh data RECEIPT lama tampil di layar riwayat baru setelah backfill; jumlah dokumen hasil backfill direkonsiliasi dan selisihnya nol atau dilaporkan baris demi baris.

**Effort: M–L, 8–14 hari.** *Blast radius:* `stockMovement.ts` (kontrak input, 5 pemanggil), `stockAdjustment.{routes,service,repository,controller}.ts`, kedua halaman FE `penerimaan-barang`, penghapusan `services/warehouse-receipts.ts`, migrasi skema + backfill data produksi. Menyentuh ledger inti → **butuh regression test pada kelima jalur stok**.

---

### F2-2 — `PurchaseOrder` ke supplier

**Delta data model:** `PurchaseOrder` (nomor unik via `DocumentNumberCounter` yang sudah ada di `prisma/schema.prisma:1340`, `supplierId`, `warehouseId` tujuan, `orderDate`, `expectedDeliveryDate`, `status`, `createdByUserId`, `approvedByUserId?`) + `PurchaseOrderLine` (`productId`, `orderedQuantity`, `receivedQuantity` terakumulasi, `unitPrice?`) + `enum PurchaseOrderStatus { DRAFT, APPROVED, PARTIALLY_RECEIVED, CLOSED, CANCELLED }`.

> Harga beli pada PO **tidak saya spesifikasikan** — itu ranah Rani. Field `unitPrice` saya sediakan sebagai tempat, keputusan soal harga/margin bukan milik dokumen ini.

**Alur & state:** `DRAFT` → `APPROVED` (mengunci baris) → `PARTIALLY_RECEIVED` / `CLOSED` (digerakkan oleh posting `GoodsReceipt`) → `CANCELLED` (hanya dari `DRAFT`/`APPROVED` tanpa penerimaan).

**Edge case:** penerimaan berlebih di atas `orderedQuantity`; pengiriman parsial berkali-kali; PO dibatalkan setelah sebagian diterima; supplier mengirim produk yang tidak ada di PO.

**Kriteria penerimaan**
1. PO `APPROVED` tidak dapat diubah barisnya.
2. `receivedQuantity` pada baris PO selalu sama dengan jumlah `countedQuantity` seluruh `GoodsReceipt` berstatus `POSTED` yang menunjuk PO tersebut — diuji dengan tiga penerimaan parsial.
3. PO otomatis `CLOSED` saat seluruh baris terpenuhi, dan tetap `PARTIALLY_RECEIVED` bila satu baris pun kurang.
4. Membatalkan PO yang sudah punya penerimaan ditolak dengan error eksplisit.

**Effort: M, 6–10 hari.** *Blast radius:* **rendah** — modul greenfield, tidak ada kode existing yang menulis ke sini. Risiko utamanya organisasi, bukan teknis (lihat §3 butir 3).

---

### F2-3 — Pencocokan 3 arah (PO vs surat jalan vs hitungan fisik)

**Delta data model:** tidak ada model baru. Mengaktifkan `GoodsReceiptLine.expectedQuantity` (diisi dari `PurchaseOrderLine.orderedQuantity` dikurangi yang sudah diterima) dan `varianceQuantity`. Tambahan `GoodsReceipt.varianceStatus` turunan (`MATCH` / `VARIANCE`) mengikuti pola `ReconciliationItemStatus` (`prisma/schema.prisma:1007-1010`).

**Alur:** operator memilih PO → sistem menarik baris beserta sisa yang belum diterima → operator memasukkan hasil hitung fisik → sistem menghitung selisih **sebelum** dokumen diposting → selisih ≠ 0 memicu F2-5.

**Edge case:** penerimaan tanpa PO (harus tetap boleh, `expectedQuantity = null`, ditandai `UNMATCHED` dan masuk laporan pengecualian); satu surat jalan mencakup dua PO; produk di surat jalan tidak ada di PO manapun; PO diterima melebihi pesanan.

**Kriteria penerimaan**
1. Penerimaan 95 pcs atas PO 100 pcs menghasilkan `varianceQuantity = -5` dan status `VARIANCE` **sebelum** stok bergerak.
2. Penerimaan tanpa PO tetap bisa diposting, ditandai `UNMATCHED`, dan muncul di laporan pengecualian harian.
3. Ada satu laporan "selisih penerimaan per periode/supplier" yang dihasilkan dari kolom database, bukan parsing teks.

**Effort: S–M, 4–7 hari.** *Blast radius:* rendah, terbatas pada modul F2-1/F2-2. **Bergantung penuh pada F2-1 dan F2-2.**

---

### F2-4 — Blind count

**Delta data model:** tidak ada. Ini murni aturan otorisasi pada lapisan serialisasi respons: untuk peran gudang, API **tidak boleh** mengirim `expectedQuantity` ke klien sebelum `countedQuantity` tersimpan. Repo sudah punya mekanisme peran yang bisa dipakai: `requireAccess({ orgRoles: WAREHOUSE_WRITE_ROLES, ... })` (`src/routes/stockAdjustment.routes.ts:31-34`).

**Alur:** operator membuka PO → melihat **daftar produk saja, tanpa angka** → memasukkan hitungan → menyimpan → barulah selisih ditampilkan.

**Edge case:** supervisor perlu melihat angka ekspektasi (peran berbeda, boleh); operator mengoreksi hitungan setelah melihat selisih (harus tercatat sebagai `recountCount++`, karena inilah sinyal paling berguna untuk menilai kualitas hitungan); operator membuka endpoint PO langsung untuk mengintip angka → **harus ditutup di server, bukan disembunyikan di UI** (kalau hanya disembunyikan di frontend, kontrolnya kosong).

**Kriteria penerimaan**
1. Respons API mentah untuk peran gudang **tidak memuat** `expectedQuantity` sebelum penyimpanan hitungan — diuji lewat pemeriksaan payload langsung, bukan lewat UI.
2. Tidak ada endpoint lain yang membocorkan angka itu ke peran gudang.
3. Perubahan hitungan setelah selisih terlihat tersimpan sebagai jejak terpisah.

**Effort: S, 2–4 hari.** *Blast radius:* rendah. **Hanya bermakna bila F2-3 ada** — tanpa angka ekspektasi, tidak ada yang perlu disembunyikan. Rasio nilai terhadap biaya paling tinggi di seluruh paket, karena inilah yang mengubah "menyalin angka" menjadi "menghitung".

---

### F2-5 — Approval selisih wajib di atas ambang

**Delta data model:** `GoodsReceiptStatus.PENDING_APPROVAL` (sudah ada di enum F2-1); `GoodsReceipt.approvedByUserId`, `approvedAt`, `approvalNote`; konfigurasi ambang (absolut dan/atau persentase) — bisa per supplier atau global.

**Keputusan desain yang harus diambil eksplisit:** stok diposting **saat approval**, bukan saat input. Alternatifnya (posting duluan lalu koreksi) akan mengulang persis masalah yang sedang kita perbaiki. Konsekuensinya: **dokumen yang menunggu approval berarti stok belum bertambah**, dan penjualan atas barang itu belum bisa dilakukan. Ini konsekuensi operasional nyata yang harus disepakati Pridata di muka — bukan detail teknis.

**Alur:** selisih ≤ ambang → langsung `POSTED`. Selisih > ambang → `PENDING_APPROVAL`, supervisor menyetujui/menolak; setuju → `POSTED` (stok bergerak sesuai hitungan fisik); tolak → kembali `DRAFT` untuk hitung ulang.

**Edge case:** supervisor tidak tersedia saat truk harus pergi (**risiko adopsi tertinggi** — butuh jalur eskalasi atau approval lewat ponsel); operator memecah satu penerimaan menjadi beberapa dokumen agar tiap selisih di bawah ambang (**harus dideteksi**: beberapa dokumen dengan `supplierDocNumber` sama sudah ditolak oleh unique constraint F2-1, tapi pemecahan per produk perlu laporan pemantauan); barang sudah terlanjur dijual saat dokumen masih `PENDING_APPROVAL`.

**Kriteria penerimaan**
1. Selisih di atas ambang **tidak dapat** memindahkan stok tanpa approval — diuji langsung di level API.
2. Approval dan penolakan tercatat lengkap dengan pelaku, waktu, dan catatan.
3. Ada laporan umur dokumen `PENDING_APPROVAL` (deteksi dokumen yang menggantung).

**Effort: M, 5–9 hari.** *Blast radius:* sedang — mengubah *kapan* stok bergerak, sehingga menyentuh asumsi ketersediaan stok di modul penjualan/DO. **Ini item dengan risiko adopsi tertinggi**, lihat §6.

---

### F2-6 — Aktor pada penerimaan + menambal audit pengubahan ⭐

**Delta data model:** `StockAdjustmentRecord.createdByUserId String?` (nullable, agar data lama tidak perlu backfill — pola yang sama dipakai migrasi idempotency yang sudah ada). `RecordStockMovementInput` (`src/repositories/stockMovement.ts:26-36`) mendapat field aktor, diteruskan dari kelima pemanggil.

**Perbaikan wajib yang menyertainya:** menambahkan audit log pada `StockAdjustmentController.update` (`src/controllers/stockAdjustment.controller.ts:155-162`) — saat ini **nol** — dan mewajibkan `reason` saat mengubah record RECEIPT (`src/services/stockAdjustment.service.ts:218`).

**Edge case:** perubahan yang dipicu sistem, bukan manusia (mis. posting dari DO, `deliveryOrder.repository.ts:711`) → butuh penanda aktor sistem; data lama tanpa aktor → tetap `null`, dan laporan harus menyatakannya sebagai "tidak diketahui", bukan menyamarkannya.

**Kriteria penerimaan**
1. Setiap penerimaan baru punya `createdByUserId` terisi.
2. Setiap pengubahan record stok menghasilkan entri `AuditLog` berisi nilai sebelum dan sesudah.
3. Mengubah record RECEIPT tanpa `reason` ditolak.
4. Kelima pemanggil `recordStockMovement` meneruskan aktor; diverifikasi lewat tes.

**Effort: S, 2–4 hari.** *Blast radius:* menyentuh kontrak `stockMovement.ts` sehingga 5 pemanggil ikut berubah — tapi perubahannya aditif dan mekanis. **Nilai tertinggi per hari kerja di seluruh paket, dan satu-satunya item yang berdiri sendiri tanpa prasyarat.** Rekomendasi: kerjakan ini lebih dulu, apa pun keputusan atas item lainnya.

---

### F2-7 — Idempotency pada penerimaan

**Delta data model:** `idempotencyKey String? @unique` pada `GoodsReceipt` (atau pada `StockAdjustmentRecord` bila F2-1 ditunda). Preseden lengkap sudah ada: `prisma/migrations/20260919090000_add_idempotency_keys/migration.sql`.

**Kriteria penerimaan:** dua request identik berurutan menghasilkan satu dokumen dan satu pergerakan stok; request kedua mengembalikan dokumen pertama, bukan error.

**Effort: S, 1–3 hari.** *Blast radius:* rendah, pola sudah terbukti di repo. Bila F2-1 dikerjakan, item ini sudah termasuk di dalamnya.

---

### F2-8 — UOM & konversi karton↔pcs ⚠️ **ITEM PALING BERISIKO**

**Delta data model:** `Product.baseUomId`, model `Uom`, dan `ProductUomConversion` (`productId`, `uomId`, `factor` — mis. 1 karton = 24 pcs). `GoodsReceiptLine` menyimpan `inputQuantity` + `inputUomId` + `baseQuantity` hasil konversi. **Ledger tetap menyimpan satuan dasar saja** — ini keputusan penting: konversi terjadi di tepi (saat input), bukan di dalam ledger.

**Mengapa ini yang paling berbahaya:** `quantity` bertipe `Int` polos tersebar di seluruh sistem — `WarehouseInventory.quantity` (`prisma/schema.prisma:416`), `StockAdjustment.quantity` (`:459`), `WarehouseTransferDetail.quantity` (`:495`), ditambah `OrderItem`, `InvoiceItem`, `DeliveryOrderItem`, `SalesReturnItem`, `ReconciliationItem`, seluruh laporan, dan modul KPI. Memperkenalkan satuan berarti **setiap tempat yang membaca angka stok harus tahu satuan mana yang dimaksud**. Salah satu saja terlewat dan hasilnya adalah kesalahan stok senyap dengan faktor 24× — jauh lebih buruk daripada masalah yang sedang kita perbaiki.

**Edge case:** faktor konversi berubah di tengah jalan (supplier ganti ukuran karton) → faktor **wajib di-snapshot** pada baris dokumen, tidak boleh dibaca ulang dari master; pembagian tidak bulat (7 pcs dari karton isi 24); satu produk dengan beberapa kemasan.

**Kriteria penerimaan**
1. Menerima 5 karton (1 karton = 24) menambah **tepat 120** pada satuan dasar.
2. Faktor konversi tersimpan sebagai snapshot pada baris dokumen; mengubah master **tidak** mengubah dokumen historis.
3. **Audit menyeluruh atas seluruh pembaca `quantity`**, dengan daftar periksa per modul yang ditandatangani — ini bagian terbesar dari pekerjaannya, bukan pembuatan model barunya.
4. Total stok seluruh produk sebelum dan sesudah migrasi identik.

**Effort: L–XL, 12–20 hari.** *Blast radius:* **tertinggi di seluruh paket** — menyentuh setiap modul yang membaca kuantitas. **Rekomendasi saya: pisahkan menjadi fase tersendiri setelah Fase 2 stabil, jangan digabung.** Bila Pridata memaksa ini masuk Fase 2, estimasinya harus memakai batas atas dan disertai anggaran regression test tersendiri.

---

### F2-9 — Scan barcode/QR + input mobile gudang

**Delta data model:** `ProductBarcode` (`productId`, `barcode @unique`, `uomId?` — satu produk bisa punya barcode berbeda untuk pcs dan karton). `Product.code` yang ada (`prisma/schema.prisma:198`) adalah kode internal dan **tidak boleh** dipakai sebagai barcode.

**Alur:** operator memindai → sistem me-resolve ke `productId` → baris bertambah otomatis → operator hanya mengetik jumlah. Ini menyerang error taxonomy (a) secara langsung: menghilangkan kesalahan *identifikasi produk*, yang pada katalog distributor dengan ribuan SKU mirip adalah sumber error yang besar.

**Edge case:** barang tanpa barcode (harus tetap bisa dicari manual — jalur cadangan wajib ada); satu barcode terpetakan ke dua produk; barcode supplier berbeda dari barcode ritel; sinyal WiFi mati di gudang → **butuh mode offline/antrean**, dan ini yang membuat estimasinya naik.

**Kriteria penerimaan**
1. Memindai barcode terdaftar mengisi baris dengan produk yang benar tanpa ketikan.
2. Barcode tak dikenal memunculkan alur pendaftaran, bukan kegagalan senyap.
3. Input jalan di perangkat genggam di kondisi gudang nyata (diuji di lokasi, bukan di kantor).

**Effort: M–L, 8–14 hari** (di luar pengadaan perangkat). *Blast radius:* rendah pada data model, sedang pada FE. **Bergantung pada satu fakta yang belum diketahui: apakah barang Pridata benar-benar berbarcode dan apakah barcodenya konsisten antar supplier.** Lihat §8.

---

### F2-10 — Batch/expiry — **REKOMENDASI: TUNDA**

Saya **tidak menganjurkan** item ini masuk Fase 2 kecuali Pridata mendistribusikan produk yang memang punya tanggal kedaluwarsa. Alasannya teknis dan serius: identitas stok saat ini adalah `(warehouseId, productId, condition)` (`prisma/schema.prisma:423`). Menambahkan batch berarti **mengubah kunci identitas ledger**, yang berdampak pada setiap kueri stok, setiap pengurangan stok, dan logika pemilihan batch (FEFO) pada setiap pengeluaran barang. Ini sekelas atau lebih berat dari F2-8.

**Bila memang dibutuhkan:** `ProductBatch` + `batchId` pada `WarehouseInventory` dan seluruh baris dokumen, plus strategi FEFO pada pengeluaran. **Effort: L–XL, 10–16 hari,** blast radius setara F2-8. **Pertanyaan untuk Ace di §8.**

---

### Ringkasan Fase 2

| Item | Effort (hari) | Blast radius | Prasyarat |
|---|---|---|---|
| F2-6 Aktor + audit pengubahan ⭐ | 2–4 | Sedang (5 pemanggil ledger) | — |
| F2-7 Idempotency | 1–3 | Rendah | — (masuk F2-1) |
| F2-1 GoodsReceipt header | 8–14 | **Tinggi** (ledger + migrasi data) | — |
| F2-2 PurchaseOrder | 6–10 | Rendah (greenfield) | — |
| F2-3 Pencocokan 3 arah | 4–7 | Rendah | F2-1, F2-2 |
| F2-4 Blind count | 2–4 | Rendah | F2-3 |
| F2-5 Approval selisih | 5–9 | Sedang (mengubah *kapan* stok bergerak) | F2-1, F2-3 |
| F2-9 Barcode + mobile | 8–14 | Sedang (FE) | F2-1 |
| F2-8 UOM & konversi ⚠️ | 12–20 | **Tertinggi** | F2-1 |
| F2-10 Batch/expiry | 10–16 | **Tertinggi** | F2-1 |

**Paket inti yang saya rekomendasikan (F2-6, F2-1, F2-2, F2-3, F2-4, F2-5): 27–48 hari-orang.**
Inilah paket yang benar-benar menjawab keluhan human error barang masuk.

**Paket inti + barcode (+F2-9): 35–62 hari-orang.**

**Seluruh item termasuk UOM dan batch: 58–101 hari-orang.** Saya tidak menganjurkan lingkup ini dijual sebagai satu fase.

Angka-angka ini adalah **effort, bukan harga, dan bukan jadwal kalender.** Penetapan harga milik Rani. Jadwal kalender perlu ditambah waktu UAT, pelatihan, dan migrasi data produksi.

---

## 5. Catatan estimasi yang tidak boleh disembunyikan

1. **F2-1 mewajibkan migrasi data produksi.** Penerimaan lama hanya ada sebagai blob JSON di kolom teks (`services/warehouse-receipts.ts:38-45`) dan sebagiannya mungkin gagal parse (`:47-78`). Backfill-nya nyata, perlu rekonsiliasi, dan sudah termasuk dalam rentang 8–14 hari — tapi **hanya batas atas rentang itu yang realistis bila volume data historisnya besar.**
2. **F2-6 menyentuh kontrak ledger inti** (`stockMovement.ts:26-36`) dan karenanya 5 pemanggil. Kelihatan sepele; tetap butuh regression test pada seluruh jalur stok. Estimasi di atas sudah mengasumsikan itu dikerjakan, bukan dilewati.
3. **F2-5 mengubah kapan stok bertambah.** Modul penjualan dan DO saat ini berasumsi stok bertambah seketika saat penerimaan. Asumsi itu menjadi tidak benar. Ini bukan biaya coding, ini biaya proses bisnis.
4. **F2-8 dan F2-10 tidak boleh diberi estimasi titik tunggal** dan tidak boleh diasumsikan memakai jalur teraman. Keduanya menyentuh kunci identitas atau satuan pada ledger yang dibaca seluruh sistem.

---

## 6. Biaya friksi operator

Kontrol yang memperlambat gudang saat puncak bongkar muat **akan diakali**. Berikut perkiraan tambahan waktu per dokumen penerimaan, dengan asumsi surat jalan ~40 baris.

| Kontrol | Tambahan waktu / penerimaan | Catatan |
|---|---|---|
| F2-1 header dokumen | **−2 s.d. −5 menit (LEBIH CEPAT)** | Sekarang operator mengetik nomor referensi + supplier lalu sistem menembak 40–80 request. Dengan header, metadata diisi **sekali**, satu kali simpan. Ini perbaikan, bukan beban. |
| F2-2 PO | **0 menit di gudang** | Beban pindah ke bagian pembelian di kantor, bukan ke operator gudang. |
| F2-3 pencocokan 3 arah | **+1 s.d. +3 menit** | Hanya pada dokumen yang selisih; yang cocok berjalan seperti biasa. |
| F2-4 blind count | **+3 s.d. +8 menit** | **Biaya nyata, dan ini yang paling mungkin diakali.** Operator tidak bisa lagi menyalin angka surat jalan; ia benar-benar harus menghitung. Inilah memang tujuannya — biaya ini adalah produknya, bukan efek sampingnya. |
| F2-5 approval selisih | **+0 menit bila cocok; +10 menit s.d. tertahan** bila selisih dan supervisor tidak ada | **Risiko adopsi tertinggi.** Mitigasi wajib: approval lewat ponsel, ambang yang tidak terlalu ketat di awal, dan jalur eskalasi. Tanpa itu, operator akan belajar memasukkan angka surat jalan apa adanya supaya selisihnya nol. |
| F2-9 barcode | **−5 s.d. −15 menit (LEBIH CEPAT)** | Menghilangkan pencarian produk manual 40 kali. Ini yang **membiayai** friksi blind count. |

**Kesimpulan friksi:** F2-4 + F2-5 sendirian akan membuat penerimaan terasa lebih lambat dan berisiko diakali. Digabung dengan F2-1 + F2-9, total waktu per penerimaan kemungkinan **sama atau lebih cepat** dari sekarang, sementara kualitas datanya jauh lebih baik. **Ini argumen urutan pengerjaan, bukan sekadar catatan:** menjual blind count tanpa barcode adalah menjual kemunduran yang terasa. Bila anggaran memaksa memilih, jangan jalankan F2-4/F2-5 tanpa F2-1.

**Ambang aman untuk disepakati:** bila tambahan waktu melebihi ~10 menit per penerimaan pada jam puncak, harapkan kontrolnya diakali. Rancang ambang approval dari data selisih nyata setelah 1 bulan berjalan, bukan ditebak di muka.

---

## 7. Target terukur

Setiap target punya baseline, cara ukur, dan batasan kejujurannya. **Tidak ada satupun yang menjanjikan human error hilang.**

### T1 — Waktu penemuan selisih *(metrik paling jujur dan paling layak dijual)*

- **Baseline:** selisih hanya ditemukan saat stock opname. Satu-satunya mekanisme yang ada adalah `ReconciliationSession` (`prisma/schema.prisma:919-954`) yang dijalankan manual per gudang. **Angka baseline harus diambil dari data nyata** — hitung jarak rata-rata antar `createdAt` pada tabel `reconciliation_sessions` per gudang. Bila kadensnya bulanan, latensi deteksi rata-rata ≈ **15–30 hari**.
- **Target:** selisih penerimaan terdeteksi **pada hari penerimaan** untuk seluruh penerimaan yang punya PO.
- **Cara ukur:** `avg(POSTED_at − receivedAt)` untuk dokumen ber-`varianceStatus = VARIANCE`, dilaporkan mingguan.
- **Batasan:** hanya berlaku untuk selisih **terhadap PO**. Selisih akibat salah hitung yang kebetulan sama dengan angka PO tetap lolos dan baru ketahuan saat opname. Katakan ini apa adanya.

### T2 — Persentase baris penerimaan yang tidak lagi diketik manual

- **Baseline: 0%.** Dapat dibuktikan dari kode hari ini — tidak ada barcode sama sekali di kedua repo (§1.6), dan produk dipilih lewat pencarian teks (`.../input/page.tsx:402`).
- **Target:** ≥70% baris terisi lewat scan dalam 3 bulan setelah F2-9, **dengan syarat** barang berbarcode. Angka ini harus direvisi setelah survei barcode di gudang (§8).
- **Cara ukur:** rasio `GoodsReceiptLine` dengan `inputMethod = SCAN` terhadap total baris.

### T3 — Keterhubungan supplier pada penerimaan

- **Baseline: 0%** untuk penerimaan yang dibuat lewat layar gudang. Terbukti dari kode: FE tidak pernah mengirim `supplierId` (`.../input/page.tsx:226-232`), nama supplier hanya teks bebas (`:172`).
- **Target: 100%** setelah F2-1 (dijamin oleh constraint `supplierId` non-null).
- **Cara ukur:** `count(*) where supplierId is null` pada penerimaan baru = 0.
- **Nilai bisnisnya:** untuk pertama kalinya Pridata bisa menjawab "supplier mana yang paling sering kurang kirim" dengan query, bukan dengan ingatan orang.

### T4 — Keterlacakan pengubahan catatan stok

- **Baseline: 0%.** `update` tidak menulis audit log sama sekali (`src/controllers/stockAdjustment.controller.ts:155-162`).
- **Target: 100%** setelah F2-6.
- **Cara ukur:** setiap mutasi record stok punya entri `AuditLog` yang bersesuaian; diuji lewat rekonsiliasi berkala.

### T5 — Integritas dokumen penerimaan

- **Baseline:** tidak terjamin. Penerimaan 40 baris = 40–80 transaksi terpisah (`.../input/page.tsx:221-248`); kegagalan sebagian meninggalkan stok separuh terposting; tidak ada idempotency (§1.4).
- **Target:** nol penerimaan terposting sebagian; nol dokumen ganda dari satu surat jalan (dijamin `@@unique([supplierId, supplierDocNumber])`).
- **Cara ukur:** jumlah `GoodsReceipt` berstatus `DRAFT` yang punya pergerakan stok = **0** (invariant yang dimonitor).

### T6 — Selisih stock opname *(target sekunder — hati-hati menjanjikan ini)*

- **Baseline:** hitung dari `reconciliation_items` yang ada: rasio baris `DISCREPANCY` terhadap total, dan nilai absolut `discrepancyQuantity` per sesi (`prisma/schema.prisma:935-954`).
- **Target:** penurunan, **tanpa angka persentase yang dijanjikan di muka.**
- **Mengapa saya menolak memberi angka:** selisih opname berasal dari banyak sebab — barang masuk, barang keluar, kehilangan, kerusakan tak tercatat. Fase 2 hanya menyentuh satu di antaranya. Menjanjikan "selisih opname turun X%" adalah janji yang tidak bisa dipertanggungjawabkan secara teknis. Ukur, laporkan, jangan janjikan angkanya.

> **Kalimat yang aman dan jujur untuk penawaran:** sistem tidak menghilangkan kesalahan manusia; ia memindahkan waktu penemuan kesalahan dari "saat opname bulanan" ke "saat barang masih di depan gudang dan supir supplier masih ada", serta membuat setiap kesalahan punya pelaku, waktu, dan dokumen induk yang jelas.

---

## 8. Ketidakpastian & pertanyaan spesifik untuk Ace

Proses gudang Pridata yang sebenarnya belum terdokumentasi. Di bawah ini rekonstruksi saya dari kode, ditandai jelas sebagai dugaan, beserta pertanyaan yang **hanya pelanggan yang bisa menjawab**. Deliverable ini tidak saya hentikan karenanya — tapi jawaban atas Q1 dapat mengubah rancangan F2-2/F2-3 secara mendasar.

**Rekonstruksi (dugaan, dari struktur data):** operator gudang menerima barang, membuka layar Penerimaan Barang, mengetik nomor referensi dan nama supplier sebagai teks bebas, menambahkan baris per produk dengan mencari nama produk, mengetik qty diterima/bagus/rusak, lalu menyimpan. Sistem mengirim puluhan request terpisah. Selisih terhadap surat jalan — bila diperiksa sama sekali — diperiksa di atas kertas, di luar sistem. Selisih baru muncul di sistem saat opname.

**Q1 — Apakah Pridata membuat Purchase Order resmi ke supplier, atau memesan lewat telepon/WhatsApp?** ⚠️ **Paling kritis.** Bila tidak ada PO sebagai praktik bisnis, F2-2 menghasilkan tabel kosong dan pencocokan 3 arah tidak akan pernah aktif. Rancangan harus berubah menjadi **pencocokan 2 arah** (surat jalan supplier sebagai dokumen ekspektasi yang diinput lebih dulu, lalu hitungan fisik dibandingkan dengannya). Itu tetap menutup akar masalah dan **lebih murah** (F2-2 gugur, hemat 6–10 hari), tapi lebih lemah karena angka ekspektasinya berasal dari supplier, bukan dari Pridata.

**Q2 — Berapa jumlah penerimaan per hari dan berapa baris per surat jalan?** Menentukan apakah biaya friksi §6 dapat ditanggung, dan menentukan ambang approval.

**Q3 — Apakah barang Pridata berbarcode, dan apakah barcodenya konsisten antar supplier?** Menentukan apakah F2-9 layak dan apakah target T2 (70%) realistis atau harus diturunkan.

**Q4 — Apakah ada produk dengan tanggal kedaluwarsa?** Menentukan apakah F2-10 gugur (rekomendasi saya: gugur) atau menjadi wajib. Dampaknya 10–16 hari dan blast radius tertinggi.

**Q5 — Berapa orang yang menangani penerimaan pada jam puncak, dan apakah ada supervisor di lokasi?** Menentukan apakah F2-5 (approval selisih) dapat diadopsi atau akan diakali sejak minggu pertama.

**Q6 — Seberapa sering stock opname dilakukan saat ini?** Diperlukan untuk menetapkan **baseline T1**, yaitu angka yang akan kita janjikan perbaikannya. Tanpa ini, klaim "dari bulanan ke harian" tidak punya dasar.

**Q7 — Apakah barang diterima dalam karton lalu dijual dalam pcs?** Menentukan apakah F2-8 (UOM, item paling berisiko) benar-benar wajib atau dapat ditunda.

Semua pertanyaan ini bersifat customer-facing → **Ace yang memegang komunikasinya**, sesuai batas peran saya.

---

## 9. Catatan untuk Rani

Item ini bukan milik saya, saya hanya menandainya agar tidak hilang:

- `PurchaseOrderLine.unitPrice` (F2-2) membuka kemungkinan pencocokan harga beli (faktur vs PO). Saya sengaja **tidak** menspesifikasikan logika harga, diskon, atau margin.
- Estimasi effort di dokumen ini adalah **hari-orang, bukan harga dan bukan jadwal**. Konversi ke harga, termasuk premi risiko untuk F2-8 dan F2-10, ada di tangan Rani.
- Bila lingkup harus dipotong karena anggaran, urutan rekomendasi saya: pertahankan **F2-6 → F2-1 → F2-3 → F2-4**; item inilah yang menjawab keluhan. F2-8 dan F2-10 keluar duluan.

---

## 10. Temuan yang tidak diminta tapi perlu dicatat

Ditemukan saat verifikasi, tidak termasuk lingkup pertanyaan, tapi relevan bagi mutu produk:

1. **Pengubahan record stok tanpa audit** (`src/controllers/stockAdjustment.controller.ts:155-162`). Ini yang paling serius; sudah masuk F2-6.
2. **Penulisan audit log bersifat best-effort di luar transaksi** (`:62-67`) — bila gagal, stok tetap berubah dan hanya ada `logger.warn`.
3. **Kegagalan parse menyembunyikan penerimaan dari layar** (`services/warehouse-receipts.ts:54`, `:84-86`, `:94`). Nilai `supplier` atau `referenceNumber` yang mengandung `}` akan membuat penerimaan lenyap dari riwayat sementara stoknya tetap masuk.
4. **Daftar penerimaan menarik seluruh riwayat tanpa paginasi** (`app/(dashboard)/gudang/penerimaan-barang/page.tsx:36-41`) — akan melambat seiring bertambahnya data.
5. **Kondisi duplikat pada perhitungan** `item.condition === "DAMAGED" || item.condition === "DAMAGED"` (`services/warehouse-receipts.ts:120` dan `:129`). Tidak berbahaya secara hasil, tapi menandakan kode ini tidak pernah di-review.

Poin 1–3 sebaiknya diperbaiki terlepas dari apakah Fase 2 jadi dijual.
