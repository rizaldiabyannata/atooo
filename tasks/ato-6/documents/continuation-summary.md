# Continuation Summary

- Issue: ATO-6 — Price list resmi NTB bertanggal — prasyarat sebelum penawaran Pridata dikirim
- Status: done
- Priority: high
- Current mode: review
- Last updated by run: d1f0501e-ca97-4cb0-bf10-963d0c8fa3db
- Agent: Ace (claude_local)

## Objective

## Kenapa tugas ini ada

Klausul ring-fence #1 di [ATO-2 · analysis](/ATO/issues/ATO-2#document-analysis) menyebut ini sebagai item aksi untuk Ace, bukan sekadar klausul kontrak:

> Harga list Rp 175.000.000 + Rp 54.000.000/tahun harus terbit sebagai price list bertanggal — dalam proposal standar, materi penjualan, dan situs — **sebelum** penawaran Pridata dikirim. Kalau list hanya ada di dokumen internal, diskon 50% tidak punya jangkar dan hanya menjadi harga yang diminta pembeli.

Diskon 50% untuk Pridata hanya bermakna kalau ada harga acuan yang terbit lebih dulu dan bertanggal. Tanpa itu, Rp 87.500.000 bukan diskon — itu harga.

## Yang harus dihasilkan

Dokumen price list menghadap-pelanggan (issue document, key `pricelist`), Bahasa Indonesia, bertanggal, siap dipakai di proposal standar dan materi penjualan:

1. Harga list Tahun 1 dan ASC tahunan, dengan rincian komponen.
2. Isi paket — 47 fitur dikelompokkan per fungsi bisnis.
3. Batas ruang lingkup: apa yang tidak termasuk dan bagaimana dihargai.
4. Tingkatan SLA dan yang dijanjikan di tiap tingkat.
5. Masa berlaku harga dan aturan indeksasi.
6. Pernyataan program diskon bertanggal dan tertutup (Program
[truncated]

## Acceptance Criteria

No explicit acceptance criteria captured.

## Recent Concrete Actions

- Run `d1f0501e-ca97-4cb0-bf10-963d0c8fa3db` finished with status `succeeded` at 2026-09-29T05:09:51.741Z.
- **ATO-6 selesai.** Keempat jawaban Anda sudah dijalankan.

**Diterbitkan apa adanya.** Dokumen `pricelist` (NTB-PL-2026-09, 29 September 2026) tidak saya sentuh — nol perubahan.

**Kanal: template proposal standar.** Saya buat **PROP-TPL-NTB-2026-09** — template proposal standar yang terikat pada daftar harga itu, tersimpan sebagai dokumen `proposal-template` di ATO-6 dan diunggah sebagai artifact. Isinya proposal lengkap dengan placeholder pembeli, plus satu halaman aturan pengisian internal yang mengunci empat hal: setiap proposal wajib melampirkan daftar harga utuh, persentase potongan tidak pernah ditulis (hanya baris rupiah terpisah), tidak ada angka Fase 2, dan syarat komersial satu mitra tidak boleh pindah ke proposal pembeli lain. Ring-fence #2 sekarang jadi bagian dari borang, bukan sekadar niat.

Ketentuan komersial yang Anda konfirmasi masuk tanpa perubahan.

**Satu catatan soal kanal.** Ring-fence #1 menyebut tiga kanal; Anda pilih satu. Itu cukup memenuhi fungsinya — asalkan setiap proposal NTB memakai template ini, termasuk proposal Pridata. Yang hilang: list tidak bisa diverifikasi pihak yang belum menerima proposal. Memasangnya di situs nanti tid
[truncated]

## Files / Routes Touched

- No file or route paths were detected in the captured run summary.

## Commands Run

- Heartbeat run `d1f0501e-ca97-4cb0-bf10-963d0c8fa3db` invoked adapter `claude_local`.
- Detailed shell/tool commands remain in the run log and transcript.

## Blockers / Decisions

- No new blocker was recorded by the latest run.

## Next Action

- Review the completed issue output and close any remaining follow-up comments.