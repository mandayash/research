# SKILL: Bab 4.1 — Analisis Kebutuhan Sistem (RE Agent)

## Identitas Skill

| Atribut | Detail |
|---|---|
| **Nama Skill** | bab4-re-agent-skill |
| **Versi** | 1.0 |
| **Subbab Target** | 4.1 Analisis Kebutuhan Sistem |
| **Format Output** | LaTeX (`.tex`) |
| **Sumber Input** | Output Requirement Engineering Agent INSPIRA |
| **Bergantung Pada** | `thesis-writing-skill` (panduan gaya bahasa & sitasi) |

---

## Kapan Digunakan

Aktifkan skill ini saat:
- Output RE Agent sudah tersedia (user stories, tabel prioritisasi, atau transkrip wawancara)
- Diminta menulis, draft, atau merevisi subbab **4.1 Analisis Kebutuhan Sistem**
- Perlu mengonversi data mentah agen menjadi narasi akademik LaTeX

**Prasyarat input yang ideal:**
- `docs/requirements/user_stories.md` — daftar user stories hasil elicitation
- `docs/requirements/priority_table.md` atau output JSON/CSV dari WSJF/AHP
- Catatan wawancara / pain points dari admin PPKI (minimal poin-poin utamanya)

---

## Struktur Subbab yang Dihasilkan

```
4.1 Analisis Kebutuhan Sistem
  4.1.1 Proses Pengumpulan Kebutuhan
  4.1.2 Hasil Elicitation: User Stories
  4.1.3 Prioritisasi Kebutuhan
  4.1.4 Evaluasi dan Validasi
```

---

## Langkah Kerja

### Langkah 1 — Baca Input

Baca secara penuh:
1. `docs/requirements/user_stories.md`
2. `docs/requirements/priority_table.md` (WSJF atau AHP)
3. Catatan wawancara atau ringkasan pain points (jika tersedia)
4. `thesis-writing-skill/SKILL.md` → bagian **Panduan Penulisan Umum** dan **BAB 4**

### Langkah 2 — Susun Narasi 4.1.1: Proses Pengumpulan Kebutuhan

Tulis paragraf yang menceritakan:
- Bagaimana RE Agent menerima trigger awal (wawancara + Figma)
- Skill mana yang aktif: `interview-extraction-skill`, `figma-extraction-skill`, atau sejenisnya
- Apa yang diekstrak: pain points, alur proses manual, aktor yang terlibat
- Kaitkan ke proses bisnis DJKI yang sudah dijelaskan di Bab 2

> **Catatan:** Jangan sekadar daftar ulang pain points — ceritakan sebagai temuan yang kontekstual. Contoh: "Dari hasil wawancara dengan admin PPKI, teridentifikasi bahwa proses pengecekan kelengkapan dokumen dilakukan secara manual dan membutuhkan waktu rata-rata 3–5 hari kerja."

**LaTeX yang dihasilkan untuk bagian ini:**
```latex
\subsubsection{Proses Pengumpulan Kebutuhan}
% narasi 3-5 paragraf
% sertakan \begin{figure} jika ada screenshot Figma atau foto wawancara
```

### Langkah 3 — Susun Narasi 4.1.2: Hasil Elicitation — User Stories

Tampilkan user stories dalam dua cara:
1. **Narasi ringkas** — jelaskan berapa total user stories, dibagi ke aktor mana saja (Dosen vs Admin PPKI), dan skill apa yang menghasilkannya
2. **Tabel LaTeX** — tampilkan semua user stories dalam format tabel

**Template tabel user stories:**
```latex
\begin{longtable}{|p{0.5cm}|p{2.5cm}|p{8cm}|p{2.5cm}|}
\hline
\textbf{No} & \textbf{Aktor} & \textbf{User Story} & \textbf{Prioritas} \\
\hline
\endfirsthead
\hline
\textbf{No} & \textbf{Aktor} & \textbf{User Story} & \textbf{Prioritas} \\
\hline
\endhead
1 & Dosen & Sebagai dosen, saya ingin mengajukan permohonan Hak Cipta secara daring agar tidak perlu datang ke kantor PPKI secara langsung. & Tinggi \\
\hline
% ... baris lainnya
\caption{Daftar User Stories Hasil Elicitation RE Agent}
\label{tab:user_stories}
\end{longtable}
```

Setelah tabel, tulis paragraf penjelas: apa pola yang terlihat, user stories mana yang paling banyak muncul, apakah ada user stories yang awalnya ambigu dan harus diklarifikasi.

### Langkah 4 — Susun Narasi 4.1.3: Prioritisasi Kebutuhan

Jelaskan metode yang digunakan (AHP atau WSJF), lalu tampilkan hasilnya.

#### Jika AHP:

```latex
\subsubsection{Prioritisasi Kebutuhan dengan AHP}

% Narasi: jelaskan kriteria yang digunakan dalam AHP
% (misal: complexity, business value, risk, dependency)

\begin{table}[H]
\centering
\caption{Matriks Perbandingan Berpasangan AHP}
\label{tab:ahp_matrix}
\begin{tabular}{|l|c|c|c|c|}
\hline
\textbf{Kriteria} & \textbf{Business Value} & \textbf{Complexity} & \textbf{Risk} & \textbf{Dependency} \\
\hline
Business Value & 1 & 3 & 5 & 2 \\
Complexity     & 1/3 & 1 & 2 & 1/2 \\
Risk           & 1/5 & 1/2 & 1 & 1/3 \\
Dependency     & 1/2 & 2 & 3 & 1 \\
\hline
\end{tabular}
\end{table}

% Tabel hasil prioritas akhir
\begin{table}[H]
\centering
\caption{Hasil Prioritisasi User Stories dengan AHP}
\label{tab:ahp_result}
\begin{tabular}{|p{0.5cm}|p{7cm}|c|c|}
\hline
\textbf{No} & \textbf{User Story} & \textbf{Skor AHP} & \textbf{Prioritas} \\
\hline
% ... isi dengan data dari output RE Agent
\hline
\end{tabular}
\end{table}
```

