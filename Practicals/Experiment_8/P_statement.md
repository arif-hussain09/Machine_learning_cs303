# 🧪 Lab Experiment 8

## 🎯 Objective
To implement and compare the **performance**, **training time**, and **hyperparameter sensitivity** of the **AdaBoost Classifier (Adaptive Boosting)** and the **XGBoost Classifier (eXtreme Gradient Boosting)** on a real-world classification task.

---

## 📊 Dataset

**Dataset Name:** Adult Income Dataset (or Census Income Dataset)  
**Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/2/adult)  
**Prediction Task:** Binary Classification  
→ Predict whether an individual's annual income exceeds \$50,000 (i.e., `>50K` vs. `<=50K`).

**Characteristics:**
- Large and multivariate dataset  
- Contains both categorical and numerical features  
- Slightly imbalanced (fewer individuals earn >50K)  
- Ideal for testing boosting algorithms  

---

## ⚙️ Experimental Phases

### **Phase 1: Data Preprocessing & Baseline**

#### 🧩 Data Loading and Initial Cleaning
- Load the dataset and handle missing values.  
- Impute missing values using **mode/median** or utilize **XGBoost's built-in missing value handling**.

#### 🧠 Feature Engineering
- **Categorical Encoding:**  
  Use **One-Hot Encoding** (or equivalent) for nominal categorical features such as  
  `workclass`, `occupation`, `education`, `marital-status`, etc.
- **Numerical Scaling:**  
  Apply **StandardScaler** or **MinMaxScaler** to continuous features such as  
  `age`, `hours-per-week`, etc.

#### 📂 Data Splitting
- Split the dataset into:
  - **Training Set:** 70%
  - **Validation Set:** 15%
  - **Test Set:** 15%
- The **validation set** will be used for **hyperparameter tuning** and **early stopping**.

#### 🧮 Baseline Model
- Build a simple **Logistic Regression** model as a baseline.
- Record the following metrics:
  - Accuracy  
  - F1-Score  
  - Precision / Recall  
  - ROC AUC  

---

### **Phase 2: Model Training and Hyperparameter Tuning**

#### 🚀 AdaBoost Classifier

- **Weak Learner:** Decision Tree Classifier (e.g., `max_depth = 1` or `max_depth = 2`) — also called a *decision stump*.
- **Hyperparameter Tuning:** Use **GridSearchCV** or **RandomizedSearchCV** with cross-validation.
  - Parameters to tune:
    - `n_estimators`: Number of weak learners  
    - `learning_rate`: Shrinkage rate for each learner  
- **Record:**
  - Best hyperparameters  
  - Training time  

---

#### ⚡ XGBoost Classifier

- **Objective:** `binary:logistic` (for binary classification)
- **Hyperparameter Tuning:** Use **GridSearchCV** or **RandomizedSearchCV** with cross-validation.
  - Key parameters:
    - `n_estimators`: Number of boosting rounds  
    - `learning_rate`: Step size shrinkage  
    - `max_depth`: Depth of each tree  
    - `subsample`: Fraction of samples per tree  
    - `colsample_bytree`: Fraction of features per tree  
    - `lambda`: L2 regularization term  
- **Early Stopping:**  
  Use the validation set to prevent overfitting and find the optimal number of trees.
- **Record:**
  - Best hyperparameters  
  - Optimal number of trees (from early stopping)  
  - Training time  

---

### **Phase 3: Evaluation and Comparison**

#### 🧾 Final Prediction
- Use the **best-tuned AdaBoost** and **XGBoost** models to predict on the **test set**.

#### 📈 Performance Metrics
Evaluate and compare:
- **Accuracy** — Overall correctness  
- **F1-Score** — Harmonic mean of precision and recall (important for imbalanced data)  
- **ROC AUC Score** — Model’s ability to distinguish between the two classes  
- **Precision / Recall** — Especially for the minority class (`>50K`)  

#### ⏱️ Training Efficiency
- Compare **training times** (including hyperparameter tuning) between AdaBoost and XGBoost.

#### 🔍 Feature Importance
- Analyze feature importance from both models to interpret which attributes most influence income prediction.

---

## 🧠 Summary
This experiment provides a comprehensive understanding of:
- How ensemble boosting methods improve classification performance  
- How hyperparameters impact training time and model accuracy  
- The trade-off between **model complexity**, **overfitting**, and **computational efficiency**
