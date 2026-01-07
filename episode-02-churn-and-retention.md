# Episode 2 — "The User Who Left"

Arjun Patel was on the call with Marketing and Finance. The CFO, a direct voice with a soft laugh, wanted to know if the recent price change caused cancellations.

CFO (Dana): "We increased the monthly plan by 10% two months ago. How much of the churn is price-driven?"

Arjun had done survival analysis before. But the product team's recent campaign — a "family-plan" rollout — overlapped with price change dates. Correlation could easily be confused with causation.

Product (Nina): "Also, we ran a targeted promo to new users in July. That might have biased cohorts."

Arjun proposed a clear plan:
1. Define cohorts that signed up before and after the price change.
2. Control for campaign exposure and plan type.
3. Look at cancellations originating in the first 30 days vs later.

Dialogues and analysis
Arjun: "Let's start with a simple cohort query. We'll compute 30-day churn rate by signup cohort."

He sketched the SQL and shared it on the call.

```sql
WITH signups AS (
  SELECT user_id, DATE(created_at) AS signup_date, plan, signup_source
  FROM users
  WHERE created_at BETWEEN '2025-06-01' AND '2025-08-31'
),
churns AS (
  SELECT user_id, MIN(start_date) AS sub_start, MIN(end_date) AS sub_end
  FROM subscriptions
  WHERE start_date >= '2025-06-01' AND start_date <= '2025-08-31'
  GROUP BY user_id
)
SELECT s.signup_date,
  COUNT(DISTINCT s.user_id) AS signups,
  SUM(CASE WHEN c.sub_end IS NOT NULL AND c.sub_end <= s.signup_date + INTERVAL '30 day' THEN 1 ELSE 0 END) AS churned_30d
FROM signups s
LEFT JOIN churns c ON s.user_id = c.user_id
GROUP BY s.signup_date
ORDER BY s.signup_date;
