# P3G2 Customer Churn

Customer churn analysis and prediction project. The supplied notebooks currently use the **PerfectPetClub** data source and naming conventions; confirm that this is the intended dataset/business context for the Customer Churn assignment before final submission.

## Repository contents

- `notebooks/01_ETL_Pipeline.ipynb` — extracts data from SQLite and CSV files, transforms customer-level features, checks data quality, and writes a Parquet dataset.
- `notebooks/02_ML_Model.ipynb` — uses PySpark to train and evaluate Logistic Regression, Decision Tree and Random Forest classifiers; includes sensitivity analysis, cross-validation, confusion matrices, ROC curves and feature importance.
- `data/raw/` — place the original database and CSV source files here.
- `data/processed/` — generated Parquet output is written here.
- `documentation/` — team agreement, contribution tracker, development log and meeting record templates.
- `reports/figures/` — location for exported charts and report figures.

## Required source data

The ETL notebook expects these files in `data/raw/`:

- `PerfectPetClub.db`
- `PerfectPetClub_CRM_report.csv`
- `PerfectPetClub_server_log.csv`
- `PerfectPetClub_survey.csv`

The database is expected to contain the tables referenced in the ETL notebook: `customer`, `payment`, `product`, `product_category`, `product_review`, `sale`, `sale_product`, `subscription`, and `subscription_type`.

**The source data files were not included in the upload used to prepare this package.** Add the authorised assignment datasets locally. Do not commit personal, confidential or restricted data to a public repository; check your module's data-sharing rules first.

## Setup

Create and activate a virtual environment, then install:

```bash
python -m venv .venv
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
```

For the ETL notebook, run `notebooks/01_ETL_Pipeline.ipynb` from the repository root (or from the `notebooks` folder). It writes:

`data/processed/perfectpetclub_processed.parquet`

The ML notebook requires Java and PySpark. Configure a compatible Java installation for your environment before running it. The notebook's processed-data path has been changed from the original JupyterHub-specific absolute path to a repository-relative path.

## Suggested execution order

1. Add the four required raw data files to `data/raw/`.
2. Run `01_ETL_Pipeline.ipynb` from top to bottom.
3. Confirm the processed Parquet file exists and inspect the churn label distribution.
4. Run `02_ML_Model.ipynb` from top to bottom.
5. Record actual model results, limitations and interpretations in the report.
6. Update the contribution tracker and development log with verifiable work.

## Reproducibility and academic integrity

Keep commit messages specific to the change made. Record actual work dates and actual contributors; do not backdate commits or attribute work to a teammate without their confirmation. If work was completed earlier but committed later, explain that distinction in the development log. Do not publish fabricated metrics or claim that an unrun notebook has passed.

## Team

See `documentation/team_agreement.md` and `documentation/contribution_tracker.csv`.
