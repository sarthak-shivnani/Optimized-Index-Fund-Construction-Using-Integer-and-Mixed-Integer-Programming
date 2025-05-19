# Index Fund Portfolio Optimization
Portfolio Optimization for NASDAQ-100: Balancing Tracking Accuracy and Sparsity

This repository contains code and data for a portfolio optimization project aimed at constructing an optimized subset index fund that closely tracks the NASDAQ-100 index with minimal tracking error. The project uses a combination of Integer Programming (IP), Linear Programming (LP), and Mixed Integer Programming (MIP) techniques to select stocks and optimize portfolio weights.

## Overview

This project aims to build a cost-effective and optimized subset index fund that replicates the performance of the NASDAQ-100 index while minimizing tracking error. It addresses key challenges in portfolio management, such as reducing transaction costs and ensuring a diversified yet manageable portfolio.

## Project Objectives

- **Stock Selection**: Use Integer Programming to select a subset of stocks (m out of n) from the NASDAQ-100 that best represent the index based on a correlation matrix.
- **Weight Optimization**: Apply Linear Programming to assign optimal weights to the selected stocks in order to minimize the tracking error relative to the index.
- **Sparsity Enforcement**: Use Mixed Integer Programming with Big-M constraints to enforce sparsity in the portfolio, ensuring that only a limited number of stocks carry non-zero weights.
- **Evaluation**: Validate the portfolio performance using in-sample data (2023) and out-of-sample data (2024).

## Methodology

### Stock Selection using Integer Programming

- **Decision Variables**: 
  - `y_j`: Binary variable indicating if stock `j` is selected.
  - `x_ij`: Binary variable that indicates if stock `j` is chosen to represent stock `i`.
- **Objective**: Maximize the total similarity score (correlation) between each stock and its representative.
- **Constraints**:
  - Exactly `m` stocks are selected.
  - Each stock is represented by exactly one selected stock.
  - Representation is allowed only if the stock is selected.

### Weight Optimization using Linear Programming

- **Objective**: Minimize the absolute deviation between the portfolio return and the NASDAQ-100 index return.
- **Constraints**:
  - The sum of portfolio weights must equal 1 (fully invested portfolio).
  - Non-negativity of weights (no short positions).
  - Deviation constraints for each time period.

### Sparse Portfolio Construction with MIP and Big-M

- **Objective**: Similar to the LP weight optimization, but with an additional focus on sparsity.
- **Big-M Constraint**: Enforces that weights can be positive only if the corresponding binary selection variable is 1.
- **Cardinality Constraint**: Limits the number of stocks with non-zero weights to `m`.

## Datasets

- **2023data.csv**: Daily price data for the NASDAQ-100 and its component stocks for the year 2023, used for portfolio construction and in-sample analysis.
- **2024data.csv**: Daily price data for the year 2024, used for out-of-sample performance evaluation.


