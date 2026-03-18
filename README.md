# OpenCharities — Stablecoin-Powered Charity Platform

## Vision

A transparent, low-cost charity platform where **every euro is traceable on-chain** — from donor to spend.

Donors contribute via familiar payment methods (card, bank transfer, iDEAL, crypto). All funds are auto-converted to EUR stablecoins and held in a foundation wallet. Initiative organizers receive stablecoin disbursements and can spend via Visa/Mastercard card or withdraw to their personal IBAN.

## Key Value Propositions

1. **Radical transparency** — every disbursement is an on-chain transaction with a public proof
2. **Low fees** — Base L2 gas costs are fractions of a cent vs. traditional intermediary chains
3. **Real-time settlement** — no T+2 banking delays for fund disbursements
4. **Programmable spending rules** — enforced at wallet level, not just policy
5. **Global reach** — stablecoins enable cross-border disbursement without SWIFT fees

## Fund Flow

```
DONATIONS IN
─────────────
Donor ──┬── Card (Visa/MC)
        ├── Bank Transfer (SEPA)
        ├── iDEAL
        └── Crypto/Stablecoin
              │
              ▼
        Foundation IBAN (NL/EU)
              │
              ▼
        Auto-Convert (Fiat → EUR stablecoin)
              │
              ▼
        Foundation Wallet (EURC on Base)

FUNDS OUT
─────────
Foundation Wallet
      │
      ▼
Initiative Organizer Wallet
      │
      ├──→ Spend via Card (Visa/MC)
      └──→ Withdraw to IBAN
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Java 25 |
| Framework | Spring Boot 4 |
| Architecture | Hexagonal (Ports & Adapters) |
| Orchestration | Temporal |
| Messaging | Kafka (AWS MSK) |
| Database | PostgreSQL (AWS RDS) — per service |
| Cache | Redis (AWS ElastiCache) |
| Blockchain | Base L2 (Coinbase) |
| Stablecoin | EURC (Circle — MiCA compliant) |
| Custody | Fireblocks (MPC) |
| Container | AWS EKS (Kubernetes) |
| Region | eu-west-1 (Ireland) / eu-central-1 (Frankfurt) |

## Documentation

| Document | Path |
|----------|------|
| System Overview | [docs/architecture/00-system-overview.md](docs/architecture/00-system-overview.md) |
| Architecture Decisions | [docs/architecture/01-architecture-decisions.md](docs/architecture/01-architecture-decisions.md) |
| Infrastructure | [docs/architecture/02-infrastructure.md](docs/architecture/02-infrastructure.md) |
| Service Index | [docs/services/00-service-index.md](docs/services/00-service-index.md) |
| Service Specs (S01–S12) | [docs/services/](docs/services/) |
| Workflow Specs | [docs/workflows/](docs/workflows/) |
| Data Model | [docs/data-model/](docs/data-model/) |
| Regulatory Compliance | [docs/regulatory/](docs/regulatory/) |

## Services (12)

| # | Service | Purpose |
|---|---------|---------|
| S01 | Donor Portal & API Gateway | Public donation UX + API gateway |
| S02 | Donation Orchestrator | End-to-end donation lifecycle (Temporal) |
| S03 | Payment Acceptance | Multi-rail fiat payment ingestion |
| S04 | Fiat-to-Stablecoin Conversion | Auto-convert EUR → EURC |
| S05 | Wallet & Custody | On-chain wallet management (Fireblocks) |
| S06 | Fund Distribution | Foundation → organizer disbursement |
| S07 | Card Issuance & Spending | Crypto-backed Visa/MC cards |
| S08 | Off-Ramp | Stablecoin → IBAN withdrawal |
| S09 | Compliance & KYC/AML | Regulatory compliance engine |
| S10 | Transparency & Reporting | Public on-chain dashboard + reporting |
| S11 | Notification | Multi-channel notifications |
| S12 | Ledger & Accounting | Double-entry bookkeeping |

## Jurisdiction

- **Primary**: Netherlands (NL) / European Union
- **Charity structure**: Dutch Stichting (Foundation) with ANBI status
- **Regulatory frameworks**: MiCA, AMLD6, PSD2, DORA, GDPR
