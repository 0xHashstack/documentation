# Slippage Control

Slippage is the gap between a trade's expected or requested price and the price at which the trade was executed. It usually happens in markets with high volatility or low liquidity.

**Factors to consider:**

* **Liquidity**: Pools must have enough liquidity to handle the expected trading volume. Pools with higher volume and longer/deep order books tend to have low slippage.
* **Slippage tolerance**: Users with higher tolerance can be willing to trade in pools with low liquidity, but those with low tolerance would prefer a more elevated liquidity pool.
* **Token pairs**: Tokens that are in demand tend to have higher liquidity → lower slippage
* **Price Volatility:** If the token in the pool is highly volatile then it leads to a higher chance of slippage which ends up being a poor user experience.



**Controlling Slippage Threshold:**

Under a practical slippage tolerance, the contract checks the execution price during the trade and breaks/stops the trade in cases where the execution price has deviated beyond the tolerable slippage set. →\[0.5, 3]%

Note: Due to low TVL at the initial phase higher slippage cases are bound to occur thus blocking a trade ultimately results in a dissatisfied user experience which is a trade-off to this approach. Thus, until the TVL of that asset grows to healthy liquidity, larger slippage is authorized as of this version.
