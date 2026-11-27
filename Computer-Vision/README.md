# 🧠 Computer Vision — Mental Model & Takeaways

Ringkasan pola dasar dan keputusan teknis dari eksplorasi awal CV di `My-AI-Labs`.

## 1. Memilih Jenis Tugas CV (Berdasarkan Output yang Dibutuhkan)
* **Image Classification:** Menjawab *"Ini kategori apa?"* untuk satu gambar utuh atau area yang sudah di-*crop* (Contoh: `NORMAL` vs `PNEUMONIA`, status 1 slot parkir).
* **Object Detection:** Menjawab *"Apa saja objeknya dan di mana letak kotaknya?"* (Output: *bounding box* + kelas).
* **Image Segmentation:** Menjawab *"Piksel mana saja yang membentuk objek ini sampai ke tepinya?"* (Output: *mask*/poligon presisi per piksel; dipakai jika bentuk kotak tidak cukup akurat).

## 2. Trade-Off Pendekatan Model
* **Feature Extraction / Landmark + ML Klasik** *(misal: MediaPipe + Random Forest)*:
  * **Kapan dipakai:** Pola objek terpusat pada struktur titik/geometri (gestur tangan, ekspresi wajah) atau fitur visual sederhana.
  * **Plus/Minus:** Sangat ringan, cepat dilatih, tahan variasi *background*, tapi bergantung penuh pada keberhasilan deteksi fitur/titik awalnya.
* **Transfer Learning / Fine-Tuning CNN** *(misal: MobileNetV2)*:
  * **Kapan dipakai:** Klasifikasi gambar mentah dengan dataset terbatas tanpa melatih bobot dari nol.
  * **Plus/Minus:** Akurasi awal cepat naik karena memakai bobot *pre-trained*, namun butuh penyesuaian *preprocessing* dan komputasi lebih besar daripada ML klasik.
* **Arsitektur Deteksi/Segmentasi Jadi** *(misal: keluarga YOLO)*:
  * **Kapan dipakai:** Butuh melokalisasi banyak objek di *scene* yang ramai atau butuh *mask* area presisi.
  * **Plus/Minus:** Sangat kuat untuk *real-time* dan *scene* kompleks, tapi biaya/waktu anotasi datanya jauh lebih tinggi.

## 3. Gotcha & Pelajaran Penting (Hal yang Sering Bikin Error/Meleset)
* **Konsistensi Preprocessing:** Aturan *resize*, urutan warna (`BGR` OpenCV vs `RGB` PIL/MediaPipe), dan skala normalisasi piksel (`0–1` vs `-1` s.d. `1`) saat *inference* **wajib identik** dengan saat *training*.
* **Kualitas Data > Kompleksitas Model:** Label yang bolong, tidak konsisten, atau jumlah sampel yang tidak seimbang jauh lebih sering merusak performa daripada sekadar kurang dalam arsitekturnya.
* **Jangan Terkecoh Output Visual:** Kotak di layar belum tentu berasal dari *object detection* (bisa saja dihitung manual dari `min/max` koordinat *landmark*), dan skor tinggi pada satu sampel belum tentu mencerminkan performa seluruh dataset—selalu cek distribusi prediksi atau *confusion matrix*.

