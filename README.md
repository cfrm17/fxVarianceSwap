# FX Variance Swap Valuation



A variance swap is a forward contract on annualized variance, the square of the realized volatility.  The holder of a variance swap at expiration receives a notional amount for every point by which the realized variance has exceeded the variance delivery price. Valuation of the swap involves decomposition of the contract into two periods, one that has become historical, and the other with FX rates still unknown. 

Variance swap does not have any dependence on spot FX rate and provides pure exposure to volatility alone. Thus, delta is zero for variance swap unless there is currency risk involved where the payoff settles in underlying currency. Vega and Rho calculations are also tested.

Suppose there are n consecutive trading days, called reset dates,  . Let   be the FX rate at time   and define daily log returns on FX rates as  . At the maturity of a variance swap, the realized variance is defined as
	 		          (1)
where   is the mean,  (mean multiplier) = 0 or 1 and   = 0 or 1. The notional amount, N, is obtained from Vega amount, V, and the volatility strike, K, as follows:
 

The payoff of the variance swap at maturity T in Atlas is given by
	 		          (2)
where   is long/short indicator (1 for long and –1 for short) and   is the variance delivery price. 


Let t be the valuation date and   the settle date. If  , the FX rates at   have become historical and   is given by,
                                              (3)	
where   and the last term   is the future realized variance and it is approximated by implied volatility  , i.e.,   for the swap with the maturity T. For a forward starting swap (i.e., the reset date starts in the future,  ), forward volatility is used to calculate the future variance. In other words,
 

Direct Quote
The rates are quoted as   and Vega amount currency is either USD or EUR. 

1. Vega amount currency = USD
The expected payoff is defined as   in USD. The price of the contract in USD is obtained by discounting the expected payoff with USD.
                                             (4)
where   is the discount factor between the value date and the settle date of the swap. As shown in (4), the price does not have any dependence on spot rate. Thus, the delta is zero in this case.

2. Vega amount currency = EUR
The expected payoff at the expiry is defined as   in USD and   is the forward FX rate for the expiry date in USD/EUR. The price of the contract in USD is obtained by
                                    (5)
As shown in (5), the forward FX rate for the expiry date depends on the spot rate and, thus, we have non-zero delta for this case. It should be noted that this delta is purely related to currency risk due to payoff settling in foreign currency. 

Indirect Quote
The rates are quoted as   and Vega amount currency is either USD or CAD. 

1. Vega amount currency = USD

The price of the contract in USD is obtained by discounting the expected payoff with USD.
                                             (6)
As shown in (6), the price does not have any dependence of spot rate. Thus, the delta is zero in this case.

2. Vega amount currency = CAD
The expected payoff at the expiry is defined as   in USD and   is the forward FX rate for the expiry date in CAD/USD. The price of the contract in USD is obtained by
                                      (7)
As shown in (7), the forward FX rate for the expiry date depends on the spot rate and, thus, we have non-zero delta for this case. It should be noted that this delta is purely related to currency risk due to payoff settling in foreign currency. 


USD Delta 

1. Direct Quote (USD/EUR)
If the notional settles in EUR, then the dollar value Delta in USD is computed as
USD Delta                          	               (3)
where   is the spot exchange rate and the perturbation on the spot rate   is set to be 0.00005. This dollar value delta is used for daily hedging.

2. Indirect Quote (CAD/USD)
The perturbation of the spot rate in delta calculation is in USD/CAD:   and   where  . If the notional settles in CAD, then the USD Delta is defined by
USD Delta =                     	                             (6)

Vega 
It is the central difference in swap values with individual volatility moving up and down by  . Let   be a volatility point, then the Vega is defined by

 

Rho 
It is the central difference in swap values with individual interest rate instrument moving up and down by  . Let   be an interest rate instrument, then the Rho is defined by

 
 

 For Value is the settlement date of the rate observed on Observation Date and it satisfies the following relationship
Settle Date (For Value) = Observation Date + Lag
and the Lag = 1 business day for indirect quote and 2 business days for direct quote. For example, Atlas valuation date is observation date and Atlas spot date is the settlement date of the Atlas valuation date. In table 2, Start Date (= ) and Expiry Date (= ) are observation date, and Settle Date (= ) is settlement date. If we distinguish the settlement dates with asterisk, the discount factor is written more specifically as:
 
where   is the valuation date for the analyses in this report and  . Implied volatility and other calculations are done based on observation dates. 

Reference:

https://finpricing.com/curveVolList.html

