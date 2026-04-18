# SKILL: Menulis Laporan Tugas Akhir INSPIRA

## Identitas Skill

| Atribut | Detail |
|---|---|
| **Nama Skill** | thesis-writing-skill |
| **Versi** | 1.0 |
| **Konteks Proyek** | INSPIRA — Intellectual Property Integrated Registration & Administration |
| **Penulis** | Mandayash |
| **Style Sitasi** | APA 7th Edition |
| **Rentang Paper** | 2020–2026 |
| **Bahasa** | Bahasa Indonesia (formal akademik, tidak kaku) |

---

## Deskripsi Singkat

Skill ini berisi instruksi prosedural untuk menulis laporan tugas akhir (skripsi S1) proyek INSPIRA secara bagian demi bagian. INSPIRA adalah sistem manajemen pendaftaran Hak Cipta berbasis web yang dibangun menggunakan arsitektur multi-agent Skill-Based AI — mencakup empat agen utama (Requirement Engineering, Architecture, Code Generation, Testing) dan satu Thin Agent Orchestrator.

Gunakan skill ini setiap kali diminta menulis atau merevisi bagian tertentu dari laporan. Output harus terasa seperti ditulis oleh manusia — akademis tapi tetap mengalir, bukan seperti template yang diisi otomatis.

---

## Konteks Proyek (Wajib Dipahami Sebelum Menulis)

### Judul (Pilihan Pertama)
> Implementasi Arsitektur Multi-Agen Berbasis Keahlian (Skill-Based AI) untuk Otomatisasi Siklus Hidup Pengembangan Perangkat Lunak Sistem Permohonan Hak Cipta

### Ringkasan Proyek

INSPIRA dirancang untuk **mengotomatisasi seluruh alur administrasi pendaftaran Hak Cipta** di lingkungan kampus (khususnya Universitas Pertamina). Pengguna utamanya ada dua: **Dosen** (pemohon) dan **Admin PPKI** (pengelola).

Sistem ini unik karena **seluruh siklus pengembangan perangkat lunaknya** — mulai dari requirement elicitation sampai testing — dijalankan oleh agen-agen AI. Setiap agen punya skill library tersendiri agar tidak boros context window dan outputnya tidak ambigu.

### Empat Agen + Orkestrasi

| Agen | Peran Utama |
|---|---|
| **Requirement Engineering Agent** | Elicitation, user stories, prioritisasi (WSJF/AHP) |
| **Architecture Agent** | Konversi user stories → UML, ERD, arsitektur sistem |
| **Code Generation Agent** | Generate kode frontend, backend, database |
| **Testing Agent** | Unit testing, end-to-end testing, composable testing |
| **Thin Agent Orchestrator** | Manajer: menerima trigger dan memanggil agen yang tepat |

### Struktur Skill Library
Setiap skill memiliki tiga komponen:
- `SKILL.md` — instruksi prosedural (apa yang harus dilakukan dan bagaimana)
- `tools/` — skrip Python/Bash untuk eksekusi (validasi, ekstraksi, dll.)
- `examples/` — contoh output yang diharapkan

### Ruang Lingkup yang Perlu Diingat
- Hanya mencakup Hak Cipta (bukan merek, paten, atau desain industri)
- Tidak mencakup fase maintenance jangka panjang
- Tidak membuat model AI baru — menggunakan model yang sudah ada (OpenAI, Google, dll.)
- Pengembangan AI hanya sampai tahap testing

---

## Struktur Laporan

Laporan terdiri dari empat bab utama:

