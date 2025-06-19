# Patient Wellness Clustering with PCA and Machine Learning

## Project Overview

In today's healthcare landscape, wellness and preventive health have become critical areas of focus. This project applies unsupervised machine learning techniques—**K-Means** and **Hierarchical Clustering**—to segment patients based on lifestyle indicators such as:

- Daily Exercise Time
- Number of Healthy Meals per Day
- Sleep Duration per Night
- Stress Level Score
- Body Mass Index (BMI)

The aim is to discover meaningful **wellness profiles** that can guide healthcare organizations in delivering **targeted interventions**. Dimensionality reduction using **Principal Component Analysis (PCA)** was applied to enhance clustering effectiveness and interpretability (Jolliffe & Cadima, 2016).

---

##  Dataset Description

The dataset includes **200 simulated patient records** with the following features:

| Feature Name              | Description                                      |
|--------------------------|--------------------------------------------------|
| `Exercise_Time_Min`      | Daily exercise time in minutes                   |
| `Healthy_Meals_Per_Day`  | Number of healthy meals consumed per day         |
| `Sleep_Hours_Per_Night`  | Number of sleep hours per night                  |
| `Stress_Level`           | Perceived stress level (scale 1–10)              |
| `BMI`                    | Body Mass Index                                  |

---

##  Methods and Techniques

### 1. Exploratory Data Analysis (EDA)

- Used **Seaborn**, **Matplotlib**, and **Plotly** to visualize data distributions and correlations.
- Correlation analysis revealed some moderate patterns (e.g., lower exercise time associated with higher BMI).
- No obvious clusters were visible from raw feature space.

### 2. Clustering Models

#### K-Means Clustering

- A partitioning method that minimizes within-cluster variance.
- Tested `k` values from 2 to 10.
- Optimal `k = 3` selected using the **Elbow Method** and **Silhouette Score** (Rousseeuw, 1987).

####  Hierarchical Clustering

- Agglomerative clustering using **Ward’s linkage** and **Euclidean distance**.
- Dendrogram visualizations used to identify natural cluster boundaries.
- Cluster count matched K-Means for comparison.

### 3. Dimensionality Reduction - PCA

- Reduced the 5-feature dataset to **2 principal components**.
- The first two components captured over 80% of variance (Jolliffe & Cadima, 2016).
- Enabled better **cluster separation** and **visual interpretation**.
- Helped reduce feature redundancy and improve clustering stability.

---

## Model Evaluation

| Model Type         | Dataset Used      | Silhouette Score | Interpretation                                               |
|--------------------|-------------------|------------------|---------------------------------------------------------------|
| K-Means            | Original Data     | 0.152            | Weak cluster separation; overlapping clusters                |
| Hierarchical       | Original Data     | 0.136            | Slightly lower performance than K-Means                      |
| K-Means            | PCA-Reduced       | **0.363**            | **Improved separation and compactness**                       |
| Hierarchical       | PCA-Reduced       | **0.363**            | **Matched K-Means; clearer boundaries post-PCA**             |

---

## Visualizations

- Pairplots, histograms, and heatmaps to explore feature relationships.
- Scatter plots of clusters before and after PCA.
- Dendrogram to visualize hierarchical cluster merging.
- PCA explained variance plot to justify component selection.

---

##  Key Findings

- **PCA significantly improved clustering quality**, increasing silhouette score from ~0.15 to ~0.36.
- In PCA space, clusters were more compact and clearly separated.
- Both clustering methods performed similarly **after dimensionality reduction**.

---

## Importance of Dimensionality Reduction

- Helps in removing irrelevant or correlated features.
- Improves computational efficiency and clustering accuracy.
- Enhances visualization by reducing data to 2D or 3D space (Wold et al., 1987).
- Particularly valuable in healthcare analytics where features may be interdependent.

---

##  Conclusions & Recommendations

- Clustering patients can support **personalized wellness plans**.
- PCA should be applied in healthcare ML projects to handle high-dimensional or correlated features.
- Future research may explore **temporal patterns** or integrate **demographic data**.

---

## 📖 References

- Jolliffe, I. T., & Cadima, J. (2016). Principal component analysis: A review and recent developments. *Philosophical Transactions of the Royal Society A: Mathematical, Physical and Engineering Sciences, 374*(2065), 20150202. https://doi.org/10.1098/rsta.2015.0202  
- Rousseeuw, P. J. (1987). Silhouettes: A graphical aid to the interpretation and validation of cluster analysis. *Journal of Computational and Applied Mathematics, 20*, 53–65. https://doi.org/10.1016/0377-0427(87)90125-7  
- Wold, S., Esbensen, K., & Geladi, P. (1987). Principal component analysis. *Chemometrics and Intelligent Laboratory Systems, 2*(1-3), 37–52. https://doi.org/10.1016/0169-7439(87)80084-9

---
