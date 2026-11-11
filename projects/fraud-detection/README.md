# Fraud Detection Models

Wake Forest MSBA, Machine Learning for Business Analytics. Team project (5 people), fall 2026. The bank, Deacon Financial Services, is a class case.

## The problem
When someone applies for a new bank account, the bank has to decide right away whether to approve it or send it to manual review. A new $200 sign-up bonus brought in about four times more applications, and more fraud came with them.

## What we did
- **HW4:** Built one row per application from a 43-table bank database (about 212,000 applications, January 2025 to August 2026). Combined the team's feature ideas into 55 candidates, narrowed them to 20 with statistical tests and stepwise selection, and fit a logistic regression.
- **HW5:** Added new features, including links to other applications through a shared phone, address, payout account, or device, for 110 features in total. Built a random forest and an XGBoost model and tuned both with Bayesian optimization (Optuna). Compared them with the HW4 logistic regression on the same 25% held-out test set.
- Chose the review cut-off with the lowest total cost, weighing the cost of a missed fraud ($305 to $505) against the cost of reviewing a good customer (about $80).

## Results (test set, 52,998 applications)
| | Bank's current score | HW4 logistic | Random forest | **XGBoost (final)** |
|---|---|---|---|---|
| Test AUC | 0.645 | 0.838 | 0.868 | **0.870** |
| Fraud found in the riskiest 5% | 6.1% | 39.8% | 46.2% | **45.8%** |
| Fraud caught at the cut-off | | 45.6% | 55.7% | **54.0%** |
| Total fraud + review cost | $983,963 (no model) | $728,093 | $626,269 | **$624,928** |

We recommend XGBoost with a 0.16 cut-off. It reviews about 6.8% of applications, catches 54% of fraud, and lowers estimated costs by about 36% compared with no model (14% compared with the HW4 model). The added review volume fits within the fraud team's current capacity.

## Files
- [`Fraud_Models_XGBoost_HW5.ipynb`](Fraud_Models_XGBoost_HW5.ipynb): final notebook with logistic regression, random forest, and XGBoost (pandas, scikit-learn, XGBoost, Optuna)
- [`Fraud_Models_Memo_HW5.pdf`](Fraud_Models_Memo_HW5.pdf): final recommendation memo
- [`Fraud_Model_Logistic_HW4.ipynb`](Fraud_Model_Logistic_HW4.ipynb) and [`Fraud_Model_Memo_HW4.pdf`](Fraud_Model_Memo_HW4.pdf): earlier logistic regression model and memo

The raw data is course material and isn't included here.
