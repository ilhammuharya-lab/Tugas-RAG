untuk text yang di gunakan URL: https://id.wikipedia.org/wiki/Hindia_Belanda


Analisis Aplikasi RAG Sejarah Indonesia
1. Pemilihan LLM (Groq API dengan LLaMA 3 70B)

Alasan Pemilihan:
Kualitas Jawaban: LLaMA 3 70B termasuk model open-weight terbaik dengan kemampuan reasoning setara GPT-4

Kemampuan Bahasa: Meski dominan Inggris, bisa menghasilkan respons Bahasa Indonesia cukup baik

Konteks Panjang: Mendukung hingga 8192 token, cocok untuk dokumen sejarah panjang

3. Pemilihan Model Embedding (BAAI/bge-small-en-v1.5)
Pertimbangan:
Efisiensi: Ukuran kecil (33MB) tetapi performa setara model besar

Multilingual: Meski "en" (English), bisa menangani teks Indonesia dengan baik

Akurasi: Skor MTEB (benchmark embedding) tinggi (63.45 untuk retrieval)

On-device: Bisa dijalankan di CPU tanpa kebutuhan GPU

3. Pemilihan Vector DB (ChromaDB)
Keunggulan:

Kesederhanaan: Setup hanya 3 baris kode Python

Open-source: Tidak ada vendor lock-in

Mode Hybrid: Bisa simpan di memori (development) atau disk (production)

Integrasi: Native support untuk embedding model dari HuggingFace

4. Mekanisme Update Knowledge Base
Strategi Pembaruan:

Batch Processing:

Sistem otomatis deteksi URL Wikipedia yang sudah diupdate

Ekstrak versi terbaru dan timpa data lama

5. Kekurangan dan Limitasi
Technical Limitations:

Akurasi Bahasa Indonesia:

Embedding model utama berbahasa Inggris

Contoh kasus: "Perjanjian Renville" bisa kurang match dengan "Renville Agreement"

Hallucination:

Meski pakai RAG, LLaMA 3 kadang masih menambahkan informasi fiktif

Contoh: Menyebut nama menteri yang tidak ada di dokumen sumber




Content Limitations:

Bias Sumber:

Hanya mengandalkan Wikipedia yang mungkin mengandung bias tertentu

Contoh: Perspektif sejarah versi Belanda vs Indonesia

Coverage:

Masih kurang detail untuk peristiwa spesifik seperti Pertempuran Surabaya

Solusi: Tambahkan sumber khusus dari buku digital atau arsip