```
Bab 1 — Pendahuluan
  1.1 Latar Belakang
  1.2 Rumusan Masalah
  1.3 Tujuan Penelitian
  1.4 Batasan Masalah
  1.5 Manfaat Penelitian

Bab 2 — Tinjauan Pustaka
  2.1 Manajemen Hak Kekayaan Intelektual (HKI)
  2.2 LLM dalam Rekayasa Perangkat Lunak
  2.3 Arsitektur Agen Modular (Multi-Agent)
  2.4 Pendekatan Skill-Based AI
  2.5 Penelitian Terdahulu

Bab 3 — Metodologi Penelitian
  3.1 Alur Penelitian
  3.2 Teknik Pengumpulan Data
  3.3 Rancangan Arsitektur AI

Bab 4 — Hasil dan Pembahasan
  4.1 Analisis Kebutuhan Sistem (Kerja RE Agent)
  4.2 Perancangan Sistem (Kerja Architecting Agent)
  4.3 Implementasi Skill Library
  4.4 Tampilan dan Penjelasan Fungsional INSPIRA
  4.5 Pengujian Sistem (Kerja Test Agent & QA)
```

---

## Panduan Penulisan Umum

### Tone dan Gaya Bahasa
- Tulis seperti mahasiswa yang **benar-benar paham proyeknya**, bukan seperti AI yang mengisi template
- Kalimat boleh panjang tapi **jangan berlebihan** — satu ide satu kalimat
- Hindari kata-kata yang terlalu formal dan berulang seperti "dalam rangka", "sehubungan dengan hal tersebut", "berkenaan dengan"
- Gunakan kalimat aktif lebih banyak daripada pasif, kecuali memang perlu
- Variasikan pembuka paragraf — jangan semua dimulai dengan "Berdasarkan..."
- Boleh sesekali menggunakan kalimat pendek yang tegas untuk efek penekanan

### Konsistensi Istilah
Pakai istilah berikut secara konsisten di seluruh dokumen:

| Gunakan | Jangan Gunakan |
|---|---|
| agen | agent (kecuali dalam konteks nama teknis) |
| pengembang | developer |
| pengguna | user (kecuali nama peran teknis) |
| perangkat lunak | software (kecuali nama spesifik) |
| rekayasa kebutuhan | requirements engineering |
| arsitektur | architecture |
| pengujian | testing |
| basis data | database |

> **Catatan**: Untuk istilah teknis yang belum punya padanan baku di KBBI, tulis dalam bahasa Inggris dengan cetak miring pada kemunculan pertama, lalu bisa digunakan langsung. Contoh: *skill-based AI* → Skill-Based AI.

### Paragraf
- Minimal 3 kalimat per paragraf
- Setiap gambar dan tabel **wajib diacu dan dijelaskan** dalam paragraf sebelumnya
- Tabel dibuat manual, bukan capture gambar
- Singkatan ditulis lengkap pada kemunculan pertama. Contoh: Sistem Permohonan Hak Cipta (SPHC) → selanjutnya cukup SPHC

### Penggunaan Kata Hubung
- **Boleh** di awal kalimat: Namun, Oleh karena itu, Dengan demikian, Selain itu, Di sisi lain
- **Hindari** di awal kalimat: dan, karena, sehingga, tetapi, atau
- Gunakan "pada" untuk tempat/waktu; "terhadap" untuk hubungan/sikap

---

## Instruksi Per Bab

---

### BAB 1 — PENDAHULUAN

Pendahuluan ditulis dengan **pola funnel (corong)**: mulai dari gambaran besar, lalu menyempit ke masalah spesifik, kemudian keluar lagi ke tujuan dan struktur laporan.

#### 1.1 Latar Belakang

**Urutan yang benar:**

1. **Buka dengan topik besar** — Jelaskan fenomena umum yang relevan. Misalnya: makin pentingnya perlindungan kekayaan intelektual di lingkungan perguruan tinggi, atau tren otomatisasi dalam pengembangan perangkat lunak menggunakan AI. Sertakan angka atau fakta menarik dari paper (2020–2026) untuk menarik perhatian pembaca. Jangan langsung bahas INSPIRA.

2. **Jelaskan konteks yang lebih spesifik** — Sambungkan ke konteks kampus: bagaimana proses pengajuan Hak Cipta saat ini dilakukan secara manual, apa saja prosedur yang harus dilalui mengacu pada regulasi DJKI, dan mengapa ini merepotkan secara administratif bagi dosen dan staf PPKI.

