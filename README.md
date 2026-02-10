# SyriaTel Customer Churn Prediction

## Project Overview

This project develops a machine learning classification model to predict customer churn for SyriaTel, a telecommunications company. By identifying customers at risk of leaving, the company can implement targeted retention strategies to protect revenue and improve customer satisfaction.

## Business Problem

SyriaTel is experiencing customer churn, which directly impacts revenue and profitability. When customers leave, the company loses not only recurring subscription revenue but also the significant investment made in acquiring them. 

**Objective:** Build a predictive model that identifies customers likely to churn, enabling proactive retention efforts.

## Dataset

- **Source:** SyriaTel customer data
- **Size:** 3,333 customer records
- **Features:** 20 features including usage patterns, service plans, customer service interactions
- **Target Variable:** Churn (binary: True/False)
- **Class Distribution:** ~14.5% churners, 85.5% non-churners (imbalanced dataset)

## Methodology

### 1. Data Understanding & Exploration
- Analyzed 21 original features
- Identified no missing values
- Examined class imbalance and feature distributions
- Explored relationships between features and churn

### 2. Feature Engineering
Created 5 new features to capture customer behavior patterns:
- `total_minutes`: Aggregated usage across all time periods
- `total_calls`: Total number of calls made
- `total_charge`: Total charges across all services
- `average_call_duration`: Average length of calls (usage pattern indicator)
- `day_minute_ratio`: Proportion of daytime usage (business vs personal user indicator)

### 3. Data Preparation
- Separated features (X) and target (y)
- Encoded categorical variables using one-hot encoding
- Split data: 80% training, 20% testing (stratified)
- Scaled features for distance-based models (Logistic Regression)

### 4. Model Development
Built and evaluated three classification models:

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| Logistic Regression (Baseline) | 85.01% | 47.06% | 24.74% | 32.43% |
| Decision Tree | 90.25% | 66.67% | 65.98% | 66.32% |
| **Random Forest (Selected)** | **93.85%** | **98.28%** | **58.76%** | **73.55%** |

### 5. Model Evaluation
- Analyzed confusion matrices for all models
- Calculated ROC curves and AUC scores
- Examined feature importance
- Identified key churn drivers

## Results

### Selected Model: Random Forest

**Performance Metrics:**
- **Accuracy:** 93.85%
- **Precision:** 98.28% (when we predict churn, we're right 98% of the time)
- **Recall:** 58.76% (catching 59% of actual churners)
- **F1-Score:** 73.55%
- **AUC:** 0.898 (excellent discriminative ability)

**Confusion Matrix:**
- True Positives: 57 churners correctly identified
- False Positives: 1 (only 1 loyal customer incorrectly flagged)
- False Negatives: 40 (missed churners)
- True Negatives: 569 (correctly identified loyal customers)

**Key Achievement:** 
The model catches **57 out of 97 churners** with only **1 false alarm** - a 137% improvement over the baseline while maintaining 98% precision.

### Top Churn Drivers

Based on feature importance analysis:

1. **Total Charge (24.8%)** - Cost is the primary churn driver
2. **Customer Service Calls (13.6%)** - Frequent service interactions signal dissatisfaction
3. **Total Minutes (11.8%)** - Overall usage patterns matter
4. **Day Minute Ratio (7.3%)** - Business vs personal usage indicator
5. **Average Call Duration (6.6%)** - Call behavior patterns

## Business Recommendations

### 1. Deploy the Predictive Model
- Implement monthly customer scoring
- Generate ranked churn risk lists for retention team
- Integrate predictions into CRM with automated alerts
- **Expected Impact:** Save 57+ customers per month

### 2. Address Cost Concerns
- Offer loyalty discounts to high-risk, high-value customers
- Create graduated pricing plans
- Provide bill optimization consultations
- **Expected Impact:** Reduce price-driven churn by 30-40%

### 3. Improve Customer Service Quality
- Flag customers with 3+ service calls for immediate outreach
- Improve first-call resolution rates
- Address root causes of service issues proactively
- **Expected Impact:** Reduce service-related churn by 25-35%

## Repository Structure
```
SyriaTel_Project/
├── data/
│   └── syriatel_data.csv    # Dataset
├── syriatel.ipynb                             # Jupyter notebook with full analysis
├── presentation.pdf                           # Non-technical presentation
├── README.md                                  # Project documentation
└── .gitignore                                # Git ignore file
```

## Technologies Used

- **Python 3.8+**
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib & seaborn** - Data visualization
- **scikit-learn** - Machine learning models and evaluation

## Key Features

✅ Comprehensive exploratory data analysis
✅ Strategic feature engineering based on domain knowledge
✅ Multiple model comparison (Logistic Regression, Decision Tree, Random Forest)
✅ Business-focused evaluation (prioritizing precision to minimize false alarms)
✅ Actionable insights tied directly to model findings
✅ Production-ready recommendations


## Model Limitations

- **Recall Trade-off:** Model catches 59% of churners; 40 customers still go undetected
- **Overfitting:** 100% training accuracy indicates some memorization
- **Class Imbalance:** Dataset has far more non-churners than churners
- **Temporal Factors:** Model doesn't account for seasonal patterns or time-based trends
- **External Factors:** Doesn't capture competitor actions, economic changes, or market conditions

**Mitigation:** Regular model retraining, performance monitoring, and threshold adjustment based on business needs.

## Future Improvements

- Implement hyperparameter tuning to reduce overfitting
- Collect additional features (customer satisfaction scores, competitor data)

## Business Impact

- Reduced customer acquisition costs (retention is 5-25x cheaper)
- Increased customer lifetime value
- Improved customer satisfaction
- Better resource allocation for retention teams

## Author

**Angela Mukami K**
- GitHub: [@yourusername](https://github.com/mkxangie)
- LinkedIn: [Your LinkedIn](https://www.linkedin.com/in/angela-mukami-k/)


---

**Project Status:** ✅ Complete | **Last Updated:** February 2026