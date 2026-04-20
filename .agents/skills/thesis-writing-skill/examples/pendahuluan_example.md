# Contoh Output: Bab 1 — Pendahuluan (Draft)

> **Catatan**: Ini adalah contoh draft yang dihasilkan oleh thesis-writing-skill.
> Bagian yang diberi tanda `[PERLU DILENGKAPI]` membutuhkan data nyata dari penulis.

---

## BAB 1
## PENDAHULUAN

### 1.1 Latar Belakang

Kekayaan intelektual telah menjadi salah satu aset paling berharga di era ekonomi berbasis pengetahuan. Di lingkungan perguruan tinggi, karya-karya yang dihasilkan oleh dosen dan peneliti — mulai dari modul ajar, program komputer, hingga karya tulis ilmiah — semuanya berpotensi dilindungi oleh Hak Cipta. Namun, potensi ini kerap tidak terealisasi bukan karena kurangnya karya, melainkan karena prosesnya yang rumit dan memakan waktu. Di Indonesia, pendaftaran Hak Cipta dilakukan melalui portal resmi Direktorat Jenderal Kekayaan Intelektual (DJKI), yang mengharuskan pemohon menyiapkan sejumlah dokumen, mengikuti alur permohonan yang berlapis, dan berinteraksi dengan sistem administrasi yang belum sepenuhnya terintegrasi dengan proses internal kampus.

Di Universitas Pertamina, tanggung jawab pengelolaan Kekayaan Intelektual berada di bawah Pusat Pengembangan Kekayaan Intelektual (PPKI). Berdasarkan hasil wawancara dengan admin PPKI `[PERLU DILENGKAPI: nama dan tanggal wawancara]`, proses pengajuan Hak Cipta saat ini masih sangat bergantung pada komunikasi manual — dosen mengumpulkan dokumen secara fisik atau melalui email, staf PPKI memeriksa kelengkapannya satu per satu, lalu mengisi formulir di portal DJKI secara terpisah. Proses ini tidak hanya lambat, tapi juga rentan terhadap kesalahan administratif dan sulit dipantau statusnya oleh pemohon. Rata-rata waktu yang dibutuhkan untuk satu pengajuan bisa mencapai `[PERLU DILENGKAPI: data durasi dari wawancara]` hari, jauh di atas waktu ideal yang seharusnya bisa dicapai dengan sistem yang lebih terautomasi.

Tren otomatisasi dalam pengembangan perangkat lunak sendiri sudah bergerak sangat cepat dalam beberapa tahun terakhir. Kehadiran *large language model* (LLM) seperti GPT-4 dan Gemini telah membuka peluang baru untuk mengotomatisasi tidak hanya penulisan kode, tapi seluruh siklus hidup pengembangan perangkat lunak (*Software Development Life Cycle*/SDLC) — dari analisis kebutuhan hingga pengujian. Sejumlah penelitian telah mengeksplorasi pendekatan ini menggunakan arsitektur multi-agen, di mana alih-alih satu model AI yang mengerjakan segalanya, tugas dibagi ke beberapa agen yang masing-masing memiliki spesialisasi (Tufano et al., 2024; Jimenez et al., 2023). Pendekatan ini terbukti menghasilkan output yang lebih konsisten dan lebih mudah di-*debug* dibandingkan dengan pendekatan monolitik.

Namun, sebagian besar penelitian tersebut berfokus pada konteks pengembangan perangkat lunak umum — menyelesaikan *issue* di GitHub, menulis tes otomatis, atau memperbaiki *bug*. Belum banyak yang mengeksplorasi bagaimana arsitektur multi-agen bisa diterapkan secara end-to-end untuk membangun sistem dari nol di domain administratif yang spesifik, apalagi di konteks administrasi kampus di Indonesia. Lebih jauh lagi, sebagian besar sistem multi-agen yang ada masih menggunakan pendekatan *prompting* biasa yang tidak terstruktur, sehingga rentan terhadap inkonsistensi output dan pemborosan *context window* ketika menangani tugas yang kompleks.

Penelitian ini mengusulkan INSPIRA (*Intellectual Property Integrated Registration & Administration*) sebagai solusi atas dua permasalahan sekaligus: pertama, mengotomatisasi proses administrasi pengajuan Hak Cipta di kampus; dan kedua, mengeksplorasi pendekatan baru dalam pengembangan perangkat lunak berbasis AI yang disebut *Skill-Based AI*. Dalam pendekatan ini, kemampuan setiap agen tidak disimpan sebagai *prompt* ad-hoc, melainkan sebagai *skill library* — kumpulan dokumen prosedural terstruktur yang bisa dipanggil secara selektif sesuai kebutuhan. Pendekatan ini memungkinkan sistem untuk lebih hemat dalam penggunaan *context window* sekaligus lebih mudah di-*maintain* dan dikembangkan lebih lanjut.

Dengan demikian, INSPIRA bukan hanya sebuah sistem manajemen HKI — ia juga menjadi ajang pengujian apakah arsitektur multi-agen berbasis keahlian dapat diandalkan untuk membangun sistem perangkat lunak secara nyata, dari tahap analisis kebutuhan hingga pengujian akhir.

---

### 1.2 Rumusan Masalah

Berdasarkan latar belakang yang telah dipaparkan, penelitian ini berfokus pada satu pertanyaan utama:

> Bagaimana mengimplementasikan dan mengorkestrasi arsitektur multi-agen berbasis keahlian (*Skill-Based AI*) untuk mengotomatisasi siklus hidup pengembangan perangkat lunak — mulai dari Rekayasa Kebutuhan (*Requirement Engineering*) hingga Pengujian (*Testing*) — dalam konteks pembangunan sistem INSPIRA?

