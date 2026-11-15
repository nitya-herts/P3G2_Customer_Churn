# Preparation manifest

## Received and included
- 01_ETL_Pipeline.ipynb (uploaded notebook)
- 02_ML_Model.ipynb (uploaded notebook)

## Not received in the upload
- PerfectPetClub.db
- PerfectPetClub_CRM_report.csv
- PerfectPetClub_server_log.csv
- PerfectPetClub_survey.csv

## Changes made during packaging
- Copied the two uploaded notebooks into `notebooks/` with clean filenames.
- Changed the ML notebook's JupyterHub-specific Parquet path to a repository-relative path.
- Made the ETL project-root detection work when launched from the repository root or `notebooks/`.
- Added project, team and evidence templates.

## Not yet verified
- Full notebook execution against the original source data.
- Model metrics and final model selection.
- Whether PerfectPetClub is the confirmed business context/name for the Customer Churn assignment.
- Individual task allocations and completed contributions (must be agreed/verified by the team).
