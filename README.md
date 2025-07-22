# Fraud_Detection
# Fraud Detection Using Machine Learning

This project focuses on proactively detecting fraudulent transactions using a machine learning pipeline built on a real-world financial dataset. The goal is to not only build an effective predictive model but also to interpret its insights and propose actionable fraud prevention strategies.

## Objective

- Predict whether a transaction is fraudulent.
- Identify key patterns and high-risk behaviors.
- Propose real-time, adaptive fraud prevention methods for infrastructure upgrade.

## Dataset Overview

- Rows Processed: 10,000 (sampled)
- Original Columns: ~11
- Features after Cleaning: 8
- Target Variable: `isFraud` (Binary: 0 = Legit, 1 = Fraud)

## Key Steps & Methodology

### 1. Data Cleaning & Preprocessing
- Removed duplicates and constant columns.
- Handled missing values using median (numerical) and mode (categorical).
- Encoded categorical variables using Label Encoding.
- Removed identifier-like columns (e.g., IDs, names).
- Processed only the first 10,000 rows for efficiency.

### 2. Model Development
- Used **Random Forest Classifier** due to its robustness, ability to rank feature importance, and suitability for imbalanced datasets.
- Tuned classification threshold to improve fraud recall without compromising precision.
- ROC AUC Achieved: **0.999**

### 3. Variable Selection
- Included all non-redundant and informative features post-cleaning.
- Feature importances were later visualized and interpreted.

### 4. Model Evaluation
- Evaluation Metrics: Accuracy, Precision, Recall, F1-score, ROC AUC
- Threshold tuning helped increase recall on fraud class from 0.70 to **0.85**.
- Achieved almost **perfect precision** for both classes.

### 5. **Key Predictive Features**
| Feature            | Role in Fraud Detection                                                  |
| ----------------- | ------------------------------------------------------------------------ |
| `newbalanceOrig`  | Often drops sharply in fraud cases.                                      |
| `oldbalanceOrg`   | High-value accounts are often targeted.                                  |
| `type`            | `TRANSFER` and `CASH_OUT` are high-risk transaction types.               |
| `amount`          | Sudden large amounts can signal fraud.                                   |
| `oldbalanceDest`  | Fraud receivers may have unusual or empty balance history.               |
| `step`            | Fraudulent activity often clusters in certain time steps.                |
| `newbalanceDest`  | Unexpected large inflows may indicate mule accounts.                     |

### 6. **Model Explainability**
- Feature importance visualized using **matplotlib**.
- (SHAP can be used if dependency issues are resolved.)

## Recommendations for Fraud Prevention

1. Implement real-time transaction scoring using the trained model.
2. Use dynamic thresholding to flag unusually large transactions.
3. Enforce secure APIs with tokens, rate-limiting, and TLS.
4. Set up RBAC for sensitive operations.
5. Add anomaly detection to flag new fraud patterns.
6. Maintain audit trails for transparency and investigations.
7. Periodically retrain the model with new data.

## Deployment & Monitoring

- Model can be exported via `joblib` or `pickle` for deployment.
- Future evaluation should compare pre- and post-implementation fraud metrics.


