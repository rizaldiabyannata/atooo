---
name: "Baseline biaya & harga normal ERP untuk pasar NTB"
assignee: "rani"
project: "onboarding"
---

## Konteks

Ato-team membangun sistem ERP/SMD untuk **CV Pridata Jaya**, distributor di Mataram (NTB), dan sekarang ingin menjual sistem itu kepada mereka. Pridata akan mendapat **diskon 50%** karena sistem ini dibuat sekaligus sebagai bahan penelitian. Masalahnya: belum ada harga "normal" yang jadi acuan, jadi diskon 50% itu belum punya dasar apa pun.

Tugasmu: **buat dasarnya.**

## Yang harus dihasilkan

Satu dokumen (issue document, key `analysis`) berisi:

1. **Rekonstruksi biaya bangun.** Tidak ada timesheet. Pakai lensa *effort-weighted feature costing*: bobot 47 fitur terkirim per level kesulitan, kalikan rate orang-hari yang kamu pertahankan, publikasikan bobot dan rate-nya.
2. **Biaya berjalan per tahun** — infrastruktur (server, object storage, Redis, DB), support, dan pemeliharaan.
3. **Harga list "normal"** untuk distributor lain seukuran Pridata di NTB, dengan isi paket yang jelas.
4. **Total biaya kepemilikan Tahun 1 / 2 / 3** untuk pembeli.
5. **Lantai walk-away** — harga terendah yang masih masuk akal.
6. **Struktur diskon mitra riset 50%** — bukan angka saja, tapi apa yang ditukar untuk itu (lihat "Timbal balik" di bawah), dan bagaimana diskon ini di-*ring-fence*