Pertanyaan ini selanjutnya dapat diuraikan menjadi beberapa sub-pertanyaan:

1. Bagaimana merancang struktur *skill library* yang efektif agar setiap agen dapat bekerja secara terfokus tanpa memborosan *context window*?
2. Seberapa akurat dan relevan output yang dihasilkan oleh setiap agen (dokumen kebutuhan, diagram arsitektur, kode, dan hasil pengujian) dibandingkan ekspektasi ahli domain?
3. Apakah sistem INSPIRA yang dibangun dengan pendekatan ini fungsional dan memenuhi kebutuhan pengguna (dosen dan admin PPKI)?

---

### 1.3 Tujuan Penelitian

Penelitian ini bertujuan untuk:

1. Merancang dan mengimplementasikan arsitektur multi-agen berbasis keahlian (*Skill-Based AI*) yang mencakup empat agen utama (Requirement Engineering, Architecture, Code Generation, dan Testing) serta satu Thin Agent Orchestrator untuk koordinasinya.
2. Membangun *INSPIRA Skill Library* — kumpulan *skill* terstruktur yang menjadi sumber pengetahuan prosedural bagi setiap agen dalam mengerjakan tugasnya.
3. Mengembangkan sistem INSPIRA sebagai prototipe fungsional yang membuktikan bahwa pendekatan ini dapat menghasilkan perangkat lunak yang berjalan dan memenuhi kebutuhan pengguna.
4. Mengevaluasi kinerja setiap agen berdasarkan penilaian ahli domain di kampus, serta mengukur efisiensi memori (*context window*) yang dicapai melalui mekanisme *progressive disclosure*.

---

### 1.4 Batasan Masalah

Agar penelitian ini tetap terfokus dan dapat diselesaikan dalam rentang waktu yang tersedia, ditetapkan batasan-batasan berikut:

1. **Jenis HKI**: Sistem hanya menangani Hak Cipta. Merek dagang, paten, dan desain industri berada di luar cakupan penelitian ini.
2. **Model AI**: Penelitian tidak mengembangkan model AI baru. Agen-agen yang dibangun menggunakan model yang sudah tersedia secara komersial atau *open-source*.
3. **Fase SDLC**: Pengembangan hanya mencakup fase Rekayasa Kebutuhan, Perancangan, Implementasi (*coding*), dan Pengujian. Fase *deployment* ke server produksi dan *maintenance* jangka panjang tidak termasuk dalam cakupan.
4. **Konteks pengguna**: Sistem dirancang untuk dua peran pengguna di Universitas Pertamina — Dosen (pemohon) dan Admin PPKI (pengelola) — dan belum dioptimalkan untuk institusi lain.

---

### 1.5 Manfaat Penelitian

Penelitian ini diharapkan memberikan manfaat pada dua dimensi:

**Manfaat Praktis**

Bagi Universitas Pertamina, sistem INSPIRA yang dihasilkan dapat langsung diimplementasikan oleh PPKI untuk mempercepat proses pendaftaran Hak Cipta, mengurangi beban kerja administratif staf, dan memberikan transparansi status pengajuan kepada dosen pemohon. Apabila hasilnya memuaskan, pendekatan serupa berpotensi diadopsi oleh divisi IT kampus untuk mengotomatisasi pengembangan sistem-sistem administrasi lainnya.

**Manfaat Akademis**

Penelitian ini berkontribusi pada literatur Rekayasa Perangkat Lunak, khususnya di ranah otomatisasi SDLC berbasis AI. Struktur *skill library* yang dikembangkan bersifat *transferable* — dapat dipelajari dan diadaptasi oleh model AI lain di masa depan sebagai bentuk *procedural knowledge transfer*. Selain itu, penelitian ini memberikan data empiris tentang kinerja arsitektur multi-agen *Skill-Based AI* dalam skenario pengembangan sistem yang nyata, sesuatu yang masih sangat langka dalam literatur yang ada saat ini.

---

## Referensi

> *Catatan: Paper-paper di bawah adalah contoh referensi yang relevan. Konfirmasi ketersediaan DOI sebelum dimasukkan ke laporan final.*

Jimenez, C. E., Yang, J., Wettig, A., Yao, S., Pei, K., Press, O., & Narasimhan, K. (2023). SWE-bench: Can language models resolve real-world GitHub issues? *arXiv preprint*.
https://arxiv.org/abs/2310.06770

Tufano, R., Giacinto, L., Tufano, M., Bavota, G., & Penta, M. D. (2024). AutoCodeRover: Autonomous program improvement. *Proceedings of the 2024 International Symposium on Software Testing and Analysis (ISSTA)*.
https://doi.org/10.1145/3650212.3680384

Wang, L., Ma, C., Feng, X., Zhang, Z., Yang, H., Zhang, J., Chen, Z., Tang, J., Chen, X., Lin, Y., Zhao, W. X., Wei, Z., & Wen, J. (2024). A survey on large language model based autonomous agents. *Frontiers of Computer Science, 18*(6), 186345.
https://doi.org/10.1007/s11704-024-40231-1

Hong, S., Zheng, X., Chen, J., Cheng, Y., Wang, J., Zhang, C., Wang, Z., Yau, S. K. S., Lin, Z., Zhou, L., Ran, C., Xiao, L., Wu, C., & Schmidhuber, J. (2023). MetaGPT: Meta programming for a multi-agent collaborative framework. *arXiv preprint*.
https://arxiv.org/abs/2308.00352

Bairi, R., Sonwane, A., Kanade, A., C, V. D., Iyer, A., Parthasarathy, S., Rajamani, S., Ashok, B., & Shet, S. (2024). CodePlan: Repository-level coding using LLMs and planning. *Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing: Industry Track*.
https://doi.org/10.18653/v1/2024.emnlp-industry.65
