# 🏝️ Isolated margin

All loans issued on hashstack are isolated margin loans. User has to choose the supply market along with their quantity to be used as collateral. Protocol then verifies the rTokens quantity to assure enough supply is pledged to use as collateral. These pledged rTokens cannot be transferred till loan is closed (We call this as locking rTokens). Only borrow contracts can lock/unlock the rTokens.
