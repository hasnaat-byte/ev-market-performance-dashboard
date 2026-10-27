# EV Market Performance & Insights

A reproducible EV market analysis project using Python, pandas, SQLite/SQL, Tableau Public, Plotly, and Flask. It profiles the supplied dataset, exports group-level summaries, provides an interactive local web preview, and supports Tableau Public dashboard/story embedding.

> **Dataset note:** The original CSVs and generated SQLite database are not included in this public repository. Add the course-provided `ev_market_train.csv` and `ev_market_test.csv` files to `data/` on your own computer before running the data build steps. These source files and the local database are excluded from Git.

## Project contents
- `data/`: local input data folder; source CSVs and database are intentionally excluded from Git.
- `src/build_data.py`: cleans data, creates SQLite tables, exports nine analysis aggregates, writes quality/performance reports.
- `src/validate_project.py`: checks row counts, null handling, database schema and aggregate outputs.
- `sql/schema.sql`: SQLite tables and indexes.
- `sql/analysis_queries.sql`: SQL examples for KPI and group-level analysis.
- `outputs/`: generated aggregate CSVs, quality report, query benchmark and validation results.
- `app.py`, `templates/`, `static/`: responsive Flask site with Plotly previews and optional Tableau embeds.
- `docs/PROJECT_DOCUMENTATION.md`: full project report.
- `docs/TABLEAU_BUILD_GUIDE.md`: nine worksheet specifications, calculated fields, dashboard/story and filters.
- `docs/WORKSPACE_REQUIREMENTS_MAPPING.md`: maps each SkillWallet requirement to its evidence and remaining actions.
- `docs/DEMO_VIDEO_SCRIPT.md`: 5–7 minute end-to-end recording script.
- `docs/performance_test.md`: actual Tableau performance log template.

## Quick start
Python 3.10+ recommended.

Place the two course-provided CSVs in `data/` before starting:

```text
data/ev_market_train.csv
data/ev_market_test.csv
```

```bash
python -m venv .venv
source .venv/bin/activate                 # Windows: .venv\\Scripts\\Activate.ps1
pip install -r requirements.txt
python src/build_data.py
python src/validate_project.py
cp .env.example .env                     # Windows: copy .env.example .env
python app.py
```

Open `http://127.0.0.1:5000`. The `/health` route reports whether the local database and Tableau URLs are configured.

## Tableau workflow
The Tableau Public workbook for this project is published as **EV Market Performance & Insights**. The dashboard includes EV distribution by vehicle category, manufacturer portfolio, battery technology mix, model-year trend by battery, and price versus range. For the expanded nine-sheet analysis and story specifications, see `docs/TABLEAU_BUILD_GUIDE.md`.

To show the dashboard inside the local Flask preview, add its public URL to `.env` as `TABLEAU_DASHBOARD_URL` and restart Flask. Keep `.env` local; it is excluded from Git.

## Important data caveat
The supplied dataset has not been independently verified against official market data. `annual_sales_units` is a record-level field; row sums are not verified global or country market totals. Use the charts as exploratory analysis of the supplied records and avoid unsupported causal claims.

## Submission
Use the published Tableau Public dashboard as the demo link and this repository as the GitHub project link. Add both links to SkillWallet. Record and upload the project walkthrough video separately if required by the assignment.
