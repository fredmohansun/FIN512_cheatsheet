## Forward

* Long forward A = Long Spot A + Long A Bond + Short B Bond = Short forward B 

* e.g. Buy forward USD(w/JPY) = Buy Spot USD(w/JPY) + Buy US Bond(Lend out) + Sell JP Bond(Borrow From)
  
* $F_{t,T}(B \; per \; A) = S_t(B \; per \; A) * \frac{Yield_B}{Yield_A}$
  
* lower bound when cost exist = replicating short = sell at forward bid
  
* upper bound when cost exist = replicating long = buy at forward ask
  
* For Asset pay discrete yield(e.g. dividends) D: $F_{t,T} = [S_t - \sum_i PV(D_i)]e^{r(T-t)}$
  
## Future

* Cash Settlement future/ non-deliverable forwards/ non-physical underlyings

* f = F when: (1) carry cost random **and** (2) carry cost highly correlated with underlying. $F > f\; iff\; \rho(S_t, (r_t-d_t)) <0$

* extra case: spot increase then r decrease: reinvestment of future cashflow is hurted

* Hedge future and Forwards given carry cost: Suppose f(T-1)>F(T-1) or Suppose f(T-1)<F(T-1) with one day until T. That’s obviously an arbitrage opportunity. So f(T-1)=F(T-1). Then suppose  f(T-2)>F(T-2).  Use So f(T-1)=F(T-1) to show that too lets you construct an arbitrage. Then so on T-3, T-4...

* $\Delta_F = 1$, $\Delta_f > 1$(Long)

## Swap

* deliver A and receiving B cannot be different than long a series of forward B (Quoted in A) and financed with lending

* $\sum_1^T F^{(dollar\; per\; B)}_{0,t} B_{0,t} =s(A \; per\; B) \sum_1^T F^{(dollar \; per\; A)}_{0,t} B_{0,t} => s(A\; per\; B) = \frac{\sum_1^T F^{(dollar \; per\; B)}_{0,t} B_{0,t}}{\sum_1^T F^{(dollar\; per\; A)}_{0,t} B_{0,t}}$ 

    - e.g. deliver gold and receiving cash: $s(gold\; per\; dollar) = \frac{\sum_1^T F^{(dollar \; per\; dollar)}_{0,t} B_{0,t}}{\sum_1^T F^{(dollar \; per\; gold)}_{0,t} B_{0,t}} => s(dollar\; per\; gold) = \frac{\sum_1^T F^{(dollar \; per\; gold)}_{0,t} B_{0,t}}{\sum_1^T F^{(dollar \; per\; dollar)}_{0,t} B_{0,t}}$

    - e.g. deliver JPY and receiving USD (Change of home country): $s(JPY\; per\; dollar) = \frac{\sum_1^T F^{(JPY\; per\; dollar)}B_{0,t}}{\sum_1^T B_{0,t}} = S_0(JPY\; per\; dollar) \frac{\sum_1^T e^{-r^{USD}t}}{\sum_1^T e^{-r^{JPY}t}}$

* When Losing, "hedged" swap position have no change in expiring payoff during counter party default/ bankruptcy

* Transaction cost: $s^{ask}(dollar\; per\; sth) = \frac{\sum_1^T B_{0,t}^{ask/lend}F^{ask}_{0,t}}{\sum_1^T B_{0,t}^{bid/borrow}}$, change side and reverse get bid

* Value of old swap in new price: $V(X, X^*) = (X^* - X)\sum_1^T B_{0,t}$ (floating receiver for a IRS)

* Rate Market:

    - Gov Debt, T-Bill/T-note(10yr-,0-coupon); T-Bond(10yr+, w/ coupon) and it's STRIP
    
    - Repo: Lend you money, taking bonds as collateral, you pay rate (typically 3m TB)
    
    - EuroDollar/ LIBOR
    
* IRS: Fixed side value $=sN\sum_1^TB_{0,t}$, Floating side value $=N(1-B_{0,T})$, $s = \frac{1-B_{0,T}}{\sum_1^TB_{0,t}}=\frac{\sum_1^TB_{0,t}R_{0,t-1,t}^f}{\sum_1^TB_{0,t}}$

* IRS from total bond review: Value of IRS must be the difference between two assets

* forward rate $R^f_{0,t_1,t_2} = \frac{B_{0,t_1}}{B_{0,t_2}}-1 => e^{-r_{0,t_2}t_2}(1+R^f_{0,t_1,t_2}) = e^{-r_{0,t_1}t_1}$

