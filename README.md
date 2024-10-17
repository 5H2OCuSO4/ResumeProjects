# ResumeProjects

# Master's Thesis: Low Risk Anomaly Strategy in the Options Market
Investing in safer assets while achieving higher returns, the low-risk anomaly has been empirically confirmed as profitable. I tested this anomaly in the US equity options market from 1996 to 2023, sorting options into five moneyness categories based on delta and six maturity groups. After cleaning the data to satisfy no-arbitrage conditions, I conducted monthly delta hedging to mimic the positions of financial intermediaries.

I measured option market risk and aggregate volatility risk using market beta and differential VIX index beta, both derived from underlying stock betas. The option market beta was bimodally distributed with a positive mean, while the differential VIX index beta showed an asymmetric distribution with a negative mean. I constructed Betting Against Beta (BAB) portfolios by going long on lower-beta options and short on higher-beta options. Positive BAB portfolio returns would confirm the low-risk anomaly, and negative returns would refute it. Additionally, I calculated the SPX option straddle factor as a control variable, since straddle portfolios tend to generate positive returns during economic recessions. If BAB portfolio returns exhibit a near-zero correlation with the straddle factor, the low-risk anomaly would hold in both economic recessions and booms. 

Hedging market risk proved to be a profitable strategy (positive alphas 0.66%), but hedging aggregate volatility risk may not be. There was a negative relationship between historical volatility of the underlying stock and option returns. Testing for option idiosyncratic risk presents a potential avenue for future research.

# Financial Engineering Project: SPX Options Calibration - Affine Jump-diffusion Model
**Section 1:** Removed options with negative bid prices, bid-ask spreads less than $5, missing prices, deep out-of-the-money, and deep in-the-money options.

**Section 2:** Estimated the SPX index dividend yield and spot rate (risk-free rate) using put-call parity. Calculated implied volatility from SPX option market prices.

**Section 3:** Explained the stochastic differential equation for the Affine Jump Diffusion model.

**Section 4:** Prepared the two-part characteristic function: one for the Heston process and one for the pure jump process.

**Section 5:** Presented the Call option pricing formula (Lewis' approach using inverse Fourier transform) and the objective function for parameter calibration (Average Relative Pricing Error, ARPE).

**Section 6:** Conducted two-step calibration based on the two-part characteristic function. First, calibrated the pure jump process parameters by assuming the volatility of the price process was the minimum implied volatility of the most out-of-the-money option using the Interior-point algorithm (local optimization). Second, calibrated the Heston process parameters using Sequential Quadratic Programming (SQP), Interior-point, and Particle Swarm Optimization (PSO) algorithms (global optimization). Achieved an ARPE of 1.16, consistent with Kokholm (2016). Calibrating the Heston process parameters was particularly challenging.

**Section 7:** Calculated SPX option model prices using the calibrated parameters and compared implied volatility surfaces between model prices and market prices for all strike prices and maturities.

**Section 8:** Used Monte Carlo simulation to illustrate the SPX index path and its stochastic variance path.

# Machine Learning Project: Anti-Money Laundering Detection - XGBoost
**Model:** applied XGBoost, a Supervised Learning method, to detect various types of money laundering transactions.

**Data Exploration:** I first conducted a statistical analysis of the features and identified a significant class imbalance. Specifically, money laundering transactions were far less frequent compared to normal transactions.

**Preprocessing:** To prepare the data, I converted categorical features into numeric values using a label encoder. I also standardized the 'Amount' feature and addressed the class imbalance issue using SMOTE (Synthetic Minority Over-sampling Technique) to generate additional instances of money laundering transactions.

**Model Tuning:** I built a parameter grid to perform hyperparameter tuning. However, due to hardware limitations (my friend assisted by running the code on her server with 200GB RAM and multi-core support, but it still took over 10 hours to complete), I was only able to search a limited parameter space.

**Training and Results:** Using the best parameters from the grid search, I trained the XGBoost model. Unfortunately, the validation curve indicated underfitting. A wider parameter grid search might yield more optimal results. Additionally, the evaluation on the test set showed that the F1-score was low, particularly for detecting money laundering transactions.

**Conclusion:** The training results are consistent with a reference paper that used a random forest model, which also had difficulty detecting complex money laundering patterns, such as Fan-in and Fan-out schemes. XGBoost has the potential to perform better with a more extensive hyperparameter search or changing to detect 'True or False' rather than money laundering types.
