# FAQs on borrow

Q. **What tokens can I borrow?**

You can borrow wBTC/wETH/USDC/USDT/DAI in Hashstack's primary markets, if enough reserves are available.



Q. **Can I withdraw from the borrowed amount?**

Yes, you can withdraw up to 70% of your collateral amount deducted from the borrowed amount. For instance, if you borrow $1000 of ETH by depositing $334 USDT, you can withdraw up to 70% of $334 (i.e., $234) into your wallet. And so, you are left with $766 ($1000 - $234) as in-platform trading capital. Note: you can only partially withdraw once for every borrowed process.



Q. **How will I know that my borrow is nearing liquidation?**

Hashstack will send you an in-app notification when your collateral value drops below a certain threshold. You can add more collateral to your borrowed assets and prevent it from entering the distressed category.



**Q. Why am I not able to borrow more than 300 USDT?**

The version of mainnet is deployed on Cairo 0.10 and is heavily restrictive in its capabilities so as to avoid congesting the Starknet network, or pass-on adverse liquidity risks onto you.

Here are the supply and borrow limitations:

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>



**Q. Why is there a 3 day timelock on withdrawing collateral in the 1 month MCP option when borrowing?**

The withdrawal time-lock is triggered when you place a withdrawal request. The withdrawal time lock provides Open a buffer time to free any deployed liquidity and meet the withdrawal requests.

Note: Incase you choose the “none” option as MCP, you will immediately receive your collateral back once the borrowed amount is repaid.
