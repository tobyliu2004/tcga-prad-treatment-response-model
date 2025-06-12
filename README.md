# TCGA-PRAD Treatment Response Prediction

This project builds predictive models to classify **prostate cancer patients** as **responders vs. non-responders** to primary therapy using **TCGA-PRAD** mutation and expression data. It was developed as part of a biomedical machine learning research internship.

---

## Data Source
- TCGA Prostate Adenocarcinoma (PRAD) cohort
- Retrieved from UCSC Xena Browser
- Modalities used:
  - **Somatic mutations (MAF)** → binary mutation matrix
  - **Gene expression (log2 FPKM)** → continuous normalized matrix
  - **Phenotype** → response labels derived from `primary_therapy_outcome_success`

---

## Modeling Pipeline

### 1. **Mutation Model**
- Feature selection via **Fisher’s Exact Test**
- 77 most significant mutation genes selected
- Deep learning classifier (Keras) → **AUC: 0.98**

### 2. **Expression Model**
- Feature selection via **t-tests**
- Top 500 genes with lowest p-values selected
- Deep learning classifier with class balancing → **AUC: 0.95**

### 3. **Combined Model**
- Concatenated 77 mutation + 500 expression features
- Final deep learning model trained
- **Test AUC: 0.88**
- **Recall (non-responders): 0.67**
- Balanced performance across classes

---

## Key Results

| Model       | Features       | AUC  | Recall (Class 0) | Notes |
|-------------|----------------|------|------------------|-------|
| Mutation    | 77 genes       | 0.98 | 0.83             | Excellent |
| Expression  | 500 genes      | 0.95 | 0.66             | Strong |
| Combined    | 577 features   | 0.88 | 0.67             | Best balance |

---

## Files

- `combined_model.ipynb`: Full multimodal training pipeline
- `figures/`: ROC + confusion matrix visualizations
- `README.md`: Project overview

---

## Future Work
- Test on additional cancer types (TCGA-BLCA, BRCA)
- Incorporate clinical features (PSA, Gleason, smoking)
- Use ensemble methods (Random Forest, XGBoost)

---

## Contact

Feel free to reach out via [LinkedIn](https://www.linkedin.com/in/toby-liu-b45090257) if you want to collaborate or learn more.
