# Dataset Information

This project uses the **NERSkill.Id** dataset for training and evaluating the IndoBERT-based Named Entity Recognition (NER) model.

---

## 📌 Dataset Source

NERSkill.Id  
Published: 14 November 2023  
DOI: 10.17632/5s8r9ndfvc.1  
License: CC BY 4.0  

Official source:
https://data.mendeley.com/datasets/5s8r9ndfvc/1

---

## ⚠️ Important Notice

The dataset is **not redistributed** in this repository.

NERSkill.Id is publicly available through Mendeley Data under CC BY 4.0 license.  
To ensure proper attribution and compliance with dataset ownership, users must download it directly from the official source.

---

## 📥 How to Use the Dataset

1. Download `NERSkill.Id.txt` from the official Mendeley repository.
2. Place the file inside this `data/` directory.

Expected structure:

```
project-root/
│
├── IndoBERT_NER_Skill_Extraction.ipynb
├── data/
│   ├── README.md
│   └── NERSkill.Id.txt
```

---

## 📊 Dataset Characteristics

- 418,868 annotated tokens
- BIO tagging scheme
- 3 entity categories:
  - Hard Skill (HSkill)
  - Soft Skill (SSkill)
  - Technology (Tech)
- CoNLL-2003 format

---

If you use the dataset in academic work, please cite the original dataset publication as well.
