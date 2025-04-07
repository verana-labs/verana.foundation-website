---
title: Reputation and Trust Deposit
date: 2024-11-05T00:00:00+02:00
subtitle: "It takes time to build a reputation."
comments: false
bigimg: [{src: "/img/triangle.jpg"}, {src: "/img/sphere.jpg"}, {src: "/img/hexagon.jpg"}]
---

## Trust Deposit

A Trust Deposit is a stake in a VPR network that any participant automatically grows when using the network. Each participant has its own Trust Deposit.

- Execution of a Validation Process grows the Trust Deposit of both the `Applicant` and the `Validator`.
- When issuing or verifying a credential, if pay per issuance and/or pay per verification is enabled by the Ecosystem, then Trust Deposit of all involved participants in the Permission Tree increase each time a credential is issued and/or verified. If applicable, involved `User Agent Owner` and `Wallet User Agent Owner` Trust Deposit increases as well.  
- Registering or renewing a DID in the Service Directory grows the Trust Deposit of the participant executing the transaction.

We can see the Trust Deposit as a percentage deduction that is executed to all circulating trust fees. Example with Verification Fees - as explained in [Business Models](/page/learn-vt-business-models.md):

{{< image "/img/verifier-fee-distrib.svg" "" "max-width: 1200x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 1200px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

- Each time fees are charged, a 20% is added and sent to the Trust Deposit of the participant executing the transaction, and corresponding amount is associated to the Permission that permitted the transaction.

- When fees are distributed to other participants, 20% is deduced and sent to their Trust Deposit, while the other 80% are liquid and immediately available.

- The percentage (here 20%) sent to Trust Deposit is defined by the VPR controller.

### Core Purposes

The main purpose behind the Trust Deposit is making sure, for a given Ecosystem, that its participants will respect the Ecosystem Governance Framework.

| **Purpose**                    | **Description**                                                                 |
|-------------------------------|----------------------------------------------------------------------------------|
| **Incentivize Good Behavior** | Entities risk losing their deposit if they act dishonestly or maliciously.      |
| **Signal Serious Intent**     | Requires "skin in the game" to filter out spam or low-effort actors.            |
| **Enable Slashing**           | Deposits can be slashed if governance rules or trust policies are violated.     |
| **Support Decentralized Governance** | Forms the economic foundation for role assignment and revocation.         |
| **Controlled by each Ecosystem** | An Ecosystem can only slash a participant the proportional amount linked to its activity on this Ecosystem|
| **Non-custodial** | Held in a VPR on-chain, not controlled by any central authority.|

{{< image "/img/verifiable-service.png" "Example of Trust Reputation." "max-width: 300px; border: 1px solid #DDDDDD; margin-top: 2.5em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em;" "text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: right; " >}}

### Slash

Ecosystems define in their EGF (Ecosystem Governance Framework) the rules for being part of their Ecosystem, and what can happen if rules are not complied.

When an Ecosystem participant is slashed, its activity is blocked until the slashed Trust Deposit is paid back by slashed participant.

### Trust Deposit Based Reputation

As information related to Network activity and Trust Deposit is public, a participant will build a digital trust reputation over time:

- its Trust Deposit will grow,
- for each Ecosystem it is taking part, its corresponding Trust Deposit history is visible by all other participants,
- for each Ecosystem it is taking part, the number of issued and/or verified credentials is visible by all other participants,
- dishonest or malicious activity, possibly sanctioned by Ecosystem with a slash, remind associated to the account owner forever.

Information can be used to compute a number of stars.

