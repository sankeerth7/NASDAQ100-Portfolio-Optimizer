# NASDAQ-100 Portfolio Optimization

This repository contains the implementation of a data-driven methodology to construct an optimized stock portfolio that closely tracks the **NASDAQ-100 Index**. The project employs **Integer Programming (IP)** and **Mixed-Integer Programming (MIP)** techniques to balance tracking accuracy, cost efficiency, and operational complexity. 

## Overview

The goal of the project is to identify a minimal subset of stocks from the NASDAQ-100 and optimize their weights to replicate the index's performance effectively. By doing so, this approach reduces portfolio complexity, minimizes transaction costs, and provides a streamlined strategy for fund management.

### Key Objectives:
1. Select an optimal subset of stocks (`m`) from the NASDAQ-100.
2. Minimize tracking error (difference in returns between the portfolio and the index).
3. Balance portfolio diversification with cost-efficiency and computational feasibility.



## Methodology

### 1. Data Preparation:
- **Data Source**: Daily price data for NASDAQ-100 component stocks (2023 in-sample, 2024 out-of-sample).
- **Preprocessing**: Calculated daily returns, handled missing values, and constructed a correlation matrix to quantify stock similarity.

### 2. Stock Selection (Integer Programming):
- Formulated a binary decision model to select `m` stocks that maximize similarity with the NASDAQ-100.
- Constraints included ensuring every stock in the index was represented and limiting the number of stocks selected.

### 3. Weight Optimization (Linear Programming):
- Optimized weights for the selected stocks to minimize tracking error.
- Constraints ensured weights summed to 1 and minimized absolute deviation from the index returns.

### 4. Mixed-Integer Programming (MIP):
- Combined stock selection and weight optimization into a single model.
- Introduced binary variables to control the number of stocks with non-zero weights.
- Achieved a sparse portfolio with high tracking accuracy using a computationally intensive approach.

### 5. Performance Evaluation:
- Metrics:
  - **Tracking Error**: Mean absolute deviation between portfolio and index returns.
  - **Portfolio Volatility**: Standard deviation of portfolio returns.
- Analyzed performance for in-sample (2023) and out-of-sample (2024) periods.



## Results

### Key Metrics:
- **Tracking Error**:
  - 2023: 0.0046
  - 2024: 0.00059
- **Portfolio Volatility**:
  - 2023: 0.0111
  - 2024: 0.0116

### Optimal Portfolio (m=5 stocks):
- Selected Stocks: HON, INTU, NXPI, PEP, SNPS.
- Optimized Weights:
  - HON: 16.20%
  - INTU: 22.01%
  - NXPI: 17.48%
  - PEP: 19.86%
  - SNPS: 24.45%

### Mixed-Integer Programming Insights:
- Stabilized tracking error at `m=40`, indicating diminishing returns with additional stocks.
- MIP allowed simultaneous optimization of stock selection and weighting.


## Tools & Technologies

- **Programming Language**: Python
- **Optimization Library**: Gurobi Optimizer
- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib


## Future Enhancements

1. **Dynamic Rebalancing**: Automate portfolio rebalancing with updated market data.
2. **Sector and ESG Constraints**: Introduce sector-based and environmental, social, and governance (ESG) factors.
3. **Tool Licensing**: Package the methodology as a software product for asset managers.
4. **Broader Applications**: Adapt the approach for international and sector-specific indices.
