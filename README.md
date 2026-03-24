<div align="center">

<img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Linear%20Regression-Best%20Model-blueviolet?style=for-the-badge"/>
<img src="https://img.shields.io/badge/R²%20Score-0.9770-brightgreen?style=for-the-badge"/>
<img src="https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
<img src="https://img.shields.io/badge/Client-EliteShoppers.com-ff6b6b?style=for-the-badge"/>

<br/><br/>

# 🛍️ Predicting Customer Annual Spending Using Behavioral Metrics

### *A regression-based analysis for EliteShoppers.com — App vs. Website: which drives revenue?*

<br/>

> **Business Question:** Should EliteShoppers.com invest more in their mobile app or their website?  
> This project answers that with data — building regression models on real customer behavior to predict yearly spending and identify what actually drives it.

<br/>

---

</div>

## 📌 Table of Contents

- [Business Context](#-business-context)
- [Dataset](#-dataset)
- [Project Workflow](#-project-workflow)
- [Models & Results](#-models--results)
- [Key Findings](#-key-findings)
- [Business Recommendations](#-business-recommendations)
- [Tech Stack](#-tech-stack)
- [How to Run](#-how-to-run)
- [Project Structure](#-project-structure)

---

## 🏢 Business Context

**Client:** EliteShoppers.com  
**Agency:** Analytica Insights

EliteShoppers.com operates across both a **mobile app** and a **website**. The analytics team noticed that customer behavior differs significantly between the two platforms — but which one actually moves the needle on revenue?

This project delivers a **data-backed recommendation**: by modeling how behavioral metrics drive yearly spending, we quantify the relative impact of the app vs. the website, and translate that into a clear strategic direction.

---

## 📊 Dataset

**Source:** [Ecommerce Customers Dataset](https://drive.google.com/file/d/1nBKev41-ZnsHs9LO-fMRNMGsaiXNhGGS/view?usp=drive_link)  
**Records:** 500 customers

| Feature | Description |
|---|---|
| `Email` | Unique customer identifier *(dropped — non-predictive)* |
| `Address` | Physical address *(dropped — non-predictive)* |
| `Avatar` | Visual profile label *(dropped — non-predictive)* |
| `Avg. Session Length` | Average session duration in minutes |
| `Time on App` | Average minutes spent on the mobile app |
| `Time on Website` | Average minutes spent on the website |
| `Length of Membership` | Years the customer has been active |
| **`Yearly Amount Spent`** | 🎯 **Target** — Annual spend in USD |

---

## 🔬 Project Workflow

```
Raw Data (500 customers)
   │
   ├── Phase 1: Data Cleaning
   │       ├── Verified dtypes, null values, duplicates
   │       ├── Dropped non-predictive columns (Email, Address, Avatar)
   │       └── Confirmed no missing or anomalous values
   │
   ├── Phase 2: Exploratory Data Analysis (EDA)
   │       ├── KDE plots — all features ~normally distributed
   │       ├── Skewness & kurtosis analysis
   │       ├── Pearson & Spearman correlation heatmaps
   │       ├── Scatterplots + regression lines per feature
   │       ├── Pairplots for pairwise relationships
   │       ├── Jointplots & hexplots for density analysis
   │       └── Boxplots + IQR-based outlier detection & removal
   │
   ├── Phase 3: Data Preparation
   │       ├── Train-test split (80/20)
   │       └── StandardScaler normalization
   │
   ├── Phase 4: Model Development
   │       └── 5 regression models compared
   │
   ├── Phase 5: Model Evaluation
   │       ├── R², MAE, MAPE metrics
   │       ├── Residual distribution analysis
   │       └── y_test vs y_pred scatterplot
   │
   └── Phase 6: Feature Importance
           └── Linear Regression coefficients → app vs. website impact
```

---

## 📈 Models & Results

Five regression algorithms trained and evaluated on identical 80/20 splits with StandardScaler preprocessing:

| Model | R² Score | MAE | MAPE |
|---|---|---|---|
| **Linear Regression** ✅ | **0.9770** | **8.29** | **1.71%** |
| Random Forest Regressor | 0.9395 | 13.52 | 2.77% |
| XGBoost Regressor | 0.9280 | 14.35 | 2.88% |
| K-Nearest Neighbors | 0.9108 | 16.34 | 3.32% |
| Decision Tree Regressor | 0.8498 | 21.68 | 4.39% |

### 🏆 Winner: Linear Regression

A surprise result — **Linear Regression outperforms all ensemble and boosting methods**, including XGBoost and Random Forest. This tells us something important: **the relationship between behavioral metrics and yearly spending is fundamentally linear**. Complex models overfit noise that simply isn't there.

---

## 💡 Key Findings

### Feature Importance (Linear Regression Coefficients)

| Feature | Relative Impact |
|---|---|
| 🥇 `Length of Membership` | **Highest** — the single strongest driver of spending |
| 🥈 `Time on App` | **High** — significant positive impact |
| 🥉 `Avg. Session Length` | **Moderate** — meaningful contribution |
| ❌ `Time on Website` | **Negligible** — near-zero coefficient |

### App vs. Website — The Verdict

> 📱 **Time on App has dramatically higher influence on Yearly Amount Spent than Time on Website.**

Correlation with spending:
- `Time on App`: ~48% (Pearson correlation)
- `Time on Website`: near-zero — effectively no linear relationship

The data speaks clearly: **the mobile app is where revenue is generated.**

---

## 🎯 Business Recommendations

Based on the modeling and EDA, three high-priority strategic actions for EliteShoppers.com:

### 1. 📱 Double Down on the Mobile App
Time on App is the #2 revenue driver after membership tenure. Every minute a customer spends on the app correlates with higher spending. Invest in:
- UX/UI improvements that increase session depth
- Personalized push notifications to re-engage dormant users
- In-app exclusive deals and loyalty rewards

### 2. 🔒 Maximize Membership Retention
Length of Membership is the **strongest predictor of spending** — loyal, long-term customers spend significantly more. Prioritize:
- Subscription perks and tiered loyalty programs
- Early access to sales for long-tenure members
- Proactive churn prevention for members approaching the 1–2 year mark

### 3. 🌐 Deprioritize Website Development (for now)
Time on Website shows virtually no correlation with spending. Redirecting engineering resources from website enhancements to app improvements offers a far better ROI based on current data.

---

## 🛠 Tech Stack

```
Language     Python 3.10+
ML Library   scikit-learn, XGBoost
Data         pandas, NumPy
Viz          matplotlib, seaborn
Environment  Google Colab / Jupyter Notebook
```

---

## ▶️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/Pfuglo1/customer-spending-prediction.git
cd customer-spending-prediction

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn xgboost

# 3. Launch the notebook
jupyter notebook Predicting_Customer_Annual_Spending_Using_Behavioral_Metrics.ipynb
```

> 📂 Place `Ecommerce Customers.csv` in the same directory before running.

---

## 🗂 Project Structure

```
customer-spending-prediction/
│
├── Predicting_Customer_Annual_Spending_Using_Behavioral_Metrics.ipynb  # Main notebook
├── _Predicting_Customer_Annual_Spending_Using_Behavioral_Metrics.pdf   # Requirements doc
├── README.md                                                            # You are here
└── Ecommerce Customers.csv                                              # Dataset
```

---

<div align="center">

**Built for EliteShoppers.com | Analytica Insights 📊**

*The data said: build the app. The model agreed.*

*Found this useful? Don't forget to ⭐ the repo!*

</div>
