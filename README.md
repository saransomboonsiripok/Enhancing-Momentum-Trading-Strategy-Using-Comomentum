# Comomentum-Enhanced Momentum Trading Strategy

This repository contains the final project for the **SMM282 - Quantitative Trading** module, part of the **MSc in Mathematical Trading & Finance** program at **Bayes Business School, City, University of London**. The project was conducted under the guidance of **Prof. Bernd Hanke**.

## Project Overview

The objective of this project was to explore and enhance a standard momentum trading strategy by incorporating the concept of **comomentum** as introduced by Lou and Polk (2021). Comomentum measures the high-frequency abnormal return correlation among stocks, providing insights into when momentum strategies are likely to perform well or poorly. This project involved:

- Calculating both standard and comomentum-adjusted momentum factors.
- Performing Fama-MacBeth regression analyses to evaluate the performance of these factors.
- Comparing the effectiveness of the standard momentum factor against the comomentum-adjusted momentum factor.

## Data Description

The project utilizes several datasets related to U.S. equity markets and the Fama-French three-factor model. Below is a detailed description of each data file used:

### 1. **US_Returns.csv**

- **Description**: Contains the weekly total returns of **7,261 U.S. stocks**, inclusive of reinvested dividends.
- **Dimensions**: 1,513 weeks (rows) × 7,261 stocks (columns).
- **Purpose**: Serves as the primary dataset for calculating the standard momentum factor by providing historical return data for each stock.

### 2. **US_live.csv**

- **Description**: Provides a binary indicator representing whether each company was active (**1**) or inactive (**0**) during each week.
- **Dimensions**: Matches the dimensions of **US_Returns.csv** (1,513 weeks × 7,261 stocks).
- **Purpose**: Ensures that only active (live) companies are included in the analysis for any given week, thereby maintaining the integrity of the momentum calculations and regression analyses.

### 3. **US_Dates.xlsx**

- **Description**: Offers a vector of **weekly dates** corresponding to the time dimension of the return matrix.
- **Format**: Dates are formatted as `YYYYMMDD`.
- **Purpose**: Provides a chronological reference for the time series data, enabling accurate indexing and time-based analyses throughout the project.

### 4. **US_Names.xlsx**

- **Description**: Contains a vector with the **names of all stocks** included in the sample.
- **Purpose**: Facilitates the identification and referencing of stocks within the momentum and comomentum computations, ensuring clarity and traceability in the analysis.

### 5. **FamaFrench.csv**

- **Description**: Comprises the weekly factor returns for the **three Fama-French factors**:
  - **Mkt-RF**: Market Excess Return
  - **SMB**: Size Factor (Small Minus Big)
  - **HML**: Value Factor (High Minus Low)
  - **RF**: Risk-Free Rate
- **Purpose**: Essential for calculating the comomentum measure by providing the necessary factors to regress against each stock's returns, thereby isolating the residuals used in comomentum calculations.

### 6. **comomentum.csv**

- **Description**: Contains the **precomputed comomentum values** for each week.
- **Purpose**: Stores the results of the computationally intensive comomentum calculations, allowing users to bypass the lengthy computation step by directly importing the precomputed values.

### 7. **Output - momentum_df.csv**

- **Description**: Stores the **computed standard momentum factors** for all stocks.
- **Purpose**: Provides the momentum factor data used in the Fama-MacBeth regression analysis for both the standard and comomentum-adjusted momentum factors.

### 8. **result_MacBeth_1.csv**

- **Description**: Contains the **Fama-MacBeth regression results** for the **standard momentum factor**.
- **Contents**: Includes the intercept and gamma (factor return) coefficients for each week.
- **Purpose**: Facilitates the evaluation of the standard momentum factor's performance over the sample period.

### 9. **result_MacBeth_2.csv**

- **Description**: Contains the **Fama-MacBeth regression results** for the **comomentum-adjusted momentum factor**.
- **Contents**: Includes the intercept and gamma (factor return) coefficients for each week.
- **Purpose**: Enables the assessment of the comomentum-adjusted momentum factor's effectiveness compared to the standard momentum factor.

## Contents

- **`SMM282 - Coursework_fin.ipynb`**: The Jupyter notebook containing the full code and analysis for the project. The notebook includes:
  - Data loading and preprocessing
  - Calculation of the standard momentum factor
  - Fama-MacBeth regression analysis for the standard momentum factor
  - Calculation of the comomentum measure
  - Adjustment of the momentum factor using comomentum
  - Fama-MacBeth regression analysis for the comomentum-adjusted momentum factor
  - Comparative analysis of results

- **Data Files**: As detailed in the [Data Description](#data-description) section.

## Results Summary

The analysis demonstrated that integrating comomentum into the momentum factor led to improved performance metrics:

### Standard Momentum Factor

- **Mean Factor Return**: 0.0004565 (weekly)
- **Annual Mean Factor Return**: 0.0240 (2.40%)
- **Annual Standard Deviation of Factor Return**: 0.1775
- **Cumulative Return**: 24.27%
- **Sharpe Ratio**: 0.1353
- **T-Statistic**: 1.27e-05 (Not statistically significant)

### Comomentum-Adjusted Momentum Factor

- **Mean Factor Return**: 0.0006394 (weekly)
- **Annual Mean Factor Return**: 0.0338 (3.38%)
- **Annual Standard Deviation of Factor Return**: 0.1775
- **Cumulative Return**: 62.33%
- **Sharpe Ratio**: 0.1905
- **T-Statistic**: 1.78e-05 (Still not statistically significant)

### Comparative Analysis

- **Mean Factor Return**: Increased from 0.0240% to 0.0338% annually.
- **Cumulative Return**: Enhanced from 24.27% to 62.33%.
- **Sharpe Ratio**: Improved from 0.1353 to 0.1905.
- **T-Statistic**: Slight improvement but remains low, indicating limited statistical significance.

**Interpretation**: The comomentum-adjusted momentum factor demonstrates better performance in terms of mean returns, cumulative returns, and Sharpe ratio compared to the standard momentum factor. However, the low t-statistics suggest that the factor returns are not statistically significant, indicating potential limitations in the robustness of the strategy.