* OIS: fixed receiver pay compound all O/N interest rate, fixed receivor gets $s - [\prod_0^{T-1}(1+r^{Fed\;Fund}_{t,t+1})-1]$

* Swap Spread = swap - rf ytm, e.g. $s^{ED} - y_T^{TB} = \frac{\sum_1^T[R_{0,t-1,t}^{f,ED}-R_{0,t-1,t}^{f,TB}]B_{0,t}^{TB}}{\sum_1^TB_{0,t}^{TB}}$

* Asset Swap: swap payout and pricipal difference at expiring

* Total-return Swap(TRS): periodically exchange realized return, then rebalancing to unit value

* Credit Default Swap(CDS):

    - you pay me cf from long X coupon bond at T; I pay you cf from long rf bond at T; both at par; exchange difference at maturity; if defaults, terminal payoff is: face value of riskless bond - recovery value of defaulted bond
    
    - fee should be the same as credit spread.

## Options

* Basic Arbitrage: (1) option value > 0 (2)$C^A > C^E, P^A > P^E$ (3) $C \leq S_t, P \leq K$ (4) $P^E \leq K B_{t,T}$ (5) $A \geq max$ (6) $A_{T_2} \geq A_{T_1}\; if\; T_2 > T_1$ (7) $div = 0, C \geq max[S - KB_{t,T},0], C^E_{T_2} \geq C^E_{T_1}\; if\; T_2 > T_1$ (8) $P^E \geq max[KB_{t,T}-S,0]$ (9) $div = 0, C^E = C^A$ (10) $C^A$ optimal exercising: right before ex-date (11) $P^A$ not optimal exercising before ex-date

* Put-Call Parity: 

    - $S_t = C^E - P^E + KB_{t,T}$ or $C^E - P^E = S_t - PV(D) - KB_{t,T}$
    
    - $S - K \leq C^A - P^A \leq S - B_{t,T}K$ or $S - PV(D) - K \leq C^A - P^A \leq S - B_{t,T}K$
    
* Butterfly and Risk Neutral: $\frac{1}{\delta K}$ share of butterfly price $b_k$, is the risk-neutral prob q times $B_{t,T}$

* Breeden and Litzenberger Theorem: one can identifying RN prob by watching curvature.

* Binomial when we have div or foreign: $q \equiv \frac{\frac{\bar{r_d}}{\bar{r_f}}-d}{u-d} \approx \frac{e^{(r_d-r_f)\Delta t}-d}{u-d} = \frac{e^{(r-div)\Delta t}-d}{u-d}$ conventional $u = e^{\sigma \sqrt{\Delta t}}$

* Black PDE General setting:

    - Geometric Brownian: $\frac{dS}{S} = \mu dt + \sigma dW$ or in general $dS = a(S,t)dt + b(S,t)dW$ a: drift, b: diffusion, a/S: expected, b/S volatility(std dev)
    
    - Ito and Delta hedge: $$
            \begin{array}{ll}
                dC = C_SdS + C_t dt + \frac{b^2}{2}C_{SS}dt\\
                d\Pi = dC - C_S dS + rIdt = C_t dt + \frac{b^2}{2}C_{SS}dt + rIdt = r\Pi dt \\
                r(C - C_S S + I)dt = C_t dt + \frac{b^2}{2}C_{SS}dt + rIdt\\
                C_t + rS C_S + \frac{b^2}{2}C_{SS} -rC = 0\\
                C_t + rS C_S + \frac{1}{2}\sigma^2S^2C_{SS} -rC = 0
            \end{array}
           $$
    - Based on Black Schole formula: $I = Ke^{-r(T-t)N(d_2)}$ => $N(d_2)$ is the precentage of PV of K we need to borrow to replicate portfolio $\Pi$
           
* Black Schole's "additional" assumption: (1) continue transaction is possible (2) no price jump (3) r $\sigma$ constant (4) d = 0

* Black Schole Greek

Greeks | Call | Put| Call Sign| Put Sign
----- | ----- | ----- | ----- | -----
$\Delta$ | $N(d_1)$ | $-N(-d_1)$ | l+ s- | l- s+
$\Gamma$ | $\frac{1}{S\sigma \sqrt{T-t}}\phi(d_1)$ | Same | l+ s- | l+ s-
$v$ | $S\sqrt{T-t}\phi(d_1)$ | Same | l+ s- | l+ s-
$\Theta$ | $\frac{S\sigma}{2\sqrt{T-t}}\phi(d_1)-rKe^{-r(T-t)N(d_2)}$ | $\frac{S\sigma}{2\sqrt{T-t}}\phi(d_1)+rKe^{-r(T-t)N(-d_2)}$ | l- s+ | l- s+
$\rho$ | $K(T-t)e^{-r(T-t)}N(D_2)$ | $-K(T-t)e^{-r(T-t)}N(-D_2)$ | l+ s- | l- s+

