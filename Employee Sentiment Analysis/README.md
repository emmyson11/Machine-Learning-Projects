# Employee Sentiment and Flight Risk Analysis

## Summary

This project analyzes employee email sentiment data to uncover communication patterns, detect flight risk indicators, and build a predictive model for monthly sentiment scores. The analysis incorporates natural language sentiment scoring, communication volume trends, and predictive modeling using linear regression.

Access to Final Report:
- [Full Employee Sentiment Analysis Report](/ESA_Final_Report.docx)

### Top 3 Employees by Overall Positive Sentiment
Based on cumulative monthly sentiment scores:
1. **lydia.delgado@enron.com** -> Sentiment Score of: 76
2. **johnny.palmer@enron.com** -> Sentiment Score of: 63
3. **eric.bass@enron.com** -> Sentiment Score of: 63

### Top 3 Employees by Overall Negative Sentiment
Based on cumulative monthly sentiment scores:
1. **kayne.coulter@enron.com** -> Sentiment Score of: 43
2. **kayne.coulter@enron.com** -> Sentiment Score of: 38
3. **rhonda.denton@enron.com** -> Sentiment Score of: 37

### Employees Flagged as Flight Risks
Flagged for sending 4 or more negative messages within a rolling 30-day window:
- **don.baughman@enron.com**
- **john.arnold@enron.com**

### Key Insights
- **Communication volume (message count and word count)** is positively correlated with sentiment.
- Employees with a high **negative message density** over a short time frame are potential flight risks.
- The final predictive model explains **61%** of the variance in monthly sentiment scores.
- Some features such as **positive message ratio** and **total word count** are strong positive indicators of sentiment.

### Recommendations
- **HR Monitoring**: Keep an eye on employees showing spikes in negative sentiment in short periods.
- **Engagement Programs**: Provide additional support to employees with persistently negative trends.
- **Continued Modeling**: Expand features to include email topics or sentiment progression for stronger predictions.

---

## Project Tasks Breakdown

### Task 1: Data Cleaning
- Removed irrelevant or empty email messages.
- Ensured proper formatting of dates and email metadata.
- Filtered out system-generated or forwarded messages.

### Task 2: Sentiment Analysis
- Used a pre-trained sentiment model to assign:
  - `positive`, `neutral`, or `negative` labels to each message.
  - A sentiment score ranging from -1 to +1.
- Added sentiment columns to the dataset for downstream analysis.

### Task 3: Feature Engineering
- Created the following features:
  - `word_count`: Number of words per message.
  - `char_count`: Number of characters per message.
  - `is_positive`, `is_negative`, `is_neutral`: Boolean flags for sentiment types.

### Task 4: Monthly Aggregation
Grouped the data by `employee` and `month`, calculating:
- `monthly_sentiment_score` (target variable)
- `message_count`, `avg_word_count`, `avg_char_count`
- `total_words`, `total_chars`
- Sentiment counts and ratios: `positive_ratio`, `negative_ratio`, `neutral_ratio`

### Task 5: Flight Risk Detection
- Identified employees who sent **≥4 negative messages within any 30-day window**.
- Used a sliding window per employee to flag potential flight risk behavior.

### Task 6: Predictive Modeling
- Objective: Predict `monthly_sentiment_score` using communication behavior.
- Model: Linear Regression
- Defined features:
  - Message volume and length: `message_count`, `avg_word_count`, `avg_char_count`, `total_words`, `total_chars`
  - Sentiment distribution: `positive_ratio`, `negative_ratio`, `neutral_ratio`
  - Additional features: `words_per_message`, `chars_per_word`, `sentiment_intensity`
- Target variable:
     - `monthly_sentiment_score`
- Outliers in target variable removed using z-score filtering.
- Results:
  - **MSE**: 1.54
  - **R²**: 0.61
- Feature importances identified `total_words`, `avg_char_count`, and `positive_ratio` as the most impactful.
- **Model Improvement Attempts**:
   - Tested regularized linear models:
     - **Ridge Regression** R²: 0.58
     - **Lasso Regression** R²: 0.69 (better fit)
   - Explored a **Random Forest Regressor** to capture non-linearity:
     - **Random Forest MSE:** 0.13  
     - **Random Forest R²:** 0.96 (significantly improved performance)

### Task 7: Visualization
- All visuals + explanations contained in visuals folder and full report document.

---

## Future Work
- Incorporate NLP-based topic modeling to understand **content themes** in messages.
- Apply **classification models** to directly predict flight risk.
- Integrate external stressor data (e.g., org changes, deadlines) to contextualize negative sentiment spikes.

---

