# AI & Data Science Explorations 🚀

Welcome to my personal laboratory for AI and Data Science. This repository serves as a documentation of my "ngulik" (hands-on exploration) sessions, moving beyond theory into practical application.

## 📌 Project Goals
- **Bridge the Gap:** Moving from 4th-semester theory at Telkom University to real-world data application.
- **Skill Building:** Mastering Python libraries (Pandas, NumPy, Matplotlib) and Machine Learning workflows.
- **Transparency:** Documenting the process, errors, and breakthroughs of every tutorial and experiment.

## 📂 Current Projects
1. **[Spotify Data Analysis](./Spotify-Data-Analysis):** - *Status:* In Progress 🚧
   - *Focus:* Analyzing track trends and artist popularity using the Simplilearn framework.
   - *Tools:* Python, Pandas, Seaborn.

## 🛠️ Tech Stack
- **Languages:** Python, SQL (PostgreSQL)
- **Environment:** Google Colab, Kaggle
- **Key Libraries:** Pandas, Scikit-Learn, Matplotlib

## 🧭 Core ML & CV Workflow (Mental Model)

Alur standar lintas eksperimen (tabular maupun citra) sebagai pegangan cepat saat membangun dan men-debug model:

1. **EDA & Problem Formulation** *(Pahami data & target)* — Tentukan fitur ($X$), target ($y$), serta jenis tugas (klasifikasi vs regresi).
2. **Data Cleaning & Preprocessing** *(Bersihkan & seragamkan)* — Tangani *missing value*/anomali di data tabular, atau *resize*/validasi/ekstraksi fitur (seperti *landmark* wajah) pada data gambar.
3. **Feature Scaling / Normalization** *(Sesuaikan skala)* — Samakan rentang nilai/piksel (`0–1`, `-1` s.d. `1`, atau *mean/std*) dengan aturan yang identik antara fase *training* dan *inference*.
4. **Train-Test Split / Cross-Validation** *(Pisahkan data latih & uji)* — Bagi data secara terkontrol untuk mengukur generalisasi dan mencegah *data leakage*.
5. **Model Training & Serialization** *(Latih & simpan model)* — Latih model (`.fit()`) lalu simpan artefaknya (`.pkl`, `.h5`, `.keras`) agar siap pakai ulang.
6. **Model Evaluation & Inference** *(Evaluasi & uji data baru)* — Cek performa lewat metrik yang relevan & *confusion matrix*, lalu uji pada data baru dengan *preprocessing* yang sama.

---
*“Done is better than perfect.” – Documenting my journey one commit at a time.*
