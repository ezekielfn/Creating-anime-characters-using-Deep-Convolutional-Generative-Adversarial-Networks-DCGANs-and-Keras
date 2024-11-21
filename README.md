<h1 align="center"> NLP With HuggingFace Transformers </h1>
<p align="center"> Berisi tentang pipeline dari HuggingFace Transformers untuk keperluan NLP (Natural Language Processing)</p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">
<img src="https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white">

</div>

<h2 align="center"> Analisis </h2> 
 

1. **Zero-Shot Classification**  
   - Mengklasifikasikan teks ke dalam label kandidat tanpa pelatihan tambahan.  
   - Cocok untuk tugas klasifikasi teks yang bersifat ad-hoc.
   - Confidence score yang dihasilkan relatif rendah (di bawah 0.3), baik untuk teks berbahasa Indonesia maupun Inggris.
   - Asumsi awal bahwa model lebih akurat untuk bahasa Inggris ternyata tidak terbukti.
   - Confidence score rendah kemungkinan karena model kurang memahami domain spesifik teks Anda (Channel Probing).
   - Meski demikian, label yang diberikan sudah cukup relevan. Model mungkin memerlukan lebih banyak data pelatihan relevan atau konteks yang lebih luas untuk meningkatkan confidence score.
    
2. **Text Generation**
   - Muncul error ValueError karena panjang teks input melebihi batas maksimum model.
   - Menambahkan parameter max_new_tokens untuk mengatasi masalah tersebut.  
   - Menghasilkan teks baru berdasarkan input.  
   - Gunakan parameter `max_new_tokens` untuk mengontrol panjang teks keluaran.  

3. **Fill-Mask**  
   - Pipeline ini berguna untuk melengkapi kalimat, memprediksi kata berikutnya, atau mengidentifikasi kata yang hilang.
   - Tidak ada batasan dalam topik yang digunakan oleh pipeline ini, termasuk topik sensitif.

4. **Named Entity Recognition (NER)**  
   - Mengidentifikasi entitas bernama seperti orang, organisasi, lokasi, dll.  

5. **Question Answering**  
   - Menjawab pertanyaan berbasis teks konteks tertentu.
   - Menggunakan 2 model (distilbert-base-cased-distilled-squad dan model default), keduanya berhasil memberikan jawaban yang benar.  

6. **Sentiment Analysis**  
   - Mengidentifikasi sentimen (positif, negatif, netral) dari teks tertentu.  

7. **Summarization**  
   - Meringkas teks panjang menjadi versi yang lebih pendek.  

8. **Translation**  
   - Menerjemahkan teks antar bahasa.  

---

<h2 align="center"> Sebelum Mulai </h2> 

**Instalasi library HuggingFace:**

    pip install transformers

<h2 align="center"> Penggunaan </h2> 
   
    from transformers import pipeline
    # Contoh: Zero-Shot Classification
    classifier = pipeline("zero-shot-classification")
    result = classifier("Teks Anda di sini", candidate_labels=["Label1", "Label2", "Label3"])
    print(result)

  **Ganti pipeline sesuai kebutuhan:**
  - "text-generation"
  - "fill-mask" 
  - "ner"
  - "question-answering"
  - "sentiment-analysis"
  - "summarization"
  - "translation_*"