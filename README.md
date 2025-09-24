# SatoshiVault - Bitcoin-Native Asset Tokenization Protocol

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stacks](https://img.shields.io/badge/Built%20on-Stacks-5546FF.svg)](https://stacks.org/)
[![Bitcoin](https://img.shields.io/badge/Secured%20by-Bitcoin-F7931A.svg)](https://bitcoin.org/)

> **Built on Stacks. Secured by Bitcoin. Powered by Innovation.**

An advanced smart contract framework that transforms traditional assets into Bitcoin-secured digital securities through fractional tokenization on the Stacks blockchain, enabling institutional-grade liquidity with Nakamoto consensus.

## 🌟 Overview

SatoshiVault represents the next evolution in decentralized finance, where Bitcoin's immutable ledger meets sophisticated asset management. This protocol empowers users to tokenize real-world assets—from Manhattan real estate to rare art collections—creating liquid markets backed by Bitcoin's century-proven security model.

Through automated compliance systems and transparent governance, SatoshiVault bridges traditional wealth preservation with DeFi innovation, making previously illiquid investments accessible to a global audience while maintaining the regulatory standards expected by institutional capital.

## 🏗️ Architecture Highlights

- **Bitcoin-Anchored Registry**: Immutable asset records with cryptographic proof
- **Micro-Investment Engine**: Fractional ownership down to satoshi-level precision
- **Automated Compliance**: Self-executing KYC/AML with tiered verification
- **Stakeholder Democracy**: Token-weighted governance with transparent voting
- **Yield Distribution**: Real-time dividend streams proportional to ownership
- **Oracle Integration**: Decentralized price feeds for accurate asset valuation
- **Institutional Framework**: Enterprise-ready infrastructure for regulated markets

## 🚀 Features

### Asset Tokenization

- **Fractional Ownership**: Split assets into 100,000 fractional units for precise ownership
- **Valuation Boundaries**: Support assets from $1K to $1T institutional ceiling
- **Metadata Management**: Immutable asset records with URI-based metadata
- **Lock Mechanisms**: Secure asset states during critical operations

### Compliance & Verification

- **Tiered KYC/AML**: 5-tier verification system for regulatory compliance
- **Time-bound Verification**: Automatic expiration with ~1 year validity
- **Admin Controls**: Protocol-level compliance enforcement
- **Institutional Standards**: Enterprise-grade verification processes

### Governance System

- **Democratic Proposals**: Token-weighted voting on asset management
- **Quorum Requirements**: Configurable participation thresholds
- **Time-bound Voting**: 2-24 hour voting periods for efficient decision-making
- **Stake Requirements**: 10% minimum ownership for proposal creation
- **Transparent Tallying**: Real-time vote counting and results

### Yield Distribution

- **Proportional Rewards**: Dividend distribution based on ownership percentage
- **Claim Tracking**: Comprehensive record of yield claims
- **Real-time Calculation**: Dynamic yield computation with pending amounts
- **Automated Distribution**: Self-executing dividend payments

### Oracle Integration

- **Price Feeds**: Decentralized asset valuation with confidence scores
- **Multi-decimal Support**: Flexible precision for different asset classes
- **Timestamp Validation**: Fresh data requirements for accurate pricing
- **Oracle Management**: Admin-controlled price feed updates

## 📋 Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) - Stacks development environment
- [Node.js](https://nodejs.org/) (v16 or higher)
- [Stacks CLI](https://docs.stacks.co/references/stacks-cli)

## 🛠️ Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/emeka-ebuka/satoshi-vault.git
   cd satoshi-vault
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Initialize Clarinet**

   ```bash
   clarinet check
   ```

## 🧪 Testing

Run the comprehensive test suite:

```bash
# Check contract syntax
clarinet check

# Run unit tests
npm test

# Run with coverage
npm run test:coverage
```

## 📖 Usage Examples

### Creating a Tokenized Asset

```clarity
;; Create a real estate asset worth $500,000
(contract-call? .satoshi-vault create-tokenized-asset
  "ipfs://QmYourMetadataHash"  ;; Asset metadata URI
  u500000000000               ;; $500K in micro-STX
)
```

### User Compliance Verification

```clarity
;; Verify a user with Tier 3 compliance for 1 year
(contract-call? .satoshi-vault verify-user-compliance
  'SP1INVESTOR123...          ;; User principal
  u3                          ;; Tier 3 verification
  u52560                      ;; ~1 year validity
)
```

### Creating Governance Proposals

```clarity
;; Propose asset management changes
(contract-call? .satoshi-vault create-proposal
  "Increase dividend distribution rate"  ;; Proposal title
  u1                                     ;; Target asset ID
  u72                                    ;; 12-hour voting period
  u50000                                 ;; 50% quorum requirement
)
```

### Claiming Yield

```clarity
;; Claim pending dividends for an asset
(contract-call? .satoshi-vault claim-asset-yield u1)
```

## 🔒 Security Features

### Access Control

- **Protocol Admin**: Centralized admin controls for critical operations
- **Compliance Gates**: KYC/AML requirements for sensitive functions
- **Time Locks**: Expiring verification and voting periods
- **Balance Checks**: Insufficient balance protection

### Validation Layer

- **Input Sanitization**: Comprehensive parameter validation
- **Range Checks**: Boundary validation for all numeric inputs
- **State Verification**: Asset existence and status validation
- **Duplicate Prevention**: Vote and asset creation safeguards

## 📊 Protocol Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| `MAX_ASSET_WORTH` | 1T micro-STX | Maximum asset valuation |
| `MIN_ASSET_WORTH` | 1K micro-STX | Minimum asset valuation |
| `MAX_VOTE_DURATION` | 144 blocks | 24-hour maximum voting |
| `MIN_VOTE_DURATION` | 12 blocks | 2-hour minimum voting |
| `FRACTIONAL_UNITS` | 100,000 | High-precision ownership |
| `MIN_GOVERNANCE_STAKE` | 10,000 | 10% minimum for proposals |
| `MAX_VERIFICATION_TIER` | 5 | Institutional grade |
| `VERIFICATION_VALIDITY` | 52,560 blocks | ~1 year validity |

## 🏛️ Contract Architecture

### Core Data Structures

#### Asset Repository

```clarity
digital-assets: {
  asset-id -> {
    owner: principal,
    metadata-uri: string-ascii,
    current-valuation: uint,
    is-locked: bool,
    created-at: uint,
    last-price-update: uint,
    total-dividends: uint,
    active-status: bool
  }
}
```

#### Ownership Ledger

```clarity
token-holdings: {
  (holder, asset-id) -> {
    balance: uint,
    last-interaction: uint
  }
}
```

#### Governance System

```clarity
dao-proposals: {
  proposal-id -> {
    title: string-ascii,
    asset-target: uint,
    start-block: uint,
    end-block: uint,
    executed: bool,
    yes-votes: uint,
    no-votes: uint,
    quorum-needed: uint,
    proposer: principal
  }
}
```

## 📈 Query Interface

### Asset Queries

- `get-digital-asset(asset-id)` - Retrieve asset information
- `get-holder-balance(holder, asset-id)` - Get token holdings
- `get-protocol-stats()` - Protocol-wide statistics

### Governance Queries

- `get-dao-proposal(proposal-id)` - Proposal details
- `get-proposal-results(proposal-id)` - Voting results and statistics
- `get-user-vote(proposal-id, voter)` - Individual vote records

### Compliance Queries

- `get-user-verification(user)` - User verification status
- `user-has-valid-compliance?(user)` - Compliance validity check

### Yield Queries

- `get-claimed-yield(asset-id, claimant)` - Claimed dividend amounts
- `calculate-pending-yield(asset-id, holder)` - Pending yield calculation

## 🌐 Deployment

### Testnet Deployment

```bash
# Deploy to Stacks testnet
clarinet deployments apply --plan devnet

# Verify deployment
clarinet console
```

### Mainnet Deployment

```bash
# Configure mainnet settings
clarinet deployments generate --plan mainnet

# Deploy to mainnet
clarinet deployments apply --plan mainnet
```

## 📚 API Reference

### Public Functions

#### Asset Management

- `create-tokenized-asset(metadata-uri, asset-valuation)` - Create new tokenized asset
- `update-asset-price(asset-id, new-price, decimals, confidence)` - Update asset pricing
- `inject-dividend-pool(asset-id, dividend-amount)` - Add dividends to asset pool

#### Compliance

- `verify-user-compliance(user, tier-level, validity-blocks)` - Verify user compliance
- `claim-asset-yield(asset-id)` - Claim pending asset yield

#### Governance

- `create-proposal(title, target-asset, voting-period, quorum)` - Create governance proposal
- `submit-vote(proposal-id, vote-yes, vote-weight)` - Submit weighted vote

### Error Codes

| Code | Error | Description |
|------|-------|-------------|
| 100 | `ERR_UNAUTHORIZED` | Unauthorized access attempt |
| 101 | `ERR_ADMIN_ONLY` | Admin-only function called by non-admin |
| 102 | `ERR_COMPLIANCE_REQUIRED` | Compliance verification required |
| 200 | `ERR_ASSET_NOT_EXISTS` | Referenced asset does not exist |
| 201 | `ERR_ASSET_EXISTS` | Asset already exists |
| 202 | `ERR_INSUFFICIENT_BALANCE` | Insufficient token balance |
| 300 | `ERR_VOTE_EXISTS` | Vote already submitted |
| 301 | `ERR_VOTING_CLOSED` | Voting period has ended |
| 400 | `ERR_INVALID_URI` | Invalid metadata URI |
| 401 | `ERR_INVALID_AMOUNT` | Invalid amount specified |

## 🤝 Contributing

We welcome contributions to SatoshiVault! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Write tests for new functionality
4. Ensure all tests pass
5. Submit a pull request

### Code Standards

- Follow Clarity best practices
- Maintain comprehensive test coverage
- Document all public functions
- Use descriptive variable names
- Add inline comments for complex logic

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
