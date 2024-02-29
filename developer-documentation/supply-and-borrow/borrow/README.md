# Borrow

Borrow contracts follows ERC20 standard while using some mathematics of EIP 4626 to maintain the relationship between total debt and dTokens issued. dTokens are debt tokens that are issues when a user takes a loan and burnt on repayment/liquidation of loan. dTokens represent the share of total debt issued by the contract. They help determine the amount to be paid by user during repayment.



