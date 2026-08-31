# Analisis Sentimen Kebijakan Efisiensi Anggaran

Analisis Sentimen Publik terhadap Kebijakan Efisiensi Anggaran Pemerintah Tahun 2025 di Media Sosial X Menggunakan Support Vector Machine (SVM) dan IndoBERT.

## Deskripsi

Penelitian ini menganalisis sentimen publik terhadap kebijakan efisiensi anggaran pemerintah tahun 2025 pada media sosial X (Twitter). Penelitian membandingkan kinerja dua metode klasifikasi sentimen, yaitu Support Vector Machine (SVM) dengan pembobotan TF-IDF dan IndoBERT melalui proses fine-tuning, untuk menentukan metode yang memberikan kinerja terbaik dalam mengklasifikasikan sentimen ke dalam kategori positif, netral, dan negatif.

Penelitian diimplementasikan menggunakan Python pada Google Colaboratory.

## Dataset

Data dikumpulkan dari media sosial X menggunakan TweetHarvest (https://github.com/helmisatria/tweet-harvest) pada periode 22 Januari–31 Maret 2025, menggunakan sembilan kata kunci terkait kebijakan efisiensi anggaran, dengan filter bahasa Indonesia.

Tahapan pembersihan data:
- Data mentah hasil crawling: 5.026 cuitan
- Setelah deduplikasi berdasarkan ID cuitan: 4.374 cuitan
- Setelah penyaringan bahasa (Indonesia): 4.345 cuitan (dataset final)

Distribusi label:
- Negatif: 3.786 cuitan (87,13%)
- Positif: 423 cuitan (9,74%)
- Netral: 136 cuitan (3,13%)

### Skema Kolom Dataset Final

| Kolom | Keterangan |
|---|---|
| full_text | Teks cuitan asli |
| normalized_text | Teks setelah tahap text preprocessing |
| skor | Skor polaritas dari leksikon InSet |
| label | Label sentimen akhir (positif, netral, netral) |

Struktur folder data:
- `dataset_mentah.csv` — data gabungan hasil crawling TweetHarvest
- `dataset_labeled.csv` — data setelah text preprocessing dan pelabelan

## Hasil Model

| Metrik | SVM | IndoBERT |
|---|---|---|
| Accuracy | 84,46% | 88,72% |
| Macro Precision | 0,5433 | 0,5998 |
| Macro Recall | 0,5568 | 0,5641 |
| Macro F1-score | 0,5401 | 0,5796 |

Berdasarkan seluruh metrik evaluasi, IndoBERT mengungguli SVM, sehingga IndoBERT merupakan metode dengan kinerja terbaik pada penelitian ini. Kedua model menunjukkan kinerja yang baik pada kelas negatif, namun masih terbatas pada kelas netral dan positif akibat jumlah data yang sedikit pada kedua kelas tersebut.

## Struktur Repositori

- `data/` — dataset mentah dan dataset final berlabel
- `notebooks/` — notebook penelitian (crawling, preprocessing, pelabelan, pemodelan, dan evaluasi)
- `requirements.txt` — daftar pustaka yang digunakan

## Pustaka

Penelitian ini menggunakan Python dengan pustaka utama seperti pandas, scikit-learn, Sastrawi, transformers, PyTorch, matplotlib, dan wordcloud. Pengumpulan data menggunakan TweetHarvest.

## Catatan

Dataset yang dibagikan tidak menyertakan informasi identitas pengguna demi menjaga privasi.
