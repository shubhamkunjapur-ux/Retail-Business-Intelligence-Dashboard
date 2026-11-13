# Retail-Business-Intelligence-Dashboard
Interactive Retail Sales Dashboard built using Python, Pandas, NumPy, Streamlit and Plotly as part of the Business Analytics Internship at Sysslan IT Solutions.
# 🛒 Big Mart Retail Analysis & Interactive Dashboard

An end-to-end retail analytics project built on the **Big Mart** dataset: data understanding, cleaning, business analysis, visualization, and an interactive **Streamlit + Plotly** dashboard for exploring product pricing, visibility, and outlet profiles.

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458)
![Plotly](https://img.shields.io/badge/Plotly-Visualization-3F4F75)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B)

---

## 📑 Table of Contents

- [Project Links](#-project-links)
- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Dashboard Features](#-dashboard-features)
- [Key Metrics (KPIs)](#-key-metrics-kpis)
- [Repository Structure](#-repository-structure)
- [Tech Stack](#-tech-stack)
- [Installation & Usage](#-installation--usage)
- [Generated Outputs](#-generated-outputs)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)

---

## 🔗 Project Links

| Resource | Link |
|---|---|
| 📊 **Dashboard** | [View Dashboard](https://drive.google.com/file/d/1areCF4l99GVaJqYms1HQYffKhsQUgH0w/view?usp=sharing) |
| 🎥 **Dashboard Demo Video** | [Watch Demo](https://drive.google.com/file/d/1areCF4l99GVaJqYms1HQYffKhsQUgH0w/view?usp=sharing) |
| 📓 **Analysis Notebook** | [`BIG_MARKET_RETAIL_ANALYSIS.ipynb`](BIG_MARKET_RETAIL_ANALYSIS.ipynb) |

---

## 📌 Project Overview

This project analyzes retail product and outlet data to understand how products are priced, how visible they are on shelves, and how outlets differ by type, size, and location. The work is organized into five progressive levels:

1. **Data Understanding** – profile the raw dataset
2. **Data Preparation** – clean and standardize it
3. **Business Analysis** – aggregate by category, outlet, and location
4. **Data Visualization** – chart the key patterns
5. **Dashboard & Insights** – deliver an interactive Streamlit app

---

## 🗂️ Dataset

**File:** `Big_Mart_Sales.csv` (raw) → `Big_Mart_Cleaned.csv` (cleaned)
**Size:** 5,681 records × 11 columns · 1,543 unique products · 10 outlets · 16 product categories

| Column | Description |
|---|---|
| `Item_Identifier` | Unique product ID |
| `Item_Weight` | Product weight |
| `Item_Fat_Content` | Low Fat / Regular |
| `Item_Visibility` | Share of display area allotted to the product in its store |
| `Item_Type` | Product category |
| `Item_MRP` | Maximum retail price |
| `Outlet_Identifier` | Unique store ID |
| `Outlet_Establishment_Year` | Year the outlet was established |
| `Outlet_Size` | Store size |
| `Outlet_Location_Type` | City tier of the outlet |
| `Outlet_Type` | Grocery store / supermarket type |

> ⚠️ The dataset does **not** include `Item_Outlet_Sales`, so this project reports pricing, visibility, and outlet profiles, not actual sales revenue.

---

## 🔄 Project Workflow

### Level 1 — Data Understanding
- Dataset shape, column names, and data types
- Missing value analysis (with bar chart)
- Duplicate record check (**0 duplicates**)
- Descriptive statistics for numerical and categorical fields
- Unique value analysis per column
- **Finding:** 976 missing `Item_Weight` values and 1,606 missing `Outlet_Size` values
- Export: `Level_1_Data_Understanding_Report.csv`

### Level 2 — Data Preparation
| Issue | Treatment |
|---|---|
| Inconsistent `Item_Fat_Content` labels (`LF`, `low fat`, `reg`, …) | Standardized to **Low Fat** and **Regular** |
| Missing `Item_Weight` | Filled with the median per `Item_Identifier`, then the overall median as fallback |
| Missing `Outlet_Size` | Filled with the mode per `Outlet_Type`, then the overall mode as fallback |
| Data types | Numeric columns coerced with `pd.to_numeric` |
| Duplicates | Removed if present |

**Result:** 0 missing values, 0 duplicates, 2 clean fat-content categories.
Exports: `Big_Mart_Cleaned.csv`, `Level_2_Data_Preparation_Report.csv`

### Level 3 — Business Analysis
- Overall pricing summary (mean, median, min, max MRP)
- Product category analysis (records, unique products, average and total MRP)
- Outlet-level analysis (records, average MRP, visibility, size, type, location)
- Outlet type and outlet location comparisons
- Top 10 products by MRP
- Item visibility analysis by category

Exports: `Level_3_Category_Analysis.csv`, `Level_3_Outlet_Analysis.csv`, `Level_3_Outlet_Type_Analysis.csv`, `Level_3_Location_Analysis.csv`, `Level_3_Top_Products_by_MRP.csv`

### Level 4 — Data Visualization
- Product distribution by category
- Average MRP by category
- Product records across outlet types
- Outlet location distribution (donut chart)
- Fat content distribution (donut chart)
- MRP distribution (histogram)
- Item visibility vs MRP (scatter plot)
- Products by outlet establishment year (line chart)

### Level 5 — Dashboard & Business Insights
An interactive Streamlit application (`app.py`) built on the cleaned dataset. See below.

---

## 📊 Dashboard Features

**Sidebar filters**
- Product category
- Outlet
- Outlet type
- Fat content
- MRP range slider

**Dashboard sections**
| Section | Contents |
|---|---|
| 📊 KPIs | 8 headline metrics that update with the filters |
| 📦 Product Category Analysis | Records by category and average MRP by category |
| 🏬 Outlet Performance Profile | Records by outlet type and location distribution |
| 🥗 Fat Content Analysis | Fat content donut chart |
| 👁️ Visibility Analysis | Visibility vs MRP scatter, coloured by category, with hover details |
| 💰 Pricing Distribution | MRP histogram |
| 🏆 Top 10 Products | Highest-MRP products table |
| 💡 Business Insights | Auto-generated summary of top category, highest-MRP category, and top outlet type |
| 🔎 Product Data Explorer | Searchable table by product identifier |
| 📥 Download | Export the filtered dataset as CSV |

---

## 📈 Key Metrics (KPIs)

| KPI | Value (full dataset) |
|---|---|
| Total Records | 5,681 |
| Unique Products | 1,543 |
| Total Outlets | 10 |
| Product Categories | 16 |
| Average MRP | ₹141.02 |
| Average Item Visibility | 0.0657 |

The dashboard also shows **Average Weight** and **Median MRP**.

---

## 📁 Repository Structure

```
├── BIG_MARKET_RETAIL_ANALYSIS.ipynb     # Full analysis notebook (Levels 1–5)
├── app.py                               # Streamlit dashboard
├── requirements.txt                     # Dashboard dependencies
├── Big_Mart_Sales.csv                   # Raw dataset
├── Big_Mart_Cleaned.csv                 # Cleaned dataset used by the dashboard
├── Level_1_Data_Understanding_Report.csv
├── Level_2_Data_Preparation_Report.csv
├── Level_3_Category_Analysis.csv
├── Level_3_Outlet_Analysis.csv
├── Level_3_Outlet_Type_Analysis.csv
├── Level_3_Location_Analysis.csv
├── Level_3_Top_Products_by_MRP.csv
└── README.md
```

---

## 🧰 Tech Stack

- **Language:** Python
- **Data processing:** Pandas, NumPy
- **Visualization:** Plotly Express, Matplotlib, Seaborn
- **Dashboard:** Streamlit
- **Environment:** Google Colab

---

## 🚀 Installation & Usage

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the dashboard
Make sure `Big_Mart_Cleaned.csv` is in the same folder as `app.py`, then run:
```bash
streamlit run app.py
```
The app opens at `http://localhost:8501`.

### 4. Reproduce the analysis (optional)
Open `BIG_MARKET_RETAIL_ANALYSIS.ipynb` in Google Colab or Jupyter, upload `Big_Mart_Sales.csv` when prompted, and run all cells. The notebook regenerates every report CSV, the cleaned dataset, `app.py`, and `requirements.txt`.

> The notebook uses `google.colab.files` for uploading and downloading. If running locally in Jupyter, replace those calls with a standard `pd.read_csv("Big_Mart_Sales.csv")`.

---

## 📦 Generated Outputs

| File | Purpose |
|---|---|
| `Big_Mart_Cleaned.csv` | Cleaned dataset (5,681 rows, no missing values) |
| `Level_1_Data_Understanding_Report.csv` | Raw data profile |
| `Level_2_Data_Preparation_Report.csv` | Cleaning summary |
| `Level_3_*.csv` | Category, outlet, outlet-type, location, and top-product analyses |
| `app.py` | Streamlit dashboard source |
| `requirements.txt` | `streamlit`, `pandas`, `numpy`, `plotly` |

---

## ⚠️ Limitations

- The dataset has no `Item_Outlet_Sales` column, so no sales revenue or sales performance analysis is possible. Findings are about **pricing, visibility, and outlet profiles**.
- Missing `Item_Weight` and `Outlet_Size` values were imputed (median and mode), which may not match true values.

---

## 🔮 Future Improvements

- Add sales data for revenue and performance analysis
- Build predictive models (e.g., price or sales forecasting)
- Deploy the dashboard publicly on Streamlit Community Cloud
- Add outlet-age and visibility-based segmentation

---

## 👤 Author

Shubham Maity

B.Tech – Artificial Intelligence & Machine Learning

---

⭐ If you found this project useful, consider giving it a star!
