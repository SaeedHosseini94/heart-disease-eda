# Heart Disease Dataset: Exploratory Data Analysis

A complete exploratory data analysis (EDA) of the Heart Disease dataset (303 patient records, 14 clinical features), with a focus on data-quality checks and rich visualizations.

## What's inside

| Step | Result |
|---|---|
| Missing values | None found (standard `NaN` or disguised placeholders like `?`) |
| Non-numeric characters | None; every cell matches a strict numeric regex |
| Duplicate rows | 1 found and removed (302 rows remain) |
| Suspicious values | `ca = 4` (5 rows) and `thal = 0` (2 rows) are outside the codebook range and flagged as likely missing-value codes |
| Outliers | Detected with the IQR method; kept because they are clinically plausible (capped versions used for visualization only) |

## Visualizations

The notebook includes boxplots, violin plots, a correlation heatmap, a pair plot, grouped bar charts, scatter plots, and cross-tab heatmaps.

| | |
|---|---|
| ![Target distribution](images/target_distribution.png) | ![Age distribution](images/age_distribution.png) |
| ![Correlation heatmap](images/correlation_heatmap.png) | ![Violin plots](images/violin_by_target.png) |
| ![Categorical vs target](images/categorical_vs_target.png) | ![Age vs max heart rate](images/age_vs_thalach.png) |

More plots are in the [`images/`](images) folder and in the notebook itself.

## Key takeaways

- Chest pain type (`cp`), max heart rate (`thalach`), and `thal` show the clearest association with disease status.
- Exercise-induced angina (`exang`) and ST depression (`oldpeak`) are strong indicators on the disease side.
- Continuous variables are largely uncorrelated with each other.
- Outlier detection should rely on the distribution of the column itself, never on the target. Using the target to decide whether a feature value is "noise" is circular reasoning.

## Notes on the data

- The codebook states `sex: 0 = male, 1 = female`. The widely used UCI version of this dataset conventionally uses the opposite coding, so verify against your source before drawing conclusions about `sex`.
- `data/Explain_Heart_Data.pdf` is the variable description used for this analysis.

## Project structure

```
heart-disease-eda/
├── heart_eda.ipynb          # Main analysis notebook (outputs included)
├── data/
│   ├── heart.csv            # Dataset
│   └── Explain_Heart_Data.pdf  # Variable descriptions
├── images/                  # Exported plots used in this README
├── requirements.txt
└── README.md
```

## Run it yourself

```bash
git clone https://github.com/SaeedHosseini94/heart-disease-eda.git
cd heart-disease-eda
pip install -r requirements.txt
jupyter notebook heart_eda.ipynb
```

## Links

- Kaggle notebook: (https://www.kaggle.com/code/ssaeedhm/exploratory-data-analysis-heart-disease-dataset)
