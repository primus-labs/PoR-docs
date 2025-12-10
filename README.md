# Proof-of-Reserves Product Introduction

## Overview

Primus enables verifiable transparency over institutional reserves through a Data Verification and Computation (DVC) architecture. By combining **zkTLS** for authenticated off-chain data retrieval with **zkVM/TEE** for verifiable computation, Primus delivers a mature, ready-to-use **Proof-of-Reserves** (PoR) solution. Institutions can securely aggregate and verify both on-chain and off-chain reserves, and continuously present their real-time financial positions with cryptographic certainty.

## Main Features & Components

The Proof-of-Reserves solution consists of two main components:

- **Admin Console**: Institutions can create projects, configure data sources, and manage what to disclose publicly.

- **Public Explorer**: A public-facing interface for transparent display of verified reserves and proofs. All details disclosed are set under the Admin Console.

#### Project Setup Workflow - Admin Console

1. **Basic Information**
- Configure the public-facing URL. Projects are published under a unified domain format:
  por.primuslabs.xyz/... and each project can define its own path.
- Set notification emails to receive alerts when reserves fall below pre-set conditions.

2. **On-chain Reserves**
- After configuring verified wallet addresses and token scopes, Primus automatically retrieves and aggregates the latest balances from token contracts **at a scheduled frequency** (e.g., every 30 minutes).
- **Wallet verification method**
  	- add wallet addresses and complete ownership verification through a random micro-transaction challenge.
	- once completed and confirmed the transaction, wallet ownership is verified.
- **Reserves Display flexibility**
	- choose which token balances to display publicly
	- multiple wallet balances can be aggregated into a single reserve figure
- **Supported blockchains**
	- **EVM**: Ethereum, Binance Chain, Polygon, Avalanche
	- **Layer-2**: Arbitrum, Optimism, Base
	- **Solana**


3. **Off-chain Reserves**
- Using a custom PoR program (combining zkTLS + zkVM), Primus securely retrieves and computes balances from off-chain sources (e.g., CEX accounts or other financial accounts) with **privacy-preserving guarantees**.
- **Setup process**
	- Primus develops the required zkTLS + zkVM program tailored to customer needs.
	- The program is deployed on customer-owned servers, where private credentials (e.g., exchange read-only API keys) are configured.
	- The Admin Console monitors the program status and displays the data source details  and verified reserve totals.

4. **Supply Details (Optional)**
- Configure token contract addresses to trace the total token supply amount for those who want to disclose the reserves backing ratio.
- Supports aggregating supply from **multiple contracts** of the same token.

5. **Additional Settings**
- Configure **price-based or percentage-based** alert thresholds. Email notifications will be triggered when reserves fall below defined conditions.
- Users may choose to publicly disclose **only on-chain or only off-chain** reserves if needed.

## Technical Overview

Primus enables off-chain reserve verification with end-to-end cryptographic guarantees by combining zkTLS, TEE, and zkVM-based verifiable computation on a decentralized proving network.

1. **zkTLS for Authenticated Data Retrieval**

Institutions deploy a custom PoR program in their own environment, where zkTLS is used to retrieve real-time asset balances from off-chain sources such as CEXs.

zkTLS produces a proof that:
- the data is fetched from the legitimate API endpoint
- over a trusted TLS session
- without exposing API credentials or raw account details

This off-chain data source, along with the hashed asset details, is validated by Attestor nodes in the Primus Network and then propagated to the proving layer.

2. **TEE-Assisted Secure Data Processing**

The retrieved off-chain data is additionally processed inside a Trusted Execution Environment (TEE), ensuring:
- data confidentiality throughout computation
- secure communication to the decentralized proving network

The TEE establishes a secure channel to the verifiable computation backend.

3. **zkVM for Verifiable Aggregation of Reserves**

Through the TEE, the committed data is sent to a zkVM network (e.g., powered by Succinct or other partners), where the PoR program performs:
- grouping by token/asset type
- aggregation of balances into a unified reserve value, which could be disclosed to the public

A zero-knowledge proof is then generated to confirm that the publicly disclosed reserve value is correctly computed from authentic, privately held balances — without revealing any sensitive account-level data.

## Sample Code

Below are code samples covering the three major components involved in an off-chain Proof-of-Reserves integration:

1. Custom PoR Program (deployed in the client’s environment): [https://github.com/primus-labs/dvc-client](https://github.com/primus-labs/dvc-client)
  
2. Primus DVC Service: [https://github.com/primus-labs/dvc-server](https://github.com/primus-labs/dvc-server)

3. zkVM Execution Program: [https://github.com/primus-labs/DVC-Succinct](https://github.com/primus-labs/DVC-Succinct)

