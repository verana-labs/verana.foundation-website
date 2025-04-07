---
title: Verifiable Trust demystified
date: 2024-11-05T00:00:00+02:00
subtitle: "Intro to Verifiable Trust, Proof-of-Trust, Deep Dive into Verifiable Trust and Business Models "
comments: false
bigimg: [{src: "/img/triangle.jpg"}, {src: "/img/sphere.jpg"}, {src: "/img/hexagon.jpg"}]
---

## Intro to Verifiable Trust: the Proof-of-Trust

{{< image "/img/proof-of-trust.png" "Proof-of-Trust." "max-width: 300px; border: 1px solid #DDDDDD; margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em;" "text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: right; " >}}

Trust Resolution is as simple as calling a method passing the DID of the service we want to resolve, to display a **Proof-of-Trust** to the end-user:

``` 
resolve_trust("did:example:gaia")
```
and receive a response similar to this one:

``` 
{
  "did":"did:example:gaia",
  "verified": true,
  "service_provider": {
      "id": "did:example:def",
      "type": "Organization",
      "name": "Gaia Registry LLC",
      "country": "zz",
      "reputation": {
        "issuedCredentials": 1234,
        "verifiedCredentials": 7678,
        "trustDepositValue": 176327.124356,
        "amountSlashed": 0,
        "stars": 5.0
      },
      "issuer": "did:example:zzz",
      ...
  },
  "service": {
      "name": "Gaia Registry",
      "termsAndConditions": "http://example.com",
      "privacyPolicy": "http://example.com",
      "minimumAgeRequired": 16,
      "description": "Create your Metaverse ID at Gaia Registry! Protect your identity with biometrics and easily recover it if you loose your phone. Use your Gaia Identity to connect to fancy services with no password."
      ...
  },
  "credentials" : [
    {
      "type": "TrademarkCredential",
      ...
    }
  ]
  ...
}
```

## Deep Dive into Verifiable Trust

Let's explain how the Verifiable Trust does it.

{{< image "/img/verifiable-service.png" "Popup of a chatbot Verifiable Service." "max-width: 200px; border: 1px solid #DDDDDD; margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em;" "text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: right; " >}}

Verifiable Trust (VT) introduces 3 main concepts:

- Verifiable Service (VS),
- Verifiable User Agent (VUA), and
- Verifiable Public Registry (VPR).

### What is a Verifiable Service (VS)?

A VS is a service that provides a way to identify itself to a peer, before the peer connects to it.

Entities that want to connect to a VS can review its presented verifiable credentials, prove their legitimacy by performing a trust resolution, and based on the result, decide to connect or not.

A VS must resolve trust of peers that attempt to connect to it (VS and/or VUA) and refuse connections from non-verifiable peers.

Additionally, a verifiable service that would like to issue or request verification of credentials, must prove it is allowed to do so, else peer must refuse that action.

### What is a Verifiable User Agent (VUA)?

A Verifiable User Agent (VUA) is a software (a browser, an app, a wallet…) for connecting to VSs and other VUAs. When establishing connections, a VUA must verify the connection peer(s) and allow connection(s) only to compliant VS and VUA peers.

Additionally, VUAs must perform a trust resolution by verifying the credentials presented by the peers and query VPR(s) to check that these credentials have been issued by verified issuers.

### What is a Verifiable Public Registry (VPR)?

A Verifiable Public Registry (VPR) is a “registry of registries” public service, which provides:

- Trust registry features, that can be used by any Ecosystem: create trust registries, for each trust registry, define its credential schemas, who can issue, verify credential of a specific credential schema, business models…

- a query API, used by VSs, VUAs, needed by trust resolution.

