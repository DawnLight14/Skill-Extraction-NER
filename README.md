# IndoBERT-Based Named Entity Recognition for Skill Extraction in Indonesian Job Postings

Domain-Specific NER using Transformer Architecture for Structured Skill Identification

This research project develops a Named Entity Recognition (NER) model based on IndoBERT to automatically extract skill-related entities from Indonesian job vacancy texts.

The study evaluates transformer-based fine-tuning performance on a domain-specific dataset (NERSkill.Id) and analyzes model behavior across different skill categories.

---

## 🎯 Research Objective

To develop and evaluate an IndoBERT-based NER model optimized for extracting three categories of skill entities:

- Hard Skill (HSkill)
- Soft Skill (SSkill)
- Technology (Tech)

The model performance is evaluated using Precision, Recall, and F1-score under the BIO tagging scheme.

---

## 📚 Dataset

This study uses the publicly available dataset:

**NERSkill.Id**  
DOI: 10.17632/5s8r9ndfvc.1  
License: CC BY 4.0  

NERSkill.Id is the first annotated Indonesian corpus specifically designed for skill entity recognition.

### Dataset Characteristics

- 418,868 tokens  
- BIO annotation scheme  
- 3 entity categories: HSkill, SSkill, Tech  
- CoNLL-2003 format  

### Token Distribution

- O (Outside): 349,597  
- B-HSkill: 17,003  
- I-HSkill: 11,508  
- B-SSkill: 10,891  
- I-SSkill: 3,858  
- B-Tech: 17,296  
- I-Tech: 4,414  

Due to licensing considerations, the dataset is not redistributed in this repository.  
Please download it directly from Mendeley Data.

---

## 🏗 Methodology

The research pipeline consists of four main stages:

### 1️⃣ Data Processing

- WordPiece tokenization using IndoBERT-base-p1 tokenizer  
- BIO label alignment for sub-token handling  
- Tensor conversion for transformer input  
- Dataset split: 80% training, 10% validation, 10% testing  

### 2️⃣ Model Configuration

- Pretrained Model: IndoBERT-base-p1  
- Task: Token Classification  
- Optimizer: AdamW  
- Early stopping based on validation F1-score  

### 3️⃣ Hyperparameter Experiments

| Experiment | Learning Rate | Epochs | Batch Size |
|------------|--------------|--------|------------|
| Exp 1 | 3e-5 | 3 | 8 |
| Exp 2 | 3e-5 | 5 | 8 |
| Exp 3 | 2e-5 | 3 | 8 |
| Exp 4 | 2e-5 | 5 | 8 |
| Exp 5 | 1e-5 | 3 | 8 |
| Exp 6 | 1e-5 | 5 | 8 |

**Best Configuration:**

- Learning rate: 3e-5  
- Epochs: 5  
- Batch size: 8  

---

## 📊 Evaluation Results

### Overall Performance (Test Set)

| Metric | Score |
|--------|-------|
| Precision | 0.77 |
| Recall | 0.80 |
| F1-score | 0.78 |
| Token-level Accuracy | 0.93 |

The model demonstrates stable performance, with slightly higher recall indicating strong sensitivity in detecting skill entities.

---

## 📈 Performance per Entity Category

| Entity | Precision | Recall | F1-score | Support |
|--------|----------|--------|----------|---------|
| HSkill | 0.60 | 0.67 | 0.64 | 1660 |
| SSkill | 0.79 | 0.85 | 0.82 | 1116 |
| Tech | 0.83 | 0.86 | 0.85 | 1831 |

### Key Observations

- Technology entities achieved the highest performance.
- Soft skills showed strong recall but minor overprediction.
- Hard skills were the most challenging category.
- Class imbalance and contextual ambiguity influenced model behavior.

---

## 🔎 Error Analysis

Dominant error types identified:

1. Boundary errors in multi-token entities (BIO misalignment).
2. Confusion between Hard Skill and Technology categories.
3. False negatives for context-dependent soft skills.
4. High stability in detecting non-entity (O) tokens.

These findings indicate that contextual semantic ambiguity and entity boundary detection remain key challenges in Indonesian skill extraction tasks.

---

## 📓 Notebook

All experiments, training processes, evaluation, and error analysis are documented in:

`ner_skill_indobert.ipynb`

The notebook includes:

- Dataset exploration  
- Tokenization & label alignment  
- Hyperparameter experiments  
- Model training  
- Evaluation using seqeval  
- Per-category analysis  
- Error analysis  
- Inference examples  

---

## 🛠 Tech Stack

- Python  
- HuggingFace Transformers  
- IndoBERT-base-p1  
- PyTorch / TensorFlow  
- Seqeval  
- Scikit-learn  
- Pandas / NumPy  
- Matplotlib / Seaborn  

---

## 🚀 Practical Implications

The proposed model can support:

- Automated skill extraction from job postings  
- Recruitment analytics systems  
- Structured talent–skill matching  
- Labor market intelligence analysis  

This project contributes to the development of domain-specific NLP solutions for Indonesian-language recruitment systems.

---

## 👤 Author

Nicholas Ryan Jonathan  
Bachelor of Informatics – Data Science  

LinkedIn: https://linkedin.com/in/nichoryjo  
GitHub: https://github.com/DawnLight14
