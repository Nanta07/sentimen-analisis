## Evaluasi Dataset & Label
**1. Struktur Dataset**
Dataset sudah **digunakan** untuk analisis sentimen karena memiliki kolom teks ulasan (`content`) dan telah melalui tahapan *cleaning*, *case folding*, *slang normalization*, *stopword removal*, hingga *tokenizing*.

**2. Pelabelan (Label Validity)**
Pelabelan sentimen menggunakan **lexicon-based labeling** (kamus positif & negatif) sudah **sesuai untuk baseline supervised learning**, namun perlu dicatat bahwa:
* Label **bukan ground truth manual**, melainkan hasil otomatis.
* Tidak ada kelas *neutral*, sehingga data bisa bias ke positif/negatif.
* Cocok untuk eksperimen awal dan perbandingan model, **namun belum ideal untuk klaim akurasi tinggi**.

**3. Notes tambahan**
* Pendekatan lexicon-based digunakan sebagai **pseudo-labeling**.
* Dataset sudah bersih dari duplikasi dan missing value.
* Pipeline preprocessing cukup lengkap untuk konteks e-commerce Indonesia.

**4. Improvements**
* Tambahkan **validasi manual (sampling)** untuk mengecek kualitas label.
* Tambahkan kelas **neutral** atau threshold score.
* Bandingkan hasil lexicon-based vs model ML (LogReg / SVM).
