---
title: Use cases
weight: 10

---

The following use cases summarize the concept of Verifiable Trust.


## 🏢 How to Obtain an Organization Credential

### ✅ 1. Obtain a Decentralized Identifier (DID)

- Create a **Organization DID** for your organization. You can use any DID method.
- This **Organization DID** will be resolvable to a **DID Document**, which contains service metadata and linked credentials used to resolve trust.


### ✅ 2. Obtain an **Organization Credential (VT-EC-ORG)**

You’ll need a **Organization Credential**, issued by an Ecosystem that is providing **Essential Credential Schemas**.

- For the chosen ecosystem, find an **issuer** that is granted issuance of **Organization Credentials** ECS.
- Start a Validation process with the Issuer.

Provide proof of:

- Legal name and registration
- Jurisdiction (country code)
- Organization type (e.g., PRIVATE, FOUNDATION)
- Registry URL and ID
- Address and logo

Additionally:

- prove you own the Organization DID

Once verified, you receive an **Organization Credential** issued to your **Organization DID**.

### ✅ 3. Update Your Organization DID Document

- Add a **Linked Verifiable Presentation**:
  - Your **Organization Credential**

### 🚀 Summary Checklist

| Step | Action |
|------|--------|
| 🆔 | Create an Organization DID and its DID Document |
| 🏛️ | Get an Organization Credential from a granted issuer |
| 🔗 | Present Organization Credential in your DID Document |


## 🏢 How to Run a Verifiable Service (VS)

Running a Verifiable Service (VS) means your organization (or you as a Person) can operate a trusted, privacy-respecting digital service on the decentralized web.

Prerequisite: you must already have an Organization Credential or a Person Credential.

### ✅ 1. Create a DID for your Service and Self-Issue a **Service Credential (VT-EC-SERVICE)**

- Create a **Service DID** for your service. You may want to use your **Organization DID** but is recommended to use a separate DID in case you want your organization to provide more than one Verifiable Service, as usually each service has its own DID.
- This **Service DID** will be resolvable to a **DID Document**, which contains service metadata and linked credentials.

Self-issue a **Service Credential** to your **Service DID**, that describes the specific service you're offering.

- It includes:
  - Service name, description, logo
  - Minimum age required
  - Terms & conditions URL
  - Privacy policy URL

### ✅ 2. Update Your Service DID Document

- Add **Linked Verifiable Presentations**:
  - Your **Service Credential**
  - Your **Organization Credential**

### ✅ 3. Start Accepting Secure Connections

Once your Verifiable Service is set up:

- Other Verifiable Services or User Agents can resolve trust by reading the DID Documents of:
  - your service
  - your organization
  - the issuer of your organization credential

Your service will check your credentials and validate them. If trust resolution passes, they’ll allow a secure connection with your Verifiable Service

### 🚀 Summary Checklist

| Step | Action |
|------|--------|
| 🆔 | Create a DID and DID Document |
| 🏛️ | Get an Organization Credential |
| 🛠️ | Get or issue a Service Credential |
| 🔗 | Add credentials to your DID Document |
| 🔍 | Ensure trust resolution works with VPR |
| 🌐 | Go live as a Verifiable Service |

## 🔹 User Experience: Connecting to a Verifiable Service

This is what the flow would feel like to an everyday user:

### 👤 1. User Opens Their VUA (e.g., Hologram, Trusted Wallet App)

- The user has a secure wallet or messaging app that supports Verifiable Trust.
- This app holds their verifiable credentials (e.g., Person Credential) and performs trust resolution in the background.

### 🔗 2. User Clicks a Link or Scans a QR Code

- They receive a connection invitation (e.g., to chat with a service, log in, access content).
- The link points to the DID of a Verifiable Service.

**Behind the scenes:**

- The VUA resolves the DID Document.
- It fetches the linked verifiable presentations from the service (e.g., Service Credential, Org Credential).

### 🔍 3. Trust Resolution Is Performed Automatically

The VUA validates:

- Are the credentials conforming to known ECS schemas?
- Are they issued by authorized issuers in trusted VPRs?
- Do terms, minimum age, and privacy policy match user preferences?

- ✅ If valid: The VUA displays a “Proof of Trust” badge (with icons, names, logos, and country info).
- ❌ If invalid: The user sees a warning and the app blocks the connection.

### 🙋 4. User Reviews the Service Info (Optional)

Before connecting, the app may display:

- ✅ Name of the service
- 🌍 Country of registration
- 🏛️ Organization name & logo
- 📜 Terms of service and privacy policy
- 🔞 Age restrictions

🔒 The user can make an informed decision without relying on branding or gut instinct.

### 🔑 5. User Shares Credentials If Needed

If the service requests a Verifiable Credential (e.g., proof of age, email, or membership):

- The VUA presents prompt the user for a compatible credential.
- The user selects which one to share (or declines).

🛡️ Selective disclosure and proofs without revealing more than needed are supported.

### 💬 6. Connection Established Securely

- A DIDComm connection is established with the service.
- From here, any trusted interaction is possible:
  - Secure chat
  - Video call
  - Credential issuance
  - Digital service access
  - eKYC / login flow, etc.

### 🚀 Summary Flow

1. **Click link / scan QR**
2. **VUA resolves & verifies service**
3. **User sees trust info**
4. **User optionally presents credentials**
5. **Secure session starts**

### ✨ What Makes This Experience Different?

| Feature       | Traditional Web                 | Verifiable Trust                            |
|---------------|----------------------------------|----------------------------------------------|
| **Identity**   | Centralized usernames / logins   | Decentralized identifiers (DIDs)             |
| **Trust**      | Based on logos or reputation     | Based on cryptographic proof (VCs + VPRs)    |
| **Onboarding** | Forms & passwords                | Credential-based, 1-click access             |
| **Privacy**    | Shared personal data             | Minimal disclosure, user-controlled sharing  |
| **Security**   | Phishing-prone                   | Peer authentication with DIDs and credentials |
| **UX**         | Variable, non-transparent        | Guided, verifiable, secure                   |