3. **Sampaikan pain points nyata** — Ini hasil dari observasi dan wawancara dengan admin LPPM/PPKI Universitas Pertamina. Ceritakan masalahnya dengan konkret: berapa banyak dokumen yang harus disiapkan, berapa lama prosesnya, di mana titik bottleneck-nya. Buat pembaca merasakan masalahnya.

4. **Perkenalkan solusi yang ditawarkan** — Hadirkan INSPIRA sebagai sistem yang dirancang untuk mengatasi masalah tersebut. Jelaskan bahwa INSPIRA tidak hanya membangun sistemnya, tapi juga **menggunakan AI untuk mengotomatisasi proses pengembangannya sendiri** (ini yang membedakan dari penelitian biasa).

5. **Jelaskan research gap** — Tunjukkan bahwa penelitian serupa (multi-agent untuk pengembangan perangkat lunak) memang sudah ada, tapi belum ada yang spesifik menggabungkan Skill-Based AI dengan domain administrasi HKI di kampus. Gunakan tabel perbandingan kalau perlu (di subbab 2.5). Di latar belakang, cukup sebutkan celahnya secara naratif. Pilih tipe research gap yang tepat (lihat bagian Research Gap di bawah).

6. **Rangkum dengan transisi ke rumusan masalah** — Akhiri latar belakang dengan kalimat yang secara alami mengantar ke 1.2.

> **Panjang ideal**: 3–5 halaman. Jangan terlalu pendek (terkesan dangkal) tapi juga jangan terlalu panjang sampai membahas teori (itu urusan Bab 2).

#### 1.2 Rumusan Masalah

Tulis sebagai pertanyaan penelitian, bukan pernyataan. Contoh pola:
- "Bagaimana mengimplementasikan dan mengorkestrasi arsitektur multi-agent Skill-Based AI untuk mengotomatisasi proses Requirement Engineering hingga Testing dalam pengembangan INSPIRA?"

Kalau ada lebih dari satu pertanyaan, pastikan semuanya masih terhubung ke satu benang merah.

#### 1.3 Tujuan Penelitian

Tulis sebagai jawaban langsung dari rumusan masalah. Gunakan kata kerja yang jelas: mengimplementasikan, merancang, mengevaluasi, menganalisis — bukan "mengetahui" atau "memahami".

#### 1.4 Batasan Masalah

Tuliskan dengan jelas tapi tidak perlu panjang. Penting untuk menjaga ekspektasi pembaca. Batasan utama INSPIRA:
- Pengembangan hanya mencakup jenis HKI Hak Cipta
- Tidak membuat model AI baru; menggunakan model yang sudah tersedia (*existing model*)
- Tahap pengembangan hanya sampai testing, tidak mencakup deployment dan maintenance jangka panjang
- Sistem dikembangkan dalam konteks kampus Universitas Pertamina

#### 1.5 Manfaat Penelitian

Tulis manfaat dari dua sudut pandang:
1. **Praktis** — untuk dosen, staf PPKI, dan divisi IT kampus yang bisa mengadopsi sistem ini
2. **Akademis** — kontribusi untuk penelitian di bidang Rekayasa Perangkat Lunak, khususnya otomatisasi SDLC berbasis AI

---

### BAB 2 — TINJAUAN PUSTAKA

Tinjauan pustaka bukan daftar ringkasan paper. Tulis sebagai **narasi yang membangun argumen**: tiap subbab mempersiapkan pembaca untuk memahami keputusan desain yang diambil di Bab 3 dan hasil di Bab 4.

**Aturan sitasi untuk Bab 2 (dan seluruh laporan):**
- Semua paper **harus dari rentang 2020–2026**
- Sertakan **link DOI atau URL PDF yang bisa diakses** di daftar referensi di akhir output
- Format sitasi dalam teks: (Nama Penulis, Tahun)
- Format daftar referensi: APA 7th Edition

#### 2.1 Manajemen Hak Kekayaan Intelektual (HKI)

