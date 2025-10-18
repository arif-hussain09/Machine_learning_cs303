[View Full AdaBoost Report (Google Docs)](https://docs.google.com/document/d/1yMBXdtLXQG9o3I6pJhftz3Usj3Qv03u8JlczORvnjao/edit?usp=sharing)

# Analysis Report: Boosting Ensemble - AdaBoost (Adaptive Boosting)

This section analyzes **Boosting**, a sequential ensemble strategy, using **AdaBoost** as the primary example.  
The observations clearly articulate how Boosting tackles the challenge of **high-bias models**.

---

## I. Core Concept: Sequential Error Correction 📈

Unlike parallel methods (**Voting**, **Bagging**) which aim to reduce **variance**, **Boosting** is fundamentally designed to build an **additive, highly accurate model** by systematically correcting the errors of preceding *weak* learners.

| Feature         | Observation (Intuition)                                             | Technical Synthesis                                                                                  |
|-----------------|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| **Process**     | "Boosting is a sequential process and good for high bias and low variance models." | Confirmed. Boosting is sequential. It is most effective when base models (like Decision Stumps) have high bias (i.e., they are weak learners). The sequential process systematically reduces this bias to create a final strong learner. |
| **Base Estimator** | "In AdaBoost specifically we use weak learners like decision stumps." | Exactly. A **Decision Stump** (a decision tree with a maximum depth of 1) is the quintessential weak learner for AdaBoost, as it has low variance but high bias—perfect for boosting. |
