# 🏠 Real Estate Intelligence Pipeline
### End-to-End ML Pipeline for Property Price Prediction & Recommendation

[![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat&logo=python)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?style=flat&logo=scikit-learn)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

> An end-to-end data science application that scrapes real estate listings from 99acres.com, performs comprehensive analysis, and delivers a **Random Forest-based price prediction model** alongside a **content-based property recommendation system** — all focused on the Gurgaon residential market.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Project Architecture](#-project-architecture)
- [Tech Stack](#-tech-stack)
- [Modules](#-modules)
- [Dataset](#-dataset)
- [Results](#-results)
- [Getting Started](#-getting-started)
- [Folder Structure](#-folder-structure)

---

## 🔍 Project Overview

This project addresses the challenge of **accurate property valuation** in the rapidly evolving Gurgaon real estate market. It delivers three core capabilities:

| Capability | Description |
|---|---|
| 🔮 **Price Prediction** | ML regression models to estimate property prices from key attributes |
| 🏡 **Property Recommendation** | Content-based engine suggesting properties based on user preferences |
| 📊 **Market Insights** | Data-driven analysis of pricing trends, hotspot locations, and feature impact |

---

## 🏗️ Project Architecture

```
99acres.com
    │
    ▼
Web Scraping (BeautifulSoup)
    │
    ▼
Raw Data (Flats, Houses, Residential Land)
    │
    ▼
Data Preprocessing
(Missing Value Imputation → Outlier Treatment → Merging)
    │
    ▼
Exploratory Data Analysis
(Univariate → Bivariate → Multivariate)
    │
    ▼
Feature Engineering & Selection
(Encoding → Scaling → Interaction Terms)
    │
    ├──────────────────────┬──────────────────────┐
    ▼                      ▼                      ▼
Price Prediction     Recommendation          Insights
(Random Forest)      (Content-Based)         (Market Analytics)
```

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| **Language** | Python 3.8+ |
| **Data Collection** | BeautifulSoup, Requests |
| **Data Manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Plotly |
| **Machine Learning** | Scikit-learn |
| **EDA Profiling** | Pandas Profiling (ydata-profiling) |
| **Environment** | Jupyter Notebook |

---

## 📦 Modules

### 1. 🌐 Web Scraping
- Scraped **3,000+ property listings** from [99acres.com](https://99acres.com) targeting Gurgaon
- Collected across **3 property types**: Flats/Apartments, Independent Houses, Residential Land
- Extracted attributes: location, BHK, area (sq. ft.), price, floor, amenities, society name

### 2. 🧹 Data Preprocessing
- **Multi-stage cleaning pipeline** with versioned checkpoints (v1, v2 CSVs)
- Missing value imputation using median/mode and domain logic
- Outlier detection and treatment using IQR and Z-score methods
- Merged flat and house datasets into a unified property dataset

### 3. 📊 Exploratory Data Analysis (EDA)
- **Univariate Analysis**: Distribution of price, area, BHK, property type
- **Bivariate Analysis**: Price vs. location, area, floor correlations
- **Multivariate Analysis**: Heatmaps, pair plots, and interaction effects
- Auto-profiling report via `pandas-profiling` for rapid data quality checks

### 4. ⚙️ Feature Engineering & Selection
- One-hot encoding for categorical features (property type, sector, furnishing)
- Interaction terms capturing combined effects (e.g., area × BHK)
- Feature scaling (StandardScaler) for distance-based computations
- Feature selection using correlation thresholds and feature importance scores

### 5. 🤖 Model Development
| Model | Description |
|---|---|
| **Linear Regression** | Baseline parametric model |
| **Decision Tree Regressor** | Non-linear, interpretable model |
| **Random Forest Regressor** | Best performer with hyperparameter tuning |
- Evaluation Metrics: **MAE**, **RMSE**, **R² Score**
- Hyperparameter tuning using `GridSearchCV`

### 6. 🏡 Recommendation System
- **Content-Based Filtering** using cosine similarity
- Recommends top-N similar properties based on:
  - Preferred location / sector
  - Budget range
  - Desired amenities and property type

### 7. 📈 Insights Module
- **Market Trends**: Sector-wise price distribution and trends
- **Location Analysis**: Identifying high-value zones and investment hotspots
- **Feature Impact**: SHAP-style analysis of which attributes drive price changes

---

## 📁 Dataset

| File | Description |
|---|---|
| `gurgaon_properties.csv` | Raw scraped data |
| `gurgaon_properties_cleaned_v1.csv` | After initial preprocessing |
| `gurgaon_properties_cleaned_v2.csv` | After outlier treatment |
| `gurgaon_properties_missing_value_imputation.csv` | Post imputation |
| `gurgaon_properties_post_feature_selection_v2.csv` | Final model-ready dataset |

> **Note:** Raw data files are excluded from version control (see `.gitignore`). CSVs > 50MB are tracked via Git LFS or excluded.

---

## 📊 Results

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| Linear Regression | — | — | — |
| Decision Tree | — | — | — |
| **Random Forest** | **Best** | **Best** | **Best** |

> *(Update this table with actual metrics from `model-selection.ipynb`)*

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn beautifulsoup4 requests ydata-profiling jupyter
```

### Run the Pipeline
```bash
# 1. Clone the repo
git clone https://github.com/smt2208/real-estate-price-prediction.git
cd real-estate-price-prediction

# 2. Start with data scraping (optional — data already included)
jupyter notebook Web_Scrapping/

# 3. Run preprocessing
jupyter notebook Preprocessing/data-preprocessing-flats.ipynb

# 4. Run EDA
jupyter notebook Exploratory_Data_Analysis/eda-multivariate-analysis.ipynb

# 5. Feature Engineering
jupyter notebook Feature_Engineering/feature-engineering.ipynb

# 6. Model Training & Evaluation
jupyter notebook Model_Selection/model-selection.ipynb

# 7. Recommender System
jupyter notebook Model_Selection/recommender-system.ipynb
```

---

## 📂 Folder Structure

```
real-estate-price-prediction/
│
├── Web_Scrapping/                  # Scraping notebooks (Flats, Houses, Land)
├── Preprocessing/                  # Data cleaning & merging notebooks
├── Exploratory_Data_Analysis/      # EDA notebooks (Univariate, Multivariate)
├── Feature_Engineering/            # Feature creation, selection, scaling
├── Model_Selection/                # ML models, recommender, insights, visualization
├── Baseline_Model/                 # Baseline regression notebook
├── Datasets/                       # Raw and processed datasets
└── README.md
```

---



## 📄 License

This project is licensed under the MIT License.

---


