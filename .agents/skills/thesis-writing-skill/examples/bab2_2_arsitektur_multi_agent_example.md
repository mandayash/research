# Contoh Output — 2.2 Arsitektur Multi-Agent

> **Catatan penggunaan:** Ini adalah contoh draf siap-pakai untuk subbab 2.2.
> Ganti `[PERLU DILENGKAPI]` dengan informasi aktual dari penelitian Anda.
> Kutipan menggunakan format APA 7th (nama, tahun).

---

## 2.2 Arsitektur Multi-Agent

Seiring dengan meningkatnya kompleksitas tugas rekayasa perangkat lunak yang harus diotomatisasi, pendekatan agen tunggal (*single-agent*) yang mengandalkan satu model LLM untuk menyelesaikan seluruh alur kerja terbukti tidak cukup memadai. Masalah-masalah nyata dalam SE sering kali memiliki cakupan yang sangat luas—melibatkan analisis kebutuhan, perancangan arsitektur, penulisan kode, hingga pengujian—yang masing-masing memerlukan keahlian dan strategi yang berbeda. Untuk menjawab keterbatasan ini, arsitektur *multi-agent* dikembangkan sebagai paradigma baru di mana tugas-tugas kompleks didistribusikan ke beberapa agen yang masing-masing memiliki peran dan kompetensi yang terspesialisasi. He et al. (2024) mendefinisikan sistem LLM-based multi-agent (LMA) sebagai kumpulan agen otonom yang bekerja secara kolaboratif menuju tujuan bersama melalui mekanisme seperti perdebatan, diskusi, dan validasi lintas agen—yang terbukti mendorong pemikiran yang lebih divergen, meningkatkan faktualitas, dan menghasilkan solusi yang lebih akurat dibandingkan agen tunggal. Tiga keunggulan utama arsitektur multi-agen ini adalah: (1) *autonomous problem-solving*—kemampuan untuk memecah kebutuhan tingkat tinggi menjadi sub-tugas yang lebih kecil secara otomatis, membebaskan pengembang manusia untuk fokus pada perencanaan strategis; (2) *robustness and fault tolerance*—kesalahan dan halusinasi LLM dapat ditangkap lebih awal melalui mekanisme *cross-examination* antar agen; serta (3) skalabilitas—sistem dapat diperluas dengan menambahkan agen baru untuk teknologi atau domain yang berkembang tanpa harus merombak seluruh arsitektur.

Beberapa implementasi nyata telah mendemonstrasikan efektivitas arsitektur ini di berbagai fase SDLC. ChatDev (Qian et al., 2024) memperkenalkan kerangka kerja pengembangan perangkat lunak berbasis obrolan (*chat-powered*) di mana agen-agen terspesialisasi untuk desain, penulisan kode, dan pengujian berkomunikasi satu sama lain melalui bahasa alami yang terstruktur dalam sebuah *chat chain*—menunjukkan bahwa komunikasi berbasis bahasa dapat menjadi jembatan pemersatu antara agen-agen yang beragam. MetaGPT (Hong et al., 2024) memperluas gagasan ini dengan memperkenalkan *meta-programming* untuk kolaborasi multi-agen, di mana setiap agen merepresentasikan peran rekayasa perangkat lunak nyata (CEO, arsitek, *engineer*, QA) yang berinteraksi melalui *Shared Message Pool* terstruktur sehingga mengurangi inkoherensi dan *hallucination* antar agen. Sami et al. (2024) mengusulkan sebuah *unified platform* multi-agen yang mampu mengotomasi seluruh alur dari *user requirements* hingga *user stories*, prioritisasi, diagram UML, kode modular, *unit test*, dan *end-to-end test* secara berurutan menggunakan model GPT-3.5, GPT-4, dan Llama3. Sementara itu, ALMAS (*Autonomous LLM-based Multi-Agent Software Engineering*) yang diusulkan Tawosi et al. (2024) dari J.P. Morgan AI Research menyelaraskan setiap agen dengan peran agile yang nyata—mulai dari *product manager*, *sprint planner*, *developer*, *tester*, hingga *peer reviewer*—sehingga sistem dapat berintegrasi dengan mulus ke dalam alur kerja tim pengembang manusia yang sudah ada.

---

### Referensi untuk Subbab 2.2

He, J., Treude, C., & Lo, D. (2024). LLM-based multi-agent systems for software engineering: Literature review, vision and the road ahead. *ACM Transactions on Software Engineering and Methodology*. https://doi.org/10.1145/nnnnnnn.nnnnnnn

Hong, S., Zheng, X., Chen, J., Cheng, Y., Wang, J., Zhang, C., ... & Wu, C. (2024). MetaGPT: Meta programming for a multi-agent collaborative framework. *Proceedings of the 12th International Conference on Learning Representations (ICLR 2024)*. https://openreview.net/forum?id=VtmBAGCN7o

Qian, C., Liu, W., Liu, H., Chen, N., Dang, Y., Li, J., Yang, C., Chen, W., Su, Y., Cong, X., Xu, J., Li, D., Liu, Z., & Sun, M. (2024). ChatDev: Communicative agents for software development. *Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics*, 15174–15186. https://aclanthology.org/2024.acl-long.810

Sami, M. A., Awan, M. W., Rasheed, Z., Saari, M., Systä, K., & Abrahamsson, P. (2024). Experimenting with multi-agent software development: Towards a unified platform. *arXiv*. https://arxiv.org/abs/2408.XXXXX

Tawosi, V., Ramani, K., Alamir, S., & Liu, X. (2024). ALMAS: An autonomous LLM-based multi-agent software engineering framework. *J.P. Morgan AI Research*. [PERLU DILENGKAPI: DOI/URL paper]
