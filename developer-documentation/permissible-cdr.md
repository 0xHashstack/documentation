# Permissible CDR

The following documentation outlines a code implementation for a function that calculates the creditworthiness and loan-to-value (LTV) ratio of a borrower based on several input parameters. The code also includes a function to calculate the overall market risk based on three input parameters.

The code implementation consists of two functions: **`calculate_creditworthiness()`** and **`calculate_market_risk()`**. The **`calculate_creditworthiness()`** function assesses the borrower's creditworthiness by considering the user's repayment history, collateral to debt correlation, and the overall market risk. The function returns both the creditworthiness score and the LTV ratio. The **`calculate_market_risk()`** function estimates the general market risk based on the effective asset flow rate, volatility, and price variation, and returns the assessed risk.

The documentation provides additional information about the input parameters used in both functions and their relationship to market risk.



### **Parameters:**

1. **`collateral_debt_correlation`**: This parameter represents the correlation between the value of the collateral and the borrower's debt. In other words, it assesses the likelihood that the value of the collateral will decrease below the borrower's debt level. The lower the correlation, the riskier the loan.
2. **`effective_asset_flow_rate`**: This parameter represents the effective flow rate of assets, which is the rate at which assets can be converted to cash in the market. It evaluates the liquidity of assets and their ability to be sold quickly at a reasonable price. A low effective asset flow rate indicates a riskier market, which is represented as a boolean as of this version.
3. **`volatility`**: This parameter represents the degree of variation of an asset's price over time. It measures the risk of the asset's price fluctuating in the market. Higher volatility indicates a riskier market.
4. **`price_variation`**: This parameter represents an asset's price variation in a given time period. It measures the magnitude of the change in the asset's price. A higher price variation indicates a riskier market.
5. **`wallet_history`**: This parameter represents the user's repayment history. It tracks the status of the borrower's previous loans, indicating their consistency in repaying loans. A good repayment history indicates a lower credit risk for the borrower.

All of these parameters, except for **`wallet_history`**, are market-associated and evaluate the market risk at the time of loan request. Understanding the relationships between these parameters and market risk is critical to assessing the borrower's creditworthiness.

```jsx
def calculate_creditworthiness(collateral_debt_correlation, effective_asset_flow_rate, volatility, price_variation):
    //Step 1: User repayment history
    wallet_history = "A track of loan's status as in success or failed loans" 
    //Consistency of the user's loan repayment justifies the trust in lending the funds
	    // A score from this can be taken with a discounting factor to older status. (Rn + delta*Rn-1 + delta^2*Rn-2 +...)
    // Step 2: Calculate credit risk
    credit_score= score*[collateral_debt_correlation + calculate_market_risk(effective_asset_flow_rate, volatility, price_variation)]/2
    
    // Step 3: Calculate loan-to-value (LTV) ratio
    ltv_ratio = 3 * credit_score
    
    // Step 4: Return creditworthiness score and LTV ratio
    return credit_score, ltv_ratio

def calculate_market_risk(effective_asset_flow_rate, volatility, price_variation):
    // Calculate overall market risk using a weighted average of effective asset flow rate, volatility, and price variation
    weights = [0.4, 0.3, 0.3] // Adjust weights as desired
    market_risk = np.average([effective_asset_flow_rate, volatility, price_variation], weights=weights)
    
    return market_risk
```
