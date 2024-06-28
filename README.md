# <ins>Stochastic-Volatility</ins>

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

The Heston model is a cornerstone of stochastic volatility modeling in finance, providing a more realistic depiction of market behavior by incorporating mean-reverting stochastic volatility. This model addresses the limitations of constant volatility assumptions in traditional models like Black-Scholes. 

This stochastic volatility model is primarily used in the pricing and risk management of financial derivatives, especially options. Here are some specific products and applications where the Heston model is commonly employed:

### Options Pricing:
- Vanilla Options: Both European and American style options.
- Exotic Options: Path-dependent options, barrier options, Asian options, etc.

### Volatility Derivatives:
- Variance Swaps: Contracts where parties exchange realized variance for a predetermined variance strike price.
- Volatility Options: Options on the future volatility of an underlying asset.

### Risk Management:
- Portfolio Management: Assessing and managing the risk of portfolios containing options or other derivatives.
- Hedging: Determining optimal hedging strategies for derivatives positions.

### Model Calibration and Validation:
- Model Calibration: Adjusting model parameters to fit observed market prices of derivatives.
- Model Validation: Assessing the accuracy of the Heston model against historical data and market behavior.

### Market and Trading Strategies:
- Volatility Trading: Strategies based on anticipated changes in volatility, utilizing volatility surfaces derived from the Heston model.
- Structured Products: Designing structured products that embed options or volatility derivatives.

## Key Features

- **Mean-Reverting Volatility**: The Heston model assumes that the variance of an asset price is not constant but follows a stochastic process that tends to revert to a long-term mean. This captures the empirically observed phenomenon of volatility clustering in financial markets.

- **Stochastic Differential Equations**: The basic Heston model assumes that the asset price $S_t$ is governed by a stochastic process. The asset price $S_t$ and its variance $v_t$ evolve according to the following dynamics where the volatility $\sqrt{v_t}$ follows an Ornstein-Uhlenbeck process:

<p align="center">
$dS_t = \mu S_t dt + \sqrt{v_t} S_t dW_t^S$
</p>

<p align="center">
$dv_t = \kappa (\theta - v_t) \, dt + \sigma \sqrt{v_t} \, dW_t^v$
</p>

&emsp;&emsp;&emsp;&dash; $\mu$ : Drift rate of the asset price.

&emsp;&emsp;&emsp;&dash; $\kappa$ : Rate at which volatility reverts to its long-term mean.

&emsp;&emsp;&emsp;&dash; $\theta$ : Long-term mean level of the variance.

&emsp;&emsp;&emsp;&dash;  $\sigma$ : Volatility of the variance (volatility of volatility).

&emsp;&emsp;&emsp;&dash; $W_t^S$ and $W_t^v$ : Correlated Wiener processes with correlation $\rho$.

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

Parameter estimation is a crucial step in implementing the Heston model for stochastic volatility in financial engineering. In this project, we leverage historical market data to accurately estimate the model parameters using advanced statistical techniques, primarily focusing on maximum likelihood estimation (MLE).

## Key Features

- **Data Collection**:

   - Gather historical data of the underlying asset's prices and optionally its volatility. This data serves as the basis for calibrating the Heston model.

- **Model Specification**:
   - Define the Heston model parameters:
     - $\mu$ : Drift rate of the asset price.
     - $\kappa$ : Rate at which volatility reverts to its long-term mean.
     - $\theta$ : Long-term mean level of the variance.
     - $\sigma$ : Volatility of the variance (volatility of volatility).
     - $\rho$ : Correlation between Wiener processes.

- **Estimation Techniques**:
   - **Maximum Likelihood Estimation (MLE)**:
     - Fit the Heston model to historical data by maximizing the likelihood function. MLE identifies parameter values that make the observed data most probable under the Heston model assumptions.
   
   - **Alternative Techniques**:
     - Explore other statistical methods such as Method of Moments or Bayesian estimation for robust parameter estimation, depending on the nature of available data and model complexity.

