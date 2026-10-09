# 📊 Marketing Campaign Optimization: A/B Testing & Time-Series Cointegration

## 🎯 Project Overview
This repository contains a data analytics and statistical modeling project designed to maximize return on investment (ROI) for a marketing agency's advertising campaigns. The study performs a comprehensive comparison between two major advertising networks: **Facebook Ads** and **Google AdWords**, evaluating performance metrics throughout the year 2019 to determine which platform yields superior results across engagement, volume, and cost-effectiveness.

---

## 💼 Business Problem & Research Question
* **Business Problem:** As a marketing agency, our primary objective is to maximize the return on investment (ROI) for our clients' advertising campaigns. By identifying the most effective platform, we can allocate resources more efficiently and optimize advertising strategies to deliver better outcomes for our clients.
* **Research Question:** Which ad platform is more effective in terms of conversions, clicks, and overall cost-effectiveness?

---

## 📂 Dataset Description
The dataset contains 365 daily tracking rows for the entire year of 2019 (January 1st, 2019, to December 31st, 2019) across the following key performance indicators (KPIs):
* **Date:** Timestamp of campaign performance tracking.
* **Ad Views:** The total number of impressions the ad received.
* **Ad Clicks:** The volume of user clicks driven by the ad.
* **Ad Conversions:** The volume of completed target actions (sales/sign-ups) generated.
* **Cost per Ad:** The daily spending metric associated with running the campaign.
* **Click-Through Rate (CTR):** The mathematical ratio of clicks to views (\(Clicks / Views\)).
* **Conversion Rate (CR):** The mathematical ratio of conversions to clicks (\(Conversions / Clicks\)).
* **Cost per Click (CPC):** The average budget incurred per single ad click (\(Ad\ Cost / Clicks\)).

---

## 🛠️ Tech Stack & Dependencies
The following data science libraries are utilized to execute data cleaning, visualization, statistical inference, and machine learning models:
* **Data Wrangling:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib.pyplot`, `seaborn`
* **Statistical Inference:** `scipy.stats` (Two-Sample Independent T-Test)
* **Time Series Analysis:** `statsmodels.tsa.stattools` (Engle-Granger Cointegration Test)
* **Machine Learning:** `sklearn.linear_model.LinearRegression`, `sklearn.metrics` (`r2_score`, `mean_squared_error`)

---

## 🔬 Execution Workflow & Insights

### 1. Exploratory Data Analysis & Feature Engineering
* Calculated key summary metrics across 365 days of data.
* Plotted histograms with Kernel Density Estimations (KDE) to discover that both campaigns exhibit clean, symmetrical normal distributions for daily click and conversion volume.
* Segmented conversion frequencies into categorical buckets (`less than 6`, `6 - 10`, `10 - 15`, `more than 15`) to visualize performance stability. Facebook demonstrated a markedly higher density of high-performing conversion days than AdWords.

### 2. Correlation Matrix Comparison
Calculated the explicit linear correlation coefficients between user clicks and ultimate conversions:
* **Facebook Ads Correlation:** `0.87` (Indicating a highly tight, positive relationship where ad engagement translates robustly into down-funnel sales).
* **AdWords Ads Correlation:** `0.45` (Indicating a moderate linear trend, suggesting external marketing variables impact performance).

### 3. A/B Testing via Hypothesis Inference
To confirm the platform conversion volume differences with mathematical certainty, a **Two-Sample Independent T-Test** was conducted:
* **Null Hypothesis (\(H_0\)):** \(\mu_{Facebook} \le \mu_{AdWords}\) (No statistically significant difference in conversion averages).
* **Alternative Hypothesis (\(H_1\)):** \(\mu_{Facebook} > \mu_{AdWords}\) (Facebook conversions are significantly greater).
* **Statistical Verdict:** The test yielded an exceptionally high T-statistic of `32.88` and an empirical \(p\)-value of `9.34e-134`. Since the \(p\)-value \(< 0.05\), the **Null Hypothesis is rejected**, proving Facebook's conversion superiority is mathematically absolute and not a byproduct of random chance.

### 4. Predictive Modeling via Linear Regression
A predictive Machine Learning model was trained on the Facebook campaign data to forecast conversion volumes given target click expectations:
* **Model Model Accuracy (\(R^2\) Score):** `76.35%` of variance explained.
* **Mean Squared Error (MSE):** `2.02`.
* **Actionable Output:** For 50 clicks, the campaign mathematically targets `13.0` conversions; expanding budget to reach 80 clicks targets an expectation of `19.31` conversions.

### 5. Advanced Time-Series Analysis: Engle-Granger Cointegration
To rule out spurious, short-term correlations caused by shared seasonal noise, an Engle-Granger Cointegration Test (`coint`) was executed to check for long-term equilibrium between **Ad Cost** and **Conversions**:
* **Cointegration Test Score:** `-14.7554`
* **Empirical P-value:** `2.1337e-26`
* **Strategic Takeaway:** The extreme \(p\)-value firmly rejects the null hypothesis of non-cointegration. This indicates a robust, long-term cointegrated equilibrium between campaign spending and actual conversion trends, granting corporate decision-makers highly predictable scaling models for future budget allocation.

---

## 🚀 How to Run the Analysis Locally
1. Clone this repository:
   ```bash
   git clone https://github.com
   ```
2. Navigate to your project folder and make sure your dataset file (`ABmarketing_campaign.csv`) is placed in the designated directory path.
3. Install the required python environment dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels
   ```
4. Run the Jupyter environment inside VS Code or via terminal:
   ```bash
   jupyter notebook
   ```
5. Open `AB Testing Analysis.ipynb` and select **Run All Cells**.
