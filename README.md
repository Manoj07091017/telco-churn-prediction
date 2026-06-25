# 📉 Telco Customer Churn Prediction

A machine learning project that predicts which telecom customers are likely
to cancel their service, so retention teams can intervene before they leave.

## 🎯 The Problem

Customer churn is expensive — acquiring a new customer costs far more than
retaining one. This project builds a model to identify at-risk customers
**before** they churn, and explains *why* they leave so the business can act.

## 📊 Dataset

[Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
— 7,043 customers with 20 features covering demographics, account details,
services subscribed, and billing. Target: whether the customer churned.

## 🔬 Approach

| Stage | What I did |
|-------|-----------|
| Data cleaning | Fixed a hidden data-quality issue (TotalCharges stored as text; 11 new customers with blank values) |
| EDA | Profiled churners: low tenure, month-to-month contracts, high charges |
| Feature engineering | One-hot encoded categoricals, scaled numeric features |
| Modelling | Logistic Regression (baseline) and Random Forest |
| Evaluation | Confusion matrix, precision/recall — not just accuracy |
| Threshold tuning | Lowered decision threshold to prioritise catching churners |
| Interpretation | Extracted churn drivers from model coefficients |

## 📈 Results

- **Caught 71% of churners** (recall) after threshold tuning — up from 57% at
  the default threshold
- Identified the **top churn drivers**: low tenure, fiber optic service, and
  month-to-month contracts
- The model would let a retention team target the highest-risk customers
  rather than guessing

![Churn Drivers](./churn_drivers.png)

## 💡 Key Insight

Accuracy alone (~81%) was misleading on this imbalanced dataset — a model
predicting "nobody churns" scores 73.5% while catching zero churners. I
optimised for **recall on the churn class**, because missing a real churner
costs far more than a wasted retention offer.

## 🛠️ Business Recommendations

1. Incentivise customers onto 1- and 2-year contracts (strongest protective factor)
2. Strengthen first-year onboarding — churn risk peaks early in tenure
3. Investigate fiber optic dissatisfaction (pricing or reliability)
4. Score customers monthly; target retention spend at high-probability churners

## 🧰 Tech Stack

`Python` `pandas` `scikit-learn` `matplotlib` `seaborn`
`Logistic Regression` `Random Forest`

## 👤 Author

*Manoj Sriramappa, [LinkedIn](https://www.linkedin.com/in/manoj-sriramappa-b404621b3/)
