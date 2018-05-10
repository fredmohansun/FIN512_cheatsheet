* Group of 30 Recommendation
    * Who: G30(1978), private, nonprofit, international body composed of very senior representatives of the private and public sectors and academia… aims to deepen understanding of international economic and financial issues, to explore decisions, and to examine the choices available to market practitioners and policymakers.
    * When: 1993
    * What: Recommendation 2-9
        1. Marking to market
        2. Market Valuation methods
        3. Identifying Revenue Sources
        4. Measuring Market Risk
        5. Stress Simulations
        6. Investing and Funding Forecast
        7. Independent Market Risk Management
        8. Practices by End-Users

* Greek Letters
    - Black-Scholes Formula
    $$C(t,S) = e^{-\delta(T-t)}SN(d_1)-e^{-r(T-t)}KN(d_2)$$
    $$N(t,S) = e^{-r(T-t)}KN(-d_2)-e^{-\delta(T-t)}SN(-d_1)$$
    $$d1 = \frac{ln(\frac{S}{Ke^{-(r-\delta)(T-t)}})+\frac{\sigma^2(T-t)}{2}}{\sigma \sqrt{T-t}}$$
    $$d2 = \frac{ln(\frac{S}{Ke^{-(r-\delta)(T-t)}})-\frac{\sigma^2(T-t)}{2}}{\sigma \sqrt{T-t}} = d1 - \sigma \sqrt{T-t}$$
    - Black-Scholes PDE
    $$V_t + \frac{1}{2}\sigma^2 S^2 V_{SS}+(r-\delta)S V_S - rV = 0$$
    - Greeks
    
Greeks | Call | Put| Call Sign| Put Sign
----- | ----- | ----- | ----- | -----
$\Delta$ | $N(d_1)$ | $-N(-d_1)$ | l+ s- | l- s+
$\Gamma$ | $\frac{1}{S\sigma \sqrt{T-t}}\phi(d_1)$ | Same | l+ s- | l+ s-
$v$ | $S\sqrt{T-t}\phi(d_1)$ | Same | l+ s- | l+ s-
$\Theta$ | $\frac{S\sigma}{2\sqrt{T-t}}\phi(d_1)-rKe^{-r(T-t)N(d_2)}$ | $\frac{S\sigma}{2\sqrt{T-t}}\phi(d_1)+rKe^{-r(T-t)N(-d_2)}$ | l- s+ | l- s+ 
$\rho$ | $K(T-t)e^{-r(T-t)}N(D_2)$ | $-K(T-t)e^{-r(T-t)}N(-D_2)$ | l+ s- | l- s+


* Value-at-Risk(VaR)
    - Key points:
        * x percent(-ile)
        * t days
        * position value
    - How:
        * Hist Simulation: Use risk factor in history to calculate P/L => Draw P/L Hist => find x percentile (Can be weighted)
        * Delta-Normal: Find position Delta => construct distribution => get x percentile
        * Monte Carlo: Simulate M times position value => find x percentile
    - Cons:
        * Hist: may ignore important risk factor
        * DN: when non-linearity becomes so strong
        * Monte Carlo: $N \times K \times M$ can be astronomical

* Variance
    - Unbiased $\frac{1}{N-1}\sum_{1}^{N}(r_t-\bar{r})^2$
    - MLE $\frac{1}{N}\sum_{1}^{N}(r_t-\bar{r})^2$    
    - Realized $\frac{1}{N}\sum_{1}^{N}r_t^2$    

