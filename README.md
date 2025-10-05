# QuantProjects-Main
What We're Building:
A Python tool that tests different portfolio strategies using historical stock data and compares their performance using risk-adjusted metrics.
The Goal:
Answer the question: "If I invested $10,000 in these stocks 5 years ago, which allocation strategy would have performed best on a risk-adjusted basis?"

Project Structure (3 Phases):
PHASE 1: DATA & METRICS
What: Get stock prices, calculate returns and risk for individual stocks
Models/Concepts:

Historical returns (mean of daily returns)
Volatility (standard deviation)
Sharpe ratio (return per unit of risk)
Correlation (how stocks move together)

Output: Understanding of individual stock characteristics

PHASE 2: PORTFOLIO CONSTRUCTION
What: Combine stocks into portfolios using different weighting strategies
Models/Concepts:

Equal-weight portfolio (25% each stock)
Markowitz portfolio theory (variance = weighted covariance matrix)
Diversification effect (why portfolio risk < sum of individual risks)

Output: Performance of simple portfolios

PHASE 3: OPTIMIZATION
What: Find the "best" portfolio weights that maximize risk-adjusted returns
Models/Concepts:

Mean-variance optimization (Markowitz efficient frontier)
Sharpe ratio maximization
scipy.optimize to find optimal weights

Output: The theoretically "best" portfolio allocation

The Complete Workflow:
Step 1: Download Data

Use yfinance to get 5 years of daily prices for 4 stocks
Clean data (remove NaN, handle missing dates)

Step 2: Calculate Individual Metrics

Daily returns = (Price_today - Price_yesterday) / Price_yesterday
Annualized return = mean(daily returns) × 252
Annualized volatility = std(daily returns) × √252
Sharpe ratio = (Return - Risk_free_rate) / Volatility
Correlation matrix = how each stock moves with others

Step 3: Build Equal-Weight Portfolio

Weights = [0.25, 0.25, 0.25, 0.25]
Portfolio return = sum(weights × individual returns)
Portfolio variance = weights^T × Covariance_Matrix × weights
Portfolio volatility = √variance
Sharpe ratio = (Portfolio_return - risk_free) / Portfolio_volatility

Step 4: Optimize Portfolio (Find Best Weights)

Define objective: maximize Sharpe ratio
Constraints: weights sum to 1, all weights ≥ 0 (no shorting)
Use optimization algorithm to find best [w1, w2, w3, w4]
Calculate performance of optimal portfolio

Step 5: Backtest & Visualize

Calculate cumulative returns over time for each strategy
Plot performance: Equal-weight vs Optimized vs Individual stocks
Compare final metrics in a table


Models/Concepts Used:

Statistical Measures:

Mean (expected return)
Standard deviation (risk/volatility)
Correlation/covariance (relationships between assets)


Financial Metrics:

Sharpe ratio (risk-adjusted performance)
Annualization formulas (252 trading days, √252 for volatility)


Portfolio Theory:

Markowitz mean-variance optimization
Diversification benefits (correlation < 1 reduces risk)
Efficient frontier concept


Optimization:

Scipy minimize function
Constrained optimization (weights sum to 1, no negatives)\

Final Output:
A Python script + visualization showing:

Individual stock performance over 5 years
Equal-weight portfolio performance
Optimized portfolio performance
Comparison table of returns, volatility, Sharpe ratios
Graph of cumulative returns
