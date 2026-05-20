# Business Story: Reducing Customer Churn

## Executive Summary

Customer churn is a critical challenge for the telecom industry. This analysis of 7,043 customers reveals that **26.5% churn rate**, costing the company significant recurring revenue. By identifying the key drivers of churn and building a predictive model, we can take proactive steps to retain at-risk customers and improve long-term profitability.

## Key Drivers of Churn

The most powerful predictors of churn are:

| Factor                      | Impact                                                                                                                |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Contract type**           | Month‑to‑month customers churn **12x more** than two‑year contract customers (42% vs 3%).                             |
| **Tenure**                  | New customers (tenure < 6 months) are far more likely to leave; median tenure of churned customers is only 10 months. |
| **Internet service type**   | Fiber optic subscribers have higher churn (41%) compared to DSL (19%).                                                |
| **Payment method**          | Electronic check users churn at 45% – the highest among all methods.                                                  |
| **Lack of add‑on services** | Customers without online security, backup, device protection, or tech support show significantly higher churn.        |
| **Paperless billing**       | While convenient, it correlates with higher churn, often reflecting self‑service users who are less engaged.          |

## Recommended Actions

Based on these insights, the company should:

1. **Shift customers to longer contracts**
   - Offer incentives (e.g., discounted monthly rates, free installation) for switching from month‑to‑month to one‑ or two‑year plans.
   - Introduce a loyalty discount for customers who renew a yearly contract.

2. **Target new customers with onboarding programs**
   - Create a "first 90 days" success program – proactive check‑ins, usage tips, and a dedicated support line.
   - Provide a small bill credit after 6 months of continuous service to reduce early churn.

3. **Address pain points for fiber optic users**
   - Investigate service reliability, speed consistency, and customer support for fiber customers.
   - Bundle fiber with security features (online security, backup) at a reduced rate to increase stickiness.

4. **Encourage autopay (non‑electronic check)**
   - Offer a $5/month discount for customers who switch from electronic check to bank transfer or credit card autopay.

5. **Promote add‑on services**
   - Market online security, backup, and tech support as low‑cost bundles, especially to month‑to‑month and new customers.
   - Use in‑app notifications highlighting “Recommended for you” based on usage patterns.

6. **Implement a predictive churn scoring system**
   - Deploy the trained XGBoost model (ROC AUC = 0.81) to flag high‑risk customers weekly.
   - Automatically trigger retention offers (e.g., $10 off for 3 months) for customers in the top risk decile.

## Model Performance Summary

- **Final model**: XGBoost with SMOTE and feature scaling.
- **ROC AUC**: 0.81 – good discrimination between churners and non‑churners.
- **At threshold 0.44**, recall for churn reaches 70%, enabling the retention team to act on ~70% of actual churners while keeping precision at 54%.
- **Top 5 features** (by importance):
  1. `Contract_Two year` (negatively correlated – strong retention)
  2. `InternetService_Fiber optic` (high risk)
  3. `Contract_One year` (retention)
  4. `PaymentMethod_Electronic check` (high risk)
  5. `Tenure` (low tenure → higher risk)

## Next Steps

- **Deployment** – The model (`churn_model.pkl`) and scaler (`scaler.pkl`) are saved and ready for integration into a CRM or marketing automation system.
- **A/B testing** – Run a controlled experiment offering retention incentives to the top 20% of predicted churners vs. a holdout group. Measure reduction in actual churn over 3 months.
- **Continuous monitoring** – Retrain the model quarterly to capture changes in customer behavior and new product offerings.

By acting on these data‑driven insights, the company can reduce churn by an estimated **15‑20%** over the next year, directly increasing customer lifetime value and reducing acquisition costs.