Bagian ini **singkat saja** — ini bukan fokus utama penelitian. Yang perlu dijelaskan:
- Apa itu HKI dan pentingnya di lingkungan akademik
- Fokus pada Hak Cipta: definisi, objek yang dilindungi, alur pendaftaran ke DJKI
- Aturan dan regulasi yang berlaku di Indonesia (UU Hak Cipta, prosedur DJKI)
- Akhiri dengan menjelaskan mengapa proses ini kompleks dan berpotensi untuk diotomatisasi

Panjang: 1–2 halaman.

#### 2.2 LLM dalam Rekayasa Perangkat Lunak

Ceritakan evolusinya:
1. Mulai dari penggunaan LLM paling sederhana dalam coding (GitHub Copilot, ChatGPT untuk debugging)
2. Berkembang ke penggunaan LLM untuk tahap-tahap SDLC yang lebih tinggi (requirement analysis, test generation)
3. Sampai ke pendekatan yang lebih terstruktur seperti yang digunakan dalam penelitian ini

Tunjukkan bahwa ada tren yang jelas menuju otomatisasi SDLC penuh menggunakan AI, dan INSPIRA masuk ke dalam tren ini.

#### 2.3 Arsitektur Agen Modular (Multi-Agent)

Ini subbab penting. Jelaskan:
- Konsep dasar multi-agent system: kenapa satu agen besar lebih buruk dari beberapa agen kecil yang spesialis
- Referensikan paper MASAI (Multi-Agent Software AI) yang membagi tugas ke spesialis: Test Template Writer, Issue Reproducer, Edit Localizer, dst.
- Jelaskan juga penelitian lain yang membagi agen berdasarkan tahap SDLC (RE Agent, Architect Agent, dll.)
- Jelaskan konsep **Thin Orchestrator**: agen kecil yang tugasnya hanya routing trigger ke agen yang tepat, bukan mengerjakan sendiri

#### 2.4 Pendekatan Skill-Based AI

Ini yang paling membedakan INSPIRA dari penelitian lain. Jelaskan dengan detail:

1. **Apa bedanya skill dengan prompt biasa?**
   - Prompt: instruksi ad-hoc yang ditulis setiap kali
   - Skill: pengetahuan prosedural yang tersimpan sebagai dokumen terstruktur, bisa dipanggil kapan saja, bisa di-*version control*

2. **Struktur hierarki folder skill:**
   ```
   agents/
   └── requirement-agent/
       └── skills/
           ├── elicitation-skill/
           │   ├── SKILL.md
           │   ├── tools/
           │   └── examples/
           └── documentation-skill/
               ├── SKILL.md
               ├── tools/
               └── examples/
   ```

3. **Keunggulan utama:**
   - *Progressive disclosure*: sistem hanya memuat skill yang relevan dengan trigger aktif → hemat context window
   - Skill bisa direplikasi ke proyek lain (*transferable knowledge*)
   - Lebih mudah di-debug dan di-update daripada prompt monolitik

#### 2.5 Penelitian Terdahulu

Buat tabel perbandingan yang menunjukkan posisi INSPIRA di antara penelitian yang sudah ada. Kolom yang disarankan:

| Peneliti | Tahun | Fokus | Pendekatan AI | Domain | Kelebihan | Keterbatasan |
|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... |

Cari paper yang mengeksplor:
- Multi-agent untuk software development (MASAI, MetaGPT, AutoGen, dll.)
- AI untuk requirement engineering
- AI untuk code generation (berbasis SDLC penuh)
- Sistem administrasi HKI digital

Akhiri subbab ini dengan paragraf yang secara eksplisit menyebut **research gap** yang diisi oleh INSPIRA.

---

### BAB 3 — METODOLOGI PENELITIAN

#### 3.1 Alur Penelitian

Gambarkan flowchart dari awal (pengumpulan data) sampai akhir (pengujian sistem). Jelaskan setiap tahap secara singkat dalam teks, lalu arahkan pembaca ke gambar flowchart. Pastikan alurnya terlihat logis dan saling mendukung.

#### 3.2 Teknik Pengumpulan Data

Jelaskan dua teknik yang digunakan:

