# 📘 **Forecasting Global GDP Growth Using ARIMA, Holt-Winters, Random Forest & XGBoost**

This repository contains the full implementation, code, datasets, and results for a comparative GDP forecasting study across high-income, emerging, and developing economies.
The project evaluates the forecasting performance of four models:

* **ARIMA**
* **Holt-Winters (Exponential Smoothing)**
* **Random Forest Regressor**
* **XGBoost Regressor**

Annual GDP growth (1960–2023) is used to generate **out-of-sample forecasts for 2016–2023**.
This repo includes the code, datasets, model outputs, accuracy metrics, and figures used in the final forecasting analysis.

---

# 📂 **Repository Structure**

```
/ (root)
│
├── data/
│     └── gdp_growth.csv                # Combined dataset of annual GDP growth for all countries
│
├── notebook/
│     ├── RPDA8412_GDP_Forecasting.ipynb   # Main modelling and analysis notebook
│     └── (auto-generated outputs saved to figures/)
│
├── figures/
│     ├── predictions/                   # Model-specific prediction CSVs
│     ├── model_results.csv              # Final accuracy metrics (RMSE, MAE, MAPE)
│     ├── *.png                          # All forecast plots (Actual vs Predicted)
│                             
│
├── reports/
│     └── (your research report PDFs)
│
└── .gitignore
```

---

# 🚀 **Project Overview**

The goal of this project is to determine **which forecasting models best predict GDP growth**, and how model performance varies across:

* **High-income countries:** United States, Germany
* **Emerging economies:** China, Brazil, India
* **Developing economies:** Bangladesh, Kenya, Nigeria

Each model forecasts 2016–2023 GDP growth using only data up to 2015.
Accuracy is evaluated using:

* **RMSE**
* **MAE**
* **MAPE**

The results show **classical models outperform ML models in most countries**, with Random Forest winning only in China.

---

# 🧠 **Technologies & Libraries Used**

* **Python 3.9+**
* **Pandas**
* **NumPy**
* **Matplotlib / Seaborn**
* **Statsmodels** (ARIMA, Holt-Winters)
* **Pmdarima** (auto_arima)
* **Scikit-Learn** (Random Forest)
* **XGBoost**

---

# 📊 **Dataset Description**

The dataset contains annual real GDP growth (% change) for:

* USA
* Germany
* China
* Brazil
* India
* Bangladesh
* Kenya
* Nigeria

Source: **World Bank WDI** and **IMF WEO**.

The notebook imports a single CSV:

```
data/gdp_growth.csv
```

The CSV includes:

| Country | Year | GDP_Growth |
| ------- | ---- | ---------- |
| USA     | 1961 | 2.3        |
| ...     | ...  | ...        |

---

# 🧪 **Methodology Summary (Code Workflow)**

### ✔️ **1. Load and clean data**

* Import GDP growth CSV
* Handle missing values
* Create country-specific time series

### ✔️ **2. Train–Test Split**

* Training data: up to **2015**
* Test data: **2016–2023**
* Forecast horizon: **8-year multi-step forecasting**

### ✔️ **3. Feature Engineering for ML**

Lagged features created:

```
GDP(t−1), GDP(t−2), GDP(t−3)
```

### ✔️ **4. Model Implementations**

**ARIMA**

* Auto-ARIMA selects optimal (p,d,q)
* Multi-step recursive forecasting

**Holt-Winters**

* Level + trend (no seasonality)
* Forecasts extrapolate last trend

**Random Forest**

* 100 trees
* Lag features as predictors
* Iterative multi-step forecasting

**XGBoost**

* Tree booster
* Depth 3–4
* Learning rate ≈ 0.1
* Early stopping

### ✔️ **5. Evaluation Metrics**

* RMSE
* MAE
* MAPE

All saved to:

```
figures/model_results.csv
```

### ✔️ **6. Figures & Outputs**

The notebook automatically exports:

* Actual vs Predicted plots
* Model-specific prediction CSVs
* Grouped accuracy tables

Saved inside:

```
figures/ and figures/predictions/
```

---

# 🏆 **Results Summary**

### **Overall winner: ARIMA & Holt-Winters outperform ML in 7/8 countries.**

**High-Income**

* Best = **Holt-Winters**
* ARIMA very close

**Middle-Income**

* Mixed results
* Random Forest wins **only for China**

**Low-Income**

* ARIMA / Holt-Winters consistently best
* XGBoost performs worst in these countries

### **Notable Highlights**

* **China:** Random Forest captured the structural slowdown → lowest RMSE
* **India:** All models struggled due to extreme pandemic shock
* **USA/Germany:** Simple exponential smoothing was sufficient
* **Nigeria:** Holt-Winters best due to trend smoothing

A full ranking table is included in:

```
figures/model_results.csv
```

---

# ▶️ **How to Run the Notebook**

1. Clone the repository:

```
git clone <your-repo-url>
```

2. Install dependencies:

```
pip install -r requirements.txt
```

3. Open the notebook:

```
notebook/RPDA8412_GDP_Forecasting.ipynb
```

4. Run all cells
   The notebook will:

* Load the dataset
* Train all four models
* Generate predictions
* Export figures/prediction CSVs
* Produce accuracy tables

---

# 📦 **Recommended .gitignore Entries**

---

# 📚 **References**

(World Bank, IMF, Hyndman, Box–Jenkins, Makridakis, Petropoulos, etc.)

---
