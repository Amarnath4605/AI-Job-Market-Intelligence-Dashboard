# AI-Based Job Market Intelligence Dashboard

An end-to-end data analytics project analyzing global AI/tech hiring trends — skills in demand, salary patterns, remote work distribution, and top hiring companies — built from real, API-collected job posting data.

## Project Overview

This project analyzes ~5,800 real job postings (collected via the Adzuna and USAJobs public APIs) to answer key hiring-market questions:
- Which skills are most in demand?
- Which countries/companies hire the most?
- Which experience levels and remote arrangements pay the highest?
- How is hiring demand trending month over month?

## Tech Stack
- **Python** (Pandas, NumPy, Matplotlib) — data cleaning, feature engineering, EDA
- **SQL** (SQLite) — business-question queries
- **Power BI** — interactive dashboard
- **Scikit-learn** — simple demand-trend forecasting

## Data Source
[AI Job Market Global 2026](https://www.kaggle.com/datasets/atharvasoundankar/ai-job-market-global-2026) — real-time job postings collected weekly via public job-board APIs.

**Known data limitations (documented, not hidden):**
- ~42% of postings are missing salary data — handled with a `has_salary` flag rather than dropping or imputing
- `required_skills` field is 81% empty — skills were instead extracted from `job_description` text using keyword + regex word-boundary matching
- `city` field occasionally contains country/region names instead of actual cities (a source data-quality issue) — flagged with a `city_reliable` column rather than silently included in city-level analysis

## Project Structure
```
Job-Market-Intelligence-Dashboard/
├── data/              # Raw and cleaned datasets
├── sql/               # SQL business-question queries
├── notebooks/         # Python cleaning, EDA, and forecasting notebook
├── dashboard/         # Power BI .pbix file
├── screenshots/       # Dashboard screenshots
└── README.md
```

## Key Findings
- **Machine Learning** is the most in-demand skill (823 mentions), followed by Cloud, Python, LLM, and MLOps
- **Junior-level salaries ($129,710 avg) closely rival Senior-level ($131,419 avg)** in this AI-focused job market — higher than Mid-level ($106,836) and Management ($115,424)
- **Onsite roles pay more on average ($142,489)** than Remote roles ($108,563) in this dataset — the opposite of a common assumption
- The **United States** has both the highest job volume (1,837 postings) and highest average salary ($132,465) among the countries analyzed
- Skill-mention volume rises sharply in early 2026, though this is partly a reflection of denser recent data collection rather than pure demand growth — a limitation worth noting rather than overselling as a trend

## Dashboard Features
- KPI cards: Total Job Postings, Average Salary, Companies Hiring, Countries Covered
- Salary by Experience Level (bar chart)
- Hiring heat map by country
- Monthly hiring trend (line chart)
- Remote vs Onsite distribution (donut chart)
- Top 10 hiring companies (bar chart)
- Experience-level filter (slicer)

## Forecasting
A simple linear regression model was used to project next-month posting volume for the top 5 in-demand skills, based on historical monthly mention counts. This is a baseline approach — a production system would benefit from a model that accounts for seasonality and data-collection density over time.

## Author
[Amarnath Ethodu] — feel free to connect on [https://www.linkedin.com/in/amarnath-ethodu-62739434a/]