1. **Wawancara semi-terstruktur** dengan admin LPPM/PPKI Universitas Pertamina
   - Apa yang ingin digali: pain points dalam proses manual, dokumen apa yang dipakai, siapa saja yang terlibat
   - Jelaskan kenapa semi-terstruktur dipilih (fleksibel tapi tetap punya arah)

2. **Analisis Artefak** — menggunakan desain Figma sebagai media requirement elicitation
   - Model Context Protocol (MCP) digunakan agar agen bisa membaca desain Figma secara real-time
   - Jelaskan apa yang bisa diekstrak: alur navigasi, elemen UI, label komponen

3. **Analisis Dokumen DJKI**
   - Dokumen resmi dari website DJKI sebagai dasar proses bisnis pengajuan Hak Cipta

Jelaskan juga bagaimana hasil pengumpulan data ini menjadi input bagi Requirement Engineering Agent.

#### 3.3 Rancangan Arsitektur AI

Ini inti Bab 3. Jelaskan dengan rinci:

1. **Thin Agent Orchestrator**
   - Tugasnya: menerima trigger dari pengguna, mengidentifikasi agen mana yang harus dipanggil, meneruskan konteks yang relevan
   - Kenapa "thin"? Karena dia tidak mengerjakan apa pun sendiri — hanya routing

2. **Empat Agen Utama dan Skill-nya**
   - Untuk setiap agen, jelaskan: tugas utamanya, skill-skill yang dimilikinya, input yang diterima, output yang dihasilkan

3. **Skill-Based RE Pipeline**
   - Tahapan: Skill Decomposition → Procedural Encoding di SKILL.md → Tool Integration (skrip Python/Bash)
   - *Progressive disclosure*: bagaimana sistem memutuskan skill mana yang dimuat

4. **Model Context Protocol (MCP)**
   - Cara agen membaca Figma Dev Mode secara real-time untuk ekstraksi kebutuhan dari desain

5. **Cara Evaluasi**
   - Setiap output agen dievaluasi oleh ahli domain di kampus (engineer, dosen terkait)
   - Sebutkan metrik evaluasi yang digunakan

---

### BAB 4 — HASIL DAN PEMBAHASAN

Bab 4 adalah pameran hasil kerja. Tulis seperti bercerita — "ini yang terjadi, ini hasilnya, ini artinya apa".

#### 4.1 Analisis Kebutuhan Sistem (Kerja RE Agent)

- Ceritakan hasil wawancara dengan admin LPPM: apa pain points yang ditemukan, dokumen apa yang biasanya dipakai
- Tampilkan hasil *Elicitation Skill*: daftar user stories yang digenerate secara otomatis oleh agen
- Tampilkan hasil prioritisasi kebutuhan menggunakan **AHP atau WSJF** dari Requirement Engineering Agent
- Jelaskan evaluasi dari ahli domain: apa yang diubah, apa yang sudah tepat

#### 4.2 Perancangan Sistem (Kerja Architecting Agent)

- Tampilkan hasil konversi user stories → spesifikasi arsitektur teks
- Tampilkan diagram visual (UML use case, ERD, class diagram) yang digenerate menggunakan PlantUML
- Jelaskan bagaimana agen menerjemahkan spesifikasi ke diagram — bukan sekadar memperlihatkan gambarnya
- Evaluasi dari ahli domain arsitektur

#### 4.3 Implementasi Skill Library

- Tampilkan struktur direktori skill library INSPIRA secara lengkap
- Bahas isi `SKILL.md` untuk salah satu skill (misalnya `hak-cipta-compliance-skill`) sebagai contoh representatif
- Jelaskan bagaimana *progressive disclosure* diimplementasikan: mekanisme pemilihan skill yang dimuat berdasarkan trigger aktif
- Bandingkan pendekatan ini dengan metode tanpa skill library (prompt biasa) dalam hal akurasi dan efisiensi context window

#### 4.4 Tampilan dan Penjelasan Fungsional INSPIRA

- Tampilkan screenshot antarmuka sistem web INSPIRA
- Jelaskan tiap fitur utama: dashboard pengajuan, tracking revisi, manajemen dokumen
- Kaitkan tampilan dengan user stories yang sudah dibuat di 4.1