#### Jika WSJF:

```latex
\subsubsection{Prioritisasi Kebutuhan dengan WSJF}

% Narasi: jelaskan komponen WSJF (CoD, RR/OE, RR/TR, Job Size)

\begin{table}[H]
\centering
\caption{Hasil Prioritisasi User Stories dengan WSJF}
\label{tab:wsjf_result}
\begin{tabular}{|p{4cm}|c|c|c|c|c|}
\hline
\textbf{User Story} & \textbf{CoD} & \textbf{RR/OE} & \textbf{RR/TR} & \textbf{Job Size} & \textbf{WSJF} \\
\hline
% ...
\hline
\end{tabular}
\end{table}
```

Setelah tabel, tulis analisis: top 5 user stories berdasarkan prioritas, mengapa mereka diprioritaskan, dan bagaimana urutan ini memengaruhi tahap arsitektur.

### Langkah 5 — Susun Narasi 4.1.4: Evaluasi dan Validasi

Tulis paragraf tentang:
- Siapa yang mengevaluasi output RE Agent (ahli domain, dosen pembimbing, atau admin PPKI)
- Apa yang diubah setelah review (user stories yang ditambah/dibuang/direvisi)
- Apakah output RE Agent konsisten dengan kebutuhan nyata yang ditemukan di lapangan
- Kaitkan ke research question: apakah RE Agent berhasil mengotomatisasi tahap ini?

---

## Elemen LaTeX yang Digunakan

| Elemen | Package | Keterangan |
|---|---|---|
| Tabel panjang (user stories) | `longtable` | Untuk tabel yang melewati satu halaman |
| Tabel pendek (AHP/WSJF) | `tabularx`, `booktabs` | Untuk tabel yang muat satu halaman |
| Gambar (screenshot, flowchart) | `graphicx`, `float` | `[H]` untuk posisi tepat |
| Flowchart proses | `tikz` + `pgf` | Gambar langsung di LaTeX, atau PNG dari draw.io |
| Kode/output agen | `listings` atau `minted` | Untuk menampilkan potongan JSON output agen |

### Preamble yang Dibutuhkan

```latex
\usepackage{longtable}
\usepackage{tabularx}
\usepackage{booktabs}
\usepackage{graphicx}
\usepackage{float}
\usepackage{listings}
\usepackage{xcolor}
```

### Cara Include Gambar

```latex
\begin{figure}[H]
  \centering
  \includegraphics[width=0.85\textwidth]{images/re-agent-flow.png}
  \caption{Alur Kerja Requirement Engineering Agent pada Proses Elicitation}
  \label{fig:re_agent_flow}
\end{figure}
```

> Nama file gambar menggunakan `kebab-case`. Simpan di folder `images/` relatif terhadap file `.tex`.

### Cara Menampilkan Output JSON Agen (opsional)

```latex
\begin{lstlisting}[language=json, caption={Contoh Output User Story dari RE Agent}, label={lst:re_output}]
{
  "id": "US-001",
  "actor": "Dosen",
  "story": "Sebagai dosen, saya ingin mengajukan Hak Cipta secara daring...",
  "priority": "high",
  "wsjf_score": 8.4
}
\end{lstlisting}
```

---

## Konvensi Penulisan

- Setiap tabel dan gambar **wajib diacu** dalam paragraf sebelumnya. Contoh: "... seperti yang ditampilkan pada Tabel \ref{tab:user_stories}."
- Gunakan `\label{}` yang konsisten: `tab:` untuk tabel, `fig:` untuk gambar, `lst:` untuk listing
- Angka dalam teks ditulis dengan kata jika kurang dari 10 (kecuali data numerik), contoh: "tiga aktor utama", "17 user stories"
- Tidak ada tabel atau gambar tanpa `\caption{}` dan `\label{}`

---

## Checklist Output

Sebelum selesai, pastikan subbab 4.1 sudah mencakup:

- [ ] Narasi bagaimana kebutuhan dikumpulkan (wawancara + Figma/dokumen DJKI)
- [ ] Tabel user stories lengkap dengan kolom: No, Aktor, User Story, Prioritas
- [ ] Tabel atau matriks prioritisasi (AHP atau WSJF) dengan data nyata dari output agen
- [ ] Analisis hasil prioritisasi (bukan sekadar tampilkan tabel)
- [ ] Paragraf evaluasi/validasi dengan expert
- [ ] Semua gambar dan tabel sudah diacu dalam teks
- [ ] Label LaTeX konsisten

---

## Batasan

- Skill ini hanya untuk subbab 4.1 — jangan menulis bagian 4.2 dst. di sini
- Jika data wawancara atau output agen belum tersedia, tandai dengan `% TODO: isi dengan data nyata` dalam LaTeX dan lanjutkan dengan placeholder
- Jika metode prioritisasi berbeda dari AHP/WSJF, sesuaikan struktur tabel tapi pertahankan narasi analisisnya
