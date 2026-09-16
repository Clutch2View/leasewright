# Security Policy — Leasewright

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.x     | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

If you discover a security vulnerability within Leasewright, please send an e-mail to **security@leasewright.example** (fictional — replace with your real address before deployment).

**Do not** open a public GitHub issue for security vulnerabilities.

We will acknowledge receipt within **48 hours** and provide a detailed response within **5 business days**.

## Compliance Framework

### DORA (Digital Operational Resilience Act)

Leasewright is architected to support DORA compliance on whichever CRM or ERP it is built on:

- **Immutable Audit Trails** — All financial ledger entries are append-only
- **Strict Access Controls** — Role-based permission sets mapped to Microsoft Entra ID groups
- **Incident Logging** — Structured event logging for ICT-related incidents
- **Third-Party Risk** — Integration monitoring for Microsoft 365 E5 dependencies

### GDPR (General Data Protection Regulation)

- **Data Classification Metadata** — Every custom object includes a `Data_Classification__c` field
- **PII Tagging** — Fields containing personal data are tagged for Shield Platform Encryption
- **Right to be Forgotten** — Pre-built flows for data subject erasure requests
- **Data Processing Records** — Automated record-keeping of processing activities
- **Consent Management** — Configurable consent tracking per data subject

### Financial Reporting Standards

- **SAF-T** — Standard Audit File for Tax (EU)
- **GoBD** — German fiscal compliance (Grundsätze zur ordnungsmäßigen Führung und Aufbewahrung von Büchern)
- **Multi-Book Accounting** — Parallel ledgers for IFRS 16 and local GAAP

## Encryption

- All PII fields support **Salesforce Shield Platform Encryption**
- Data at rest and in transit is encrypted per Salesforce platform standards
- Microsoft Purview sensitivity labels are mapped to Salesforce data classification

## Authentication

- **SSO** via Microsoft Entra ID (Azure AD) with SAML 2.0
- **JIT Provisioning** — Users are automatically provisioned with correct permission sets
- **MFA** — Enforced via Entra ID Conditional Access policies

---

*This security policy applies to the Leasewright open-source project. Organizations deploying Leasewright must conduct their own security assessments and adapt this policy to their specific regulatory requirements.*
