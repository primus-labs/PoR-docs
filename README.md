# Proof-of-Reserves Product Introduction

## Overview

Primus enables verifiable transparency over institutional reserves through a Data Verification and Computation (DVC) architecture. By combining **zkTLS** for authenticated off-chain data retrieval with **zkVM/TEE** for verifiable computation, Primus delivers a mature, ready-to-use **Proof-of-Reserves** (PoR) solution. 

Institutions can securely aggregate and verify both on-chain and off-chain reserves, and continuously present their real-time financial positions with cryptographic certainty. 

**Integration can be completed in under a week, with no upfront costs and no operational overhead beyond the subscription fee.**


## Why Proof-of-Reserves Matters

| **Challenge**                                                | **Primus Solution**                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Lack of trust in off-chain assets or custodian balances      | zkTLS attests the authenticity and provenance of off-chain data while institutions retain full control of all private credentials. |
| Infrequent or manual reserve disclosure                 | Automated, high-frequency PoR refreshing with customizable verification intervals. |
| Privacy concerns when disclosing account-level balances       | zkVM enables privacy-preserving aggregation with selective disclosure. |
| Fragmented on-chain and off-chain reserve data | Primus aggregates all sources into one consolidated, verifiable reserve total.|



## Product Highlights

**1. Intuitive and Simple to Operate**

Primus provides a user-friendly **PoR Admin Console** that allows institutions to configure both on-chain and off-chain assets, define disclosure preferences, and determine exactly what information becomes publicly visible.

[dashboard](./pics/dashboard.png)

Each institution receives a dedicated **public Explorer page**, automatically generated based on your configuration. This page offers users, auditors, and partners a transparent, continuously updated view of your verified reserves.

[frontend](./pics/frontend.png)

**2. One Integration, Zero Maintenance**

Primus abstracts away all external integrations and ongoing operational work.

A single integration grants access to all supported on-chain networks, off-chain data sources, and the full verification pipeline—including zkTLS attestation, secure computation (TEE), zkVM proving, node infrastructure, and API integrations.


## Workflow

**Step1. Create a project in the Admin Console**

Define your organization's identity and configure a showcase URL under the unified domain format 'por.primuslabs.xyz/....'. Each project can specify its own unique path.

**Step 2. Configure your reserve sources and disclose preferences**

In this step, you can add the on-chain and off-chain assets you want to include in your Proof-of-Reserves.

For on-chain reserves, you can manage wallet addresses and token disclosure scopes. Each wallet requires a one-time micro-transaction challenge to verify ownership. 

For off-chain reserves, Primus will provide a customized PoR program based on your data requirements.

You can also optionally configure supply details if you wish to show the reserve-backing ratio, and define alert thresholds to receive email notifications when reserves fall below your desired conditions.

**Step 3. Preview the Explorer page**

Review how your PoR will appear publicly, directly in the Admin Console.

**Step 4. Publish the project**

Publish the project and share the showcase URL with users, auditors, and partners.



## Pricing

Primus PoR follows a simple, transparent pricing model.

We provide a **7-day free publishing period**, allowing you to create and publish a PoR project at no cost. After the 7-day trial ends, continued public hosting requires a **monthly subscription**.

You can subscribe directly in the Admin Console or contact our team for assistance.



## Technical Overview

Primus combines zkTLS, TEE, and zkVM in a decentralized proving network to enable authentic and privacy-preserving verification of off-chain reserves.

**zkTLS for Authentic Off-Chain Data**

A custom PoR program runs in your own environment, using zkTLS to retrieve real-time balances from sources such as CEX accounts. zkTLS proves the data comes from the legitimate API endpoint over a trusted TLS session—without exposing API keys or raw account details.

**TEE for Secure Data Handling**

Retrieved data is processed inside a Trusted Execution Environment (TEE), ensuring confidentiality during computation and establishing a secure channel to the proving network.

**zkVM for Verifiable Aggregation**

Through the TEE, committed data is sent to a zkVM network for aggregation and final computation. A zero-knowledge proof guarantees that the disclosed reserve value is correctly derived from authentic balances, while all sensitive information remains private.



## Examples

Below are code samples covering the three major components involved in an off-chain Proof-of-Reserves integration:

1. Framework Intro: [https://github.com/primus-labs/DVC-Intro](https://github.com/primus-labs/DVC-Intro)

2. Custom PoR Program (deployed in your environment): [https://github.com/primus-labs/dvc-client](https://github.com/primus-labs/dvc-client)
  
3. Primus DVC Service (the server side): [https://github.com/primus-labs/dvc-server](https://github.com/primus-labs/dvc-server)

4. zkVM Program: [https://github.com/primus-labs/DVC-Succinct](https://github.com/primus-labs/DVC-Succinct)

