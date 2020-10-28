# All The Keeps: Guide for TBTC System Control

<p align="center">
  <img width="250" src="https://user-images.githubusercontent.com/68087535/97370062-f3d14b80-188c-11eb-989e-e84eb8146297.png">
</p>

## Intro

This document describes how to use the information from [AllTheKeeps](https://allthekeeps.com) site to support the most common workflows and functions associated with the tBTC System for the main participants listed below. It shows the up to date detailed information about the activitiy (Deposits and Redemptions contracts and states) and Network Operators (Used and Available Capacity), of the tBTC system.

?>You can find details about most aspects (Purpose, Economics, Node Set Up and Operation, etc) related to the tBTC System in this site.

The tBTC System has three main participants:

- **Random Beacon Node Operators**: randomly create groups of Signers for New Keeps, which hold the Private Key that store the supplied Bitcoin

- **ECDSA Node Operators**: sign Keeps and support the BTC -> tBTC Supply Peg with staked KEEP tokens and bonded ETH

- **tBTC Network Users (Minter/Redeemer)**: Move Bitcoin <-> Ethereum


## Workflows supported by All The Keeps

### **ECDSA Node Operator Management**

As an ECDSA Node Operator you need to understand and monitor your participation in the Network:
* Keeps signed by your Operator: this will determine the Fees and Rewards that you will be entitled to, and also the Risk you are exposed to.
* Collateralization Ratio of each Deposit guaranteed by your Operator: 
!>_Undercollateralization will lead to Liquidation and loss of bonds. You should redeem that Deposit to avoid Liquidation_
<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/68087535/96767623-2671d480-13b3-11eb-803d-c71fb39686ba.png">
</p>

### **Random Beacon Node Operator Management**

As a Random Beacon Operator you need to understand and monitor your participation in the Network: 
* Groups your Operator participates to randomly select Signers for new Keeps: this will determine the Fees and Rewards that you will be entitled to. There are no Risks associated with the Random Beacon operation.
<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/68087535/96767623-2671d480-13b3-11eb-803d-c71fb39686ba.png">
</p>

### **Deposits Tracking**

As a Depositor/Redeemer of TBTC in the Keep Network you need to understand:
* Status of your Deposit, both in the Bitcoin Chain as well as in the Ethereum Chain
<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/68087535/96767623-2671d480-13b3-11eb-803d-c71fb39686ba.png">
</p>

### **tBTC System Governance Tracking**

Understand and track the main variables of the tBTC System Governance (BTC lot sizes, ETH/BTC ratio, etc.)

The first workflow (ECDSA Node Operator Management) is the most important for a Node Operator as you need to actively monitor Activity and States and take actions to protect your investment. The other workflows are for monitoring and informational purposes only, no actions are required.
<p align="center">
  <img width="450" src="https://user-images.githubusercontent.com/68087535/96767623-2671d480-13b3-11eb-803d-c71fb39686ba.png">
</p>

## ECDSA Node Operator Management
**The first workflow (ECDSA Node Operator Management) is the most important for a Node Operator as you need to actively monitor Activity and States and take actions to protect your investment. The other workflows are for monitoring and informational purposes only, no actions are required.**


Your Operator may be selected by a Random Beacon Group to participate as a signer in a Keep to hold a deposit of Bitcoin and mint TBTC.

To monitor Deposits signed by your Operator, go to the [Operators](https://allthekeeps.com/operators) page.
Here you can see all the active Operators, and selecting an Address, you can see all activity for that Operator. The two main tabs are:
* Keeps: a list of all Keeps signed by your Operator, in any state. The address shown for a Keep is the Deposit address.
* Beacon Groups: a list of all the Random Beacon Groups in which your Operator participated. The groups are tracked by names (e.g. silver tapir) here to make it easy to understand if groups are different or the same (vs. an Address), as randomness is important for the integrity of the network.

### A Deposit can have the following Statuses during the Deposit, Active and Redeem Phases. 

Details can be found in the Appendix below.

_Deposit States_
* Awaiting Signer Setup
* Signer Setup Failed
* Awaiting Funding
* Awaiting Funding Proof
* Funding Timeout

_Active State_
* Active

_Redeem States_
* Awaiting Withdrawal Signature
* Awaiting Withdrawal Proof
* Redemption Time Out
* Redeemed
* Courtesy Call
* Liquidation in Progress
* Liquidated

!>**You need to monitor and take action when a deposit enters any of the following three states :**

**1. Awaiting Funding Proof**

Sometimes this is created by latencies in the BTC network that are higher than the tBTC system defined time outs.
This is being worked out in a later release of the tBTC system. Current solution is to contact the Keep Team in Discord.


**2. Courtesy Call (Pre-Liquidation)**

At the first threshold of 125% for the ETH/BTC ratio, a deposit enters pre-liquidation, also referred to as “courtesy call”. In this state, a deposit can be redeemed by anyone, even if the deposit is locked (see the sections on redemption and minting for more). Pre-liquidation indicates that the signers _**should close the deposit**_ or face forced liquidation after a pre-liquidation period. 

If the deposit is not closed within 6 hours, or if the deposit collateral falls below 110% collateralization, liquidation will follow. This gives each signer an incentive to close the position before it becomes severely undercollateralized. Alternatively, if the ETHBTC ratio recovers such that the deposit becomes at least 125% collateralized during the 6 hours, the deposit is safe and is moved away from the pre-liquidation state.

_Workflow to avoid Liquidation_

You need to close the deposit at risk: 
* Acquire TBTC in the amount of the deposit (e.g. through the Decentralized Exchanges). You will use this TBTC to redeem the undercollateralized deposit. 
* Start the Redemption from Deposit Details Page and click the "Redeem" Button. This will take you to the tBTC Dapp to finish the process
?>_It is recommended to either have TBTC or an equivalent amount easily and quickly available, as time is of the essence for avoiding Liquidation._

**3. Awaiting Withdrawal Proof**

Sometimes this is created by latencies in the BTC network that are higher than the tBTC system defined time outs.
This is being worked out in a later release of the tBTC system. Current solution is to contact the Keep Team in Discord.



## Appendix: Deposit States details
The details in this Appendix are taken from the [tBTC System Design Document](https://docs.keep.network/tbtc/index.html#_overview_2)

Each DEPOSIT is a simple State Machine

<p align="center">
  <img width="550" src="https://docs.keep.network/tbtc/img/generated/deposit-state-machine.png">
</p>

### Deposit Flow

`START`
- Deposit does not exist yet

`AWAITING_SIGNER_SETUP` -> **Awaiting Signer Setup**
- The funder has placed a bond, and requested a signing group
- The Keep contracts must select a signing group or return failure
- If failed:

`FAILED SETUP` -> **Signer Setup Failed**
- Failed Setup because of timeout.

`AWAITING_BTC_FUNDING_PROOF` -> **Awaiting Funding Proof**
- A signing group has been formed, and their public key hash returned
- The funder MUST return a SPV proof of funding before a timeout
- If timed out:

`FAILED_SETUP` -> **Funding Timeout**
- Failed becaus its funder has failed to submit a funding proof in time


`FRAUD_AWAITING_BTC_FUNDING_PROOF`
- Signing group fraud has been detected before the funding proof has been provided
- Signers bonds are seized when this state is entered.
- If the funder can provide a funding proof in a reasonable amount of time, then they will receive the singer bonds
- If the timeout elapses, signer bonds will be partially slashed and then returned.

NOTE: the timeout on this state should be relatively short. We want to make it risky for a depositor who has not already funded when this state is entered to fund in order after this state is entered in order to try to receive the full signer bond amount



`ACTIVE`
- TBTC is minted and active.

### Redemption Flow

`AWAITING_WITHDRAWAL_SIGNATURE`
- A redemption has been initiated
- The signers MUST sign a digest
- The signers may return the signature for verification
NOTE: there is a disincentive to return a signature, as the caller must pay for ecrecover gas and storage slot updates (to transition states).

`AWAITING_WITHDRAWAL_PROOF`
- The signers has returned a valid signature on the message
- The signers MUST provide a settlement proof

`LIQUIDATION_IN_PROGRESS`

- via an ECDSA or BTC fraud proof
- via a state timeout

`REDEEMED`




