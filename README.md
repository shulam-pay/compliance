# Shulam Compliance

KYT/AML/OFAC screening service for transaction monitoring and regulatory compliance.

## Overview

Real-time transaction screening to ensure all payments comply with sanctions requirements and AML regulations.

## Features

- **KYT (Know Your Transaction)** — Screen every transaction before settlement
- **OFAC SDN List** — Block sanctioned wallet addresses
- **PEP Screening** — Flag politically exposed persons
- **Velocity Checks** — Detect unusual transaction patterns
- **SAR Generation** — Suspicious Activity Report automation

## Integrations

| Provider | Purpose | Status |
|----------|---------|--------|
| Chainalysis KYT | Transaction screening | 🔜 Planned |
| TRM Labs | Wallet risk scoring | 🔜 Planned |
| Elliptic | Sanctions screening | 🔜 Planned |

## Architecture

```
src/
├── screening/
│   ├── ofac.ts           # OFAC SDN list checks
│   ├── chainalysis.ts    # Chainalysis KYT integration
│   └── trm.ts            # TRM Labs integration
├── monitoring/
│   ├── velocity.ts       # Transaction velocity rules
│   ├── patterns.ts       # Pattern detection
│   └── alerts.ts         # Alert generation
├── reporting/
│   ├── sar.ts            # SAR generation
│   └── ctr.ts            # CTR generation (if needed)
└── rules/
    ├── engine.ts         # Rules engine
    └── definitions.ts    # Rule definitions
```

## Screening Flow

```
Transaction Request
        ↓
   OFAC Check → BLOCK if sanctioned
        ↓
   KYT Score → REVIEW if high risk
        ↓
   Velocity Check → FLAG if unusual
        ↓
   APPROVE → Proceed to settlement
```

## Risk Thresholds

| Risk Level | Action | KYT Score |
|------------|--------|-----------|
| Low | Auto-approve | 0-30 |
| Medium | Approve + log | 31-60 |
| High | Manual review | 61-80 |
| Severe | Auto-block | 81-100 |

## Environment Variables

```
CHAINALYSIS_API_KEY=
TRM_API_KEY=
OFAC_UPDATE_INTERVAL=86400
ALERT_WEBHOOK_URL=
COMPLIANCE_OFFICER_EMAIL=
```

## Getting Started

```bash
# Install dependencies
npm install

# Download latest OFAC list
npm run update-ofac

# Run service
npm run dev

# Run tests
npm test
```

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/screen` | POST | Screen a transaction |
| `/wallet/:address` | GET | Get wallet risk score |
| `/alerts` | GET | List active alerts |
| `/alerts/:id/resolve` | POST | Resolve an alert |

## Compliance Documentation

Internal policies (not in repo):
- AML/BSA Policy
- SAR Filing Procedures
- Transaction Monitoring Rules
- Compliance Officer Designation

## License

Proprietary — Shulam, Inc.
