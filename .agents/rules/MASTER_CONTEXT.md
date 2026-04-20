# Master Context: INSPIRA

> **Activation**: Always On
> **Tujuan**: Fondasi konteks proyek yang wajib dipahami agent sebelum mengerjakan tugas apapun di workspace ini.

---

## Identitas Proyek

| Atribut | Detail |
|---|---|
| **Nama Sistem** | INSPIRA — Intellectual Property Integrated Registration & Administration |
| **Jenis** | Sistem web manajemen pendaftaran Hak Cipta |
| **Platform Pengembangan** | Anti Gravity (Google IDE with Agent) |
| **Model AI** | Gemini (via Anti Gravity) |
| **Penulis** | Mandayash — Tugas Akhir S1, Universitas Pertamina |

---

## Deskripsi Proyek

INSPIRA mengotomatisasi seluruh alur administrasi pendaftaran **Hak Cipta** di lingkungan kampus (Universitas Pertamina). Dua pengguna utama: **Dosen** (pemohon) dan **Admin PPKI** (pengelola).

Yang membuat INSPIRA unik: **seluruh siklus pengembangan perangkat lunaknya** — dari requirement engineering sampai testing — dijalankan oleh agen-agen AI menggunakan arsitektur **Skill-Based Multi-Agent**. Setiap agen punya skill library tersendiri agar tidak boros context window.

---

## Arsitektur: 5 Agen

```
Thin Agent Orchestrator
├── Requirement Engineering Agent
├── Architecture Agent
├── Code Generation Agent
└── Testing Agent
```

| Agen | Peran | Input | Output |
|---|---|---|---|
| **Thin Agent Orchestrator** | Routing trigger → agen yang tepat | Prompt pengguna | Panggilan ke agen spesifik |
| **RE Agent** | Elicitation, user stories, prioritisasi (WSJF/AHP) | Transkrip wawancara, Figma, dokumen DJKI | User stories + prioritas |
| **Architecture Agent** | Konversi user stories → diagram | User stories | UML, ERD, class diagram (PlantUML) |
| **Code Generation Agent** | Generate kode frontend, backend, DB | Spesifikasi arsitektur | Source code |
| **Testing Agent** | Unit test, E2E test, composable testing | Source code | Test suite + hasil |

---

## Skill Library (Anti Gravity)

Semua skill ada di `.agents/skills/`. Setiap skill: `SKILL.md` (instruksi), `examples/` (contoh output).

```
.agents/
├── rules/
│   └── MASTER_CONTEXT.md           ← file ini
└── skills/
    ├── thesis-writing-skill/        ← menulis laporan TA
    ├── elicitation-skill/           ← RE Agent: wawancara + artifact analysis
    ├── user-stories-skill/          ← RE Agent: generate + format user stories
    ├── prioritization-skill/        ← RE Agent: WSJF atau AHP
    ├── srd-documentation-skill/     ← RE Agent: Software Requirements Document (ISO)
    ├── uml-generation-skill/        ← Architecture Agent: use case, class, sequence
    ├── erd-skill/                   ← Architecture Agent: entity-relationship diagram
    ├── frontend-skill/              ← Code Gen Agent: UI components
    ├── backend-skill/               ← Code Gen Agent: API + business logic
    ├── database-skill/              ← Code Gen Agent: schema + migration
    ├── unit-testing-skill/          ← Testing Agent: unit tests
    ├── e2e-testing-skill/           ← Testing Agent: end-to-end tests
    └── composable-testing-skill/    ← Testing Agent: antar-skill compatibility
```

**Progressive Disclosure**: Agent hanya memuat skill yang relevan dengan trigger aktif. Contoh: saat mengerjakan requirement, hanya `elicitation-skill` dan `user-stories-skill` yang dimuat — skill lainnya tidak dibaca.

---

## Scope / Batasan

- **HKI**: Hanya Hak Cipta (bukan merek, paten, desain industri)
- **Pengguna**: Dosen (pemohon) + Admin PPKI (pengelola)
- **AI**: Tidak membuat model baru — menggunakan model existing (Gemini via Anti Gravity)
- **Fase**: RE → Architecture → Code Generation → Testing (tidak mencakup deployment & maintenance)
- **Konteks kampus**: Universitas Pertamina, mengikuti regulasi DJKI

---

## Teknik Pengumpulan Data

1. **Wawancara semi-terstruktur** — dengan admin LPPM/PPKI UP
2. **Analisis Artefak Figma** — via MCP Figma Dev Mode untuk ekstraksi requirement dari desain
3. **Analisis Dokumen DJKI** — alur pendaftaran, template surat, panduan resmi

---

## Anti Gravity Workspace Setup

### Struktur Folder Proyek
```
workspace/
├── .agents/
│   ├── rules/          ← Rules (Always On, Manual, Model Decision)
│   └── skills/         ← Skill library
├── docs/               ← Output dokumen (SRD, arsitektur, dll.)
├── diagrams/           ← PlantUML + generated diagrams
├── src/                ← Generated source code
└── tests/              ← Generated test files
```

### MCP yang Dipakai
- **Figma MCP** — membaca Figma Dev Mode secara real-time untuk requirement elicitation
- **GitHub MCP** (opsional) — untuk version control output agen

### Permission yang Direkomendasikan
```
# Allow list
command(git)
command(python)
read_file(/workspace)
write_file(/workspace/docs)
write_file(/workspace/src)
write_file(/workspace/tests)
mcp(figma/*)
```

---

## Konvensi Bahasa & Istilah

| Gunakan | Jangan Gunakan |
|---|---|
| agen | agent (kecuali nama teknis) |
| perangkat lunak | software |
| rekayasa kebutuhan | requirements engineering |
| basis data | database |
| pengujian | testing |

- Bahasa: **Bahasa Indonesia formal** untuk dokumentasi dan laporan
- Kode: **Bahasa Inggris** untuk variabel, fungsi, komentar kode
- Sitasi laporan: **APA 7th Edition**, paper 2020–2026

---

## Output Akhir yang Diharapkan

1. **INSPIRA Skill Library** — folder skill lengkap untuk semua agen
2. **Thin Agent Orchestrator** — agen routing sederhana
3. **Functional Prototype** — website INSPIRA (tracking revisi, dashboard pengajuan)
4. **Dokumen SDLC** — SRD, diagram arsitektur, source code, hasil testing
5. **Laporan Tugas Akhir** — skripsi S1 tentang implementasi ini

---

## File Referensi Penting

| Tipe | File |
|---|---|
| Skill menulis laporan | `.agents/skills/thesis-writing-skill/SKILL.md` |
| Transkrip wawancara | `User Interview INSPIRA.pdf` |
| Panduan ejaan | `PUEBI Panduan Ejaan Bahasa Indonesia.pdf` |
| Paper skill-based AI | `W8-*.pdf` (Agent Skills, Knowledge Activation, SWE-Skills-Bench) |
| Paper multi-agent | `W1-*.pdf`, `W3-*.pdf`, `W6-METAGPT*.pdf` |
| Dokumentasi Anti Gravity | `2-*.pdf` s/d `13-*.pdf` |
