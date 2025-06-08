# Unsupervised Segmentation of Wholesale Customers

## 📖 Overview  
This project applies **unsupervised learning** to a real-world wholesale‐customer dataset, with the goal of discovering natural customer segments based on annual spending patterns. We perform extensive exploratory data analysis (EDA), compare multiple clustering algorithms, tune their hyperparameters, and arrive at three actionable customer groups that can drive targeted marketing and inventory decisions.

---

## 📂 Dataset  
- **Source:** “Wholesale customers” dataset on Kaggle  
  (https://www.kaggle.com/datasets/binovi/wholesale-customers-data-set)  
- **Description:** 440 customers × 8 columns  
  | Column             | Type    | Description                                                  |
  |--------------------|---------|--------------------------------------------------------------|
  | Channel            | int     | 1 = Hospitality, 2 = Retail                                  |
  | Region             | int     | 1 = Lisbon, 2 = Oporto, 3 = Other                            |
  | Fresh              | numeric | Annual spending on fresh products (\$)                       |
  | Milk               | numeric | Annual spending on milk products (\$)                        |
  | Grocery            | numeric | Annual spending on grocery items (\$)                        |
  | Frozen             | numeric | Annual spending on frozen products (\$)                      |
  | Detergents_Paper   | numeric | Annual spending on detergents & paper products (\$)          |
  | Delicassen         | numeric | Annual spending on deli items (\$)                           |

---

## 🎯 Project Goal  
1. **Understand**: Explore and visualize spending distributions, feature relationships, and latent structure.  
2. **Segment**: Compare clustering methods (K-Means, GMM, Hierarchical, DBSCAN), tune hyperparameters (e.g. k=2–6), and select the best unsupervised model.  
3. **Action**: Interpret and profile each segment, then propose targeted promotions or inventory strategies for each group.

---

## 🔬 Methodology  
1. **Data Cleaning & Transformation**  
   - Checked for missing values, duplicates, and zero spenders (none found).  
   - Applied `log1p` to all six spending features to reduce right skew and handle zeros safely.  
   - Standardized features (zero mean, unit variance).

2. **Exploratory Data Analysis**  
   - **Univariate:** Histograms & boxplots (raw vs. log1p) to assess skew and outliers.  
   - **Bivariate:** Correlation heatmap to identify strongly related categories.  
   - **Dimensionality Reduction:** PCA & t-SNE to visualize the dominant signal (Channel vs. Retail).

3. **Clustering & Tuning**  
   - **Algorithms:**  
     - **K-Means** (k=2…6)  
     - **Gaussian Mixture Models** (components=2…6, covariance types)  
     - **Hierarchical Clustering** (linkages: ward, average, complete; k=2…6)  
     - **DBSCAN** (grid over eps & min_samples)  
   - **Metrics:** Silhouette score, Davies–Bouldin index, Calinski–Harabasz score  
   - **Validation:** Stability checks via multiple random seeds, bootstrap resampling, and hold-out testing.

---

## 🏆 Results  
- **Final Model:** Hierarchical clustering (average linkage, k = 3)  
- **Cluster Quality:**  
  - Full data silhouette ≈ 0.54  
  - Hold-out silhouette ≈ 0.17  
- **Three Customer Segments:**  
  1. **Grocery & Dairy–Heavy**  
     - Very high Grocery ($9.7K) & Milk ($5.6K) spend  
  2. **All-Around Large Accounts**  
     - Highest spend across all categories (Fresh ≈ $11.3K, Grocery ≈ $10.5K, etc.)  
  3. **Produce & Frozen Specialists**  
     - Focus on Fresh ($8.0K) & Frozen ($2.0K), minimal Grocery/Milk  

---

## 🚀 Next Steps  
- **Business Actions:**  
  - Cluster 0 → offer Dairy/Grocery bundle promotions  
  - Cluster 1 → negotiate enterprise‐scale contracts  
  - Cluster 2 → upsell Fresh & Frozen product bundles  
- **Further Improvements:**  
  - Incorporate temporal order patterns or customer demographics  
  - Test cluster stability by season or quarter  
  - Experiment with advanced methods (e.g. HDBSCAN or ensemble clustering)  
  - Pilot A/B tests to measure promotion lift  

