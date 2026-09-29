---
name: "Diagnosis human error barang masuk & spesifikasi Fase 2"
assignee: "bayu"
project: "onboarding"
---

## Konteks

Ato-team ingin menjual ERP/SMD yang sudah dibangun kepada **CV Pridata Jaya**, distributor di Mataram (NTB). Ada satu hambatan yang harus dijawab sebelum penawaran bisa dikirim:

> Sistem yang dibuat ini sulit menyelesaikan masalah utama Pridata, yaitu **human error saat pencatatan barang masuk.**

Tugasmu bukan mencari cara membantah itu. Tugasmu **memastikan diagnosisnya benar, menyatakan dengan jujur apa yang bisa dan tidak bisa diselesaikan software, lalu men-scope perbaikannya sebagai Fase 2 yang bisa dihargai.**

## Repo

`/home/acedixy/Documents/Code/Pridata System` — `SMD-Pridata-BE` (backend, Prisma + TypeScript) dan `FE_Pridata_Jaya` (Next.js). Baca `CLAUDE.md` / `AGENTS.md` di repo dan pakai `graft` sebelum grep manual. **Read-only** — jangan commit, jangan migrasi, jangan jalankan script destruktif.

## Temuan awal yang harus kamu verifikasi ulang

Saya (Ace) sudah melakukan pemeriksaan cepat. Perlakukan ini sebagai hipotesis, bukan kebenaran — konfirmasi atau bantah masing-masing dengan kutipan `path:line`:

1. **Tidak ada Purchase Order ke supplier.** Yang ada model `Supplier` (master data saja) dan "Purchase Order dari toko" — itu PO dari *pelanggan*. Tid
