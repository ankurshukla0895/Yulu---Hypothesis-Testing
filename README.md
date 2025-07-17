## 📄 Project Description: Yulu Demand Hypothesis Testing

This project analyzes key factors influencing the **demand for shared electric cycles** from **Yulu**, India’s premier micro-mobility service. Using a dataset of \~10,886 records, the objective was to perform **exploratory data analysis** (EDA) and **hypothesis testing** to identify meaningful patterns and statistical dependencies in user demand.

---

### 🎯 Objective

To identify variables that significantly impact the number of electric bikes rented (`count`) and provide actionable insights to improve operational efficiency and revenue generation.

---

## 🔢 Metrics & Statistical Methods Used

### 📈 **Exploratory Data Analysis (EDA)**

#### ➤ **Descriptive Statistics & Distributions**

* Evaluated summary statistics (mean, median, std deviation) for:

  * `casual`, `registered`, `count`, `temp`, `humidity`, `windspeed`
* Identified skewed distributions and potential **outliers** using:

  * **Histograms with KDE plots**
  * **Boxplots**

#### ➤ **Categorical Analysis**

* Frequency counts via **countplots** for:

  * `season`, `holiday`, `workingday`, `weather`
* Distribution comparisons using **boxplots** between `count` and each categorical variable.

#### ➤ **Correlation Analysis**

* **Pearson Correlation Coefficients** to assess linear relationships between:

  * `count` vs `temp`, `humidity`, `windspeed`, etc.
* **Heatmap** used to visualize correlation matrix.

---

### 🧪 **Hypothesis Testing**

#### ✅ **1. Chi-Square Test** – *Weather vs Season*

* **Purpose**: Check for independence between `weather` and `season`.
* **Metric**: Chi-square statistic (χ²)
* **Result**:

  * χ² statistic ≈ 44.09
  * p-value ≈ 1.35e-6
  * **Conclusion**: Reject Null Hypothesis → *Weather is dependent on season*

---

#### ✅ **2. Two-Sample T-Test** – *Effect of Working Day on Rentals*

* **Purpose**: Compare rental counts on working days vs non-working days.
* **Metric**: t-statistic & p-value
* **Variance Check**: Ratio of variances ≈ 1.1 → Assumed equal variance
* **Result**:

  * t-statistic ≈ -1.21
  * p-value ≈ 0.226
  * **Conclusion**: Fail to reject Null Hypothesis → *Working day has no significant effect on rentals*

---

#### ✅ **3. ANOVA / Kruskal-Wallis Test** – *Rentals vs Weather & Season*

* **Purpose**: Compare rental counts across different weather and seasonal conditions.
* **Test Selection**:

  * ANOVA **not applicable** due to failed assumptions (non-Gaussian, unequal variance based on **Levene's Test**)
  * Used **Kruskal-Wallis Test** (non-parametric alternative)
* **Metric**: Kruskal-Wallis H statistic & p-value
* **Result**:

  * p-value ≈ 4.61e-191
  * **Conclusion**: Reject Null Hypothesis → *Rental counts differ significantly across weather and seasons*

---

## 🔍 Summary of Key Metrics Used

| Metric/Test          | Purpose                                      | Key Value                              | Conclusion                 |
| -------------------- | -------------------------------------------- | -------------------------------------- | -------------------------- |
| Pearson Correlation  | Correlation of `count` with numeric features | High with `temp`, low with `windspeed` | Supports feature relevance |
| Chi-Square Test (χ²) | `weather` vs `season` independence           | p ≈ 1.35e-6                            | Dependent                  |
| Two-Sample T-Test    | `workingday` effect on `count`               | p ≈ 0.226                              | No significant effect      |
| Levene’s Test        | Equal variance check for ANOVA               | p ≈ 3.46e-148                          | Variances are not equal    |
| Kruskal-Wallis Test  | Rentals across weather/season                | p ≈ 4.61e-191                          | Rentals vary significantly |

---