#### 4.5 Pengujian Sistem (Kerja Test Agent & QA)

- Hasil *Composable Testing*: pengujian apakah antar-skill tidak bentrok satu sama lain
- Hasil Unit Testing dan End-to-End yang dihasilkan oleh Testing Agent
- Pembahasan efisiensi memori: perbandingan token/context window dengan dan tanpa progressive disclosure
- Apakah semua fungsionalitas berjalan sesuai user stories?

---

## Panduan Sitasi (APA 7th Edition)

### Dalam Teks

**Satu penulis:**
> ... sistem multi-agent telah terbukti meningkatkan efisiensi dalam pengembangan perangkat lunak (Wang, 2023).

**Dua penulis:**
> ... (Li & Zhang, 2024)

**Tiga atau lebih penulis:**
> ... (Chen et al., 2022)

**Kutipan langsung** (jarang dipakai, lebih baik parafrase):
> "Multi-agent systems enable specialization at scale" (Kim et al., 2023, p. 45)

### Di Daftar Referensi (Akhir Output)

Setiap kali menuliskan bagian yang menggunakan referensi, **sertakan daftar referensi lengkap di akhir output** dengan format berikut:

**Jurnal:**
```
Penulis, A. B., & Penulis, C. D. (Tahun). Judul artikel. Nama Jurnal, Volume(Nomor), halaman–halaman. https://doi.org/xxxxx
```

**Prosiding konferensi:**
```
Penulis, A. B. (Tahun). Judul paper. Dalam Nama Editor (Ed.), Judul Prosiding (hal. xx–xx). Penerbit. https://doi.org/xxxxx
```

**Website/laporan resmi:**
```
Nama Organisasi. (Tahun). Judul dokumen. URL
```

### Aturan Penting Sitasi
1. **Semua paper harus dari 2020–2026** — tidak ada pengecualian kecuali untuk referensi historis yang benar-benar foundational (dan itu pun harus dijelaskan alasannya)
2. **Link DOI atau PDF harus bisa diakses** — jangan tulis DOI yang dead link. Kalau tidak yakin, gunakan Google Scholar, Semantic Scholar, atau ArXiv untuk mengonfirmasi aksesibilitasnya
3. **Prioritaskan** jurnal bereputasi (IEEE, ACM, Elsevier, Springer) dan konferensi top (ICSE, FSE, EMNLP, NeurIPS, ICLR) untuk topik AI
4. **Parafrase, jangan copy-paste** isi paper — tulis ulang dengan bahasamu sendiri

---

## Panduan Research Gap

Gunakan kerangka berikut untuk mengidentifikasi dan menyampaikan research gap INSPIRA:

| Tipe Gap | Definisi | Relevansi ke INSPIRA |
|---|---|---|
| **Theoretical Gap** | Kurangnya teori atau model untuk fenomena yang diamati | Belum ada kerangka teori yang menggabungkan Skill-Based AI dengan SDLC automation secara holistik |
| **Methodological Gap** | Kekurangan dalam metode yang digunakan penelitian sebelumnya | Penelitian sebelumnya kebanyakan evaluasi black-box, belum menggunakan progressive disclosure sebagai metrik efisiensi |
| **Empirical Gap** | Data atau bukti empiris yang kurang | Belum ada studi yang mengukur efisiensi multi-agent dalam domain administrasi HKI |
| **Conceptual Gap** | Ketidakjelasan konsep atau definisi | Belum ada konsensus tentang apa yang dimaksud "skill" dalam konteks AI agent vs. prompt |
| **Temporal Gap** | Kurangnya penelitian di periode tertentu | Skill-Based AI masih sangat baru (2023–2024), penelitian terapannya masih sangat sedikit |
| **Spatial Gap** | Kurangnya penelitian di area geografis tertentu | Hampir tidak ada penelitian multi-agent untuk konteks administrasi kampus di Indonesia |

> Untuk INSPIRA, **Temporal Gap** dan **Spatial Gap** adalah yang paling kuat untuk ditonjolkan di latar belakang.

---

