# Verana, a Verifiable Trust ecosystem

## About the Verana Foundation

The Verana Foundation is a non-profit organization focused on defining, specifying, developing, and providing open-source components and decentralized services for building a verifiable internet. It was founded by [Fabrice Rochette](https://www.linkedin.com/in/fabricerochette/) and [Ariel Gentile](https://www.linkedin.com/in/aogentile/).

## The Verana Ecosystem

Verana is a verifiable trust ecosystem, or zero trust ecosystem, where all participating Entities, such as Humans, Services (AI Autonomous Services, Corporate Services, Social Channel Services...) and User Agents (Mobile Apps, Browsers,...), are **verifiable**.

Verana is solving all common trust issues that we are all currently facing when using the Internet:

- As a Service, how do I know if this inbound connection is from a Human?
- As a Human (or Service #1), how do I know who is the provider of Service #2?
- As a Service, shall I trust the software that is used to connect to me?
- As a Human, shall I trust the software I'm connecting to?
- ...

Any service or software can become part of the Verana ecosystem by implementing the [Verifiable Trust Specification](https://verana-labs.github.io/verifiable-trust-spec/), a specification based on open standards such as Decentralized Identifiers (DIDs), Verifiable Credentials, and more. This specification defines what are Verifiable Services, Verifiable User Agents, and Verifiable Public Registries.

## The Verana Network

Based on Cosmos SDK, the Verana Network is an implementation of a Verifiable Public Registry, which is a critical needed infrastructure for providing a Verifiable Trust ecosystem. It provides the following features:

* **Trust Registry Management**, including the publishing of governance frameworks, credential schemas, and list of granted credential issuers, verifiers...
* A **trust resolver**: Is Entity A allowed to verify a credential issued by Entity B for a Credential Schema managed by Trust Registry C?
* A **DID Directory**, so that anyone can register its Services in the directory, and be searchable in the Verana Search Engine.
* A **search engine**, for searching verifiable service metadata.

### Tokenomics

VNA, the token of the verana network is used by participants for exchanging trust fees, and for locking money into Trust Deposits.

#### Trust Fees

A participant that want to persist trust-related entities in the ledger, such as trust registries, credential schemas, or registering a DID in the DID Directory, must pay trust fees, and some of these fees are automatically sent to its trust deposit.

Same happens for the so-called Validation Process which is run between 2 participants, an applicant and a validator, for registering new issuers and new verifiers for a given credential schema.

#### Trust Deposit

When using the Verana Network, each participant account has a corresponding trust deposit. This trust deposit is automatically funded when executing transactions that involve trust.

Fundamentally, the trust deposit enables the so called "Proof-of-Trust" (PoT) feature of the Verana Network:

- the more a participant uses the Verana Network, the more its trust deposit grows.
- a trust deposit generates yield: in the Verana Network, block execution transaction fees are distributed not only to network validators, but to trust deposit owners as well.
- if a participant do not comply with the governance framework of a given trust registry it is interacting with (as issuer, verifier, holder, etc...), part of its deposit can be slashed by the governance authority of the corresponding trust registry.
- when a deposit has been slashed, participant needs to refill it in order to continue to use the services that generated the sanction.
- when a participant stops using a service, it can free its corresponding trust deposit.
- freed deposit can be reused in other service(s), or withdrawn (with penalties: part of the withdrawn tokens are burnt, for disincentivizing cash-out).

Checking the Trust Deposit of a given participant (its value, increase over time, slash history...) can give a clue of how trustable is the participant in the ecosystem.

#### Pay per issued/verified credential

The Pay per issued credential fees are partially sent to specific participant(s), the rest is sent to trust deposits or distributed using the normal distribution logic.

- When a participant is granted an ISSUER (resp. VERIFIER) permission for a given schema, trust registry may define *issuance (resp. verification) fees* for each issued (resp. verified) credential. In this case, ISSUER (resp. VERIFIER) must pay these fees in order to be able to deliver (resp. verify) the credential to the holder.
- Participating User Agents are rewarded, too.

## Who is using Verana?

Example of existing User Agents software:

- [Hologram Messaging](https://hologram.zone), a Zero Trust decentralized messaging mobile app and verifiable credential Wallet, that anyone can use to provide decentralized chatbots such as corporate chatbots, AI autonomous chatbots, or simple human to human p2p connections; Hologram is available in major app stores.

Examples of existing Service Agents software:

- [Unic ID](https://unic.id), a privacy preserving service for getting issued a verifiable credential from a NFC-compatible passport or id card. Users onboard by scanning the NFC chip of their document, perform a biometric verification and get issued a credential that they can present to third parties for proving their identity, age, or perform a simple proof of personhood;

## Community

