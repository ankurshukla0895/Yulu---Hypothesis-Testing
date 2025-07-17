
## 📊 Yulu Shared Electric Cycles Demand Analysis

This project analyzes the key factors influencing the demand for Yulu's shared electric cycles in India. Using a combination of **exploratory data analysis (EDA)** and **statistical hypothesis testing**, we identify the significant variables affecting usage patterns, such as weather, season, holidays, and working days.

### 🔍 Problem Statement

Yulu, a leading micro-mobility provider in India, has observed a decline in revenue and seeks to understand what influences electric cycle demand. The objective is to:

* Identify which variables significantly affect rental demand.
* Evaluate how well these variables explain usage patterns.

# 📘 Yulu Demand Analysis – Hypothesis Testing

## 📌 Project Overview

This project analyzes the demand factors for **Yulu**, India’s leading micro-mobility service provider. The company has seen a drop in revenue and seeks to identify key factors affecting the demand for its shared electric cycles through **exploratory data analysis (EDA)** and **hypothesis testing**.

---

## 📂 Dataset Overview

* **Rows**: 10,886
* **Columns**: 12
* **Missing Values**: None
* **File**: `yulu dataset.txt` (CSV format)

### Key Columns:

* `datetime`
* `season`, `holiday`, `workingday`, `weather` *(categorical)*
* `temp`, `atemp`, `humidity`, `windspeed`
* `casual`, `registered`, `count` *(rental counts)*

---

## 🧪 Analysis Steps

### 1. **Data Preprocessing**

* Converted appropriate columns to `datetime` and categorical types.
* Checked for outliers in `casual`, `registered`, and `count`.

### 2. **Univariate Analysis**

* Distribution plots show:

  * `casual`, `registered`, and `count`: Log-normal distribution.
  * `temp`, `atemp`, `humidity`: Normal distribution.
  * `windspeed`: Binomial-like.

### 3. **Bivariate Analysis**

* **Boxplots & Scatterplots** were used to analyze relationships between:

  * `count` and categorical features (`season`, `holiday`, `weather`, `workingday`)
  * `count` and numerical features (`temp`, `humidity`, etc.)

---

## 📊 Hypothesis Testing

### ✅ **Chi-Square Test**: *Weather vs Season*

* **H₀**: Weather is independent of season.
* **Result**: **Rejected** (p < 0.05) → Weather **is dependent** on season.

### ✅ **2-Sample T-Test**: *Working Day vs Count*

* **H₀**: Working day has no effect on rentals.
* **Result**: **Not Rejected** (p > 0.05) → No significant difference in rentals between working and non-working days.

### ✅ **ANOVA / Kruskal-Wallis Test**: *Effect of Weather and Season on Rentals*

* **ANOVA Assumptions** failed (non-Gaussian, unequal variance).
* Used **Kruskal-Wallis Test** instead.
* **Result**: **Rejected** H₀ → Rentals **vary significantly** across different seasons and weather conditions.

---

## 📈 Key Insights

* Higher demand in **summer and fall**.
* More bikes rented on **holidays and weekends**.
* Rentals **drop** significantly:

  * In **rain, snow, fog**.
  * When **humidity < 20**.
  * When **temperature < 10°C**.
  * When **windspeed > 35 km/h**.

---

## 💡 Recommendations

* **Increase** bike availability during **summer and fall**.
* **No need** to adjust stock based on working day.
* **Reduce** stock on:

  * **Low humidity** days.
  * **Cold weather** days.
  * Days with **high windspeed or bad weather** (e.g., thunderstorms).

---

## 🛠 Tools Used

* Python: `pandas`, `matplotlib`, `seaborn`, `scipy.stats`
* Data Visualizations: Histograms, Boxplots, Scatterplots, Heatmaps
* Statistical Tests: Chi-Square, T-Test, Kruskal-Wallis

---

## 👨‍💼 Prepared For

**Yulu Micro-Mobility Pvt. Ltd.**
To support decision-making around demand planning and operational strategies.
