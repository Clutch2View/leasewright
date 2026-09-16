# Platform Implementations

Leasewright defines the leasing data model once. Only the platform specific layer changes when it is built on top of a different CRM or ERP.

| Platform | Status | Location |
| --- | --- | --- |
| Salesforce | Reference implementation | `force-app` at the repository root |
| Microsoft Dynamics 365 | Open for contribution | `platforms/dynamics-365` |
| SAP | Open for contribution | `platforms/sap` |
| NetSuite | Open for contribution | `platforms/netsuite` |

To add a platform, create a folder here containing the objects, rules and UI for that platform and map each one back to the model in the root README.
