---
title: Verifiable Trust Business Models
date: 2024-11-05T00:00:00+02:00
subtitle: "Subscription Business Model for Credential Schema Permissions, *Privacy-preserving* pay per issuance and pay per verification for credentials"
comments: false
bigimg: [{src: "/img/triangle.jpg"}, {src: "/img/sphere.jpg"}, {src: "/img/hexagon.jpg"}]
---

## Business Models

VPR spec defines two kind of business models:

- subscription based business model, for being granted a Permission in the Credential Schema Permission tree.
- pay per issuance and pay per verification.

### Subscription based Validation Process

Based on configured issuance and verification policies, if schema is not OPEN, to get granted a permission, an `Applicant` must run a Validation Process. `Applicant` starts the Validation Process by selecting an existing `Validator` Permission. Validation Process may require payment of fees, as defined by the `Validator` in its permission. Fees are usually charged using a yearly subscription which means applicant must renew its permission each year, else it expires.

Fee Structure:

| Validator → Applicant ↓  | Trust Registry                      | Issuer Grantor                        | Verifier Grantor                    | Issuer                              | Verifier | Holder                                  |
|------------------|-------------------------------------|---------------------------------------|-------------------------------------|-------------------------------------|----------|-----------------------------------------|
| Issuer Grantor   | renewable subscription (1)          |                                       |                                     |                                     |          |                                         |
| Verifier Grantor | renewable subscription (2)          |                                       |                                     |                                     |          |                                         |
| Issuer           | renewable subscription (3)          | renewable subscription (1)            |                                     |                                     |          |                                         |
| Verifier         | renewable subscription (4)          |                                       | renewable subscription (2)          |                                     |          |                                         |
| Holder           |                                     |                                       |                                     | renewable subscription              |          |                                         |

- (1): if *issuer PermissionManagementMode* is set to GRANTOR_VALIDATION.
- (2): if *verifier PermissionManagementMode* is set to GRANTOR_VALIDATION.
- (3): if *issuer PermissionManagementMode* is set to TRUST_REGISTRY.
- (4): if *verifier PermissionManagementMode* is set to TRUST_REGISTRY.


Example: If the `Applicant` would like to be an `Issuer` and the PermissionManagementMode is configured to GRANTOR_VALIDATION for credential issuance, then to be an Issuer, `Applicant` must run a Validation Process with an `Issuer Grantor` that will act as the `Validator`. If defined, issuer candidate will pay validation fees as defined in issuer grantor permission.

During the Validation Process `Applicant` will prove ownership of DIDs, VPR keys, and exchange information required by the `Validator` to accept issuer candidate as an `Issuer`. Requirements for process execution must be specified in the EGF (Ecosystem Governance Framework) of the Trust Registry controller.

Example of a permission tree where schema policy is set to GRANTOR_VALIDATION for issuance, and GRANTOR_VALIDATION for verification:

{{< image "/img/validation-tree-td.png" "" "max-width: 800x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 800px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

In this example:

- An `Applicant` will need to pay 1,000 * (1 + TD)  = 1,200 TUs to run a validation process with `Issuer Grantor B` and get granted an Issuer Permission `Issuer C` for this Credential Schema of `Trust Registry A`.
- Validation starts, fees paid by `Applicant` are escrowed.
- `Applicant` connects to the Verifiable Service provided by `Validator` (the DID registered in the Validator’s Permission). They exchange information for completing the Validation process.
- When Validation process completes, `Applicant` Permission is created, then fees are distributed.

{{< image "/img/vp-fees-distrib-issuer.png" "" "max-width: 800x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 800px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

The validation fees are partially sent to specific participant(s), the remaining fees are sent to trust deposits or treated as normal network fees and distributed using the normal distribution principle of a distributed network.

### Pay per issued/verified credential

Added to the validation fees, granted Permissions may indicate that some fees must be paid when issuing or verifying (presentation request) a Verifiable Credential of a given schema.

Example:

{{< image "/img/pay-per-issuance-verif.png" "" "max-width: 1200x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 1200px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

In this example:

- Total paid by `Issuer C` for issuing a credential: (10 + 5) * (1 + UAR + WUAR + TD) = 21 TUs
- Total paid by `Verifier E` for verifying a credential: (20 + 5 + 2 + 30) * (1 + UAR + WUAR + TD) = 79.8 TUs

This is a flexible pay per issuance/verification model that rewards all participants.

Fees involved and distributed, when a credential is issued:

{{< image "/img/issuer-fee-distrib.svg" "" "max-width: 1200x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 1200px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

Fees involved and distributed, when a credential is verified:

{{< image "/img/verifier-fee-distrib.svg" "" "max-width: 1200x;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 0.5em; " "max-width: 1200px; text-align: center; font-style: italic; font-size: smaller; text-indent: 0;  margin-top: 0em; margin-bottom: 0.5em; margin-right: 0em; margin-left: 2.5em; padding: 0em; float: none; " >}}

**Payment enforcement**:

It is responsibility of the VSs and the VUAs to verify that issuer(s) or verifier(s) paid before accepting a new issued credential of an issuer, or before presenting a requested credential from a verifier.
