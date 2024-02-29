# 💸 Liquidations

Hashstack uses a dual-liquidation methodology to ensure loans get liquidated in time, removing bad debt from the protocol. Dual-liquidation involves community-backed liquidations along with protocol-backed liquidations. When a loan becomes liquidable, we allow the community to liquidate. However, if the health factor drops further, protocol-managed liquidation bots come into action to remove loans before they create losses.&#x20;



The health factor is used to determine when a loan can be liquidated and who can liquidate loans at which state. (More about health factor [here](https://docs.hashstack.finance/developers/supply-and-borrow/borrow/health-factor)).

1. Hf > 109% - Healthy loan
2. 109% ≥ Hf > 106% - Liquidation call
3. Hf ≤ 106% - Liquidable by anyone
4. Hf ≤ 104.5% - Liquidable by protocol



Hashstack currently uses [pragmaoracle.com](https://pragmaoracle.com) (formerly Empiric) as its trusted oracle. The oracle is used at various points in the contracts:

1. Determining the amount of leverage allowed based on the collateral and requested loan USDT value.
2. Computing if a loan is liquidable.
3. Allowing slippage in L3 integrations (Todo).
