# 📝 Mini Proyek 2: LLM Automated Essay Scoring (AES) 2.0

Proyek ini adalah implementasi sistem *Automated Essay Scoring* (Penilaian Esai Otomatis) menggunakan *Large Language Models* (LLM) yang berjalan sepenuhnya secara lokal. Proyek ini dikembangkan untuk menyelesaikan tantangan Mini Proyek 2 berdasarkan dataset Kaggle: **[Learning Agency Lab - Automated Essay Scoring 2.0](https://www.kaggle.com/competitions/learning-agency-lab-automated-essay-scoring-2)**.

Sistem ini mengevaluasi teks esai siswa dan memprediksi skor (skala 1-6) menggunakan pendekatan *Prompt Engineering* standar serta simulasi keagenan buatan (*AI Agents*).

## 🚀 Fitur & Metodologi

Proyek ini mengeksplorasi metode berikut dalam memanfaatkan LLM untuk penilaian otomatis:
1. **Zero-Shot Learning:** Meminta LLM untuk langsung menilai esai berdasarkan instruksi sistem (tanpa memberikan contoh esai sebelumnya).
2. **Few-Shot Learning:** Memberikan sampel esai (nilai rendah dan nilai tinggi) beserta skor aslinya sebagai referensi standar penilaian sebelum LLM menilai esai target.
3. **Multi-Agent System (Bonus Poin 1):** Menggunakan *framework* `pyautogen` untuk mensimulasikan proses *peer-review* layaknya manusia. Sistem terdiri dari:
   * **Admin:** Memberikan instruksi dan teks esai.
   * **Penilai Utama:** Menganalisis tata bahasa dan isi esai, lalu memberikan argumen skor awal.
   * **Reviewer Senior:** Membaca analisis dari Penilai Utama dan menetapkan skor keputusan final yang objektif.

## 🛠️ Teknologi yang Digunakan
* **Bahasa Pemrograman:** Python 3.12+
* **LLM Engine:** [Ollama](https://ollama.com/) (Menjalankan model lokal)
* **Model AI:** Llama 3 (8B Parameters)
* **Framework Multi-Agent:** PyAutoGen
* **Data Processing & Evaluasi:** Pandas, Scikit-learn (Quadratic Weighted Kappa / QWK)

## 📂 Struktur Repositori

```text
MiniProject_AES_LLM/
│
├── dataset/                     # (Harus diunduh manual dari Kaggle)
│   ├── train.csv                
│   └── test.csv                 
│
├── notebooks/                   
│   ├── 01_zero_and_few_shot.ipynb  # Kode implementasi Zero-Shot dan Few-Shot
│   └── 02_bonus_autogen.ipynb      # Kode implementasi Multi-Agent
│
├── outputs/                     # Lokasi file hasil prediksi disimpan
│   ├── submission.csv           
│   └── submission_autogen.csv   
│
├── requirements.txt             # Daftar dependensi library
└── README.md                    # Dokumentasi proyek

```

## ⚙️ Cara Instalasi & Persiapan
1. Clone Repositori ini:
```bash
git clone https://github.com/theoitssurabaya/miniProyek2DeepL.git
cd miniProyek2DeepL
```

2. Siapkan Dataset:
* Buat folder bernama dataset di dalam folder utama proyek.
* Unduh data dari halaman Kaggle AES 2.0.
* Masukkan file train.csv dan test.csv ke dalam folder dataset/.

3. Siapkan Environment Python:
```bash
python -m venv venv

# Aktivasi di Windows:
venv\Scripts\activate
# Aktivasi di Mac/Linux:
source venv/bin/activate
```

4. Instal Dependensi:
```bash
pip install -r requirements.txt
```

5. Siapkan Ollama & Model AI:
* Unduh dan instal Ollama dari [ollama.com](https://ollama.com/).
* Buka Terminal/CMD dan jalankan perintah berikut untuk mengunduh model Llama 3:
```bash
ollama run llama3
```
* PENTING: Biarkan terminal Ollama ini tetap berjalan di background selama Anda mengeksekusi kode di notebook.

## 💻 Cara Menjalankan
1. Buka dan jalankan notebooks/01_zero_and_few_shot.ipynb untuk menjalankan penilaian menggunakan prompting standar dan melihat perbandingan evaluasi metrik QWK.
2. Buka dan jalankan notebooks/02_bonus_autogen.ipynb untuk menjalankan simulasi diskusi Multi-Agent dalam menilai esai.

File hasil prediksi akhir akan otomatis dibuat di dalam folder outputs/ dengan format yang siap diunggah (submit) ke kompetisi Kaggle.