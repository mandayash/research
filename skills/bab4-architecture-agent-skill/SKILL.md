# SKILL: Bab 4.2 — Perancangan Sistem (Architecture Agent)

## Identitas Skill

| Atribut | Detail |
|---|---|
| **Nama Skill** | bab4-architecture-agent-skill |
| **Versi** | 1.0 |
| **Subbab Target** | 4.2 Perancangan Sistem |
| **Format Output** | LaTeX (`.tex`) |
| **Sumber Input** | Output Architecture Agent INSPIRA |
| **Bergantung Pada** | `bab4-re-agent-skill` (hasil 4.1 sebagai konteks), `thesis-writing-skill` |
| **Tool Diagram** | PlantUML → PNG/PDF, atau draw.io → PNG |

---

## Kapan Digunakan

Aktifkan skill ini saat:
- Output Architecture Agent sudah tersedia (minimal: system design doc + satu diagram UML)
- Diminta menulis, draft, atau merevisi subbab **4.2 Perancangan Sistem**
- Perlu mengonversi diagram dan spesifikasi arsitektur menjadi narasi akademik LaTeX

**Prasyarat input yang ideal:**
- `docs/architecture/system_design.md` — spesifikasi arsitektur teks
- `docs/architecture/diagrams/usecase.puml` — Use Case Diagram
- `docs/architecture/diagrams/erd.puml` atau `erd.png` — Entity Relationship Diagram
- `docs/architecture/diagrams/sequence_*.puml` — Sequence Diagram (opsional tapi dianjurkan)
- `docs/architecture/diagrams/class.puml` — Class Diagram (opsional)

---

## Struktur Subbab yang Dihasilkan

```
4.2 Perancangan Sistem
  4.2.1 Alur Kerja Architecture Agent
  4.2.2 Arsitektur Sistem INSPIRA
  4.2.3 Diagram Use Case
  4.2.4 Perancangan Basis Data (ERD)
  4.2.5 Diagram Sequence (Alur Fungsional Utama)
  4.2.6 Evaluasi Hasil Perancangan
```

> Sesuaikan subchapter yang ada dengan diagram yang benar-benar dihasilkan oleh agen. Jika class diagram tidak ada, lewati 4.2.5 dan lanjutkan ke evaluasi.

---

## Langkah Kerja

### Langkah 1 — Baca Input

1. `docs/architecture/system_design.md`
2. Semua file `.puml` atau gambar diagram yang tersedia
3. Output Bab 4.1 (untuk memastikan koneksi narasi user stories → arsitektur)
4. `thesis-writing-skill/SKILL.md` → bagian BAB 4

### Langkah 2 — Susun Narasi 4.2.1: Alur Kerja Architecture Agent

Ceritakan bagaimana Architecture Agent bekerja:
- Skill mana yang aktif: `system-design-skill`, `uml-generation-skill`, `erd-generation-skill`
- Input yang diterima: user stories dari RE Agent
- Proses transformasi: user stories → spesifikasi teks → diagram
- Tool yang digunakan: PlantUML, Prisma (untuk ERD), dll.

**Sertakan flowchart alur kerja agen ini:**

```latex
\subsubsection{Alur Kerja \textit{Architecture Agent}}

% Narasi 2-3 paragraf

\begin{figure}[H]
  \centering
  \includegraphics[width=0.80\textwidth]{images/architecture-agent-flow.png}
  \caption{Alur Kerja \textit{Architecture Agent} dalam Menghasilkan Artefak Perancangan}
  \label{fig:arch_agent_flow}
\end{figure}

% Narasi penjelas gambar
```

> Buat flowchart ini dengan draw.io atau TikZ. Alurnya: Terima User Stories → Aktifkan system-design-skill → Generate spesifikasi teks → Aktifkan uml-generation-skill → Generate PlantUML → Render diagram → Output ke docs/architecture/

### Langkah 3 — Susun Narasi 4.2.2: Arsitektur Sistem INSPIRA

Jelaskan arsitektur keseluruhan sistem INSPIRA (bukan arsitektur agen — itu ada di Bab 3):
- Arsitektur layered: Frontend (Next.js/React) → Backend API (Express + TypeScript) → Database (PostgreSQL)
- Komponen utama dan tanggung jawabnya
- Pola komunikasi antar komponen (REST API, Prisma ORM)
- Keputusan arsitektur penting: kenapa layered? kenapa tech stack ini?

