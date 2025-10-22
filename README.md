# Seismic & Tsunami ML Project

This repository contains data and an analysis notebook for exploring the relationship between earthquakes and tsunamis and building predictive models.

Contents
- `earthquake_data_tsunami.csv` — earthquake and tsunami dataset (source: user)
- `seismic_tsunami_analysis.ipynb` — Jupyter notebook for EDA, feature engineering, and ML modeling

Quick start
1. Create and activate a Python virtual environment (recommended):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -r requirements.txt
```

If `requirements.txt` is not present, install the following core packages:

```powershell
pip install pandas numpy scikit-learn matplotlib seaborn plotly folium geopy
```

3. Open the notebook in VS Code or Jupyter and run the cells.

Notes
- The notebook may contain placeholder or example code that assumes column names for magnitude, depth, latitude/longitude, and tsunami occurrence. Adjust column names based on your dataset schema.
- Consider adding a `.gitignore` to exclude `.ipynb_checkpoints`, virtual environment folders, and other temporary files.

License
This repository does not include a license file. Add one if you plan to share the project publicly.

Contact
For questions, contact the repository owner: `Nasalciuc`