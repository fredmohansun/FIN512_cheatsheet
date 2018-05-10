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
    
* T-dist
    - One can Fit Garch with $\tilde{t}(d)$ or $t_{assym}(d)$. Modified MLE likelihood L1 by $lnL_2 = ln L_1 - \sum_1^Tln(\sigma^2_{t})/2$. Quasi-MLE: with Garch already estimated (How?), calculate d from kurtosis $\xi_2$. $VaR^p_{t+1} = -\sigma_{t+1}\sqrt{(d-2)/d}t_p^{-1}(d)$. $ES_{t+1}^p = -\sigma_{t+1} \frac{\Gamma((d+1)/2)}{p\Gamma(d/2)\sqrt{\pi(d-2)}}((1+\frac{1}{d-2}t_p^{-1}(d))^{\frac{1-d}{2}}\frac{d-2}{1-d})$
    - t dist: $f_{d(x;d)}=\frac{\Gamma((d+1)/2)}{\Gamma(d/2)\sqrt{d\pi}}(1+x^2/d)^{-(1+d)/2}$, $\mathbb{E}[x] = 0(d>1)$, $Var[x] = \frac{d}{d-2}(d>2)$
    - z ~ standardized $\tilde{t}(0,1)$ by x ~ t(d) $z = \frac{x - \mathbb{E}[x]}{\sqrt{Var[x]}}$, where $f_d(z;d) = \frac{\Gamma((d+1)/2)}{\Gamma(d/2)\sqrt{\pi(d-2)}} (1+z^2/(d-2))^{-(1+d)/2},(d>2)$, MVSK: $0,1,0,\frac{6}{d-4}$
    - Asymetric t: with $A = 4d_2C\frac{d_1-2}{d_1-1}, B = \sqrt{1+3d_2^2 - A^2}, C=\frac{\Gamma((d_1+1)/2)}{\Gamma(d_1/2)\sqrt{\pi(d_1-2)}},d_1>2,-1<d_2<1$
    $f(z;d1,d2)=BC(1+\frac{(Bz+A)^2)}{(1-(+)d_2)^2(d_1-2)})^{-(1+d_1)/2},z<(\geq)-\frac{A}{B}$
    - Asymetric t MVSK: $0,1,\frac{m_3,3Am_2+2A^3}{B^3}, \frac{m_4-4Am_3+6A^2m_2-3A^4}{B^4}-3$, moments:$0, 1+3d_2^2, 16Cd_2(1+d_2^2)\frac{(d_1-2)^2}{(d_1-1)(d_1-3)}(d_1>3), 3\frac{d_1-2}{d_1-4}(1+10d_2^2+5d_2^4)(d_1>4)$

