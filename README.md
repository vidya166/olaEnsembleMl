

## 🏎️**About Ola**  
Ola is a major player in the ride-hailing industry, known for its vast network of drivers and vehicles, providing convenient and affordable transportation options. However, it faces significant challenges in driver recruitment and retention, which directly impact its operational efficiency and customer satisfaction.

## 🔴**Problem Statement**

Ola is struggling with high attrition rates among its drivers. This churn creates multiple challenges:  
1. **Operational Challenges**: A constant need to recruit new drivers, which is costly and resource-intensive.  
2. **Retention Issues**: Difficulty in retaining existing drivers who might leave due to dissatisfaction, better offers, or other factors.  
3. **Business Impact**: Frequent driver exits impact morale, operational consistency, and financial stability since acquiring new drivers is more expensive than retaining current ones.  

The goal is to predict whether a driver will leave the company based on historical and demographic data, enabling Ola to take proactive steps to improve retention.

## 🎯 **Objective**  

The primary objective is:  
- **Predict driver attrition** using available data (demographics, tenure, performance, etc.).  
- This prediction will help Ola identify at-risk drivers and design targeted interventions (e.g., incentives, support programs, or policy changes) to retain them and reduce operational costs.  

## **Concepts Used**  
This project incorporates the following key data science and machine learning techniques:  

1. **Ensemble Learning - Bagging**:  
   - A technique that combines predictions from multiple models (e.g., Random Forest) to reduce variance and improve prediction stability and accuracy.  

2. **Ensemble Learning - Boosting**:  
   - An iterative approach that focuses on correcting errors made by weak models in the previous iterations (e.g., Gradient Boosting, XGBoost).  

3. **KNN Imputation of Missing Values**:  
   - A method to handle missing data by imputing values based on the similarity (proximity) of data points.  

4. **Working with an Imbalanced Dataset**:  
   - Addressing class imbalance where attrition (leaving drivers) might be a minority class compared to non-attrition. Techniques such as SMOTE (Synthetic Minority Oversampling Technique), under-sampling, or class-weighted algorithms may be used to balance the dataset for better model performance.
  
  
  
🕵🏽‍♂️- **Findings**:
  

| **Metric**              | **Bagging (Random Forest)**         | **Boosting (XGBoost)**            | **Comparison**                                                                 |
|--------------------------|-------------------------------------|------------------------------------|--------------------------------------------------------------------------------|
| **Train Accuracy**       | 1.00                               | 1.00                              | Both models fit the training data perfectly, indicating no underfitting.       |
| **Test Accuracy**        | 0.92                               | 0.93                              | XGBoost performs slightly better, showing better generalization.               |
| **Recall for Churned**   | 0.94                               | 0.96                              | XGBoost has higher recall, critical for identifying churned drivers.           |
| **Precision for Churned**| 0.93                               | 0.94                              | XGBoost slightly outperforms Random Forest in minimizing false positives.       |
| **F1-Score (Churned)**   | 0.94                               | 0.95                              | XGBoost achieves a better balance between precision and recall.                |
| **ROC AUC**              | 0.96                               | 0.96                              | Both models are equally effective in distinguishing between classes.           |
| **Confusion Matrix**     | More false negatives (18)          | Fewer false negatives (13)        | XGBoost reduces false negatives, crucial for preventing missed churn cases.    |
| **Top Features**         | `Year_of_joining`, `Reportings`    | `Rating_increase`, `Year_of_joining` | Feature importance insights vary, showing distinct value in different aspects. |



✍🏽**Key Insights:**

1. **Generalization**:
   - Both models generalize well, but XGBoost (93%) slightly outperforms Random Forest (92%) on the test set.

2. **Class Imbalance Handling**:
   - XGBoost handles class imbalance better, as indicated by higher recall for churned drivers (96% vs. 94%). This makes it more effective for reducing churn by identifying most at-risk drivers.

3. **False Negatives**:
   - XGBoost predicts fewer false negatives (13 vs. 18). Given the business objective to minimize driver churn, this is a critical advantage.