{{< image "/img/verifiable-public-registry.png" "A VPR is a Registry of Registries (RoR)." "max-width: 600px;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 600px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

#### Trust Registries

Each Ecosystem Trust Registry is identified by a resolvable DID, and provides, at least:

- Governance Framework document(s).
- Zero or more Credential Schemas.

{{< image "/img/tr.png" "A Trust Registry." "max-width: 200px;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 200px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

A VPR doesn’t care about the DID methods used because trust resolution is performed outside the VPR.

#### Credential Schemas

Credential Schemas are created by Trust Registry owners (Ecosystems). Each Credential Schema is composed of, at least:

- a Json Schema, to define the corresponding Verifiable Credential schema.
- a PermissionManagementMode to configure issuance policy for issuing credentials of this schema. It can be granted to anyone (OPEN), granted directly by the Trust Registry controller (TRUST_REGISTRY) to issuers, or granted by an issuer grantor (GRANTOR_VALIDATION).
- a PermissionManagementMode to configure verification policy for verifying credentials of this schema. It can be granted to anyone (OPEN), granted directly by the Trust Registry controller (TRUST_REGISTRY) or granted by a verifier grantor (GRANTOR_VALIDATION).
- a Permission tree.

{{< image "/img/permission-tree-small.png" "A Permission tree." "max-width: 600px;  margin-top: 0em; margin-bottom: 0em; margin-right: 0em; margin-left: 0em; " "max-width: 600px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0em; padding: 0em; float: none; " >}}

Participant roles are defined in the table below:

| **Participant Role**   | **Description**                                                  |
|-----------------------|------------------------------------------------------------------|
| **Trust Registry**    | Create and control Credential Schemas. Grant other roles.        |
| **Issuer Grantor**    | Grant Issuer permissions to candidate issuers.                   |
| **Verifier Grantor**  | Grant Verifier permissions to candidate verifiers.               |
| **Issuer**            | Can issue credentials of this schema.                            |
| **Verifier**          | Can request presentation of credentials of this schema.          |
| **Holder**            | Special role used for selected business models.          |

Example of a Json Schema credential schema:

```
{
  "$id": "vpr-mainnet:/vpr/v1/cs/js/VPR_CREDENTIAL_SCHEMA_ID",
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "SimpleExampleCredential",
  "description": "SimpleExampleCredential using JsonSchema",
  "type": "object",
  "properties": {
    "credentialSubject": {
      "type": "object",
      "properties": {
        "id": {
          "type": "string",
          "format": "uri"
        },
        "firstName": {
          "type": "string",
          "minLength": 0,
          "maxLength": 256
        },
        "lastName": {
          "type": "string",
          "minLength": 1,
          "maxLength": 256
        },
        "expirationDate": {
          "type": "string",
          "format": "date"
        },
        "countryOfResidence": {
          "type": "string",
          "minLength": 2,
          "maxLength": 2
        }
      },
      "required": [
        "id",
        "lastName",
        "birthDate",
        "expirationDate",
        "countryOfResidence"
      ]
    }
  }
}
```

After creating the Json Schema, the ecosystem owner of the Trust Registry will issue a [Json Schema Credential](https://www.w3.org/TR/vc-json-schema/) with the DID it registered as DID of the Trust Registry in the VPR, to prove ownership of the schema and the DID:

```
{
  "@context": [
      "https://www.w3.org/ns/credentials/v2"
  ],
  "id": "https://trust-registry/example-credential-json-schema-credential.json",
  "type": ["VerifiableCredential", "JsonSchemaCredential"],
  "issuer": "did:example:trust-registry",
  "issuanceDate": "2024-01-01T19:23:24Z",
  "credentialSchema": {
    "id": "https://w3c.github.io/vc-json-schema/schema/json-schema-credential-schema.json",
    "type": "JsonSchema",
    "digestSRI": "sha384-S57yQDg1MTzF56Oi9DbSQ14u7jBy0RDdx0YbeV7shwhCS88G8SCXeFq82PafhCrW"
  },
  "credentialSubject": {
    "id": "vpr-mainnet:/vpr/v1/cs/js/12345678",
    "type": "JsonSchema",
    "jsonSchema": {
      "$ref": "vpr-mainnet:/vpr/v1/cs/js/12345678"
    },
    "digestSRI": "sha384-ABCSGyugst67rs67rdbugsy0RDdx0YbeV7shwhCS88G8SCXeFq82PafhCeZ" 
  }
}
```

Finally, the Ecosystem must declare the Json Schema Credential in the DID Document of the declared Trust Registry DID in the VPR, as well as the location of the Trust Registry in the VPR:

```
"service": [
    {
      "id": "did:example:trust-registry#vpr-schemas-example-credential-schema-credential",
      "type": "LinkedVerifiablePresentation",
      "serviceEndpoint": ["https://trust-registry/example-credential-schema-presentation.json"]
    },
    {
      "id": "did:example:trust-registry#vpr-schemas-trust-registry-1234",
      "type": "VerifiablePublicRegistry",
      "version": "1.0",
      "serviceEndpoint": ["vpr-mainnet:/vpr/v1/"]
    }
    ...
  ]
```

#### Issue Verifiable Credentials

When the Ecosystem has created its Credential Schemas in the VPR, created its corresponding Json Schema Credentials, and properly setup the "service" section of its trust registry DID Document, it is now possible to issue credentials based on these schemas.

Credentials that comply with the Verifiable Trust specification are called Verifiable Trust Credentials. These credentials must refer to, in their credentialSchema attribute, the corresponding JsonSchemaCredential issued by the Trust Registry DID.

In our previous example, that would mean and ExampleCredential should look like this example:

```
{
  "@context": [
    "https://www.w3.org/ns/credentials/v2"
  ],
  "id": "did:example:issuer",
  "type": ["VerifiableCredential", "VerifiableTrustCredential", "ExampleCredential"],
  "issuer": "did:example:issuer",
  "credentialSubject": {
     "id": "did:example:abcdef",
    ...
  },
  ...
  "credentialSchema": {
    "id": "https://trust-registry/example-credential-json-schema-credential.json",
    "type": "JsonSchemaCredential"
  }
}

```

We can summarize the dependencies, from trust registry created in VPR, until issued credential.

{{< image "/img/vt-cred.png" "" "max-width: 800px;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 800px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}