* Intraday
    - Basic Idea: $RV^m_{t+1} = \sum_1^mR_{t+j/m}^2 \neq (ln(S_{t+1}) - ln(S_t))^2$, $ln(RV^m_{t+1})~N(\mu_{RV},\sigma^2_{RV})$, and $\frac{R_{t+1}}{\sqrt{RV^m_{t+1}}}~N(0,1)$
    - obsevations: 1.$RV^m$ is a better estimator, 2. large + autocorr for many lags(persisitant), 3. log-normal 4. return over RV is i.i.d standard normal
    - HAR and ARMA are two ways to model RV. R can be added to explanatory side of Regression model to capture leverage effect.
    - Realized GARCH is also a good way to model RV
    - All RV estimator vs Sparse RV estimator: latter try to avoid bid-ask volatility by relaxing the grid intensity. For more liquid asset, the intensity would be higher(Look for the smallest s that the avg RV doesn't change too much)
    - Average RV estimator issue: need to scale up the Sparse estimators that have less nodes(might linearly).
    - 24H issue: 1. $RV^{24H}_{t+1} = (\frac{\sum_1^TR_t^2}{\sum_1^TRV_t^{Open}})RV^{Open}_{t+1}$, 2.$RV_{t+1}^24H = ln(\frac{S_{t+1}^{Open}}{S_t^{Close}})^2 + RV_{t+1}^{Open}$

* DCC
    - DCC Steps: 1. Estimate Garch or RiskMetric for all assets 2. Standardize return 3. write down a model of $q_{ij}$ 4. calculate $\rho_{ij,t+1} = \frac{q_{ij,t+1}}{\sqrt{q_{ii,t+1}q_{jj,t+1}}}$ 
    - DCC with RiskMetrics: $\textbf{Q}_{t+1} = (1-\lambda)(\textbf{z}_t\textbf{z}_t^T) + \lambda \textbf{Q}_t$, with $\textbf{Q}_1$ being long term mean
    - DCC with Garch: $\textbf{Q}_{t+1} = \mathbb{E}[\textbf{z}_t\textbf{z}_t^T](1-\alpha-\beta) + \alpha(\textbf{z}_t\textbf{z}_t^T) + \beta \textbf{Q}_t$, where $\bar{\rho}_{i,j} = \frac{\sum_1^Tz_{i,t}z_{j, t}}{T}$ and with $\textbf{Q}_1$ being long term mean
    - Bivariate MLE function: $f(z_{1,t},z_{2,t})=\frac{1}{2\pi\sqrt{1-\rho_{12,t}^2}}e^{-\frac{z_{1,t}^2-2\rho_{12,t}z_{1,t}z_{2,t}+z_{2,t}^2}{2(1-\rho_{12,t}^2)}}$
    - Multi-Dimension MLE log-likelihood: $lnL_c = -\frac{1}{2}\sum_t(ln|\Upsilon_t|+\textbf{z}^T_t\Upsilon_t^{-1}\textbf{z}_t)$, where $\Sigma=\textbf{D}\Upsilon\textbf{D}$ is the correlation Matrix, Quasi-MLE log-likelihood(add up all bivariate log-likelihood): $lnL_c = -\frac{1}{2}\sum_{t=1}^T\sum_{i=1}^n\sum_{j>i}(lnL)$
    - Can Make DCC(Garch) assymetric by adding a term $\gamma(\eta_t\eta_t^T) - \mathbb{E}[\eta_t\eta_t^T]$
    
* Term Strucuture of Risk
    - Term Structure means longer horizon, e.g. $K\sigma^2$ for K days
    - RiskMetric approach: $\sigma^2_{t+1:t+K} \equiv \mathbb{E}_t[\sum_1^KR^2_{t+k}] = \sum_1^K \mathbb{E}_t[\sigma^2_{t+k}]=K\sigma^2_{t+1}$
    - Garch approach: $\sigma^2_{t+1:t+K} = K\sigma^2 + \sum_1^K(\alpha+\beta)^{k-1}(\sigma^2_{t+1}-\sigma^2) \neq K\sigma^2_{t+1}$
    - MC & Garch approach: 0. Get a Garch Model, 1. Generate N $z_{i,t+1}$, 2. Calculate $\check{R}_{t+1}$ and $\check{\sigma}^2_{t+1}$, 3. Repeat 1 and 2 until time t+K, 4.$\check{R}_{i,t+1:t+K} = \sum_1^K\check{R}_{i,t+k}$ and calculate VaR or ES
    - Filtered Historical Simulation: 0. Get a Garch Model 1. Generate N $z_{i, t+1}$ by bootstrap technique 2. Calculate $\check{R}_{t+1}$ and $\check{\sigma}^2_{t+1}$, 3. Repeat 1 and 2 until time t+K, 4.$\check{R}_{i,t+1:t+K} = \sum_1^K\check{R}_{i,t+k}$ and calculate VaR or ES
    - MultiVariate Setting: $\textbf{r}_{t+1} = \textbf{D}_{t+1}\textbf{z}_{t+1}$, where D is the diag matrix of volatility and $\textbf{z}_{t+1} = \textbf{A} \textbf{z}^{i.i.d}_{t+1}, \textbf{A}\textbf{A}^T = \Upsilon_{t+1}$
    - FHS and MC are substitute ways to generate shocks, with FHS has no assumption on the conditional distribution.

* Principal Components Analysis
    - Say if $\textbf{x}$ is a column vector of all risk factors, it must can be written as $\textbf{x} = \textbf{A}\varepsilon$, where $\varepsilon$ is uncorrelated factor contribute to risks, often assumed to normal.
    - $\textbf{A}$ can be further written as $\textbf{A} = \textbf{V}diag(\sqrt{\lambda})$, where the first part is an unit-orthognoal matrix (eigenvectors) and second part is a diagnoal matrix with square root of eigenvalues
    - Then $\textbf{x} = \textbf{V}diag(\sqrt{\lambda})\varepsilon = \textbf{V}\textbf{p}$, $p = \textbf{V}^{-1}\textbf{x} = \textbf{V}^T\textbf{x}$, order p by $\lambda$ from largest to smallest become prin. comp.
    - Solve $\textbf{V}, \lambda$ by: $(\Sigma - \lambda_iI) = \textbf{v}_i=0$ and $det(\Sigma - \lambda_iI)=0$
    - $\lambda_i$ is the variance contribution by the ith component.

* Credit Risk
    - Expected loss rate$=\mathbb{P}(default)(1-R(ate of recover))\approx$ credit spread (Market-implied or Risk Neutral)
    - Short-Term vs Long-Term view of credit risk: 1.Short = no real distinction between credit risk and market risk. cons are cannot disentangle probability and recover rate and requirement that bonds are liquid (not hold to maturity). 2. Long = focusing default and recover rate (or loss given default on the other hand), good for loans that are illiquid and will jump to default.
    - Methods to calculate default prob: 1. Statistical-based(rating) 2. Model-based(Merton-KMV) 3. Implied from CDS spreads
    - Methods to model default dependency: 1. Gaussian Copula 2. structural model(Merton-KMV) 3. Reduced-form intensity-based
    - Facts about rating: 1. >BBB- (Baa3) = Investment Grade 2. Company rating = senior unsercured debt rating 3. cumulative default rate $(1 - d_{T, rating}) = \mathbb{P}(survive\; T\; years) = (1-d_{1, rating})^5 = e^{-\lambda T}$ 4. Markov Chain approach can be used to calculate default probability  5. Issue: a. internal data b. non-US borrower c. different source d. use direct multi-year vs calculate multi-year e. business cycle 6. portfolio rating will resemble the worst rating in portfolio 7. Monthly transition Matrix is annual matrix raise to 1/12 power 
    - Gaussian Copula combined with implied default risk from CDS swap is the most commonly used approaches
    - Gaussian Copula: 1.Simulate default time $\tau$ with $\mathbb{P}(\tau \leq t) = 1-e^{-\lambda t}$ or $\tau = -ln(1-u)/\lambda$ 2.Then, $p_i = \mathbb{P}(\tau \leq t) 3.Default happen when $Z_i \leq N^{-1}(p_i) 4.Simulate $Z_i$ as $Z_i = \rho^{1/2}m + (1-\rho)^{1/2}\varepsilon_i$ with $\rho$ is the copula correlation, m is common risk factor and $\varepsilon_i$ is idiosyncratic factor for asset i(both can be N(0,1)) 5. 
    - Sklar: existence of copula function G that $F(\textbf{z}) = G(\textbf{F(z)})$
    - Gaussian copula: $G(u_1,u_2;\rho)=\Phi_\rho(\Phi^{-1}(F_1(z_1)),\Phi^{-1}(F_2(z_2)))=\Phi_\rho(z_1,z_2)(Only for standar normal marginals)$
    - Think about recovery:1. Recovery based on post-default trading prices 2.Ultimate recovery
    - Implied copula correlation: 1. Get default correlation using 2 binary for A default and B default $\rho_{Default} = \frac{\mathbb{P}(A\land B)-\mathbb{P}(A)\mathbb{P}(B)}{\sqrt{\mathbb{P}(A)(1-\mathbb{P}(A))}\sqrt{\mathbb{P}(B)(1-\mathbb{P}(B))}}$ 2.$\mathbb{P}(A\land B) = \frac{X(X-1)}{Y(Y-1)}$ with X is the number of default and Y is the number available to default.
    - Parameter Calibration: can use default probabilities, but std dev are more commonly used.
    - Merton-KMV Facts: 1. Debt = writing put on asset value(K=FV), Equity = buying call on asset value(K=FV) 2. $E_0 = V_0N(d_1)-e^{-rT}FVN(d_2)$, So Market value of debt is V - E; default probability is 1-N(d_2); credit spreads solves MV = e^{-(r+s)T}FV 3. T as weighted average of duration; $V_0$ as sum of all Market value of equity and debt and $\sigma_V$ is the asset log return standard deviation or Solve BS and $\sigma_E E_0 = N(d_1)\sigma_V V_0$ for $V_0$ and $\sigma_V$, with $\sigma_E = \frac{\partial E_0 V_0}{\partial V_0 E_0}(elasticity) \sigma_V$
    - Merton-KMV true default prob: Instead of changing r to $\mu$ in d_2, calculate the distance to default in standard deviation $M = \frac{(V_0 - e^{-rT}FV)}{V_0 \sigma_V}$, where $e^{-rT}FV$ is sum of all short-term and half of long-term debt. Also, instead of using elasticity to calculate asset volatility directlty, they use elasticity and return of equity to find return of asset, then calculate volatility from return(equity volatility inrease as approach default). 
    - Merton-KMV default dependency: 1. Find $V_0, Boundary, \sigma_V, \mu_V$ which is the increase of the asset value, and $\rho_ij$ of asset return. 2. Siumlate GBM, when V touches barrier it died 3. Use copula approach for Z if multiple assets.
    - Simpler DtD: assume asset value V ~ GBM<, default boundary $dD_t = \alpha D_tdt$, then DtD: $m = \frac{ln(V_t)-ln(D_t)}{\sigma}$. Then m has drift: $a = \frac{\mu-\alpha-\sigma^2/2}{\sigma}$. Then with initial distance, survival prob at u: $ \mathbb{P}(\tau > u) = H(m_0,u) = N(\frac{m_0+au}{\sqrt{u}})-e^{-2am_0}N(\frac{-m_0+au}{\sqrt{u}})$
    - Wrong Way default: $V = Disc (\mathbb{E}[(1-d)F(S)] + \mathbb{E}[dRF(S)])$, if d and S are not independent then there is wrong way default. Derivative that hedge(speculate) de(in)crease default probability.

* Risk Decomposition
    - risk contribution: $\frac{\partial \sigma (\textbf{w})}{\partial w_i}w_i = \frac{\sum_1^N w_j cov(r_i,r_j)}{\sigma (w)}w_i$
    - percentage contribution: $\frac{\partial \sigma(\textbf{w})w_i}{\partial w_i \sigma (\textbf{w})} = \frac{cov(r_i,r_{PF})}{\sigma^2(\textbf{w})} w_i = \beta_i w_i$, where $\beta$ is regression coefficient and $\sum_1^N\beta_iw_i = 1$
    - For VaR: $\frac{\partial VaR(\textbf{w})}{\partial w_i}w_i = -\mathbb{E}[r_i]w_i + p\frac{\partial \sigma(\textbf{w})}{\partial w_i}w_i$
    - use of risk contribution: change in risk = contribution x relative change in weight
    - Mean-variance and risk contribution: define $U \equiv \mathbb{E}[r_{PF}]-\lambda \sigma^2_{PF}$, then $max U = max(\sum_i^N w_i\mathbb{E}[r_i]-\lambda \sum_1^N\sum_1^N w_iw_jcov(r_i,r_j))$, with FONC: $\mathbb{E}[r_i] = 2\lambda \sum_1^Nw_jcov(r_i,r_j)$ or $w_i\mathbb{E}[r_i] = (2\lambda\sigma)\frac{\sum_1^Nw_jcov(r_i,r_j)}{\sigma}w_i = (2\lambda\sigma) \times Risk\; contribution_i$
    
* Something fun
    - optimal bin width: $b = \alpha \times 1.364min(\sigma, \frac{Q}{1.340})n^{-\frac{1}{5}}$
    - KDE: \hat{f}(x) = \frac{1}{nh}\sum_1^NK(\frac{x-x_i}{h})