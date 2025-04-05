---
title: Trust Resolution explained
date: 2024-11-05T00:00:00+02:00
subtitle: To empower digital trust and privacy by developing open standards, decentralized infrastructure, and transparent governance frameworks that enable secure, verifiable, and user-controlled interactions across the digital world
comments: false
bigimg: [{src: "/img/triangle.jpg"}, {src: "/img/sphere.jpg"}, {src: "/img/hexagon.jpg"}]
---



{{< image "/img/proof-of-trust.png" "" "max-width: 300px; border: 1px solid #DDDDDD; float: right; margin-top: 0px; margin-bottom: 20px; margin-right: 20px; margin-left: 20px;" >}}

## Trust Resolution explained

Trust Resolution is as simple as calling a method passing the DID of the service we want to resolve, to display a Proof-of-Trust to the end-user:

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
      ...
    }
  ]
  ...
}
```




