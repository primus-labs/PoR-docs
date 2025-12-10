# Proof-of-Reserves Product Introduction

## Overview

Primus enables verifiable transparency over institutional reserves through a Data Verification and Computation (DVC) architecture. By combining **zkTLS** for authenticated off-chain data retrieval with **zkVM/TEE** for verifiable computation, Primus delivers a mature, ready-to-use **Proof-of-Reserves** (PoR) solution. Institutions can securely aggregate and verify both on-chain and off-chain reserves, and continuously present their real-time financial positions with cryptographic certainty.

## Main Features & Components

The Proof-of-Reserves solution consists of two main components:

- **Admin Console** — Institutions can create projects, configure data sources and manage what to disclose publicly.

- **Public Explorer** — A public-facing interface for transparent display of verified reserves and  proofs.

#### Project Setup Workflow - Admin Console

1. **Basic Information**
- Configure the public-facing URL. Projects are published under a unified domain format:
  por.primuslabs.xyz/... and each project can define its own path.
- Set notification emails to receive alerts when reserves fall below pre-set conditions.

2. **Supply Details (Optional)**
- Configure token contract addresses to trace the total token supply amount.
- Supports aggregating supply from **multiple contracts** of the same token.

3. **On-chain Reserves**
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

4. **Off-chain Reserves**
- Using custom zkTLS + zkVM programs, Primus securely retrieves and computes balances from off-chain sources (e.g., CEX accounts or other financial accounts) with **privacy-preserving guarantees**.
- **Setup process**
  - Primus develops the required zkTLS + zkVM program tailored to customer needs.
  - The program is deployed on customer-owned servers, where private credentials (e.g., exchange read-only API keys) are configured.
  - The Admin Console monitors the program status and displays the data source details  and verified reserve totals.

5. **Additional Settings**
- Configure **price-based or percentage-based** alert thresholds: Email notifications will be triggered when reserves fall below defined conditions.
- Users may choose to publicly disclose **only on-chain or only off-chain** reserves if needed.


## Code Example

