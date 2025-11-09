# 🧪 Lab 06 (2 hrs) – Model Metrics & Hyperparameter Tuning

## 🎯 Learning Outcomes
By the end of this lab, students will be able to:

1. Apply and interpret **confusion matrix**, **ROC AUC**, **precision**, **recall**, and **F1-score**.  
2. Perform **stratified cross-validation** and explain its importance in imbalanced datasets.  
3. Run **grid search** and **random search** for hyperparameter tuning.  
4. Visualize and compare model performance across different hyperparameters.  
5. Justify model selection based on both metrics and computational trade-offs.  

---

## ⏱️ Activities (100 min)

### 1. Preprocessing (15 min)
- Load and clean **churn dataset**.  
- Encode categorical variables, scale features, and check class distribution.  
- Perform **train/test split**.

---

### 2. Baseline Logistic Regression (20 min)
- Train with **default parameters**.  
- Create metrics table (**accuracy**, **precision**, **recall**, **F1**, **ROC AUC**).  
- Plot **confusion matrix** and **ROC curve**.

---

### 3. Cross-Validation (20 min)
- Apply **Stratified k-Fold Cross-Validation (k=5)**.  
- Compare with **non-stratified CV** to show stability improvement.

---

### 4. Hyperparameter Tuning (30 min)
- Tune **Logistic Regression** (`C` parameter).  
- Tune **Random Forest** (`n_estimators`, `max_depth`).  
- Use:
  - `GridSearchCV`
  - `RandomizedSearchCV`
- Visualize results (validation score heatmap, best parameters).

---

### 5. Model Comparison (15 min)
- Compare **best Logistic Regression** vs **best Random Forest**.  
- Summarize performance using:
  - **Confusion Matrix**
  - **ROC Curve**
  - **Cross-Validation metrics**

---

📘 **End of Lab**
