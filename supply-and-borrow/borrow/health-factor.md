# Health factor

We compare the total current debt of the token with underlying loans current value and collateral(s) to determine the health.

$$
Hf = \frac{C_{cv} + LA_{cv}}{L_{net}}
$$



where,

$$Hf =$$ Health factor

$$C_{cv} =$$ Collateral current value in USD

$$LA_{cv} =$$ Loan account current value in USD

$$L_{net} =$$ Net liabilities (Original loan + interest) in USD

Note: For on-chain computations, we use USDT as base value to compute values.



Health is monitored at two levels:

1. dToken level: Determines the total health of the protocol for this asset
2. user loan level: Determines health of a user’s individual loan



### **dToken health:**

$$L_{net} =$$ total value of the debt issued by the contract across the protocol

&#x20;$$C_{cv} = \Sigma_{1}^{n} C_{icv},$$ n is the total number of supported collaterals, $$C_{icv}$$ is the net value of the ith collateral locked.

$$LA_{cv}$$ unspent loan amounts + Sum (spent loan amounts)



### **User loan health:**

For the above loan discussed, the health factor can be computed as below:

1.  **Before partial withdrawl**

    * $$C_{cv} =$$ 1 ETH \* 100 = 100
    * $$LA_{cv} =$$ 300 USDC = 300
    *   Assuming an interest of 2 USDC accrued,

        $$ $L_{net} =$ $$ 300 + 2 USDC = 302



So, Health factor $$(Hf) =$$ (100 + 300)/302 = **1.32**

***

2. **Post spend**

$$LA_{cv}$$ = 3 ETH x $100 = $300

So, Health factor $$(Hf) =$$ (100 + 300)/302 = **1.32**



**Health factor determines if a loan can be liquidated. Read Liquidations for more info.**