```latex
\subsubsection{Arsitektur Sistem INSPIRA}

% Narasi 3-4 paragraf

\begin{figure}[H]
  \centering
  \includegraphics[width=0.90\textwidth]{images/system-architecture.png}
  \caption{Arsitektur Komponen Sistem INSPIRA}
  \label{fig:system_architecture}
\end{figure}

% Tabel komponen (opsional tapi dianjurkan)
\begin{table}[H]
\centering
\caption{Komponen Utama Arsitektur INSPIRA}
\label{tab:arch_components}
\begin{tabularx}{\textwidth}{|l|l|X|}
\hline
\textbf{Layer} & \textbf{Teknologi} & \textbf{Tanggung Jawab} \\
\hline
Frontend & Next.js, TypeScript & Antarmuka pengguna, routing halaman, state management \\
\hline
Backend API & Express.js, TypeScript & Business logic, validasi, autentikasi (JWT) \\
\hline
ORM & Prisma & Abstraksi query database, type-safe access \\
\hline
Database & PostgreSQL & Penyimpanan data permanen \\
\hline
\end{tabularx}
\end{table}
```

### Langkah 4 — Susun Narasi 4.2.3: Diagram Use Case

Tampilkan use case diagram dan jelaskan setiap use case utama.

```latex
\subsubsection{Diagram \textit{Use Case}}

% Narasi: berapa aktor, berapa use case, apa yang dicakup

\begin{figure}[H]
  \centering
  \includegraphics[width=0.85\textwidth]{images/usecase-diagram.png}
  \caption{Diagram \textit{Use Case} Sistem INSPIRA}
  \label{fig:usecase}
\end{figure}

% Tabel deskripsi use case
\begin{longtable}{|p{0.5cm}|p{3cm}|p{2.5cm}|p{7cm}|}
\hline
\textbf{No} & \textbf{Nama Use Case} & \textbf{Aktor} & \textbf{Deskripsi} \\
\hline
\endfirsthead
\hline
\textbf{No} & \textbf{Nama Use Case} & \textbf{Aktor} & \textbf{Deskripsi} \\
\hline
\endhead
1 & Mengajukan Permohonan & Dosen & Dosen mengisi formulir pengajuan Hak Cipta dan mengunggah dokumen pendukung \\
\hline
2 & Memverifikasi Dokumen & Admin PPKI & Admin memeriksa kelengkapan dan keabsahan dokumen yang diunggah \\
\hline
% ... isi dari output Architecture Agent
\caption{Deskripsi Use Case Sistem INSPIRA}
\label{tab:usecase_desc}
\end{longtable}
```

Setelah tabel, tulis paragraf: pola yang terlihat dari use case, hubungan `<<include>>` atau `<<extend>>` yang ada, dan bagaimana ini mencerminkan kebutuhan dari 4.1.

### Langkah 5 — Susun Narasi 4.2.4: Perancangan Basis Data (ERD)

```latex
\subsubsection{Perancangan Basis Data}

% Narasi: berapa entitas, relasi utama, keputusan normalisasi

\begin{figure}[H]
  \centering
  \includegraphics[width=\textwidth]{images/erd.png}
  \caption{Entity Relationship Diagram (ERD) Sistem INSPIRA}
  \label{fig:erd}
\end{figure}
```

Setelah gambar ERD, sertakan tabel deskripsi entitas:

```latex
\begin{table}[H]
\centering
\caption{Deskripsi Entitas Utama Basis Data INSPIRA}
\label{tab:entities}
\begin{tabularx}{\textwidth}{|l|X|l|}
\hline
\textbf{Entitas} & \textbf{Deskripsi} & \textbf{Primary Key} \\
\hline
User & Menyimpan data pengguna (Dosen dan Admin PPKI) & user\_id \\
\hline
Submission & Menyimpan data permohonan Hak Cipta & submission\_id \\
\hline
Document & File yang diunggah untuk satu permohonan & document\_id \\
\hline
% ... sesuaikan dengan ERD nyata dari Architecture Agent
\hline
\end{tabularx}
\end{table}
```

### Langkah 6 — Susun Narasi 4.2.5: Diagram Sequence (jika tersedia)

Pilih 2–3 alur fungsional paling penting untuk ditampilkan sequence diagram-nya. Kandidat utama:
1. Alur pengajuan permohonan baru (Dosen → System → DB)
2. Alur verifikasi dokumen (Admin → System → Notifikasi Dosen)
3. Alur autentikasi (Login JWT)

```latex
\subsubsection{Diagram \textit{Sequence} Alur Pengajuan Permohonan}

% Narasi singkat sebelum diagram

\begin{figure}[H]
  \centering
  \includegraphics[width=0.90\textwidth]{images/sequence-submission.png}
  \caption{Diagram \textit{Sequence} Proses Pengajuan Permohonan Hak Cipta}
  \label{fig:seq_submission}
\end{figure}

% Narasi penjelas: langkah-langkah yang terjadi sesuai diagram
```

### Langkah 7 — Susun Narasi 4.2.6: Evaluasi Hasil Perancangan

Tulis paragraf tentang:
- Siapa yang mengevaluasi output Architecture Agent
- Apa yang direvisi (misalnya: ERD yang awalnya tidak ternormalisasi, use case yang redundan)
- Kesesuaian antara output agen dengan standar arsitektur yang diharapkan
- Kaitkan ke research question: apakah Architecture Agent berhasil mengotomatisasi tahap perancangan?

---