- **Validation and Sensitivity Analysis**:
   - Validate estimated parameters through goodness-of-fit tests and sensitivity analysis. Assess the robustness of the model by varying input assumptions and data sets.

### Benefits of Parameter Estimation

- **Enhanced Model Accuracy**: Accurate estimation of Heston model parameters improves the model's ability to reflect real market conditions and asset price behaviors.
- **Risk Management**: Better parameter estimates facilitate more effective risk management strategies, particularly in pricing derivatives and managing portfolio volatility.
- **Decision Support**: Provides valuable insights for investment decisions based on comprehensive modeling of asset price dynamics.

By employing rigorous parameter estimation techniques, this project aims to enhance understanding and application of stochastic volatility models in financial analysis and decision-making.

# Model Comparison

In this section, we compare the performance of the Heston model with the Black-Scholes model, focusing on their ability to accurately represent and predict asset price dynamics under different market conditions.

## Methodology

- **Model Specifications**:
   - **Heston Model**:
     - Incorporates stochastic volatility, capturing the mean-reverting nature of volatility in financial markets.
     - Parameters include $\mu$, $\kappa$, $\theta$, $\sigma$, and $\rho$, derived through parameter estimation techniques such as maximum likelihood estimation (MLE).

   - **Black-Scholes Model**:
     - Assumes constant volatility over time, providing a baseline for pricing derivatives under the assumption of efficient markets.
     - Parameterized by the asset price, volatility, risk-free rate, time to maturity, and strike price.

- **Backtesting on Historical Data**:
   - Utilize historical market data to simulate and compare the performance of both models in pricing options and predicting asset prices.

- **Evaluation Metrics**:
   - **Accuracy**: Compare model-generated prices with observed market prices.
   - **Robustness**: Assess model sensitivity to changes in market conditions and parameter estimates.
   - **Risk Management**: Evaluate the models' effectiveness in managing portfolio risk and hedging strategies.
 
# Monte Carlo Simulation

Monte Carlo simulation is a powerful technique used in finance to simulate the behavior of asset prices and calculate option prices under stochastic volatility models like the Heston model. In this section, we employ Monte Carlo methods to simulate price paths and derive option prices, providing insights into the dynamics and risk profiles of financial instruments.

## Methodology

- **Heston Model Simulation**:
   - Implement the Heston model dynamics using stochastic differential equations (SDEs) like referenced before.

- **Monte Carlo Simulation Steps**:
   - Generate random paths for the asset price $S_t$ and volatility $v_t$ using the Heston model dynamics.
   - Iterate over multiple simulations to capture the distribution of possible outcomes.

- **Option Pricing**:
   - Price European options using the simulated asset price paths and volatility.
   - Use the payoff function of the option (e.g., call or put) to calculate option prices at maturity.

# Conclusion

This project has been an enriching journey into the realm of financial engineering through the exploration and implementation of the Heston model for stochastic volatility modeling. It has provided me with invaluable insights into asset price dynamics, derivative pricing, and risk management strategies.

By delving into advanced techniques such as parameter estimation, model comparison, and Monte Carlo simulation, I've gained a deeper understanding of how stochastic volatility models operate in real-world financial scenarios. These experiences have not only bolstered my theoretical knowledge but also equipped me with practical skills in Python for model implementation and analysis.

Through this project, I've come to appreciate the complexities of financial markets and the significance of dynamic modeling approaches in capturing and interpreting market behaviors. It has reinforced the importance of informed decision-making in financial strategies, highlighting the transformative impact of quantitative methods in shaping effective risk management and pricing strategies.

Overall, this journey has been incredibly rewarding, allowing me to bridge theory with practical application and paving the way for continuous learning and exploration in financial engineering.


## Contact

