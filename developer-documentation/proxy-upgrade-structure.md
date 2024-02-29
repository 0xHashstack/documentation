# Proxy/Upgrade Structure

Given the nature of Hashstack's integrations, there was a requirement to have an upgrade structure robust enough to handle additions of integrations over time and the addition of new functionality frequently, while maintaining previous user balances without the need for migration. Therefore, the Open protocol is designed using the Modular Smart Contract standard, which closely mirrors the Diamond standard outlined in [https://eips.ethereum.org/EIPS/eip-2535](https://eips.ethereum.org/EIPS/eip-2535).&#x20;



There are two diamonds: the Open protocol diamond, which contains core Open functionality, and the L3-Integrations diamond, which contains all integration functionality, allowing us to independently add integrations or new functionality in a modular and seamless fashion.
