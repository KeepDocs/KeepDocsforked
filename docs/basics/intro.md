# Introduction to tBTC & Keep Network 


## DeFi
Decentralized Finance (DeFi) is a system of open, permissionless and interwoven financial services and products built and delivered mainly on Etherum. As of July 2020, almost $4Billion is currently deployed across all Defi applications offering loans, stable coins, derivatives, exchanges all through decentralized smart contracts. This volume is expected to grow significantly.

DeFi protocols are modular so they can stack on top of each other to build an increasingly complexer system of interoperating parts. Since DeFi products are code distributed across a decentralized blockchain like Ethereum, they can never be shut down or prohibited to those who want to use them. Thus anyone with an internet connection is able to use lending services, complex financial products, stable stores of value, and investment and trading opportunities on DeFi.

## Purpose of the tBTC System
Despite the exponential growth of the projects in Defi and Ethereum, Bitcoin still accounts for two thirds of the world’s total value in cryptocurrencies.

As Ilias Hatzis introduces tBTC in his [story](https://medium.com/@iliashatzis/could-bitcoin-on-defi-displace-banks-yes-4c0ad99f0da4) :
> “Bitcoin DeFi has been a dream for Bitcoiners. Maybe the dream is over and new tBTC project will bring Bitcoin to the DeFi world.
> Bitcoin can greatly transform DeFi and that is exactly what the Keep team, the creators of the Keep protocol understands.” 

Keep Team launched tBTC, which is a decentralized, trustless and insured custody system for Bitcoin that creates TBTC Ethereum ERC-20 tokens, with a 1:1 BTC supply peg. Bitcoin holders who want to spend their BTC on Ethereum and DeFi don’t have to trust custodians, aka signers, because signers have to deposit a bond higher then the value of the BTC they hold in custody. 

!> You'll want to see this excelent [tBTC System Explanatory Video](https://www.youtube.com/watch?v=cfmQiArg3B8) by Artem#4718.

Signers are randomly chosen of a larger network fo signing nodes and operate in groups fo three. The bond ensures that signers behavior in the system remains honest, at risk of losing their bond in case of fraud or undercollateralization.  If signers were to move funds unauthorized, leaving more TBTC outstanding than BTC in custody, the system would confiscate their bond to buy and burn an equivalent of TBTC from the market, bringing the amount of TBTC and BTC in custody in equilibrium.

<p align="center">
  <img width="619" alt="Beacon" src="https://user-images.githubusercontent.com/68087535/88100735-57075f80-cb73-11ea-996f-ec2d9590b073.png">
</p>


## Keep Network

tBTC is an application on [Keep Network](https://keep.network), for which Ben Longstaff gives us an excellent [description](https://medium.com/@ben_longstaff/secure-multi-party-computation-smpc-explained-visually-ecde155fc7c0):

> “The Keep Network intends to become the default privacy solution for storing small, sensitive packages of data securely off-chain, and in doing so, both dramatically expand the functionality of smart contracts and the mainstream uptake of blockchain technology.”

The Keep Network is a privacy solution where keeps hold distributed small amounts of data, such as a private key, and support interoperability across chains. Keeps are smart contracts that allow other smart contracts to interact with private data in a secure way. They are built on ECDSA, an algorithm supported by many of the top blockchains, and facilitate decentralized group signing with multi-party threshold signatures.

The Keep Network is a [Messari](https://messari.io/article/announcement-messari-adds-11-new-disclosures-registry-participants-surpassing-50-members) Disclosure Registrant Participant. By joining this Registry these projects have committed to bringing a higher level of transparency to the cryptoasset space through ongoing disclosures.

This [Keeps Grants Explorer](https://explorer.keep-grants.info/) from MutedTommy#3155 (in Discord) keeps track of the Keep token Grants distributed so far.

### t-ECDSA Node

T-ECDSA keeps secure the transactions with multiple individual key shares, held independently by multiple signers. Decentralized signing is performed with sMPC ( secure multi-party computation) for computation on private key shares without revealing them. Responsibility for signatures is divided, requiring a threshold number of participants to create a signature using their key shares.

In general it works like this: an Ethereum smart contract asks the Keep Network to open a new t-ECDSA keep. This keep is backed by a group of randomly selected signers from the sMPC cluster, the larger network of signing nodes. Those signers use t-ECDSA to generate the key and provide a signature. The signers can sign anything, including blockchain transactions. The Ethereum smart contract can ask the keep to sign a transaction on any blockchain-based on ECDSA, Bitcoin is just one of them.

This mechanism is trustless because signers are independent; they’re people and organizations running sMPC cluster nodes. 

<p align="center">
  <img width="319" alt="Beacon" src="https://user-images.githubusercontent.com/68167410/88845610-05ca2200-d1aa-11ea-9d8b-400516fed25c.png">
</p>

### Random Beacon Node

Random Beacon is the other part of the network: a decentralized random selection tool for selecting signers from a pool in a cryptographically secure and decentralized way. This beacon takes the form of a BLS Threshold Relay and cannot be gamed or manipulated. It is a trusted source of randomness for the process of trustless group election. No one knows who the signers will be – including the signers themselves – until the moment they are selected by the Random Beacon. This ensures that signers are not able to collude to steal funds or attack the network, and it’s why the true randomness supplied by the beacon is so important.

**The Random Beacon and t-ECDSA Keeps are the core technology of the network. Random Beacon operator and t-ECDSA client/operator, the signer, are the nodes which we operate and where we stake.**



***

**Sources and further information :**
- [Could Bitcoin on DeFi displace banks? Yes](https://medium.com/@iliashatzis/could-bitcoin-on-defi-displace-banks-yes-4c0ad99f0da4) by Ilias Hatzis
- [Bridging Bitcoin and Ethereum](https://blog.keep.network/bridging-bitcoin-and-ethereum-b2f9923630a7) from the Keep Network Blog
- [Secure Multiparty Computation](https://medium.com/@ben_longstaff/secure-multi-party-computation-smpc-explained-visually-ecde155fc7c0) by Ben Longstaff
- [Building Bridges between Blockchains with tECDSA keeps](https://blog.keep.network/building-bridges-between-blockchains-with-t-ecdsa-keeps-e58d6debb8fd) by Piotr Dyraga from the Keep Network Blog
- [Staking Documentation](https://keep-network.gitbook.io/staking-documentation/) from the Keep Network Documentation
- [tBTC Technical Overview](https://tbtc.network/developers/tbtc-technical-system-overview/) from the tBTC Website
- [What's in a beacon](https://blog.keep.network/whats-in-a-beacon-12c34b0bc078) by Antonio Salazar Cardozo from the Keep Network Blog
- [Why is Trusted Randomness So Important?](https://blog.keep.network/why-is-trusted-randomness-so-important-c22de1c1c5ee) by Antonio Salazar Cardozo from the Keep Network Blog
- [Threshold ECDSA — Safer, more private multi-signatures](https://blog.keep.network/threshold-ecdsa-safer-more-private-multi-signatures-51153f3e9ed2) by Antonio Salazar Cardozo from the Keep Network Blog on Keep developer Piotr Dyraga’s presentation on threshold-ECDSA from San Francisco Blockchain Week 2018.
- [Defi explained](https://decrypt.co/resources/defi-decentralized-finance-explained-guide-learn) by Decrypt.co
- [What is Defi](https://defipulse.com/blog/what-is-defi/) by Defipulse
- [Keep promo video](https://www.youtube.com/watch?v=h2IErqf-VrQ) by Lelka Bo in Discord Design Channel
- [TBTC: A New Sidechain Design for Bitcoin](https://insights.deribit.com/market-research/a-new-sidechain-design-for-bitcoin/) by Su Zhu in Deribit Insights
- Images are from SpaceWalker (Discord Design Channel), [Ilias Hatzis](https://medium.com/@iliashatzis) (from his story), Keep Team (Discord Design Channel).

---
`Written & assembled by Keep Community.`
`Contributors: Ramaruro, EstebanK`