## Daftar Kesalahan Umum yang Harus Dihindari

Ini diambil dari panduan penulisan skripsi Universitas Pertamina:

1. **Inkonsistensi istilah** — pilih satu dan pakai terus. Jangan mix "pengguna" dan "user" secara acak
2. **Kata tidak baku** — cek KBBI untuk: praktik (bukan praktek), apotek (bukan apotik), analisis (bukan analisa)
3. **Penulisan imbuhan di-** — disambung kalau diikuti kata kerja (*digunakan*), dipisah kalau bukan (*di kampus*)
4. **Kata hubung di awal kalimat** — "dan", "karena", "sehingga" tidak boleh membuka kalimat
5. **Paragraf terlalu pendek** — minimal 3 kalimat per paragraf
6. **Kalimat terlalu panjang** — satu ide satu kalimat, pisah kalau sudah terlalu panjang
7. **Singkatan tidak diperkenalkan** — tulis kepanjangan di kemunculan pertama
8. **Gambar/tabel tidak diacu** — setiap gambar dan tabel wajib dirujuk dan dijelaskan di paragraf
9. **Tabel berupa gambar** — buat tabel secara manual, bukan screenshot
10. **Redundansi** — hindari mengulang informasi yang sama di tempat berbeda tanpa tujuan
11. **Huruf kapital berlebihan** — hanya untuk judul, nama tempat, nama sistem, dan istilah khusus yang memang harus kapital

---

## Cara Menggunakan Skill Ini

### Trigger yang Dikenali

Gunakan perintah seperti berikut untuk memanggil skill ini:

| Perintah | Aksi |
|---|---|
| `tulis latar belakang` | Generate draft 1.1 Latar Belakang |
| `tulis rumusan masalah` | Generate draft 1.2 Rumusan Masalah |
| `tulis bab 2 subbab [X]` | Generate draft subbab tertentu di Bab 2 |
| `tulis metodologi` | Generate Bab 3 secara keseluruhan |
| `tulis hasil [bagian]` | Generate bagian tertentu dari Bab 4 |
| `revisi [bagian] — [feedback]` | Revisi bagian tertentu berdasarkan feedback |
| `cari paper untuk [topik]` | Sarankan paper 2020–2026 yang relevan untuk topik tertentu |
| `cek kesalahan` | Review teks yang diberikan berdasarkan daftar kesalahan umum |

### Output yang Diharapkan

Setiap kali menulis bagian laporan, output harus terdiri dari:

1. **Teks bagian laporan** — dalam Bahasa Indonesia yang natural dan akademis
2. **Catatan internal** (opsional) — hal-hal yang masih perlu dikonfirmasi atau dilengkapi oleh penulis manusia (misalnya: data dari wawancara, screenshot sistem)
3. **Daftar Referensi** — semua paper yang dikutip dalam bagian tersebut, format APA 7th, **dengan link DOI atau URL PDF**

### Format Daftar Referensi di Akhir Output

```
---
## Referensi

Nama, A. B., & Nama, C. D. (Tahun). Judul artikel. Nama Jurnal, Vol(No), hal-hal. 
https://doi.org/[doi-aktif]

Nama, E. F. (Tahun). Judul paper. Dalam Judul Prosiding (hal. xx-xx). 
https://doi.org/[doi-aktif] atau https://arxiv.org/abs/[id] (arXiv)
```

---

## Checklist Sebelum Submit Setiap Bagian

- [ ] Semua istilah digunakan secara konsisten
- [ ] Tidak ada kata tidak baku (cek KBBI)
- [ ] Setiap paragraf minimal 3 kalimat
- [ ] Tidak ada kata hubung ("dan", "karena", dst.) di awal kalimat
- [ ] Semua gambar dan tabel diacu dalam teks
- [ ] Semua singkatan diperkenalkan di kemunculan pertama
- [ ] Semua sitasi dari 2020–2026
- [ ] Semua link DOI/PDF aktif dan bisa diakses
- [ ] Format APA 7th sudah benar
- [ ] Teks terasa natural, bukan seperti template diisi otomatis
