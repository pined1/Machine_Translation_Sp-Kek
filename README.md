# 📖 Spanish–Kekchi Machine Translation Enhancement

This project explores methods to improve **low-resource machine translation** for the Spanish–Kekchi language pair using:

- **Interlinear Glossed Text (IGT) Pretraining** based on IBM Model 2 alignments
- **Hybrid Random Embeddings** for rare word handling
- **Baseline fine-tuning** with mBART-50 on parallel sentence pairs

The experiments demonstrate substantial improvements in translation quality through linguistically motivated pretraining and embedding strategies.

---

## 🚀 Project Structure

| File | Description |
|------|-------------|
| `Baseline_Transformer.ipynb` | Fine-tuning mBART-50 directly on Spanish–Kekchi sentence pairs (Baseline). |
| `IBM_2_Transformer.ipynb` | Pretraining with Interlinear Glossed Text triples from IBM Model 2 alignments. |
| `IBM_&_Hybrid_Embedding_0_7.ipynb` | Gloss pretraining + hybrid embeddings (threshold = 0.7). |
| `IBM_&_Hybrid_Embedding_0_9.ipynb` | Gloss pretraining + hybrid embeddings (threshold = 0.9). |

---

## 📝 Methodology

1. **Baseline Fine-Tuning:**  
   Fine-tune the mBART-50 multilingual model on Spanish–Kekchi aligned sentence pairs.

2. **Interlinear Glossed Text (IGT) Pretraining:**  
   Pre-train the model by formatting the input as `[SRC] Spanish Sentence [GLOSS] Glosses` triples generated using IBM Model 2 alignments.

3. **Hybrid Random Embeddings:**  
   Replace embeddings for rare tokens (frequency < threshold) with random Gaussian vectors to improve rare word translation.

---

## 📊 Results Summary

| Model | BLEU | ChrF++ | ROUGE-L | Exact Match (%) | COMET |
|------|------|--------|---------|----------------|-------|
| Baseline | 25.43 | 46.95 | 0.41 | 0.50 | 0.6366 |
| + IGT Pretraining | 35.31 | 60.67 | 0.59 | 2.70 | 0.7304 |
| + IGT Pretraining + Hybrid Embedding (0.9) | **38.77** | **62.79** | **0.61** | 2.10 | **0.7383** |
| + IGT Pretraining + Hybrid Embedding (0.7) | 0.24 | 5.46 | 0.05 | 0.00 | 0.2238 |

---

## 📂 Dataset

- **Corpus:** Spanish–Kekchi parallel corpus from the BYU Machine Translation Lab
- **Size:** 164,903 aligned sentence pairs
- **Domain:** Primarily religious (LDS Church translations)

---

## 📚 References

- McCarthy, Arya D., Mielke, Sabrina J., & Yarowsky, David (2020). *Using Interlinear Glosses as Pivot in Low-Resource Multilingual Machine Translation*. EMNLP 2020. [Link](https://aclanthology.org/2020.emnlp-main.304)
- Zhang, Xuan & Duh, Kevin (2023). *Improving Sign Language Gloss Translation with Low-Resource Machine Translation Techniques*. Springer. [Link](https://doi.org/10.1007/978-3-031-14280-4_2)

---

## Link to video Loom:
[Loom Video](https://www.loom.com/share/2f3516256307415ba195325f26a82555?sid=8c258945-20f2-42c8-bc9d-c6c80bc29788)

## ✨ Acknowledgements

Special thanks to the BYU Machine Translation Lab for providing the Spanish–Kekchi dataset.
