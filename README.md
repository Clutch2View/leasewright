# Leasewright

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Build: SFDX](https://img.shields.io/badge/build-SFDX-blue.svg)
![Compliance: DORA | GDPR](https://img.shields.io/badge/compliance-DORA%20%7C%20GDPR-orange.svg)

> Open source asset leasing modules that can be built on top of the CRM or ERP a lessor already runs. Designed for the user; engineered for the enterprise.

Leasewright is not a new system of record. It is a leasing layer: legal entities, assets, lessees, lease contracts, currency rates and a chart of accounts, defined once as a portable data model and delivered as modules for the platform underneath. The first reference implementation targets Salesforce. The same model is designed to be built on top of other CRMs and ERPs (for example Microsoft Dynamics 365, SAP, NetSuite or Certinia style ERPs running on a CRM) by re-implementing the platform specific layer only.

## Philosophy

> "You've got to start with the customer experience and work backwards to the technology." — Steve Jobs

Leasewright is built for asset leasing operations of any kind: equipment, vehicles, vessels, aircraft or property. We believe enterprise software shouldn't require a training manual. Every screen, every workflow, and every automation is designed with one goal: **it just works.**

### Core Principles

- **Zero-Training UI** — If a leasing operator can't complete a billing run without reading a manual, we've failed
- **3-Click Rule** — No routine task should require more than 3 clicks
- **Leasing Vocabulary** — Asset, Serial Number, Lease Identifier, Lessee, Legal Entity, Utilisation
- **Modular by Default** — Install only the modules you need; on Salesforce these ship as Unlocked Packages
- **Platform Agnostic Model** — The data model and business rules are the product; the CRM or ERP underneath is an implementation detail
- **Configuration over Customization** — Sensible, industry-standard defaults pre-loaded

## How It Fits Your Stack

Most lessors already have a CRM holding customers and deals and an ERP holding the ledger. Leasewright is built to sit between them rather than replace either:

- **On top of your CRM** — assets, lessees and lease contracts become native objects next to your accounts and opportunities, so commercial and contract data live together
- **On top of your ERP** — chart of accounts, currency rates and multi-book entries map to the ledger you already close on, so finance keeps its system of record
- **Across both** — the same lease identifier ties the commercial record in the CRM to the billing and revenue record in the ERP

Each platform gets its own `platforms/<name>` implementation. The Salesforce one lives in `force-app` today and is the reference for the others.

## Quick Start (Salesforce reference implementation)

```bash
# 1. Clone the repository
git clone https://github.com/Clutch2View/leasewright.git
cd leasewright

# 2. Authenticate with your Salesforce DevHub
sf org login web --set-default-dev-hub --alias DevHub

# 3. Create a scratch org
sf org create scratch --definition-file config/project-scratch-def.json --alias Leasewright --duration-days 30 --set-default

# 4. Open the org
sf org open --target-org Leasewright
```

## Architecture

The model is split so that only the bottom layer changes when you build it on a different CRM or ERP:

- **Model Layer** — Platform neutral definitions of the leasing objects, fields and rules
- **Selector Layer** — SOQL queries and data retrieval
- **Domain Layer** — Trigger handlers and record validation
- **UI Layer** — Lightning Web Components (LWC) only

On Salesforce, all modules are packaged as **Unlocked Packages (2GP)** under the `leasewright` namespace. Implementations for other CRMs and ERPs follow the same 4 layer split with their own packaging.

## Enterprise Integrations

Leasewright natively supports the **Microsoft 365 E5** technology stack:

- **Entra ID (Azure AD)** — SSO and JIT provisioning via permission set mapping
- **SharePoint Online** — Heavy document storage via Salesforce Files Connect
- **Microsoft Teams** — Adaptive Cards for Stage 1 & Stage 2 approval workflows
- **Power BI Premium** — Structured OData/REST APIs for analytics
- **Microsoft Purview** — Data classification mapping for enterprise DLP

## Security & Compliance

This system is architected to meet strict European financial standards:

- **DORA** — Immutable audit trails, strict access controls, incident logging
- **GDPR** — Data classification metadata, Shield encryption readiness, Right to be Forgotten flows
- **SAF-T / GoBD** — Multi-book accounting with localized compliance format support

See [SECURITY.md](SECURITY.md) for full details.

## License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

*Built for lessors. Built on top of the CRM or ERP you already own.*
