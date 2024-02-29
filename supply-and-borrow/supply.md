# Supply

When a user supplies funds to the protocol, they receive rTokens. We use the following formula (as per EIP 4626) to calculate the number of tokens minted to the user.

$$
rTokens_{new} = \frac{Asset_{new} \cdot rTokens_{total}}{Asset_{total}}
$$

The formula uses existing total rTokens supply and Total asset supply to decide the quantity of rTokens to be minted as per the user deposit.

$$
Asset_{total} = Asset.balanceOf(contract) + Assets_{lent} + Interest_{accrued}
$$



```jsx
// Definitions
Assets_lent => Assets borrowed by borrower contract to issue loans to the user
Interest_accrued => Interest recievable by suppliers since last update
```

The contract exposes the following features for user and open contracts to interact with:

1. **User:** Technically, a user can usually perform 3 main actions with supplier contract: Deposit, Withdraw & Transfer. User can further use the received rTokens as collateral to borrow or stake to earn higher yield.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Fig. 2 - Supply use-cases</p></figcaption></figure>

2. **Open:** The supply contract provides special privileges to the Open contract to allow it for some book-keeping. These options include:

* Accrue the interest
* Lock/unlock supply - to prevent the transfer of collateralised supply
* Transfer & withdraw supplied funds on the users behalf - to liquidate the loan
* Borrow and repay - to utilise funds to issue & close loans
