# Summary of Regression Tree Mechanism: Findings Report

This document synthesizes our key observations regarding the function and structure of the **Regression Tree** model.  
The findings focus on the model's approach to data segmentation, its core splitting criterion, and the methods used to manage its complexity.

---

## I. Core Intuition: The Power of Local Clustering

We observed that the **Regression Tree** excels when there's an underlying tendency for the data to form clusters.  
It essentially carves up the feature space into distinct neighborhoods to make predictions.

### **Output Type**
- The tree continuously produces **real-valued outputs**, confirming its purpose for **regression**, not classification.

### **The Prediction Surface**
- The output is not smooth; instead, it forms **piecewise constant regions** — a series of **flat steps**.
- These “steps” correspond to local clusters in the input feature space.

---

## II. The Splitting Logic: MSE as the Guiding Metric

The tree determines where to make splits using **Mean Squared Error (MSE)** minimization.  
It chooses the threshold that results in the **greatest reduction in overall squared error**.

### **The Observed Process ("Cut" Calculation)**

1. **Finding the Cut**  
   - The algorithm tests multiple thresholds for each feature.  
   - Example: “Take two points, find their mean, and separate the rest.”  
   - This represents a **greedy search** for the best division.

2. **Calculating Error**  
   - After each potential split, the algorithm calculates the **MSE** for the resulting groups:  
     \[
     \text{MSE} = \frac{1}{N} \sum_{i=1}^{N}(y_i - \hat{y})^2
     \]

3. **Optimal Selection**  
   - The split (feature and threshold) that achieves the **lowest total MSE** is selected.  
   - This becomes the **first cut** in the tree.

4. **Recursion**  
   - The process repeats **recursively**, building a hierarchical tree structure.  
   - Each level refines the local predictions, leading to smaller, more specialized regions.

---

## III. Controlling Complexity and Avoiding Overfitting 🛑

### **Observation**
The recursive nature of splitting can cause **overfitting**, as the model might over-specialize by forming very small clusters.

### **Mitigation Strategy**
To control complexity, we impose limits on how detailed the tree can become.

### **Technical Implementation**
- Introduce a minimum sample size constraint using the hyperparameter:
  \[
  \texttt{min\_samples\_leaf}
  \]
- This ensures each leaf node has enough data points, preventing overfitting and improving generalization.

---

### ✅ **Key Takeaway**
Regression Trees segment data into locally consistent regions using **MSE-based greedy splits**.  
Proper control via hyperparameters like `min_samples_leaf` is crucial for balancing **bias and variance**.
