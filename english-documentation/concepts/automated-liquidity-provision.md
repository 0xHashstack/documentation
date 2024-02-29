# 📈 Automated Liquidity Provision

Automated Liquidity Provision emphasizes the importance of allocating the entire loan amount to a user's preferred liquidity pool and simplify record-keeping.

* Here, the protocol divides and allocates a loan amount to a user's preferred liquidity pool.
* Ideally, there should be nothing left from the loan amount because it makes record-keeping complicated.
* For example, if someone takes a $1000 loan and chooses the USDT/ ETH pool, the entire $1000 must be added as liquidity to this pool.
* With this problem statement, we concluded that the following should provide us with what we seek: `get_amount_out(x) = quote(1000 - x) [JediSwap functions]`
* Readjusting the equation to the standard form would give:

$$
(997*x) / ((reserveIn * 1000) + (997 * x)) + x = (1000-x)/reserveIn
$$

* Read [this](https://docs.hashstack.finance/developers/automated-liquidity-provision) article to understand how we came to this equation.
