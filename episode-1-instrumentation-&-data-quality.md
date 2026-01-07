# Episode 1 — "The Missing Seconds"

Maya Sinha, Senior Data Analyst, liked tidy datasets. She liked them the way some people like calm mornings and strong coffee. But tidy datasets were a luxury in the wilds of streaming analytics.

It was a Tuesday. Maya's Slack ping lit up.

Product Manager (Liam): "Maya — our retention metric dipped 3% MoM. Can you tell me why?"

Maya skimmed the dashboard. The retention funnel looked odd: week-1 retention was down only for Android users, but sessions for Android had jumped 40% the same week.

Maya: "Before I deep-dive, did anything change in Android instrumentation last week?"

Liam: "Not that I'm aware of. We shipped a minor SDK update."

Maya opened the events table and ran a quick query to compute average watch_seconds per view by device.

[inside her head the query ran — she thought in SQL]
```sql
SELECT device, COUNT(*) AS views, AVG(watch_seconds) AS avg_watch_sec
FROM views
WHERE start_ts >= '2025-12-01'
GROUP BY device;
```
