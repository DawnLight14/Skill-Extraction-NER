# IndoBERT for Skill Entity Extraction in Indonesian Job Vacancy Text

Named Entity Recognition (NER) for extracting skill entities (Hard Skill, Soft Skill, Technology) from Indonesian job vacancy text using a fine-tuned IndoBERT model.

This repository contains the experimental implementation associated with the published journal article listed below.

---

## 📌 Research Background

The rapid digital transformation in recruitment processes has increased the need for automated extraction of structured information from unstructured job vacancy text. One critical component in recruitment is identifying candidate skills from job descriptions.

However, extracting skill entities from Indonesian text presents several challenges:

- Limited annotated domain-specific datasets
- Imbalanced entity distribution
- Multi-word skill expressions
- Ambiguity between hard skills and technologies
- Code-mixing (Indonesian–English terms)

To address these challenges, this study fine-tunes **IndoBERT-base-p1** for Named Entity Recognition (NER) using the **NERSkill.Id** dataset.

---

## 📊 Dataset

This study uses:

**NERSkill.Id**  
Published: 14 November 2023  
DOI: 10.17632/5s8r9ndfvc.1  
License: CC BY 4.0  

Dataset characteristics:

- 418,868 annotated tokens
- BIO tagging scheme
- 3 entity categories:
  - Hard Skill (HSkill)
  - Soft Skill (SSkill)
  - Technology (Tech)
- CoNLL-2003 format
- Highly imbalanced (dominant O label)

Dataset source:
https://data.mendeley.com/datasets/5s8r9ndfvc/1

⚠️ The dataset is not redistributed in this repository.  
Please download it directly from the official source.

---

## 🧠 Methodology

### 1️⃣ Data Preprocessing

- Tokenization using IndoBERT tokenizer (WordPiece)
- BIO label alignment for sub-tokens
- Tensor conversion for transformer input
- Data split:
  - 80% Training
  - 10% Validation
  - 10% Testing

---

### 2️⃣ Model Architecture

Base model:
- IndoBERT-base-p1
- Token classification head

Training setup:
- Optimizer: AdamW
- Hyperparameter search:
  - Learning rate: 3e-5, 2e-5, 1e-5
  - Epochs: 3 and 5
  - Batch size: 8
- Early stopping based on validation F1-score

Best configuration:
- Learning rate: 3e-5
- Epochs: 5
- Batch size: 8

---

## 📈 Results

### Overall Performance (Test Set)

| Metric      | Score |
|------------|--------|
| Precision  | 0.77   |
| Recall     | 0.80   |
| F1-Score   | 0.78   |
| Token Accuracy | 0.93 |

The slightly higher recall indicates the model is more sensitive in detecting skill entities, which is beneficial in recruitment contexts where missing important skills is costly.

---

### Performance per Entity Category

| Category | Precision | Recall | F1-Score |
|----------|-----------|--------|----------|
| HSkill   | 0.60      | 0.67   | 0.64     |
| SSkill   | 0.79      | 0.85   | 0.82     |
| Tech     | 0.83      | 0.86   | 0.85     |

Observations:

- Technology (Tech) performs best due to clearer lexical patterns
- Soft Skill performs well but slightly over-predicts
- Hard Skill is most challenging due to ambiguity and overlap with Tech

---

## 🔍 Error Analysis Summary

Main error types:

1. Boundary errors (B- / I- confusion)
2. Hard Skill vs Tech misclassification
3. Multi-word entity segmentation errors
4. Context-dependent soft skill detection failures

Example issue:
"SQL Query" → incorrect B/I boundary prediction.

These findings highlight the importance of contextual modeling and better handling of multi-token entities.

---

## 📁 Repository Structure

```
IndoBERT_NER_Skill_Extraction.ipynb   → Full training & evaluation pipeline
README.md
```

All stages are implemented in a single notebook with clear sections:

- Data loading
- Preprocessing
- Label alignment
- Model training
- Evaluation
- Per-category analysis
- Error analysis
- Inference visualization

---

## 🚀 How to Run

1. Download the dataset from Mendeley
2. Place it in your working directory
3. Install dependencies:

```bash
pip install transformers torch seqeval scikit-learn pandas numpy matplotlib
```

4. Open and run:

```
IndoBERT_NER_Skill_Extraction.ipynb
```

GPU is recommended for faster training.

---

## 📖 Citation

If you use this repository in academic work, please cite:

Jonathan, N. R., Syafrijon, S., Novaliendry, D., & Budayawan, K. (2025).  
Ekstraksi Entitas Keterampilan pada Teks Lowongan Pekerjaan Berbahasa Indonesia Menggunakan Model IndoBERT.  
Jurnal Pendidikan Tambusai, 9(3), 40165–40171.  
https://doi.org/10.31004/jptam.v9i3.35210

### BibTeX

```bibtex
@article{jonathan2025indobert,
  title={Ekstraksi Entitas Keterampilan pada Teks Lowongan Pekerjaan Berbahasa Indonesia Menggunakan Model IndoBERT},
  author={Jonathan, Nicholas Ryan and Syafrijon, S. and Novaliendry, D. and Budayawan, K.},
  journal={Jurnal Pendidikan Tambusai},
  volume={9},
  number={3},
  pages={40165--40171},
  year={2025},
  doi={10.31004/jptam.v9i3.35210}
}
```

---

## 👤 Author

Nicholas Ryan Jonathan  
Bachelor of Informatics – Data Science  

GitHub: https://github.com/DawnLight14  
LinkedIn: https://linkedin.com/in/nichoryjo  

---

## 📌 Research Contribution

This study contributes to:

- Domain-specific NER for Indonesian language
- Skill extraction for recruitment automation
- Empirical evaluation of transformer-based NER on imbalanced datasets
- Detailed per-category and error analysis

---
