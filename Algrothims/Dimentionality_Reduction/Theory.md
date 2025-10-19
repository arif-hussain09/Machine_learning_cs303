# 💡 Intuitive Guide to Dimensionality Reduction Techniques

Here are the core concepts behind the key dimensionality reduction methods:

---

[For theory and graphical intuition](https://docs.google.com/document/d/1TkHlduNFsXIjI-z1CSKG7g2zRPM_dwcEj3xPWJrQBRc/edit?usp=sharing)
## 1. Principal Component Analysis (PCA)

**Concept Intuition**

- **Goal:** To find the straight lines (axes) that best represent the overall spread or variance of the data.  
- **How it Works:** Imagine shining a light on a 3D object to cast a 2D shadow. PCA finds the angle of the light that creates the longest, most informative shadow. The first component captures the most spread, the second component captures the most remaining spread, and so on.  
- **Limitation:** It's linear. It fails if the data is wrapped up in a complicated, curved shape (a manifold), like a rolled-up scroll.  
- **Image:** *(Visualization of principal components on a 2D plane)*  

---

## 2. t-distributed Stochastic Neighbor Embedding (t-SNE)

**Concept Intuition**

- **Goal:** To ensure that points close together in the original high-dimensional space stay close together in the new low-dimensional space. It prioritizes local clustering.  
- **How it Works:** It models the "closeness" of points using probabilities in both spaces. It wants the low-dimensional probabilities to match the high-dimensional ones. It uses a heavy-tailed distribution (like a loose-fitting circle) in the low dimension, which helps clusters push apart and prevents them from all crowding into the center (the *crowding problem*).  
- **Focus:** Visualization of distinct, local clusters. The distances between the clusters are often not reliable—only the internal structure of the clusters is preserved well.  
- **Image:** *(Example: colorful clusters in 2D scatter plot)*  

---

## 3. Uniform Manifold Approximation and Projection (UMAP)

**Concept Intuition**

- **Goal:** To preserve the overall topological structure (the connections and relationships between all the data points, locally and globally).  
- **How it Works:** It first maps the high-dimensional data into an abstract concept called a *fuzzy graph* (a mathematical web of connections). It then searches for the simplest, lowest-dimensional representation of that web that still retains its essential structure.  
  Think of it as mapping a complex street network onto a simpler, 2D map while trying to keep all the relative connections intact.  
- **Advantage:** It's generally faster than t-SNE and tends to do a better job of preserving the global structure (the true relationships between the clusters).  
- **Image:** *(Visualization showing global structure with separated clusters)*  

---

## 4. Other Key Methods

**Method Intuition**

- **Linear Discriminant Analysis (LDA):** It's a supervised method. Its goal is not to preserve variance, but to find the axes that provide the maximum separation between predefined classes or categories. It’s best for classification pre-processing.  

- **Isomap:** It correctly measures distances along a curved surface. Imagine two points on a rolled-up carpet; Isomap finds the shortest path by measuring along the carpet, not by tunneling straight through it.  

- **Locally Linear Embedding (LLE):** It assumes a point can be perfectly described by a weighted average of its immediate neighbors. It then tries to replicate those same neighbor relationships in the low-dimensional space.  