* Lira-Peso Case Margarbe's Formula: $option = S^{Lira}_t e^{-r^{Lira}(T-t)}N(d_1) - S^{Peso}_t e^{-r^{Peso}(T-t)}N(d_2)$, where $d_1 = \frac{ln(\frac{S^{Lira}_t}{S^{Peso}_t})+(r^{Peso} - r^{Lira})(T-t) + \frac{1}{2}\sigma^2(T-t)}{\sigma \sqrt{T-t}}$, and $\sigma = \sqrt{\sigma^2_X+\sigma^2_Y-2\rho\sigma_X\sigma_Y}$ is the volatility of the ratio 

* Lira-Peso Case II Future Option: $C = S_t B_{t,T^{Lira}}N(d_1) - K B_{t,T}^{Peso} N(d_2) = e^{r(T-t)}[FN(d_1)-KN(d_2)]$, where $d_1 = \frac{ln(\frac{F}{K})+\frac{1}{2}\sigma^2(T-t)}{\sigma\sqrt{T-t}}$, $e^{r(T-t)}$ for future, $e^{r(T'-t)}$ for Forward.

* Merton's Forward volatility: $\bar{\sigma_{12}} = \sqrt{\frac{(T_2-t)\bar{\sigma_2}^2-(T_1-t)\bar{\sigma_1}^2}{T_2-T_1}}$

## From Midterm

* 2017Q3 OIS: $V(s) = B_{0,T}(1+s)-1$ => $s=R_{0,T}$, one year simple rate(EAR).

* 2017Q4 Bound: find best and worst scenario

* 2016Q2 $max[Se^{-r_f(T-t)}-Ke^{-r_d(T-t)},0]$ and $max[S-K,0]$. Treat as a func of S, find $K^*$ 

* 2016Q4 Through Black Schole PDE back into ito's result

## Volatility

* short-dated options Deeo OTM, not sensitive to volatility

* Heston Model: $d\sigma_t = \kappa(\sigma_0-\sigma_t)+s\sigma_tdW_t^{\sigma}$

* When $\kappa$ is high and s is low, mean reverting faster and behave like constant vol.

* VS GARCH: GARCH is 1. discrete in time, 2. when take time to limit become non-stochastic

* Multi dimensional Ito: add $\frac{1}{2}b_Y^2\frac{\partial^2 C}{\partial Y^2}d<Y>_t$, $\frac{\partial C}{\partial Y}dY$, and a $b_Yb_{\theta}\frac{\partial C}{\partial Y \partial \theta} d<Y, \theta>_t$ to all other risk factors.

* Idea of hedging non-tradable risk factor(e.g. Heston): Creating a all-else neutral (e.g. BS delta-neutral) portfolio $\Pi_C$ and, create another such portfolio $\Pi_P$, long 1 $\Pi_C$ and short ratio $=\frac{Vol_C[Payoff]}{Vol_P[Payoff]}$ (e.g. $\frac{b_C\Pi_C}{b_P Pi_P}$)

* Doing hedge above, get (not RN) market price of risk factor $\lambda = \frac{a - r}{b}$, a kind of sharpe ratio (use sharpe ratio approach to estimate from hist data).

* Feymann-Kac: 1. risk-neutralize (traded asset drift to $r_f S$, non-traded asset drift to $a-\lambda b$) in PDE 2. calculate value w.r.t that drift 3. disc at $r_f$  4. take $E^*[DF_{t,T} C(X_T)]$

* Observation from Heston Model: 1. fatter tail of return dist 2. leptokurtic 3. Deep OTM option more valuable, Near-the-money option less valuable 

* $\rho$ positive: 1.less likely to go down after go down, higher likely to go up after go up 2.left low right high 3. OTM call more/ put less likely to payoff ITM 4. Smile skewed ll to ur 5. vice versa for $\rho$ negative

* Problem with Multi-dimension: (Econometrics)1. stochastic model of each 2. parameters (Market Completeness)3. two securities you can use to hedge (risk X only, long and short) 4. Jumps negligible (Risk preference)5. $\lambda$

* Given GBM and using Feymann-Kac: $E[S_T] = S_0 e^{a^{S,RN} T}$

* Vasicek: $dr = \kappa(r^* - r)dt + bdW$ (RN, change to $\bar{r}$ if physical), $r_T~N$, CIR: change b to $s\sqrt{r}$

* Vasicek way to calculate Term Strucuture: $B_{t,T}(r_T) = e^{G_0(t,T)-r_tG_1(t,T)}, G_1 = \frac{(1-e^{-\kappa(T-t)})}{\kappa}, G_0 = \frac{(G_1-(T-t))(r^*\kappa^2 - b^2/2)}{\kappa^2} - \frac{(bG_1)^2}{4\kappa}$ 

* Error of MC: 1. Discretization ($\epsilon ~ \mathcal{O}(N^-1)$) 2. Not enough paths ($\epsilon ~ \mathcal{O}(M^{-\frac{1}{2}})$)

* Short Log forward get $L_0 = B_{0,T} -\frac{1}{2}\int_0^{T}\sigma_t^2dt$, where $MFIV^2 = \frac{1}{T}E_0^Q[\int_0^T\sigma_t^2dt]$

* Butterfly approach toward VIX: $L_0 = \sum_k log(\frac{k}{F})b(k)$ => $MFIV^2 = \frac{2}{T}B^{-1}_{0,T}(\int_0^{F_{0,T}}\frac{p(k)}{k^2}dk + \int_{F_{0,T}}^{\infty}\frac{c(k)}{k^2}dk)$

## Credit

* Merton's Model: Equity is a long european Call with K = Debt FV => CFO increase volatility of stock to max shareholders benefit (hurting Bond holders), assuming 1.$dV = (\mu -\Pi)Vdt + \sigma_VVdW$ 2. no taxes and reorganization cost 3. won't do unanticipated financing 4. enforcable 

* Modigliani-Miller Theorem: market value of firm is independent of its capital structure and only cash flows instaed.

* assuming earning ~ GBM, constant rate, and perpetual, $V(E) = \frac{E_t}{r-(\mu_E-\lambda_E\sigma_E)}$ => $\Pi = \frac{E}{V} = r-(\mu_E - \lambda_E\sigma_E)$. Then F, a claim on V, follow BS PDE with $r = r-\Pi$ and add a coupon rate $\Gamma$ and has soluntion $F = FVe^{-r(T-t)}N(d_2) + VN(-d_1)$, yield spread = $y_t - r = -\frac{1}{t} log(N(d_2)+\frac{1}{d}N(-d_1))$

* Equity Model: assume S ~ CEV $dS = \mu S dt + \omega \sqrt{S}dW$ then F follow BS PDE with $S^2$ => S in second derivative term, add a coupon rate $\Gamma$ and change r to (r-div)

* Convertible Bond: Change BC on Stock to $F(S_t,t) \geq NS_t$ where $N=\frac{FV}{S_C}$, Manager convert whenever Bond Value is greater than that. 

* Better model = 1. Jump 2. Future Financing 3. Restructring 4. Constraint

* CDS: long credit spread = protection buyer = pay fee to protection seller = short credit spread = pay (1-R) to buyer when credit events happen.

* CLN: Z =pricinpal=> Y, won't payback pricipal if X default still need to pay high coupon rate.

* Assuming no recovery, risky Bond $\hat{B_{t,T}}(V_T) = B_{t,T} (1 - H(T;t))$, $H(T;t) = 1-e^{\lambda^X(T-t)}$ => cdf of dying before T, h => pdf, f = $\lambda$ => conditional probability (if constant = $\phi$, or credit spread)

* CDS $\phi = \frac{\int_t^T\hat{B_{t,s}}f(s;t)ds}{\int_t^T\hat{B_{t,s}}ds}$, MtM value $V = (\phi_{new,s} - \phi)\int_s^T\hat{B_{s,u}}du$

* fetching RN probablity of default: $\phi_{t,t+1} = \frac{(1-R)B_{t,t+1}h(t+1;t)}{B_{t,t+1}(1-h(t+1;t)}$, then recursively solve all others.

* Credit Value Adjustment = Expected Discounted Unrecoverable Mark-to-Market Profit = $E^*[\int_t^T DF_{t,s}h(s;t)(R^Y-1)max[V(Y),0]ds]$

* If CVA is a loss on one leg, then Debit Value Adjustment is the same idae on the other leg. Generally: adj. value to protection leg = protection Leg value - fee leg value - CVA + DVA

* ABS, CDO and unhedgeable Repayment Risk(Timing risk): transfer! long tranch in CDO = long rf + short CDS on those tranch(or short CDX NA IG)
