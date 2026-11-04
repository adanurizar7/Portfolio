# Fraud Detection Model

Wake Forest MSBA, Machine Learning for Business Analytics. Team project (5 people), fall 2026. The bank, Deacon Financial Services, is a class case.

## The problem
When someone applies for a new bank account, the bank has to decide right away whether to approve it or send it to manual review. A new $200 sign-up bonus brought in about four times more applications, and more fraud came with them.

## What we did
- Built one row per application from a 43-table bank database: about 212,000 applications from January 2025 to August 2026.
- Combined the feature ideas from all five team members into 55 candidate features. Every feature only uses information the bank has when the application comes in.
- Narrowed the 55 features down to 20 using chi-square and F-tests, then forward, stepwise, and backward selection with 5-fold cross-validation. All three selection methods picked the same 20 variables.
- Fit a logistic regression and chose the review cut-off with the lowest total cost, weighing the cost of a missed fraud against the cost of reviewing a good customer.

## Results (25% held-out test set, 52,998 applications)
| | Bank's current score | Our model |
|---|---|---|
| AUC | 0.651 | **0.844** |
| Fraud found in the riskiest 5% | 6.4% | **40.6%** |

At the recommended 0.12 cut-off, the model:
- catches 48% of fraud while reviewing about 7% of applications.
- cuts estimated fraud-related costs from $1.03M to $0.71M (about 31%).
- adds review volume that fits within the fraud team's current capacity.

## Files
- [`Fraud_Detection_Model.ipynb`](Fraud_Detection_Model.ipynb): full Python notebook (pandas, statsmodels, scikit-learn)
- [`Fraud_Model_Memo.pdf`](Fraud_Model_Memo.pdf): 4-page recommendation memo to the bank's Head of Fraud Risk

The raw data is course material and isn't included here.
