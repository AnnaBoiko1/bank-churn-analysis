# Bank Customer Churn Analysis
### From Raw Data to Interactive Dashboard & Predictive Model

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly%20Dash-5.x-3F4F75?logo=plotly&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3-F7931E?logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

> **Capstone project** completed as part of the **NPower Canada Data Analytics Program** (Toronto, ON)  
> Full end-to-end workflow: raw messy data → cleaning → EDA → interactive dashboard → ML churn prediction

---

## Project Overview

Customer churn is one of the most critical challenges in banking. Acquiring a new customer costs **5–7× more** than retaining an existing one. This project analyzes churn behavior across **10,000 bank customers** from France, Germany, and Spain — uncovering the key drivers of churn, delivering actionable insights through an interactive dashboard, and scoring every customer by churn probability using machine learning.

**What this project covers:**
- Real-world **data wrangling** (missing values, currency symbols, inconsistent categories, duplicates)
- **Exploratory Data Analysis** answering 6 core business questions
- **Interactive Plotly Dash dashboard** with dynamic Geography and Gender filters
- **Predictive modelling** — Logistic Regression and Random Forest (ROC-AUC 0.859)
- **Risk scoring** — every customer assigned a churn probability and risk tier

---

## Business Questions Answered

1. What is the overall churn rate?
2. Which country has the highest churn rate?
3. Which age group is most at risk?
4. Do gender and account activity influence churn?
5. Does holding more products increase loyalty?
6. Are high-balance customers at greater risk?
7. **Which individual customers are most likely to churn next?**

---

## Dataset

