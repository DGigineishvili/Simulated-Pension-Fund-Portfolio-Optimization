# We built a simplified Pension fund optimization model using linear programming

The project was inspired by the investment strategy and reporting framework of the Georgian Pension Fund. The model incorporates realistic portfolio management considerations, including diversification requirements, asset allocation limits, minimum domestic investment requirements, bond allocation requirements, and a minimum return target designed to achieve positive real returns.

5 of the ETF's used are exactly the ones primarily invested in by Georgian pension fund excluding EWY (Korean stocks)

The assets used:

### Equity ETFs
- **INTC** – Intel Corporation stock (US semiconductor company)
- **SPY** – SPDR S&P 500 ETF (tracks S&P 500 index)
- **IVV** – iShares Core S&P 500 ETF (tracks S&P 500 index)
- **VGK** – Vanguard FTSE Europe ETF (developed European equities)
- **VPL** – Vanguard FTSE Pacific ETF (developed Asia-Pacific equities)
- **VWO** – Vanguard FTSE Emerging Markets ETF
- **EWY** – iShares MSCI South Korea ETF
- **ILF** – iShares Latin America 40 ETF

### Bonds
- **IEF** – iShares 7–10 Year Treasury Bond ETF
- **TLT** – iShares 20+ Year Treasury Bond ETF

### Georgian Assets
- **BOG** – Bank of Georgia Group PLC stock
- **TBC** – TBC Bank Group PLC stock
- **CGEO** – Georgia Capital PLC stock

### Consumer Stock
- **KO** – Coca-Cola Company stock
**All of the stocks traded on London stock exchange were converted to USD using historical daily GBP-USD exchange rates**

## Optimization Model

The portfolio allocation problem was formulated as a linear programming model using the Mean Absolute Deviation (MAD) framework.

The model minimizes the average absolute deviation of portfolio returns from the expected portfolio return while satisfying the following constraints:

- Portfolio weights sum to one
- No short selling is allowed
- Individual equity assets cannot exceed 10% allocation
- Individual bond assets cannot exceed 12% allocation
- Minimum 20% allocation to bonds
- Minimum 10% allocation to Georgian-related domestic assets
- Minimum 1% allocation to each Georgian-related asset
- Minimum annual return requirement of 4%

The model was implemented and solved using Pyomo in Python.

## Analysis Performed

The project includes several additional analyses:

- Exploratory data analysis of asset returns
- Comparison of Mean Absolute Deviation and standard deviation as risk measures
- Analysis of optimal portfolio weights
- Shadow price analysis to identify binding constraints and their impact on risk minimization
- Sensitivity analysis of domestic investment requirements and minimum return constraints
- Robustness analysis using alternative price scenarios based on low and high historical daily prices
- Efficient frontier analysis to evaluate the position of the optimized portfolio

## Main Findings

The optimal portfolio allocation was strongly influenced by institutional constraints. Bond ETFs reached their maximum allowed allocation due to their role in reducing portfolio risk. Equity allocations were mainly determined by diversification limits, while Georgian-related assets were included due to domestic investment requirements.

The minimum return constraint was not binding in the baseline model, as the optimized portfolio achieved an expected annual return above the required threshold. Shadow price analysis showed that bond allocation constraints had the largest impact on the objective function, suggesting that relaxing these restrictions could further reduce portfolio risk.

## Repository Contents

- Model code: Python implementation of the optimization model using Pyomo
- Dataset files: Historical financial data used in the model
- Report: Full project documentation and analysis

## Technologies Used

- Python
- Pyomo
- Pandas
- NumPy
- Matplotlib
- Yahoo Finance data
- Linear Programming optimization
