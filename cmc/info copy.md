# CMC info

## What Is Verana?

Verana is a **Zero Trust** ecosystem, where all participating Entities, such as Humans, Service Agents (AI Autonomous Services, Corporate Services, Social Channel Services...) and User Agents (Mobile Apps, Browsers,...), are **verifiable**.

Verana is solving all common trust issues that we all are facing in the Internet:

- As a Service, how do I know if this inbound connection is from a Human?
- As a Human (or Service #1), how do I know who is the provider of Service #2?
- As a Service, shall I trust the software that is used to connect to me?
- As a Human, shall I trust the software I'm connecting to?
- ...

Any service or software can become part of the Verana ecosystem by implementing the [Decentralized Trust Specification](https://verana-labs.github.io/decentralized-trust-spec/), a specification based on open standards.

* Decentralized Trust - Services (DT-Ss) are Services that identify themselves by presenting Verifiable Credential(s) to other Entities that want to connect to them. An Entity can decide, by verifying the Verifiable Credential(s) presented by a DT-S, if it decides to connect to the Service or not. Examples of DT-Ss include: a chatbot operated by a bank, a social channel managed by an influencer, an AI autonomous Service, a webrtc communication hub, a web page...

* Decentralized Trust - User Agents (DT-UAs) are User Agents (such as a Browser, a Mobile App, a Wallet...) that identify themselves to DT-Ss or others DT-UAs by presenting Verifiable Credential(s). When a DT-S or a DT-UA receives an inbound connection of a DT-UA, it can verify, prior from accepting the connection, the Verifiable Credential(s) presented by the DT-UA and then decide to accept or refuse the connection.

* A Decentralized Trust - Registry (DT-R), is a public Registry of Registries (RoR) used by Governments, Organizations and Persons for creating Trust Registries, their associated governance frameworks, Verifiable Credential Schemas, and their associated Verifiable Credential Issuer and Verifier permissions.

By enforcing strict verification of all participants by default, trusted communication channels are enabled by default.

### The Verana Network (VNA) : the first Decentralized Trust - Registry

Based on Cosmos SDK, the Verana Network is the very first implementation of a Decentralized Trust - Registry. It provides the following features:

* Trust Registry Management, including publishing governance frameworks, credential schemas, and list of granted credential issuers, verifiers...
* A trust resolver: Is Entity A allowed to verify a credential issued by Entity B for a Credential Schema managed by Trust Registry C?
* A DID Directory management, so that anyone can register its DT-S in the directory, and be searchable in the Verana Search Engine
* Several token-based business models, for rewarding all ecosystem participants: Service providers, credential issuers, trust registries, User Agent vendors, wallet builders...

### Tokenomics

The VNA token is used by all participants for interacting with the network. Participants must lock VNA token as a Proof-of-Trust.

#### Trust Deposit

When using the Verana Network, each participant account has a corresponding trust deposit.

This trust deposit is automatically funded when executing transactions that involve trust: creation of entities such as trust registries, credential schemas, did in did directory; fees transferred from one participant to other participant(s) for the execution of a trust-related service,...

Fundamentally, the trust deposit enables the so called "Proof-of-Trust" (PoT) feature of Verana:

- the more you use the Verana Network, the more your trust deposit grows.
- a trust deposit generates yield: in the Verana Network, block execution transaction fees are distributed not only to network validators, but to trust deposit owners as well.
- if you do not respect the governance framework of the trust registries you are interacting with (as issuer, verifier, holder, etc...) part of your deposit can be slashed by the governance authority of the corresponding trust registry.
- when your deposit has been slashed, you need to refill it in order to continue to use the services that generated the sanction.
- when you stop using a service, you can free its corresponding trust deposit.
- freed deposit can be reused in other service(s), or withdrawn (with penalties: part of the withdrawn tokens are burnt).

#### Entity creation

*This section is non-normative.*

The following fees are not directly sent to a specific participant but are distributed using the normal distribution principle of a [[ref: DTR]].

Creating an instance of one of the following entities implies paying fees and sending funds to the trust deposit:

- Trust Registries (once)
- Credential Schema (once)
- Did Directory (renewable subscription)

Other operations that just imply paying fees:

- Updating governance frameworks of Trust Registries
- Removing a Did from the Did Directory
...

#### Pay per execution of the validation process

The validation fees are partially sent to specific participant(s), the rest is sent to trust deposits or distributed using the normal distribution principle of a [[ref: DTR]].

| Payee → Payer ↓  | Trust Registry                      | Issuer Grantor                        | Verifier Grantor                    | Issuer                              | Verifier | Holder                                  |
|------------------|-------------------------------------|---------------------------------------|-------------------------------------|-------------------------------------|----------|-----------------------------------------|
| Issuer Grantor   | renewable subscription (1)          |                                       |                                     |                                     |          |                                         |
| Verifier Grantor | renewable subscription (2)          |                                       |                                     |                                     |          |                                         |
| Issuer           | renewable subscription (3)          | renewable subscription (1)            |                                     |                                     |          |                                         |
| Verifier         | renewable subscription (4)          |                                       | renewable subscription (2)          |                                     |          |                                         |
| Holder           |                                     |                                       |                                     | renewable subscription              |          |                                         |

- (1): if *issuer mode* is set to GRANTOR_VALIDATION.
- (2): if *verifier mode* is set to GRANTOR_VALIDATION.
- (3): if *issuer mode* is set to TRUST_REGISTRY.
- (4): if *verifier mode* is set to TRUST_REGISTRY.

#### Pay per issued credential

*This section is non-normative.*

The Pay per issued credential fees are partially sent to specific participant(s), the rest is sent to trust deposits or distributed using the normal distribution principle of a [[ref: DTR]].

- When a participant is granted an ISSUER permission for a given schema, trust registry and issuer grantor may define *issuance fees* for each issued credential. In this case, ISSUER must pay these fees in order to be able to deliver the credential to the holder.
- Wallet User Agent and User Agent are rewarded, too.
- Part of the fees are sent to trust deposits.

#### Pay per verified credential

*This section is non-normative.*

The Pay per issued credential fees are partially sent to specific participant(s), the rest is sent to trust deposits or distributed using the normal distribution principle of a [[ref: DTR]].

- When a participant is granted a VERIFIER permission for a given schema, trust registry, issuer grantor, issuer, verifier grantor may define *verification fees* for each verified credential. In this case, VERIFIER must pay these fees in order to be able to request presentation, for a specific issuer, of a credential of this schema to the holder.
- Wallet User Agent and User Agent are rewarded, too.
- Part of the fees are sent to trust deposits.


## 





* [DIDs](https://www.w3.org/TR/did-core/)
* [w3c verifiable credentials](https://www.w3.org/TR/vc-data-model-2.0/)
* [DIDComm](https://identity.foundation/didcomm-messaging/spec/)
* [DIF linked verifiable presentations](https://identity.foundation/linked-vp/)
* [json schema](https://json-schema.org/)
* [json schema credentials](https://www.w3.org/TR/vc-json-schema/)
* [ToIP Trust Registry Query Protocol](https://trustoverip.github.io/tswg-trust-registry-protocol/)

## Who is using Verana?

Example of existing User Agents software:

- [Hologram Messaging](https://hologram.zone), a Zero Trust decentralized messaging mobile app and verifiable credential Wallet, that anyone can use to provide decentralized chatbots such as corporate chatbots, AI autonomous chatbots, or simple human to human p2p connections; Hologram is available in major app stores.

Examples of existing Service Agents software:

- [Unic ID](https://unic.id), a privacy preserving service for getting issued a verifiable credential from a NFC-compatible passport or id card. Users onboard by scanning the NFC chip of their document, perform a biometric verification and get issued a credential that they can present to third parties for proving their identity, age, or perform a simple proof of personhood;

## DID Directory Management

The DID directory is a public database of [DIDs](https://www.w3.org/TR/did-core/) that is used by crawlers to index the metadata of the Decentralized Trust Services provided by these [DIDs](https://www.w3.org/TR/did-core/).

Search engines simply need to iterate over the DID Directory, resolve the DIDs and index the corresponding Decentralized Trust - Services based on DT-S metadata (DID Document, presented credentials,…)



The DID Directory 

Business models

Additionally, Ver
Don't trust! Verify. Verana is solving all common trust issues that we all are facing in the Internet:

- As a Service, how do I know if this connection if from a Human?
- As a Human (or Service #1), how do I know who is the provider of Service #2?
- As a Service, shall I trust the software that is used to connect to me?
- As a Human, shall I trust the software I'm connecting to?

Current internet software is trying to add workarounds to fix the fact that the world wide web has not been designed to be trustable, but this makes the user experience painful without really making the web a trustable place.

Don't trust. Verify. Verana redefines the web by adding a missing trust layer:

- As a Service, I can instantly verify that this new inbound connection is from a Human.
- As a Human (or Service #1), I can verify who is the provider of Service #2 before even connecting to it.
- As a Service, I can verify what is the software (User Agent or Service Agent) that connects to me and decide if I accept the connection or not.
- As a Human, I can verify the software of the Service I'm connecting to.




- zero trust
- build decentralized autonomous chatbots
- proof of personhood

Verana is a Decentralized Trust - Registry (DT-R), a public Registry of Trust Registries (RoTR). Based on Cosmos SDK, Verana is the very first implementation of a DT-R, one of the needed modules for providing an implementation of the [Decentralized Trust Specification](https://verana-labs.github.io/decentralized-trust-spec/).

In a Zero Trust ecosystem, a Trust Registry is an approved list of Issuers and Verifiers that are authorized to issue/verify certain Verifiable Credentials, and is queried by ecosystem participants to verify things. Each Trust Registry provides:

* Governance Framework document(s);
* Zero or more Credential Schemas;
* For each Credential Schema, a tree of permissions to define who can issue or verify credentials based on this schema;
* Business rules, for charging / rewarding involved ecosystem participants.

As an example, a Trust Registry would provide an answer to these questions:

* Is Issuer A granted issuance of Driving License Credential Schema governed by Trust Registry TR?
* Is Company B granted verification of credentials linked to the Driving License Credential Schema governed by Trust Registry TR?

Added to Decentralized Trust - Registry (DT-R), Decentralized Trust introduces the concepts of Decentralized Trust - Service (DT-S), Decentralized Trust User Agent (DT-UA):

* A Decentralized Trust - Service (DT-S) is a Service that identify itself by presenting Verifiable Credential(s) to other Entities that want to connect to it. Entities can decide, by analyzing the Verifiable Credential(s) presented by the DT-S, if service is trustable or not and then decide to connect or not. Examples of DT-S include: a chatbot operated by a bank, a social channel managed by an influencer, a webrtc communication hub, a web page...

* A Decentralized Trust - User Agent (DT-UA) is an User Agent (a Browser, a Mobile App, a Wallet...) that identify itself to DT-Ss or others DT-UAs by presenting Verifiable Credential(s). When a DT-S or a DT-UA receives an inbound connection of a DT-UA, they can verify, prior from accepting the connection, if the Verifiable Credential(s) presented by the DT-UA are trustable or not, and then decide to accept or refuse the connection.

* A Decentralized Trust - Registry (DT-R), is a public Registry of Registries (RoR) used by Governments, Organizations and Persons for creating Trust Registries, their associated governance frameworks, Verifiable Credential Schemas, and their associated Verifiable Credential Issuer and Verifier permissions.

Verana provides a full SDK for has been build around the Decentralized Identity ecosystem and is 






NEAR Protocol is a decentralized application platform designed to make apps usable on the web. The network runs on a Proof-of-Stake (PoS) consensus mechanism called Nightshade, which aims to offer scalability and stable fees.

NEAR is the native utility token that is used for:

* Fees for processing transactions and storing data.
* Running validator nodes on the network via staking NEAR tokens.
* Used for governance votes to determine how network resources are allocated.

NEAR tools include: 

* NEAR SDKs which includes standard data structures and testing tools for Rust and AssemblyScript. 
* Gitpod for NEAR to create a zero time onboarding experience for developers. 
* NEAR Wallet that lets application developers create streamlined user experiences. 
* NEAR Explorer to aid with both debugging of contracts and the understanding of network performance. 
* NEAR Command Line Tools to allow developers to deploy applications from local environments.


## How Many NEAR Coins Are There in Circulation?

NEAR Protocol launched its mainnet on April 22, 2020 with 1 billion NEAR tokens created at genesis. 5% of additional supply is issued each year to support the network as epoch rewards, of which 90% goes to validators (4.5% total) and 10% to the protocol treasury (0.5% total). 30% of transaction fees are paid out as rebates to contracts which interact with a transaction, while the remaining 70% are burned.


### Who Are the Founders of NEAR Protocol?

NEAR Protocol is the brainchild of developers Alex Skidanov and Illia Polosukhin, both of whom have extensive experience in programming.

The two met while Skidanov worked at U.S. startup accelerator Y Combinator, and in July 2018 began work on a project which focused on allowing developers to build and release software with less friction.

This project became what is now the NEAR Protocol, and employs more than 40 staff, including developers with experience at Google and MemSQL.

According to NEAR Protocol’s official website, many of the developers hold prizes and nominations from competitions in coding and related fields, notably the International Collegiate Programming Contest (ICPC).

Skidanov himself worked at both MemSQL and Microsoft, while Polosukhin contributed to end-to-end open source machine learning platform TensorFlow and Google Search.


### Where Can I Buy NEAR Protocol (NEAR)?

NEAR is available for trading on a growing number of exchanges, with cryptocurrency and [stablecoin](https://coinmarketcap.com/alexandria/article/what-is-a-stablecoin) pairs currently available.

[Binance](https://coinmarketcap.com/exchanges/binance/) offers the largest number of pairs as of October 2020, while [Huobi Global](https://coinmarketcap.com/exchanges/huobi-global/) also offers [Bitcoin](https://coinmarketcap.com/currencies/bitcoin/) (BTC), [Ethereum](https://coinmarketcap.com/currencies/ethereum/) (ETH) and [Tether](https://coinmarketcap.com/currencies/tether/) (USDT) options.

New to cryptocurrency? Read CoinMarketCap’s [easy guide](https://coinmarketcap.com/how-to-buy-bitcoin/) to buying Bitcoin or any other token.
## What Is TrueUSD (TUSD)?

TrueUSD is a U.S. dollar [stablecoin](https://coinmarketcap.com/alexandria/article/what-is-a-stablecoin) pegged to USD at 1:1. First launched to a limited investor base in January 2018, TrueUSD has since grown to incorporate almost $400 million of backed tokens as of October 2020.

TrueUSD is one of a number of cryptocurrency stablecoins administered by TrustToken, a platform for tokenizing real-world assets.

As with other stablecoins, TrueUSD aims to facilitate increased liquidity and provide cryptocurrency traders and general users with a nonvolatile asset relative to free-floating tokens such as [Bitcoin](https://coinmarketcap.com/currencies/bitcoin/) (BTC).

As of October 2020, TUSD is the 38th largest cryptocurrency by market cap. 


### Who Are the Founders of TrueUSD?

TrueUSD is a stablecoin launched by parent company TrustToken, whose co-founder and CEO is Rafael Cosman.

Cosman has a lifelong attachment to cryptography, studying it along with artificial intelligence (AI) before working at both Google Brain and software company Palantir. He left Google to create TrustToken in 2017.

Cosman has stated that TrueUSD was always just the start of TrustToken’s product line, involving relatively little work in return for creating a high-impact asset. 

At the time of launch, he noted that regular auditing of the stablecoin formed an important focus for the company, giving investors peace of mind at a time when many cryptoassets were seeing heavy volatility in the wake of the initial coin offering ([ICO](https://coinmarketcap.com/alexandria/glossary/initial-coin-offering-ico)) phenomenon.


#### What Makes TrueUSD Unique?

TrueUSD aims to balance stability and utility — the main use cases of any stablecoin — with security in the form of regular attestations. 

From its launch onwards, parent company TrustToken has sought to underscore the importance of independent verification of the stablecoin’s provenance. As such, the stablecoin’s appeal is geared towards larger investors looking to reduce risk, in addition to smaller private traders.

TrustToken describes TUSD as “the first regulated stablecoin fully backed by the US Dollar.”

TrueUSD is part of an ever-expanding stablecoin market, which now includes a large number of USD-backed assets. [Tether](https://coinmarketcap.com/currencies/tether/) (USDT) remains by far the largest, with a market cap of $15 billion as of October 2020, compared to TUSD’s $382 million.

TrustToken has entered various corporate partnerships as part of its business activities, including options for TUSD holders to increase annualized passive income returns.


#### Related Pages:

Learn more about Tether [here](https://coinmarketcap.com/currencies/tether/).

Learn more about USD Coin [here](https://coinmarketcap.com/currencies/usd-coin/).

New to cryptocurrency? Find all the information you need with [Alexandria](https://coinmarketcap.com/alexandria/categories/crypto-basics), CoinMarketCap’s dedicated education resource.


#### How Many TrueUSD (TUSD) Coins Are There in Circulation?

There was around 381.9 million TUSD in circulation as of October 2020. Given its status as a stablecoin, the supply is uncapped, and will continue to expand according to demand.

There are two incarnations of TUSD available: an [ERC-20](https://coinmarketcap.com/alexandria/glossary/erc-20) token on [Ethereum](https://coinmarketcap.com/currencies/ethereum/) and another, also known as TUSDB, a BEP-2 token on Binance Chain.

TrueUSD’s equivalent redeemability for USD is maintained via partnerships with banks and fiduciary entities.


### How Is the TrueUSD Network Secured?

TrustToken aims to deliver maximum transparency using tools such as real-time auditing of TUSD’s backing and reliability. 

Beyond trusting the validity of its USD peg, any security issues relate to those which affect all ERC-20 standard tokens. Transactions, for example, can suffer from abnormally high fees if [gas prices](https://coinmarketcap.com/alexandria/glossary/gas-price) on the Ethereum blockchain spike.


### Where Can You Buy TrueUSD (TUSD)?

As one of the largest USD stablecoins, TUSD is freely available on major exchanges, with pairs for cryptocurrencies and other stablecoins available.

Among the largest volume currently belongs to [Binance](https://coinmarketcap.com/exchanges/binance/) and DeFi automated market maker [Curve](https://coinmarketcap.com/exchanges/curve-finance/).

New to crypto? Read our [easy guide](https://coinmarketcap.com/how-to-buy-bitcoin/) to buying Bitcoin and other cryptocurrencies."


