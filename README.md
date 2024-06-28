# Stochastic-Volatility

# Overview 
Hello, 

You may already know about my project, but for those who don't, I'm a Masters student in financial engineering and I've set myself a challenge called [**OneWeekOneProject**](https://github.com/Quacox?tab=repositories). Each week, I dive deep into a new topic within the vast world of market finance and quantitative methods. This week's focus is on Stochastic Volatility Modeling and its implementation in Python.

In financial markets, volatility is not constant but varies over time. Traditional models often assume constant volatility, but real market behavior tells a different story. Stochastic Volatility (SV) models capture this dynamic nature, providing a more accurate representation of market conditions.

# Project Highlights

- **Comprehensive Heston Model**: Implementation of key stochastic volatility models, including the Heston model, which features mean-reverting stochastic volatility.

- **Parameter Estimation**: Utilize historical market data to estimate the Heston model parameters through maximum likelihood estimation or other advanced statistical techniques.

- **Model comparison**: Evaluate the performance of the Heston model against the Black-Scholes model by backtesting both on historical data and assessing their accuracy.

- **Monte Carlo simulation**: Employ Monte Carlo methods to simulate price paths and calculate option prices under the Heston model.

# Comprehensive Heston Model

The Heston model is a cornerstone of stochastic volatility modeling in finance, providing a more realistic depiction of market behavior by incorporating mean-reverting stochastic volatility. This model addresses the limitations of constant volatility assumptions in traditional models like Black-Scholes. Key features and implementation details of the Heston model in this project include

## Key Features

- **Mean-Reverting Volatility**: The Heston model assumes that the variance of an asset price is not constant but follows a stochastic process that tends to revert to a long-term mean. This captures the empirically observed phenomenon of volatility clustering in financial markets.

- **Stochastic Differential Equations**: The basic Heston model assumes that the asset price $S_t$ is governed by a stochastic process. The asset price $S_t$ and its variance $v_t$ evolve according to the following dynamics where the volatility $\sqrt{v_t}$ follows an Ornstein-Uhlenbeck process:

<p align="center">
$dS_t = \mu S_t dt + \sqrt{v_t} S_t dW_t^S$
</p>

<p align="center">
$dv_t = \kappa (\theta - v_t) \, dt + \sigma \sqrt{v_t} \, dW_t^v$
</p>

&ensp;&ndash; $\mu$ : Drift rate of the asset price.

&ensp; &dash; $\kappa$ : Rate at which volatility reverts to its long-term mean.

&ensp; &ndash; $\theta$ : Long-term mean level of the variance.

&ensp; &ndash;  $\sigma$ : Volatility of the variance (volatility of volatility).

&ensp; &ndash; $W_t^S$ and $W_t^v$ : Correlated Wiener processes with correlation $\rho$.

- **Model Assumptions**:
  - The returns on the asset follow a geometric Brownian motion.
  - Volatility is stochastic and mean-reverting.
  - The model incorporates the leverage effect, where asset price changes are correlated with changes in volatility.

- **Advantages Over Black-Scholes**:
  - Captures the skew and kurtosis observed in the returns distribution.
  - Provides a better fit for pricing derivatives, especially for options with longer maturities or those that are deeply in- or out-of-the-money.

- **Implementation**:
  - The model is implemented in Python, leveraging numerical methods to solve the stochastic differential equations.
  - Includes functions for simulating asset paths, calculating option prices, and estimating model parameters.

By incorporating the Heston model into this project, we aim to provide a robust tool for analyzing and simulating the behavior of financial markets under more realistic conditions of stochastic volatility.

# Parameter Estimation




