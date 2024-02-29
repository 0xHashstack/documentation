# General risks and safeguards

1. The dual liquidation strategy balances the risks associated with over-dependency on liquidators by ensuring all bad loans are timely liquidated independent of the network constraints. This critical feature mitigates adverse risks stemming from a sell-cascade event.
2. Whitelisted smart contracts: Access to Hashstack’s core functionality is limited to direct interaction from the user's wallet or through allowed smart contracts, mitigating the scope for bad players from discovering a vulnerability and exploiting it through smart contract automated actions.
3. Compartmentalised supply & borrow through minimum commitment periods improves Hashstack's ability to predict liquidity availability.&#x20;
4. Looping & flash loans are not permitted. However, delegated contract interactions are permitted for allowlisted accounts and designated liquidators.&#x20;
5. Tier 1 capital. Hashstack recognises that no amount of risk & security measures ensure a fool-proof system. For this reason, Hashstack will build a tier 1 capital of 15% of total deposits to absorb adverse risks. This capital will be built over a period of 18 months.
6. Insurance: A trusted insurance provider will insure all user-provided liquidity up to US $1,000,000.&#x20;
7. Audits: Hashstack's contracts underwent one round of audit. Currently, a bug bounty is active. Two additional security audits will be performed on Hashstack's starknet contracts before the re-genesis version release.&#x20;
8. Bridges: Hashstack relies on its internal relayer built atop Stargate to transfer assets between ETH L1 & Starknet L2.