* Extreme Value Theorem
    - what: Behavior of certain extreme values is the same, regardless of the distribution that generates the data
    - How: 
        1. Block Maxima Model: Maxima of large samples of (identically distributed) observations satisfy the generalized extreme value (GEV) distribution
        2. Peaks Over Threshold (POT) Model: For a large class of distributions, extreme realizations above a high (or below a low) threshold follow the generalized Pareto distribution
    - GPD:
    $$
    \left\{
       \begin{array}{ll}
          1-\bigg(1 + \xi\frac{x}{\beta}\bigg)^{-\frac{1}{\xi}}, \xi \neq 0 \\
          1-e^{-\frac{x}{\beta}}, \xi = 0
       \end{array}
    \right. 
    $$
    $$
    \xi \; is \; shape \; parameter, \; \beta \; is \; scaling \; parameter 
    $$
    - GPD VaR:
    $$P(X-u>x|X>u)\approx 1-G(X) = \bigg(1+\frac{x}{\beta}\bigg)^{-\frac{1}{\xi}} $$
    $$P(X-u>x) = P(X>u) \bigg(1+\frac{x}{\beta}\bigg)^{-\frac{1}{\xi}} $$
    $$
        \alpha = P(X>VaR) = P(X>u+x) = P(X>u)(1 + \xi \frac{VaR-u}{\beta})^{-\frac{1}{\xi}} 
    $$
    $$VaR = u + \frac{\beta}{\xi}\bigg[\bigg(\frac{\alpha}{P(X>u)}\bigg)^{-\xi} - 1\bigg] $$
    - GPD parameter:
        * $\beta$ and $\xi$: MLE
        * $P(X>u)$: frequency probability
        * u:
            - Theoretical mean excess function: $e(u) = E[X-u|X>u] = \frac{\beta +\xi u}{1-\xi}$
            - Estimated by: $e(u) \approx \frac{1}{n_u}\sum_{1}^{n_u}(X_i-u)$
            - Choose u: choose the smallest "large enough" u: where estimated e(u) becomes linear

* Coherent Risk Measure
    - What: 
        $$
        \begin{array}{ll}
        i.\rho(x+y)\leq\rho(x) + \rho(y), \; diversification \\
        ii.\rho(\alpha x) = \alpha\rho(x) \\
        iii.\rho(x) \geq \rho(y), \; if \; x \leq y \\
        iv.\rho(x+(1+r)b) = \rho(x) - b \; adding \; risk-free \;reduce\;risk
        \end{array}
        $$
    - Standard Portfolio Analysis of Risk(SPAN) And Conditional VaR(CVaR)
        * SPAN: weight 1 for asset i, repeat M times(possibly size of instruments), choose the largest loss
        * Expected Shortfall: $CVaR = E[loss|loss>VaR_{1-\alpha}]$
            - $\phi_{Tr}(z|z\leq Tr) = \frac{\phi(z)}{N(Tr)}$ and $E[z|z\leq Tr] = -\frac{\phi(Tr)}{N(Tr)}$
            - $$ES^p_{t+1} = -\sigma_{portfolio,t+1}\frac{\phi(-VaR^p_{t+1}/\sigma_{portfolio,t+1})}{N(-VaR^p_{t+1}/\sigma_{portfolio,t+1})}=\sigma_{portfolio,t+1}\frac{\phi(N^{-1}_p)}{p}$$
            - $$\frac{ES^p_{t+1}-VaR^p_{t+1}}{VaR^p_{t+1}}=-\frac{\phi(N^{-1}_p)}{pN^{-1}_p}-1$$

* Stress Test
    - limitation of VaR:
        * does not provide information on the magnitude of the losses when the value-at-risk is exceeded
        * provides no information about the direction of the risk exposure
        * VaR says nothing about the risk due to factors that are omitted from the VaR model
    - Select Scenario:
        * Past extreme market events
        * Zero-out scenarios: assume shock in key market factors, zero-out other peripheral market factor
        * Anticipatory Stress Scenarios: e.g. Second Korean War
        * Predictive Anitcipatory Stress Scenarios: assume changes in core risk factors and use covariance matrix of changes in the market factors to compute the conditional expected changes
            1. Use Market model $x_2 = \beta_{20} + \beta{21}x_1 + \epsilon_2$
            2. $E[x_2|x_1 = r] = \beta_{20} + \beta{21}x_1 + E[\epsilon_2|x_1] = \beta_{20} + \beta_{21} r = \mu_2 - \beta_{21} \mu_1 + \beta_{21} r = \mu_2 - \frac{cov_{21}}{\sigma_1^2} \mu_1 + \beta_{21} r = \mu_2 - \frac{\sigma_1\sigma_2\rho_{21}}{\sigma_1^2} \mu_1 + \beta_{21} r$
    - Stress VaR
        * Stress coef times vol is stressed vol

* Regression
    - Pitfall 1 Hurwitz bias: sample bias in dynamic models, so $\phi_1$ in AR(1) is smaller and close to 1
    - Pitfall "2" When the data-generating process is stationary, OLS is good, not good if neither stationary nor cointegration. 
    
* Time Series
    - Strictly Stationary Process: $\forall m,n, (Y_1,\dots,Y_n)\; and \;(Y_{1+m},\dots,Y_{n+m})\; have\; same\; dist$
    - Weakly Stationary: $E = \mu, Var(Y_t) = \sigma^2, Cov(Y_t,Y_s) = \gamma(|t-s|)$
    
* MLE
    - Fisher Infomation: $I(\theta) = -E\bigg[\frac{d^2}{d\theta^2}log(L(\theta))\bigg]$, $s_{\hat{\theta}} = \frac{1}{\sqrt{I(\hat{\theta})}}$
    - CLT for MLE: CI = $[\hat{\theta}-s_{\hat{\theta}}z_{\alpha/2},\hat{\theta}+s_{\hat{\theta}}z_{\alpha/2}]$
    - Observeed Fisher Information: $I^{obs}(\theta) = -\frac{d^2}{d\theta^2}log(L(\theta))$, $s^{obs}_{\hat{\theta}} = \frac{1}{\sqrt{I^{obs}(\hat{\theta})}}$
    - Multivariate case: replace second derivative for Hessian Matrix $H_{ij} = f_{x_ix_j}$
    - Likelihood ratio test:
        * m = constraints on $\boldsymbol{\theta}$
        * reject $H_0$ if $2[ln(L(\hat{\boldsymbol{\theta}}_{ML}))-ln(L(\hat{\boldsymbol{\theta}}_{0,ML}))] > c$ where c is $\alpha$ quantile of $\chi^2_m$ (qchisq(alpha, df=m))

* Garch
    - GARCH(1,1): $\sigma^2_{t+1} = \omega + \alpha R^2_t + \beta \sigma^2_t, \alpha + \beta <1, define \sigma^2 = \frac{\omega}{1-\alpha-\beta}$ 
    - Use of GARCH: Mean-var optimization// DN and MC VaR// Filtered Hist Simulation VaR// when IV not available
    - NGARCH(1,1): $\sigma^2_{t+1} = \omega + \alpha (R^2_t-\theta\sigma_t)^2 + \beta \sigma^2_t = \sigma^2_{t+1} = \omega + \alpha \sigma^2_t(z_t -\theta)^2+ \beta \sigma^2_t$
    - GJR-GARCH(1,1): $\sigma^2_{t+1} = \omega + \alpha R_t^2 + \alpha \theta I_tR^2_t + \beta \sigma_t^2, I_t= 1,\; if\; R_t<0$
    - EGARCH(1,1): $ln(\sigma^2_{t+1}) = \omega + \alpha(\phi R_t+\gamma[|R_t|-E[|R_t|]]) + \beta ln(\sigma^2_t)$, display leverage effect when $\alpha \phi < 0$
    - With NIF: $NIF(z_t) = (|z_t-\theta_1| - \theta_2(z_t-\theta_1))^{2 \theta_3}$, and $\sigma^2_{t+1} = \omega + \alpha \sigma^2_t NIF(z_t) + \beta \sigma_t^2$, GARCH: (0,0,1), NGARCH: ($\theta_1$,0,1)
    - Return standarized by conditional volatility conform to normal distribution except for extreme left (loss tail is thicker or left skew)