4. **Feature Interpretability**:
   - Random Forest highlights `Year_of_joining` and `Total Business Value` as key factors, whereas XGBoost emphasizes `Rating_increase` and `Year_of_joining`. Both offer actionable insights but from different perspectives.

5. **Performance Stability**:
   - XGBoost shows marginally better stability across metrics like recall, F1-score, and precision, making it more reliable for this business case.


🤔**Recommendation:**

- **XGBoost is the preferred model** for this problem because:
  - It achieves slightly better recall and precision for the churned class, directly addressing the business goal of identifying at-risk drivers.
  - It reduces false negatives, ensuring fewer missed opportunities for retention efforts.
  - While both models perform similarly in AUC and generalization, XGBoost’s edge in churn-related metrics aligns better with the business objective.

### Random Forest remains a strong alternative, particularly if simplicity or interpretability is prioritized over slight performance gains.

### ✍🏽🔸**Business Insights**

1. **High Churn Risk Among Drivers with Low Quarterly Ratings and Business Value:**
   - Drivers with lower quarterly ratings and business contributions are more likely to churn, as evidenced by the median `Quarterly Rating` of 1 and `Total Business Value` of approximately 465,000 for churned drivers compared to significantly higher values for retained drivers.  

2. **Impact of Driver Age and Tenure on Churn:**
   - Younger drivers (median age of 33) and those who joined recently (notably higher churn among drivers with `Year_of_Joining` closer to the current year) are more prone to leave. This could be due to insufficient work experience, dissatisfaction with early job roles, or lack of adequate support during their initial tenure.

3. **City-Specific Trends in Churn:**
   - Some cities, such as `C20`, exhibit a higher proportion of drivers, potentially with specific churn-related trends. Differences in competition, local demand, or operational challenges might be contributing to these regional disparities.

4. **Gender Balance in Driver Churn:**
   - With a male-to-female driver ratio of approximately 59:41, the churn analysis highlights no stark gender differences, suggesting that both groups face similar challenges. This opens up opportunities to explore targeted gender-neutral retention strategies.

5. **Income and Incentive Influence:**
   - A significant proportion of drivers (98%) reported no income increase, and most churned drivers had relatively lower incomes (median `Income` of ~51,630). This indicates dissatisfaction with pay structures and incentive mechanisms, which might not be competitive enough to retain top talent.



### 🤔🔸**Recommendations**

1. **Enhance Driver Performance Support:**
   - Provide personalized training programs and feedback mechanisms for drivers with low quarterly ratings. Partner them with mentors to improve their work experience and performance.

2. **Targeted Retention Strategies for Younger Drivers:**
   - Introduce tailored onboarding programs, periodic role evaluations, and growth opportunities to engage and retain younger drivers. Special initiatives for drivers in their first year can significantly improve retention.

3. **Optimize Pay and Incentive Structures:**
   - Design tiered incentives linked to `Total Business Value`, `Quarterly Ratings`, and reporting consistency. Offering bonuses or incremental pay increases to drivers exceeding performance benchmarks can mitigate churn risk.

4. **Regional Customization of Operations:**
   - Conduct city-level operational studies to address unique challenges faced in high-churn areas such as `C20`. Modify policies, shift timings, or demand management strategies to cater to regional needs effectively.

5. **Improve Reporting and Grievance Systems:**
   - Drivers with higher reporting rates exhibit a higher churn tendency. Implement real-time issue resolution and acknowledgment systems to ensure that drivers feel heard and supported.



### 😀**Conclusion**😀

The analysis underscores key factors influencing driver churn, including performance metrics, age, income levels, and regional disparities. By addressing these areas through tailored training, incentive structures, and enhanced support mechanisms, Ola can significantly improve driver retention, operational efficiency, and long-term profitability.

-----------

## 🛠️ Tech Stack

```
Python 3.x  |  Pandas  |  NumPy  |  Matplotlib  |  Seaborn
Scikit-learn (Random Forest, RandomizedSearchCV, SMOTE, KNN Imputer, Label Encoder)
XGBoost
imbalanced-learn (SMOTE)
```

---

