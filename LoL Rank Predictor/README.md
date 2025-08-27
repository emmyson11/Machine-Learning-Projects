# League of Legends Rank Prediction

## Overview
This project focuses on predicting a player’s ranked tier in *League of Legends* based on in-game performance and player statistics. The dataset contains both gameplay and demographic-style features, and the prediction task is framed as a multi-class classification problem, mapping players into rank categories ranging from **Iron** to **Challenger**.  

The goal of this project is to explore the relationships between player statistics and rank, handle class imbalance in competitive tiers, and develop machine learning models that can generalize to unseen matches.  

---

## Dataset
The dataset consists of player match statistics collected from the Riot Games API and other data sources.  

**Key Features** include:
- **Demographics & Metadata**: `summonerName`, `preferred_lane`, `rank`
- **Performance Metrics**: `kills`, `deaths`, `assists`, `goldEarned`, `visionScore`
- **Objective Control**: `turretTakedowns`, `dragonKills`, `campsKilled`
- **Game Dynamics**: `longestTimeSpentLiving`, `totalDamageDealt`, `totalDamageTaken`, `gameDuration`
- **Derived Features**: `winRate`, `KDA`, role-specific efficiency metrics  

The target variable is the **rank tier** of the player.  

---

## Methodology
1. **Data Preprocessing**
   - Handled missing values and inconsistent records.
   - Encoded categorical variables such as `preferred_lane`.
   - Normalized numerical features for algorithms sensitive to scale.
   - Applied **class weighting** to address imbalance (most players clustered between Iron–Platinum).  

2. **Exploratory Data Analysis (EDA)**
   - Examined distributions of key metrics by rank.
   - Visualized correlations between gameplay stats and rank tiers.
   - Identified performance gaps (e.g., Gold+ players tend to have higher objective control).  

3. **Modeling**
   - Implemented baseline models: Logistic Regression, Decision Trees.
   - Experimented with advanced models: Random Forest, XGBoost, Gradient Boosting, Neural Networks.
   - Applied **Stratified K-Fold Cross-Validation** for fair evaluation across imbalanced ranks.
   - Hyperparameter tuning with grid search for optimization.  

4. **Evaluation**
   - Metrics: Accuracy, Weighted F1 Score, and Confusion Matrix analysis.
   - Emphasis on **Weighted F1 Score** to reflect fairness across underrepresented tiers.  

---

## Results
| Model                  | Accuracy | Weighted F1 Score |
|------------------------|----------|------------------|
| Logistic Regression     | 0.54     | 0.50             |
| Random Forest           | 0.72     | 0.68             |
| XGBoost                 | 0.75     | 0.71             |
| Neural Network (MLP)    | 0.77     | 0.73             |

- **Neural Network (MLP)** achieved the best balance between accuracy and fairness across classes.  
- Feature importance analysis highlighted **KDA**, **visionScore**, and **goldEarned** as the strongest predictors of rank.  

---

## Key Insights
- Lower-ranked players (Iron–Bronze) often show higher death counts and lower vision control.  
- High-ranked players (Diamond–Challenger) consistently excel in **objective control** (turrets, dragons) rather than raw kills.  
- Class weighting was crucial to prevent the model from over-predicting mid-tier ranks.  

---

## Technologies Used
- **Python**
- **Pandas, NumPy, Matplotlib, Seaborn** (Data preprocessing & visualization)
- **Scikit-learn** (Logistic Regression, Decision Trees, Random Forest)
- **XGBoost**
- **TensorFlow / Keras** (Neural Networks)

---

## Future Work
- Incorporate **temporal features** such as player progression over multiple matches.  
- Explore **transformer-based models** for sequential match history.  
- Deploy as a **web app** for real-time rank prediction based on input stats.  
