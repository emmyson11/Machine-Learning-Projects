# Food Desert Prediction Project

**Team Members:** Rin Hinosawa, Julina Vuong, Emmy Son  
**Organization:** DataGood @ Berkeley  

---

## Project Overview

Food deserts limit access to healthy, affordable food, exacerbating health and economic inequalities across communities. Traditional studies focus on current mapping, but our project aims to **predict future food deserts using machine learning**, offering data-driven tools for early intervention and policy planning.  

By combining **geospatial analysis, feature engineering, and predictive modeling**, we aim to identify at-risk areas and provide insights for policymakers and community organizations.

---

## Research Objectives

1. Use **K-Means clustering** and **Random Forest classifiers** to uncover patterns and predict emerging food deserts.  
2. Develop an **interactive dashboard** to visualize food access risks across demographics, states, and counties.  
3. Test the hypothesis that machine learning models can accurately predict emerging food deserts, enabling early interventions.

---

## Data Sources

- **USDA 2019 Food Access Research Atlas:** Census, income, SNAP participation, and supermarket data at the tract level.  
- **Historical context:** Literature on redlining and systemic inequalities affecting food access.  

We used **Python, Google Colab, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Geopandas, and Tableau** for data cleaning, modeling, and visualization.

---

## Methodology

### 1. Data Cleaning & Feature Engineering
- Filtered irrelevant data and imputed missing values.  
- Computed correlations to identify informative features such as **income, transportation, and racial demographics**.  
- Derived additional features like **distance to nearest supermarket** and **cumulative transportation access**.

### 2. Modeling
- **Algorithms tested:** K-Nearest Neighbors (KNN) and Random Forest.  
- **Rationale:** KNN identifies local similarity patterns; Random Forest captures complex interactions between features.  
- Random Forest outperformed KNN by effectively modeling how income, race, and transportation intersect to reveal food desert patterns.

---

## Results

The Random Forest model achieved strong classification performance, accurately identifying regions at high risk of becoming food deserts.

| Model           | Accuracy | Macro Avg Precision | Macro Avg Recall | Macro Avg F1-Score |
|-----------------|---------|-------------------|----------------|------------------|
| K-Nearest Neighbors (KNN) | 0.85    | 0.80              | 0.78           | 0.79             |
| Random Forest   | 0.97    | 0.97              | 0.85           | 0.97             |

- Random Forest effectively captured interactions between **income, race, and transportation**.  
- KNN performed well locally but struggled to generalize across complex feature interactions.

### Visualizations
- **Interactive Tableau dashboard:** Darker shades indicate higher probability of a region being a food desert.  
- Key predictors include **poverty rate, median family income, racial demographics, and transportation access**.

---

## Discussion & Reflection

Food deserts emerge from **intersecting socioeconomic and structural factors**, not a single variable. The Random Forest model successfully captures these patterns, providing actionable insights for policymakers. Visualizations reinforce the relationship between income, race, and access to healthy food, highlighting systemic inequalities.  

**Next Steps:**  
- Integrate community survey data for local validation.  
- Expand the analysis to additional regions to test generalizability.  
- Collaborate with local organizations to design targeted interventions for high-risk areas.

---

## References

- USDA Food Access Research Atlas (2019)  
- "Historical Redlining and Food Environments" study  
- Python libraries: Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Geopandas  
- Tableau for visualization and interactive dashboard  
