# Time Series Stationarity Analysis Tool

A simple and interactive Python-based workflow for loading time series data (from Yahoo Finance or local CSV files) and testing for **stationarity** using visual plots and combined statistical tests (**ADF** and **KPSS**).

---

## 📌 Features

- **Flexible Data Sources:** Fetch live stock/commodity data directly from Yahoo Finance or load your own custom CSV file.
- **Visual Inspection:** Automatically plots price trends over time to spot obvious directional drift.
- **Dual Statistical Testing:** Combines **Augmented Dickey-Fuller (ADF)** and **Kwiatkowski-Phillips-Schmidt-Shin (KPSS)** tests for accurate results.
- **Automated Recommendations:** Automatically interprets test results and suggests whether to difference, detrend, or proceed directly to modeling.

---

## 🔄 Execution Flow

```text
[ 1. Setup & Imports ] ──► Load required libraries (Pandas, Statsmodels, Matplotlib, YFinance)
           │
           ▼
[ 2. Load Data ]      ──► Fetch from Yahoo Finance OR read local CSV file
           │
           ▼
[ 3. Visual Check ]   ──► Plot line graph to visually inspect trends
           │
           ▼
[ 4. Run Tests ]      ──► Execute ADF & KPSS statistical tests concurrently
           │
           ▼
[ 5. Verdict ]        ──► Output final decision (Stationary, Non-Stationary, Trend-Stationary)
                          and actionable next steps.
```

---

## 🛠️ Prerequisites & Installation

Make sure you have Python installed (version 3.8 or higher). You can install all required libraries by running:

```bash
pip install pandas yfinance matplotlib statsmodels
```

---

## 🚀 How to Run & Use

1. **Open the Notebook:** Open the `.ipynb` file in **Google Colab**, **Jupyter Notebook**, or **VS Code**.
2. **Configure Data Source (Cell 2):**
   - **To fetch from Yahoo Finance:** Set `USE_YFINANCE = True` and enter your desired ticker symbol (e.g., `"GC=F"` for Gold Futures or `"AAPL"` for Apple).
   - **To use your own CSV file:** Set `USE_YFINANCE = False`, place your file in the project folder, and update `CSV_FILE_PATH`, `DATE_COLUMN`, and `PRICE_COLUMN` names.
3. **Run All Cells:** Run the notebook cells in order from top to bottom.

---

## 📊 Understanding Test Verdicts

| ADF Test | KPSS Test | Verdict | Action Required |
| :--- | :--- | :--- | :--- |
| Non-Stationary | Non-Stationary | **Non-Stationary** | Differencing needed (e.g., `df.diff()`). |
| Stationary | Stationary | **Stationary** | Ready for modeling (e.g., ARMA/ARIMA). |
| Non-Stationary | Stationary | **Trend-Stationary** | Detrending needed (e.g., remove trend line). |
| Stationary | Non-Stationary | **Difference-Stationary** | Differencing recommended. |

---

## 📜 License

This project is open-source and free to use for education and research.