For any questions or further information, please feel free to reach out to me on [LinkedIn :](https://www.linkedin.com/in/maxime-le-floch-1ba66a1b1/) or by mail : [Maxime Le Floch](mailto:maximebeguin02@gmail.com?subject=[GitHub]%20Source%20Han%20Sans) .


## Bibliography Use 

[Efficient Simulation of the Heston Stochastic Volatility Model](https://elsevier-ssrn-document-store-prod.s3.amazonaws.com/07/01/25/ssrn_id959385_code111031.pdf?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFcaCXVzLWVhc3QtMSJHMEUCIFZoeHGjsf3kd58HF2VtQAJ52cDTmaJk5vzDk9yHDXCkAiEAvLVo22TjUctQCFCGxyqhylGJHceUGSwrOWcYJlXreOgqvgUIEBAEGgwzMDg0NzUzMDEyNTciDLfWrG9hQvXdkecUayqbBSlepWWVrEMxh8%2FOE%2Fb8isZhrw%2B2WP4X0p%2ByXnb%2F4Vx3tLN6vNIXe9MsT1MNtg0%2F5F4jaunHvZZR96SfLS1qqHJ%2BtZlopmRfVuJctOcQo13jwgxovBGeHfKlo%2BbkdInDH7p2KE7ouHVmAcqerNWzvvd4k8AOQJNYhG5qT6Oy5xZPxDUFZSf81YEmxjwE2cKezqlSKfwFSN4OXeyhuE5FKhZx87aJL5GCisSbygcsC2lCB6KrE%2F6J9Qk6FbWKJ0kZ9Fm1JulPtDJlGa6XR%2BQTPzjCqTSzT5XvB0csPDu6lFYBjq%2FMVqg%2FUz0ModQvyL9mmFeL1nRa8Oa70RqmI324g27RVT9%2BVFpw7bbZ9qliaOBZqV7eB5%2BEAtTBbq6RBlksJxHenfBgtF55QpI3niEUG%2FObOpmtQeclaA52UriFISL8hR%2FLMoEdvvBA4nkfVj8bG47X6tP2SKsby0%2FWFfsLWfrFyIBq7RBot01fb4NYwcI%2BAKUNR1zo0kOgIueHw2%2BF1SFIyg1ZUp725W9TISvcSZC9rfQYV5KPqzXICn%2B77fKgWuTkYlHctvzpVXlpgYoMVOwgOiTdC%2F0A6KHdv1Iwz%2FMXlP4XnBiHzjV3sAxVMB%2FnlaKPqWgwtCHajtU7ALd9xcBOFy1eE98JY6Nk8tYQW7mhKspnMs%2FHUGJYtFW%2FbhOm82yiMBSq638lFV0iQhaYaETrXnYgjeA%2FrIHLM9cqgDkab2RjY4DRsyv7iWpChanucaXprDpCYaoYNBVuqJOt7EEgDDZxNc34PKawxTLFOUwAkTUoMqDuzQl3AX7hoAK0A0btqjFe7Z%2FHUKuNl60dcmiCvq6i50n%2BW1vgM0%2FKVVMBWz19FyZx2eLmYfm%2BaBHVSpJ7m8m%2FRXx9SswwlK75swY6sQHFaxSEu28He3vMD3RlgD5vt4BT6ksXJqeZoz%2BOupl1NPzkxTKbna38IaHicQCHfO%2B4LKxgTtXyfbD8SO2zz2BnY9YumECQxsoxjdevPZWvYaPk%2FYgQVqicwTHc7uLJc5dup6tADWWaBgENUQkJUo3EgH0DJHt5gICepVc9UA1sujsxTF15J4ZBHAOqbXVxJkSzIx0IYfQvFouyxZG2xLlN0237Oc%2F23kdZCppy2vCWaoI%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20240628T065109Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAUPUUPRWE4C3INSVS%2F20240628%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=f0c9e66c67969e23f5965c2d511c99165883e96a194075b86995c996e8e58e74)

[Heston model](https://en.wikipedia.org/wiki/Heston_model)

[Mean-Reverting Volatility](https://www.investopedia.com/terms/m/meanreversion.asp)

[Discretization of Euler Scheme](https://www.wias-berlin.de/people/bayerc/files/euler_talk_handout.pdf)


