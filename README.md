# 📖 Spanish–Kekchi Machine Translation Enhancement

This repository contains all code, notebooks, models, and documentation for **David Pineda’s final project** in Machine Translation. The work explores methods to improve **low-resource translation** using linguistically motivated gloss pretraining and hybrid random embeddings.

---

## 🧩 Project Overview

- **Languages:** Spanish → Kekchi
- **Corpus:** 164,903 sentence pairs from LDS religious text domain
- **Backbone:** mBART-50
- **Techniques Used:**
  - IBM Model 2 alignment for gloss pretraining
  - Interlinear Glossed Text (IGT) input formatting
  - Random Gaussian embeddings for rare tokens
  - Fine-tuning and evaluation using BLEU, ChrF++, ROUGE-L, COMET

---

## 🗂️ Repository Structure

| File / Folder | Description |
|---------------|-------------|
| `Baseline_Transformer.ipynb` | Baseline mBART-50 fine-tuning on Spanish–Kekchi |
| `IBM_2_Transformer.ipynb` | Gloss pretraining using IGT format |
| `IBM_&_Hybrid_Embedding_0_7.ipynb` | Gloss + Hybrid Embeddings (threshold 0.7) |
| `IBM_&_Hybrid_Embedding_0_9.ipynb` | Gloss + Hybrid Embeddings (threshold 0.9) |
| `baseline_transformer.py` | Script version of baseline notebook |
| `ibm_2_transformer.py` | Script version of gloss pretraining notebook |
| `ibm_&_hybrid_embedding_0_7.py` | Script version for hybrid (0.7) |
| `ibm_&_hybrid_embedding_0_9.py` | Script version for hybrid (0.9) |
| `README.md` | 📄 This document |
| `data/` | Train, validation, and test splits (not uploaded here) |
| `models/` | Final model checkpoints (local directory only) |
| `demo_video_link.txt` | Link to video walkthrough |

---

## 🧠 Methodology

### 1. Baseline Fine-Tuning
Fine-tune the mBART-50 multilingual model on aligned sentence pairs.

### 2. Gloss Pretraining (IGT)
Pretrain using `[SRC] ... [GLOSS] ...` formatted triples.

**Example:**
```
yo → INFL.PRS.1 → in  
quiero → WANT.PRS.1 → k'ut  
comer → EAT → wa'  
```

**Triple:**
```
("yo quiero comer", "INFL.PRS.1 WANT EAT", "in k'ut wa'")
```

### 3. Hybrid Random Embeddings
Replace rare word embeddings (based on frequency threshold) with random Gaussian vectors to enhance robustness in low-resource settings.

---

## 📊 Results Summary

| Model | BLEU | ChrF++ | ROUGE-L | Exact Match (%) | COMET |
|-------|------|--------|---------|------------------|--------|
| Baseline | 25.43 | 46.95 | 0.41 | 0.50 | 0.6366 |
| + IGT Pretraining | 35.31 | 60.67 | 0.59 | 2.70 | 0.7304 |
| + IGT + Hybrid Embedding (0.9) | **38.77** | **62.79** | **0.61** | 2.10 | **0.7383** |
| + IGT + Hybrid Embedding (0.7) | 0.24 | 5.46 | 0.05 | 0.00 | 0.2238 |

---

## 📦 Requirements

```bash
pip install transformers sentencepiece torch sacrebleu pandas scikit-learn
```

---

## ▶️ How to Run

You can run any `.ipynb` notebook directly, or use the `.py` script versions like this:

```bash
python ibm_&_hybrid_embedding_0_9.py
```

Make sure the training/validation/test data is in a folder named `data/` with files like:
- `train.csv`
- `val.csv`
- `test.csv`

---

## 📹 Demo Video

🎥 Loom walkthrough of the project:  
[https://www.loom.com/share/2f3516256307415ba195325f26a82555?sid=8c258945-20f2-42c8-bc9d-c6c80bc29788](https://www.loom.com/share/2f3516256307415ba195325f26a82555?sid=8c258945-20f2-42c8-bc9d-c6c80bc29788)

---

## 🔁 Revisions Based on Feedback

- **Presentation:** Added slide examples of gloss triples with Kekchi equivalents (`in`, `k’ut`, `wa’`)
- **Paper:** Emphasized threshold impact (0.9 > 0.7), clarified hybrid method
- **Related Work:** Cited 2024 paper on random embeddings: *Tokarchuk & Niculae (2024)*

---

## ⏱️ Hours Log

| Task                        | Hours |
|-----------------------------|-------|
| Research + Paper Writing    | 26    |
| Code Development & Training | 22    |
| Data Preprocessing & Alignments | 10 |
| Slide Design + Presentation | 6     |
| Demo Video Recording        | 2     |
| **Total**                   | **66 hrs** |

---

## 📚 References

- Tokarchuk, E., & Niculae, V. (2024). *The Unreasonable Effectiveness of Random Target Embeddings...*
- NLLB Team (2022). *No Language Left Behind.*
- Liu et al. (2020). *Multilingual Denoising Pretraining...*

---

## 🙏 Acknowledgments

Special thanks to the BYU Machine Translation Lab for providing the Spanish–Kekchi dataset and guidance.

---