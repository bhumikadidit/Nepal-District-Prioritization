Nepal Education + Jobs Prioritization (UNESCO-style)

## What this project does
This project builds a simple district "priority score" to help decide where investment in girls' STEM education could be most urgent (based on education gaps + unemployment need + local digital job opportunity signals).

## Repository workflow (how files connect)
- `data/raw/` contains the three input datasets (education, unemployment, digital jobs).
- `notebooks/EOF.ipynb` merges the datasets, calculates `EOF_Priority_Score`, creates a few plots, then exports `data/processed/final_data.csv` for Power BI.
- `dashboard/EOF_Nepal_Dashboard.pbix` is the Power BI report built from `data/processed/final_data.csv`.
- `src/jobsscraping.ipynb` generates the example `data/raw/nepal_digital_jobs.csv` file (currently a curated example dataset; the scraping section is just a demo).

## How the priority score works (in plain language)
In `notebooks/EOF.ipynb`, the score is a weighted combination of normalized (0-1) metrics:
- Lower `Female_STEM_Enrollment_Pct` => higher priority (this metric is inverted after scaling).
- Higher `Youth_Unemployment_Rate` => higher priority.
- Higher `Digital_Job_Postings` and `Digital_Jobs_Per_1000` => higher priority (more opportunity if skills improve).

Current weights:
- Education gap: 0.35
- Unemployment need: 0.30
- Opportunity: 0.25
- Job density: 0.10

## Current data coverage
The repo currently ships a **sample dataset of 15 districts** (see `data/raw/` and `data/processed/final_data.csv`). If you want "all Nepal districts", you'll need full-coverage source files and to rerun the notebook.

## Notes on the "prediction" section
The notebook includes a simple linear regression "what-if" scenario (e.g., +15 percentage points STEM enrollment) to illustrate directionally how outcomes *might* change. This is not a causal model; it should be presented as an illustrative scenario only (not a guaranteed impact estimate).

## How to use
- Open `dashboard/EOF_Nepal_Dashboard.pbix` in Power BI to explore the visuals.
- Open `notebooks/EOF.ipynb` to see/modify the analysis and re-export `data/processed/final_data.csv`.

## Contact
Email: bhumikaojha01@gmail.com