| Attribute | Details |
|:----------|:--------|
| **Source** | [Kaggle — Bank Customer Churn Prediction](https://www.kaggle.com/datasets/shubhammeshram579/bank-customer-churn-prediction) |
| **Records** | 10,000 customers |
| **Features** | 13 columns |
| **Target** | `Exited` (1 = churned, 0 = retained) |
| **Countries** | France · Germany · Spain |

### Data Dictionary

| Column | Description | Type |
|:-------|:------------|:-----|
| `CustomerId` | Unique customer identifier | int |
| `Surname` | Customer last name | string |
| `CreditScore` | Credit score (350–850) | int |
| `Geography` | Country of residence | string |
| `Gender` | Male / Female | string |
| `Age` | Customer age | int |
| `Tenure` | Years with the bank | int |
| `Balance` | Account balance (€) | float |
| `NumOfProducts` | Number of bank products held | int |
| `HasCrCard` | Has credit card (0/1) | binary |
| `IsActiveMember` | Active member (0/1) | binary |
| `EstimatedSalary` | Estimated annual salary (€) | float |
| `Exited` | **Target** — churned (1) or retained (0) | binary |

---

## Project Workflow

```
Raw Source Files
  ├── Bank_Churn_Messy.xlsx               (demographics, 8 cols)
  └── Bank_Churn_Messy_Customer_Info.csv  (full records, 13 cols)
         │
         ▼
Step 1 — Data Wrangling
  ├── Fill missing values (Surname → 'Unknown', Age → mean)
  ├── Strip currency symbol (€) from EstimatedSalary
  ├── Standardize Geography ('FRA', 'French' → 'France')
  ├── Encode IsActiveMember ('Yes'/'No' → 1/0)
  ├── Drop empty column (Unnamed: 13)
  ├── Remove duplicate CustomerIds
  └── Feature engineering (AgeGroup, BalanceTier, TenureGroup)
         │
         ▼
Step 2 — Exploratory Data Analysis
  ├── Overall churn rate (20.4%)
  ├── Churn by Geography, Age Group, Gender
  ├── Churn by Activity Status & Products Held
  ├── Balance distribution by churn status
  └── Feature correlation matrix
         │
         ▼
Step 3 — Interactive Dashboard (Plotly Dash)
  ├── KPI cards — Total, Churned, Churn Rate, Avg Balance
  ├── Churn by Geography (bar chart)
  ├── Churn by Age Group (line chart)
  ├── Active vs Inactive members (donut chart)
  └── Balance distribution (box plot)
         │
         ▼
Step 4 — Predictive Modelling
  ├── Logistic Regression  →  ROC-AUC 0.777
  ├── Random Forest        →  ROC-AUC 0.859 ✓ best model
  ├── Feature importance   →  Age (0.358), NumOfProducts (0.229)
  └── Risk scoring         →  1,823 high-risk customers identified
```

---

## Key Findings

### EDA Findings

| # | Finding | Metric | Recommendation |
|:--|:--------|:-------|:---------------|
| 1 | Overall churn rate | **20.4%** (1 in 5 customers) | Set churn rate as a primary KPI |
| 2 | Germany churns at nearly **2× the rate** of France/Spain | DE: 32.4% vs FR: 16.2% | Dedicated retention program for German market |
| 3 | Customers aged **51–60** are the highest-risk segment | **56.2%** churn rate | Personalised offers for mid-to-late career customers |
| 4 | **Inactive members** churn at 2× the rate of active ones | 26.9% vs 14.3% | Automate re-engagement campaigns |
| 5 | **2 products = loyalty sweet spot**; 3–4 products → 83–100% churn | Very high, small segment | Review cross-sell strategy |
| 6 | **Female customers** churn significantly more | 25.1% vs 16.5% for males | Gender-sensitive retention outreach |
| 7 | **High-balance customers** are leaving | Positive balance–churn correlation | Premium relationship management |

### Model Results

| Model | ROC-AUC (test) | ROC-AUC (5-fold CV) |
|:------|:--------------|:--------------------|
| Logistic Regression | 0.777 | 0.767 |
| **Random Forest** | **0.859** | **0.857** |

### High-Risk Segment (1,823 customers, actual churn 71.7%)
- **50.5%** from Germany
- **71.7%** inactive members
- **59.6%** female
- Average age **47.8**, average balance **€98,054**

---

## Tech Stack

| Tool | Purpose |
|:-----|:--------|
| **Python 3.10** | Core programming language |
| **Pandas** | Data manipulation and cleaning |
| **NumPy** | Numerical operations |
| **Plotly** | Interactive visualizations |
| **Dash + Bootstrap** | Interactive dashboard |
| **Scikit-learn** | Machine learning models |
| **Jupyter Notebook** | Development environment |

---

##  How to Run

### Option 1 — View notebook on GitHub
Click `Bank_Churn_Analysis.ipynb` to browse the full analysis directly in GitHub — all charts and outputs render inline.

### Option 2 — Run locally

```bash
# 1. Clone the repository
git clone https://github.com/AnnaBoiko1/bank-churn-analysis.git
cd bank-churn-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook Bank_Churn_Analysis.ipynb
```

### Option 3 — Open in Google Colab
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AnnaBoiko1/bank-churn-analysis/blob/main/Bank_Churn_Analysis.ipynb)

> **Note:** In Colab, update file paths from `data/` to the uploaded file locations.

---

## Repository Structure

```
bank-churn-analysis/
│
├── 📓 Bank_Churn_Analysis.ipynb          # Main notebook (cleaning → EDA → dashboard → ML)
│
├── 📂 data/
│   ├── Bank_Churn_Messy.xlsx             # Raw file 1 — demographics (messy)
│   ├── Bank_Churn_Messy_Customer_Info.csv # Raw file 2 — full records (messy)
│   ├── Bank_Churn_Clean.csv              # Reference clean dataset
│   └── Bank_Churn_Data_Dictionary.csv    # Column descriptions
│
├── 📂 images/                            # Dashboard screenshots
│
├── requirements.txt                      # Python dependencies
└── README.md
```

---

## About

**Anna Boiko**  
Data Analytics Graduate — NPower Canada Program, Toronto

annaboiko1@icloud.com  
 [LinkedIn](https://www.linkedin.com/in/anna-boiko1/) · [GitHub](https://github.com/AnnaBoiko1)· [Portfolio](https://annaboiko.me)

---

*⭐ If you found this project useful, feel free to star the repository!*
