## Forward

* Long forward A = Long Spot A + Long A Bond + Short B Bond = Short forward B 

* e.g. Buy forward USD(w/JPY) = Buy Spot USD(w/JPY) + Buy US Bond(Lend out) + Sell JP Bond(Borrow From)
  
* $F_{t,T}(B \; per \; A) = S_t(B \; per \; A) * \frac{Yield_B}{Yield_A}$
  
* lower bound when cost exist = replicating short = sell at forward bid
  
* upper bound when cost exist = replicating long = buy at forward ask
  
* For Asset pay discrete yield(e.g. dividends) D: $F_{t,T} = [S_t - \sum_i PV(D_i)]e^{r(T-t)}$
  
## Future

* Cash Settlement future/ non-deliverable forwards/ non-physical underlyings

* f = F when: (1) carry cost random **and** (2) carry cost highly correlated with underlying. $ F > f\; iff\; \rho(S_t, (r_t-d_t)) <0$

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
