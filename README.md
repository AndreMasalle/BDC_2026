# BDC 2026

| Nama Anggota | ID           |
|--------------|--------------|
| Darel Ajni Fahrezi          | 103012580009 |
| Ramadhan Abdul Aziz         | 103012580007 |
| Andre Fransiscus Masalle       | 103012580019 |

Repo ini berisi model untuk kompetisi BDC 2026 – klasifikasi teks tweet ke dalam 8 aspek kebijakan Makan Bergizi Gratis (MBG).

## Arsitekur Sistem
- **Model**: IndoBERTweet (`indolem/indobertweet-base-uncased`)
- **Loss**: Focal Loss dengan class weight
- **Augmentasi**: Penyisipan golden N-gram eksklusif untuk kelas minoritas
- **Evaluasi**: 5-fold stratified cross-validation, metrik Balanced Accuracy
- **Inferensi**: Ensemble 5 model

## Struktur Repo
1. `eda.ipynb` – Notebook eksplorasi data (panjang teks, emoji, golden N-gram)
2. `train.ipynb` – Notebook pelatihan 5-fold, augmentasi, dan error analysis
3. `inference.py` – Kelas `MBGPipeline` untuk inferensi(penggunaan) model ensemble


## Langkah Penggunaan

1. Instalasi: 
   ```bash
   pip install -r requirements.txt

2. Cleaning: tercakup dalam 1 function
3. EDA :
   - Menunjukkan distribusi panjang teks
   - Analisis N-gram
   - Analisis Emoji
3. Train:
   - Augmentasi dengan N-gram
   - Melatih 5 model
   - Menyimpan model
   - Menampilkan evaluasi

3. Error Analysis: 
   - Menunjukkan Heatmap dari confusion matrix
   - Memberikan Evaluasi dari klasifikasi

4. Inferensia:
   - Menggabungkan model pada semua fold menjadi ensemble model
   - Memprediksi data yang diberikan
   - Menyimpan hasil dalam bentuk 'submission_ensembl.xlsx'