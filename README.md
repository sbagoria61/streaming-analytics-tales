# OTT Data Analyst Stories

Welcome to "OTT Data Analyst Stories" — a repository of narrative-driven, real-world scenarios that explain typical challenges data analysts face at streaming (OTT) companies. Each episode reads like a short story and includes dialogues between a data analyst and cross-functional partners (Product, Engineering, Marketing, Content, Legal, Finance). The stories use dummy names and titles but mirror real problems, and each episode contains concrete examples (SQL or Python) you can use as starting points.

Repository structure
- stories/
  - episode-01-instrumentation-and-data-quality.md
  - episode-02-churn-and-retention.md
  - episode-03-recommendations-and-ab-tests.md
  - episode-04-metrics-and-governance.md
- examples/
  - query-churn.sql
  - sessionization.py
- data/
  - dummy-schema.md
- CONTRIBUTING.md
- LICENSE (not included by default — add one if you publish)

How to use
1. Read the story to understand the human and organizational context.
2. Review the example queries/scripts in `examples/`.
3. Create a small sandbox database (or use a local DuckDB/Postgres) with the schema in `data/dummy-schema.md` to run examples.
4. Use the dialogues as templates for internal docs or onboarding materials.

License and attribution
- The stories and examples are intentionally fictional. All names and scenarios are dummy and meant for educational use.
- If you publish this repository, add an appropriate LICENSE file.

Want me to push this to GitHub?
- I can create a repo and push these files for you if you give me the owner/repo name. (I'll need the repository owner explicitly.)

Enjoy — and feel free to request more episodes, notebooks, or a small simulated dataset to run the code.
