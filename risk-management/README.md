# Risk management framework

Risks associated with any decentralised financial product can be categorised into two baskets.

1. **Primary**: Risks related to the product and processes.
2. **Secondary**: Risks associated with external integrations such as Integrated dapps, oracles, bridges, and networks.

### General safeguards

* Automated all-systems check to run every 24hrs across four layers - Unit, Integration, Fuzz, and Penetration tests.&#x20;
* Secure against all known vulnerabilities listed in the Smart contract weakness classification registry and all DeFi exploits between 2020-2023.&#x20;
* In-house DevSecOps, key security management & Hardware security management practices.



## General risks & safeguards

### Loss of funds

a) Loss of funds / Debt recovery: Hashstack never cedes ownership of the loan exceeding 70% of the borrower's collateral value. It does not take up add-on capital risks. E.g., On a $300 loan acquired against $100 collateral, a maximum of $70 can be transferred into the borrower's wallet. Hashstack retains ownership of $330 ― a $30 capital cushion.&#x20;

b) A cap on permitted liquidity outflow overrides general withdrawal requests if the withdrawal amount pushes the cumulative flows above the outflow threshold. The initial point is set at 20% of total reserves. This necessary feature helps contain the scope of exploits, as well as mitigate bank-run.



### High-value bad debt

Many DeFi lenders undermine the adverse effect of a new loan - big/small on the total outstanding loans. This second-order risk reduces the protocol health when a crypto-asset's cumulative outstanding loans exceed that of the market's ability to absorb the liquidity without significant slippages. For example, Aave & MakerDao suffered a US $6M loss due to this oversight. At Hashstack, the `permissibleCDR()` compares the net effect of each new loan to that of the total outstanding debt to evaluate the scenario, if this particular asset goes to zero, will there be any adverse risks to the protocol before it can successfully market-sell the asset? If the boolean response is false, the permissibleCDR() rejects the loan request and pauses the debt market.



### Unaudited upgrades

A function, `donateToReserve()`, implemented in the Euler's upgrade contracts was the source of \~ US $200Mn exploit on 13th March 2023. While auditing every upgrade is impractical, Hashstack plans to open up a flash bug bounty for two weeks before deploying each significant upgrade. However, hotfixes could be exempted.





## Is the liquidity provider exposed to additional risks of capital loss?&#x20;

No. Hashstack achieves a higher degree of capital efficiency as compared to its competitors without adding up extra risk layers. However, higher loan-to-value is a cause for concern if the loan disbursed is in an illiquid asset and if the permitted loan withdrawal amount into the borrower's wallet exceeds that of collateral, In which case, second-order risks such as adverse risks during sell-cascades get amplified. Hashstack's careful curation and segmentation of crypto-assets into primary & secondary assets, added with the protocol-level innovations such as dynamic interest rate, the algorithm, & dual liquidation mechanism, mitigates this risk vector. In addition, permitting a maximum of 70% collateral equivalent to be transferred to the borrower's wallet ensures that the protocol retains an adequate 30% collateral in addition to the loan value in ownership.
