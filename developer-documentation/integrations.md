# Integrations

Hashstack allows users to spend their loan on supported integrations in a variety of ways like swapping, staking and last but not the least adding liquidity. This list of integrations will only grow along with the growth of the Starknet ecosystem and the birth of new protocols.

While supporting these integrations we also monitor activity on these pools because they introduce a certain level of risk to the system. Protection of the users deposits is paramount so we have certain measures in place to be able to disable user activity on certain pools if it increases the risk taken on by the protocol and likewise only stable pools are currently whitelisted to be used as a part of risk management.



## Adding Liquidity

Of the user actions mentioned above, swapping and staking are fairly simple, but adding liquidity to an AMM pool is not that straightforward. Adding liquidity can be roughly broken down into two scenarios -

1. Loan market A is adding liquidity to pool BC: For this scenario, there is no common market between loan market A and the pool of markets B and C. Therefore, the first step is to swap A to either B or C, which is done to achieve the best result/route.

The liquidity split of B and C to the pool BC while ensuring the least/no amount of loan is left over is done through simplifying the equation -

$$getAmountOut(x) = quote(loan - x);$$

Here `get_amount_out(x)` and `quote(x)` are common view functions used in AMM’s which operate on the reserves of the pool and return the values. The simplification of the above equation is used to calculate the liquidity split for the best performance. It will resolve to a quadratic equation in x, which is then solved by calculating the determinant.