## Cara Menghasilkan Gambar dari PlantUML

Jika diagram masih dalam format `.puml`, render dulu ke PNG sebelum di-include ke LaTeX:

```bash
# Install PlantUML (butuh Java)
java -jar plantuml.jar docs/architecture/diagrams/usecase.puml -o images/

# Atau via Docker
docker run --rm -v $(pwd):/data plantuml/plantuml -tpng /data/docs/architecture/diagrams/usecase.puml
```

Simpan semua PNG hasil render ke folder `images/` di root proyek LaTeX.

### Cara Membuat Flowchart dengan TikZ (alternatif draw.io)

```latex
\usepackage{tikz}
\usetikzlibrary{shapes.geometric, arrows, positioning}

\tikzstyle{startstop} = [rectangle, rounded corners, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=blue!20]
\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=orange!20]
\tikzstyle{decision} = [diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=green!20]
\tikzstyle{arrow} = [thick,->,>=stealth]

\begin{figure}[H]
\centering
\begin{tikzpicture}[node distance=1.5cm]
\node (start) [startstop] {Terima User Stories};
\node (design) [process, below of=start] {Aktifkan system-design-skill};
\node (uml) [process, below of=design] {Generate UML dengan PlantUML};
\node (erd) [process, below of=uml] {Generate ERD};
\node (eval) [decision, below of=erd, yshift=-0.5cm] {Valid?};
\node (revise) [process, right of=eval, xshift=3cm] {Revisi Spesifikasi};
\node (output) [startstop, below of=eval, yshift=-0.5cm] {Output ke docs/architecture/};

\draw [arrow] (start) -- (design);
\draw [arrow] (design) -- (uml);
\draw [arrow] (uml) -- (erd);
\draw [arrow] (erd) -- (eval);
\draw [arrow] (eval) -- node[anchor=east] {Ya} (output);
\draw [arrow] (eval) -- node[anchor=south] {Tidak} (revise);
\draw [arrow] (revise) |- (design);
\end{tikzpicture}
\caption{Alur Kerja \textit{Architecture Agent}}
\label{fig:arch_agent_tikz}
\end{figure}
```

---

## Elemen LaTeX yang Digunakan

| Elemen | Package | Keterangan |
|---|---|---|
| Gambar diagram | `graphicx`, `float` | `[H]` wajib untuk posisi |
| Tabel komponen | `tabularx`, `booktabs` | Lebar kolom fleksibel |
| Tabel panjang use case | `longtable` | Untuk tabel multi-halaman |
| Flowchart | `tikz`, `pgf` | Langsung di LaTeX |
| Kode PlantUML (opsional) | `listings` | Jika perlu tampilkan source diagram |

### Preamble yang Dibutuhkan

```latex
\usepackage{graphicx}
\usepackage{float}
\usepackage{tabularx}
\usepackage{booktabs}
\usepackage{longtable}
\usepackage{tikz}
\usetikzlibrary{shapes.geometric, arrows, positioning}
\usepackage{listings}
```

---

## Konvensi Penulisan

- Istilah teknis bahasa Inggris dicetak miring pada kemunculan pertama: *use case*, *sequence diagram*, *entity*, *foreign key*
- Nama tabel/entitas basis data ditulis dalam `monospace` menggunakan `\texttt{}`
- Setiap gambar harus diacu: "... ditunjukkan pada Gambar~\ref{fig:usecase}." (gunakan `~` sebelum `\ref` untuk menghindari line break)
- Caption gambar: kalimat deskriptif, bukan sekadar nama diagram
- Jangan tampilkan seluruh isi `system_design.md` — pilih informasi yang paling relevan untuk pembaca laporan

---

## Checklist Output

Sebelum selesai, pastikan subbab 4.2 sudah mencakup:

- [ ] Narasi alur kerja Architecture Agent (dengan flowchart)
- [ ] Penjelasan arsitektur sistem INSPIRA (layered) + tabel komponen
- [ ] Use Case Diagram + tabel deskripsi use case
- [ ] ERD + tabel deskripsi entitas
- [ ] Minimal satu Sequence Diagram untuk alur utama
- [ ] Paragraf evaluasi/validasi hasil perancangan
- [ ] Semua gambar dan tabel sudah diacu dalam teks
- [ ] File gambar ada di folder `images/` dan nama sesuai `\includegraphics{}`
- [ ] Label LaTeX konsisten (`fig:`, `tab:`, `lst:`)

---

## Batasan

- Skill ini hanya untuk subbab 4.2 — jangan menulis 4.1 atau 4.3 di sini
- Jika diagram belum dirender dari `.puml`, tandai dengan `% TODO: render dari usecase.puml` dan lanjutkan dengan struktur LaTeX yang sudah siap
- Class diagram bersifat opsional — sertakan hanya jika Architecture Agent benar-benar menghasilkannya
- Jangan mengarang arsitektur yang tidak ada di `system_design.md` — gunakan `% TODO:` jika data belum tersedia
