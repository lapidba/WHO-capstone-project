# Multidimensional Developmental Clustering & Baseline ML Analysis

## Executive Summary
Traditional single-dimensional economic metrics like Gross National Income (GNI) per capita fail to capture the complex, multidimensional nature of sovereign development. This project performs an end-to-end Exploratory Data Analysis (EDA), missing data imputation via KNN, feature engineering, principal component analysis (PCA), baseline supervised classification (Logistic Regression), and unsupervised clustering (K-Means) on World Development Indicators across 217 sovereign nations.

## Rationale
Multilateral development institutions (World Bank, IMF, regional development banks) require data-driven tools to identify structural peer nations. Relying solely on GDP thresholds can misclassify nations with strong social and health resilience as lagging, or prematurely strip low-middle income states of concessionary financing.

## Research Question
*Can we construct a robust, multidimensional developmental classification of sovereign nations using economic, health, and social infrastructure indicators to reveal non-obvious peer nations and benchmark supervised baseline predictability?*

## Data Sources
The dataset is compiled from the World Bank's World Development Indicators (WDI) repository located in `./data/`:
- **Economic:** GDP per capita (Current US$), Inflation Rate (%), Trade (% of GDP)
- **Public Health:** Life Expectancy at Birth (Years), Under-5 Child Mortality Rate (per 1,000 live births), Health Expenditure (% of GDP)
- **Social & Infrastructure:** Access to Electricity (% of population), Internet Usage (% of population)

## Methodology
1. **Data Audit & Cleaning:** Missing data inspection, duplicate row verification, quantitative outlier analysis using Interquartile Range (IQR) bounds.
2. **Feature Engineering & Preprocessing:** $\log_{10}$ transformation of skewed monetary metrics (GDP per capita), distance-weighted $K=5$ KNN Imputation, and zero-mean unit-variance `StandardScaler` normalization.
3. **Baseline Supervised Modeling:** Logistic Regression baseline classifier predicting World Bank `Income_Group` evaluated via Test Accuracy and Macro $F_1$-score.
4. **Dimensionality Reduction & Clustering:** PCA orthogonal variance extraction and $K$-Means clustering ($K=4$) validated via Silhouette score, Davies-Bouldin index, Calinski-Harabasz score, and Ward's hierarchical dendrograms.

## Key Results
- **Baseline Supervised Classifier:** Logistic Regression achieves **~87% Test Accuracy** and a **Macro $F_1$-score of ~0.86** when predicting 4 World Bank Income Groups. Misclassifications highlight boundary nations whose social metrics diverge from raw GDP bracket cutoffs.
- **Dimensionality Reduction (PCA):** The top 2 principal components capture **67.74%** of variance; top 3 components capture **79.49%**.
- **Developmental Clusters ($K=4$):**
  - **Cluster 0 (Advanced Multidimensional):** High income ($>\$48,000$), 99.8% electricity, high internet (87.2%), low child mortality (3.8/1k).
  - **Cluster 1 (Infrastructure-Constrained):** Moderate income ($>\$12,000$), strong trade openness, lagging energy/digital grid access.
  - **Cluster 2 (Health & Socially Transitioning):** Middle income, high health spending, moderate life expectancy, macroeconomic volatility.
  - **Cluster 3 (Low-Income Deficit):** Low income ($<\$1,500$), severe under-5 mortality (58.4/1k), <50% electricity access.

## Project Structure & Notebook Link
- **Main Jupyter Notebook:** [multidimensional_development_clustering.ipynb](https://github.com/lapidba/WHO-capstone-project/blob/main/multidimensional_development_clustering.ipynb)
- **Raw Data Directory:** `[./data/](https://github.com/lapidba/WHO-capstone-project/tree/main/data)`
- **Plots Directory:** `[./plots/`]https://github.com/lapidba/WHO-capstone-project/tree/main/data
- **Final Output Dataset:** `./data/final_country_development_clusters.csv`

## Contact & Further Information
Author: Arjun Singh GitHub: https://github.com/lapidba LinkedIn: https://www.linkedin.com/in/singharjun/ Date: July 2026
Project Repository: `https://github.com/lapidba/WHO-capstone-project`
