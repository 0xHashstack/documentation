# Debt management

Each borrow contract maintains the tokens associated with its lending activity. Borrow contracts have special rights to interact with supply contracts to borrow assets to issue loans, liquidate collateral to close loan. The borrow contract is liable to return the funds to respective supply vault along with interest on loan closure and free up any remaining collateral.

To explain the details, assume two rTokens - 1) rETH 2) rUSDC. and a borrow token dUSDC.

Assume users wants to borrow 300 USDC using 1 ETH as collateral (1 ETH = 100 USDC).



1. On Borrow: dUSDC contract will request 300 USDC from rUSDC contract. rUSDC contract shall use its supply reserves to full-fill the requests. rUSDC uses `lent_assets` variable to track the borrowing it has done. dUSDC shall also call the rETH contract requesting it to lock users 1rETH as collateral.



2.  **On Repay:** This has 2 cases:



    a) Loan has sufficient funds to close the loan without liquidating any collateral. dUSDC contract shall repay the loan including interest owned by the user to the protocol (fees) and rUSDC contract. Any remaining loan funds are sent back to the user. And finally, dUSDC will call rETH contract requesting it to unlock the users 1rETH.



    b) Current loan amount is insufficient to close the loan by itself. This could be because of the extra interest accrued on the loan and any losses made be user when spending the loan. Hashstack provides two options to deal with this:

    * Repay deficit amount: Allow user to pay the deficit amount. If the total debt during repayment is 310 USDC, and protocol only has 300 USDC of the loan, user can send the remaining 10 USDC to avoid collateral liquidation. In this case, entire collateral is unlocked
    * Self liquidate: User can use this option to request the protocol to use their collateral to close the loan. In this protocol will roughly sell 0.1 ETH worth of user’s rTokens (for 10 USDC, assuming no price change) and close the loan. Finally, it will unlock the remaining 0.9 ETH worth rETH of the user.



3. **On Spend:** Assume the user decides to spend the loan on an AMM to buy ETH. This results in shorting USDC and longing ETH. With about 230 USDC in current loan amount, user will receive roughly 2.3 ETH.

<pre class="language-rust"><code class="lang-rust"><strong>actual_debt: 300 USDC + interest
</strong>current_loan_amount: 2.3 ETH
current_collteral: 1 ETH
</code></pre>

We call these as spent assets and these assets remain with the respective dToken contracts based on the loans they handle.
