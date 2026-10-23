# SCM Delay & Risk Analysis

A data analysis and feature-engineering project focused on understanding and predicting late-delivery risk in a supply chain context. The project uses the DataCo Supply Chain Dataset to explore delivery behavior, identify operational bottlenecks, and prepare a cleaned dataset for downstream analysis and predictive modeling.

## Project overview

This repository is organized around a notebook-based workflow:

- Data inspection and profiling
- Data cleaning and preprocessing
- Exploratory data analysis (EDA)
- Feature engineering and model-ready dataset preparation

The project is designed to answer questions such as:

- Which order and shipping characteristics are associated with delays?
- How do region, shipping mode, order status, and product attributes affect late-delivery risk?
- What data quality issues need to be fixed before modeling?
- Which features should be retained or excluded to avoid leakage?

## Dataset

The project uses the DataCo Supply Chain Dataset, which contains transactional order and logistics information, including:

- order dates and shipping dates
- shipping mode and delivery status
- geographic information for customers and orders
- product and category details
- financial values such as sales, profit, discounts, and totals
- target signal: `late_delivery_risk`

Source data location:

- `data/raw/DataCoSupplyChainDataset.csv`

Prepared data outputs:

- `data/cleaned/cleaned_supply_chain_data.csv`
- `data/cleaned/cleaned_supply_chain_data.parquet`

## Folder structure

```text
SCM_Delay_&_Risk_Analysis/
├── data/
│   ├── raw/
│   │   └── DataCoSupplyChainDataset.csv
│   └── cleaned/
│       ├── cleaned_supply_chain_data.csv
│       └── cleaned_supply_chain_data.parquet
├── notebooks/
│   ├── 01_data_overview.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_eda_business_insights.ipynb
│   └── 04_feature_engineering.ipynb
├── outputs/
│   └── figures/
│       └── delay_heatmap.html
├── .gitignore
├── .python-version
├── main.py
├── pyproject.toml
├── README.md
├── requirements.txt
├── uv.lock
└── .venv/
```

## Notebook workflow

### 1. Data overview
`notebooks/01_data_overview.ipynb`

- loads the raw dataset
- reviews schema and data types
- checks shape, duplicates, and missing values
- identifies the target variable and possible leakage columns

### 2. Data cleaning
`notebooks/02_data_cleaning.ipynb`

- standardizes column names
- converts date fields to a usable format
- removes or flags irrelevant/identifier-like columns
- handles missing values and duplicates
- saves a cleaned dataset for analysis

### 3. EDA and business insights
`notebooks/03_eda_business_insights.ipynb`

- analyzes delay patterns by market, order status, and shipping mode
- explores relationships between delay risk and business performance
- visualizes risk drivers and geographic patterns

### 4. Feature engineering
`notebooks/04_feature_engineering.ipynb`

- prepares model-ready features
- identifies leakage-prone variables
- structures data for predictive analysis and risk scoring

## Outputs

The project produces analytical artifacts in `outputs/` and `data/cleaned/`, including:

- cleaned CSV and Parquet versions of the dataset
- business charts and figures
- delivery risk heatmap outputs

## Environment setup

This project uses Python 3.13 and a virtual environment.

### Option 1: pip

```bash
python -m venv .venv
source .venv/bin/activate  # Linux/macOS
.venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

### Option 2: uv

```bash
uv sync
```

## Running the project

Start Jupyter from the project root:

```bash
jupyter lab
```

or:

```bash
jupyter notebook
```

Then open the notebooks in the `notebooks/` directory to reproduce the analysis pipeline.

## Dependencies

Key libraries in this project include:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- folium
- pyarrow
- jupyter

The full dependency list is defined in `pyproject.toml` and `requirements.txt`.

## Notes

- The project is primarily exploratory and notebook-driven.
- Some columns may look informative but should be reviewed carefully for leakage before building a predictive model.
- The analysis is focused on operational risk, delivery performance, and business insight rather than production deployment.

## License

This project does not currently declare a repository-specific license. If you are planning to share or reuse it publicly, add an appropriate license file and update this section.
