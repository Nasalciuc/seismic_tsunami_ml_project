# Seismic & Tsunami ML Project

Comprehensive analysis and modeling pipeline for detecting tsunami risk from earthquake data.

This repository contains a cleaned seismic dataset and an advanced Jupyter notebook that runs through exploratory data analysis, domain-driven feature engineering, modeling, and production-readiness checks.

Contents
- `earthquake_data_tsunami.csv` — dataset with earthquake events and a `tsunami` label (0/1).
- `seismic_tsunami_analysis.ipynb` — analysis notebook with the full pipeline (EDA → FE → Modeling → Evaluation → Deployment checklist).
- `README.md` — this document.

Dataset schema (columns)
- `magnitude` — earthquake magnitude (Richter-like scale)
- `cdi`, `mmi`, `sig`, `nst`, `dmin`, `gap` — seismological signal/meta features
- `depth` — focal depth (km)
- `latitude`, `longitude` — event location
- `Year`, `Month` — temporal information
- `tsunami` — target label (1 = tsunami recorded, 0 = no tsunami)

Quick stats (from the dataset)
- The dataset contains global earthquake events across multiple years.
- Tsunami events are relatively rare (imbalanced classification). The notebook performs imbalance analysis and recommends techniques (SMOTE, class weights, stratified CV).

What the notebook does (high level)
- Phase 1 — Advanced EDA & Domain Analysis:
	- Data quality checks, missing values, leakage checks.
	- Target imbalance analysis and basic statistical tests (Mann–Whitney U).
	- Visualizations: magnitude/depth distributions, geographic scatter, temporal trends.

- Phase 2 — Feature Engineering:
	- Domain-specific features (tsunami risk score, tectonic intensity, ocean proximity).
	- Interaction and polynomial features, rolling temporal statistics, z-score standardization.
	- Advanced transforms (Box–Cox, QuantileTransformer) and binning.

- Phase 3 — Modeling Pipeline:
	- Prepare train/test splits (random + temporal split to simulate production).
	- Evaluate many models (Logistic Regression, RandomForest, GradientBoosting, SVM, ExtraTrees, KNN, Naive Bayes) and ensembles.
	- Cross-validation with StratifiedKFold and imbalanced-aware metrics.

- Phase 4 — Hyperparameter Optimization:
	- RandomizedSearchCV/GridSearchCV with nested CV for robust selection.
	- Custom scoring prioritizing recall (70% recall, 30% precision) suitable for early warning systems.

- Phase 5 — Evaluation & Production Readiness:
	- Detailed evaluation: ROC/PR curves, confusion matrix, cost analysis, calibration, SHAP/perm importances.
	- Temporal validation on a holdout future period (e.g., 2020+).
	- Production readiness checklist and deployment recommendations.

How to run locally (recommended)
1. Create and activate a virtual environment (PowerShell example):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install required packages. I can generate a `requirements.txt` if you want; for now install the core dependencies used in the notebook:

```powershell
pip install pandas numpy scipy scikit-learn matplotlib seaborn plotly shap imbalanced-learn folium geopy
```

3. Open the notebook in VS Code or Jupyter and run cells in order. The notebook is organized in phases; run sequentially to reproduce results.

Notes & practical tips
- Column names are used throughout the notebook. If your CSV has different names, rename them or update the notebook cells.
- The notebook does heavy ML work (nested CV, randomized search). For full runs, use a machine with enough CPU (or set n_jobs=1 to run slowly).
- For SHAP and large models, sample the dataset before running explanations to save time.
- Add a `.gitignore` to exclude `.venv/`, `.ipynb_checkpoints/`, `__pycache__/`, and large artifacts.

Suggested next steps I can do for you
- Create `requirements.txt` from the notebook imports.
- Add a `.gitignore` and push both files.
- Clean or reset the notebook if you want a blank starting template.
- Export the notebook as a markdown or HTML report for sharing with stakeholders.

If you want any of the suggested next steps, tell me which and I will create the files and push them to GitHub.