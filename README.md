# Algorithmic Trading Strategy for Cryptocurrency Markets

### A Submission for the UM Datathon 2024 by Team OTAKGONE

[![Python Version](https://img.shields.io/badge/Python-3.9%2B-blue.svg?style=for-the-badge&logo=python)](https://www.python.org/downloads/)
[![Libraries](https://img.shields.io/badge/Libraries-Pandas%20%7C%20NumPy%20%7C%20Scikit--learn-orange.svg?style=for-the-badge)](https://scikit-learn.org/stable/)
[![Models: XGBoost & LightGBM](https://img.shields.io/badge/Models-XGBoost%20%7C%20LightGBM-green.svg?style=for-the-badge)](https://xgboost.ai/)

---

## 1. Project Overview

This project was developed for the UM Datathon 2024, focusing on analyzing the factors that influence cryptocurrency price dynamics and developing a profitable, data-driven trading strategy. Our analysis delves into a rich time-series dataset to understand the relationships between on-chain metrics, market activity, and price movements.

The core objective is to move beyond simple correlation and build a predictive model that can generate actionable trading signals, which are then backtested and optimized for risk-adjusted returns.

---

## 2. Research Questions

Our investigation was guided by the following key questions:

1.  **How do various on-chain and market factors affect cryptocurrency price movements?**
2.  **Which factors are most influential in predicting price changes?**
3.  **How does market behavior differ during periods of high versus low volatility?**
4.  **What quantitative thresholds must be crossed for these factors to have a significant impact on price?**

---

## 3. Methodology & Analysis

Our approach combined in-depth exploratory data analysis (EDA), advanced statistical modeling, and machine learning to uncover insights and build a robust trading model.

### 3.1. Data Preprocessing & EDA

-   **Data Cleaning:** Handled missing values and performed data type conversions.
-   **Feature Engineering:** Created lagged features to analyze time-series dependencies and rolling statistics to capture trends.
-   **Correlation Analysis:** A comprehensive correlation matrix was generated to identify initial relationships between the 42 available features and the target variable, `close_price`.
-   **Visualization:** Plotted relationships between key variables (`difficulty`, `taker_buy_volume`, `blockreward_usd`) and `close_price` to visually inspect trends.

### 3.2. Advanced Analysis Techniques

-   **Piecewise Regression:** Applied to the `difficulty` metric to identify structural breaks in its relationship with price. This revealed that the price reacts differently to changes in difficulty above and below a specific threshold.
-   **Volatility Clustering:** Analyzed periods of high and low volatility to understand how factors like `taker_buy_volume` behave under different market conditions.
-   **Feature Importance:** Used machine learning models to determine the most significant predictors of price movement.

---

## 4. Key Findings

Our analysis revealed several critical factors that drive cryptocurrency prices:

1.  **Taker Buy Volume is the Strongest Predictor:** Our models consistently identified `taker_buy_volume` as the most important feature (59% importance), indicating that aggressive buying pressure is a primary driver of price increases.
2.  **Mining Rewards are Highly Influential:** `blockreward_usd` was the second most important factor (41% importance), highlighting that miner incentives and profitability are strongly linked to market prices.
3.  **Mining Difficulty Shows a Non-Linear Relationship:** Piecewise regression identified a breakpoint at a difficulty level of 2.0. Below this point, price increases are gradual, but above it, the price rises much more steeply (slope of 4.43 vs. 0.54).
4.  **Trading Volume Dictates Price Action:** Higher buy volumes consistently correlate with price increases, while higher sell volumes lead to price drops.

![Feature Importance Chart](https://imgur.com/a/ReB4c8J)
*(Chart showing the importance of taker_buy_volume and blockreward_usd)*

---

## 5. Predictive Modeling & Trading Strategy

### 5.1. Model Development

-   **Models Used:** We trained and evaluated several regression models, including **Linear Regression**, **Random Forest**, **XGBoost**, and **LightGBM**, to predict the `close_price`.
-   **Performance:** The tree-based models (Random Forest, XGBoost, LightGBM) significantly outperformed Linear Regression, with Random Forest achieving an R-squared value of **0.99**.

### 5.2. Algorithmic Trading Strategy

-   **Signal Generation:** A momentum-based strategy was developed using the Relative Strength Index (RSI) and moving averages to generate buy and sell signals.
-   **Backtesting Framework:** A custom backtesting framework was built to evaluate the strategy's performance, accounting for a 0.02% transaction fee.
-   **Performance Metrics:** The strategy was evaluated using the **Sharpe Ratio** and **Maximum Drawdown**.

### 5.3. Strategy Optimization

The initial backtesting revealed a profitable but highly volatile strategy with significant drawdowns. We implemented an optimization layer to improve its risk-adjusted returns.

-   **Before Optimization:** The strategy was unpredictable, with a wide, negatively-skewed Sharpe Ratio distribution and deep drawdowns.
-   **After Optimization:** The optimized strategy showed a much smoother equity curve, a Sharpe Ratio distribution shifted towards positive values, and significantly reduced maximum drawdowns. This demonstrates a more stable and reliable trading performance.

![Sharpe Ratio Distribution](https://i.imgur.com/your-sharpe-ratio-chart.png)
*(Comparison of Sharpe Ratio distribution before and after optimization)*

---

## 6. How to Run This Project

To replicate this analysis, please follow these steps:

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/crypto-trading-datathon.git](https://github.com/your-username/crypto-trading-datathon.git)
    cd crypto-trading-datathon
    ```

2.  **Set up a Python Environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: You will need to create a `requirements.txt` file with libraries like pandas, numpy, scikit-learn, xgboost, lightgbm, matplotlib, etc.)*

4.  **Run the Analysis:**
    -   The core analysis and modeling are contained within the Jupyter Notebook: `Datathon_Analysis.ipynb`.
    -   Open and run the cells sequentially to reproduce the findings.

---

## 7. Team

**Team Name:** OTAKGONE
- Lee Wen Kang
- Nabil Yusaidi
- Tan Shi Ying
