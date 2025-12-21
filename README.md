<p align="center">
  <h1>SoSecureSwitch - ISMS Documentation</h1>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ISMS_Standard-ISO_27001%3A2022-blue" alt="ISO 27001:2022">
  <img src="https://img.shields.io/badge/Compliance-PCI_DSS_Context-orange" alt="PCI DSS">
  <img src="https://img.shields.io/badge/Environment-On_Premise-lightgrey" alt="On-Premise">
  <img src="https://img.shields.io/badge/Status-Approved_Internal-brightgreen" alt="Status: Approved">
</p>
<p align="center">
  <img src="https://github.com/mojitba/ISMS-for-SoSecureSwitch/blob/main/images/Logo.png" alt="Logo" width="250" height="450">
</p>

## About This Repository

This repository contains the complete documentation for an Information Security Management System (ISMS) for **SoSecureSwitch Ltd.**, a fictional, high-risk financial vendor providing transaction switching and back-office services.

The documentation is designed to be a practical, auditable example of an ISMS that meets the requirements of **ISO/IEC 27001:2022**. It is built from the ground up, starting with organizational context and flowing through risk assessment to operational procedures.

## ISMS Governance Structure

This ISMS follows the "Plan-Do-Check-Act" (PDCA) model. The documentation is structured around the core clauses and domains of the ISO 27001 standard.

* **ISMS Owner:** CTO (SoSecureSwitch)
* **ISMS Manager:** Information Security Manager
* **Environment:** 100% On-Premise (No cloud in scope)
* **Core Assets:** On-prem transaction switch, HSMs, transaction database, source code (IP).
* **Key Risks:** Transaction modification, source code (IP) theft, key compromise, service outage.

## ISMS Document Inventory

This repository is organized by document ID. The traceability, or continuity of information, flows from Clause 4 (Context) through Risk Assessment (6.1) to the Controls (Annex A).

### Clause 4: Context of the Organization
| Document ID | Document Title | Purpose |
| :--- | :--- | :--- |
| `SSS-DOC-ISMS-001` | Context of the Organization | Defines internal/external issues (e.g., key-person risk, legacy tech, regulatory demands). |
| `SSS-DOC-ISMS-002` | Interested Parties & Requirements | Identifies stakeholders (Banks, Regulators, IP Owner) and their security needs. |
| `SSS-DOC-ISMS-003` | ISMS Scope Statement | Defines the ISMS boundaries (people, processes, tech) and exclusions. Includes the Org Chart. |

### Clause 5: Leadership
| Document ID | Document Title | Purpose |
| :--- | :--- | :--- |
| `SSS-DOC-ISMS-004` | ISMS Policy | Top management's commitment, roles, and measurable security objectives (KPIs). |
| `SSS-DOC-ISMS-010` | Access Control Policy | The core policy for identity, privileged access (PAM), least privilege, and access lifecycle. |
| `SSS-DOC-ISMS-011` | Incident Response Plan | The plan for handling P1-P4 incidents, including the IRT, SLAs, and reporting lines. |
| `SSS-DOC-ISMS-013` | Role-Based Access Control Matrix | Maps specific job titles (from the Org Chart) to the systems and access levels they are granted. |
| `SSS-DOC-ISMS-014` | ISMS Operating Procedures Manual | A master document containing all key SOPs (Change, Backup, DR, Patching, Supplier Mgmt, etc.). |
| `SSS-DOC-ISMS-015` | ISMS Roles and Responsibilities Matrix | Matrix requires top management to ensure that Information Security roles are clearly defined, assigned and communicated. |

### Clause 6: Planning
| Document ID | Document Title | Purpose |
| :--- | :--- | :--- |
| `SSS-DOC-ISMS-005` | Risk Management Methodology | Defines the qualitative 5x5 matrix (L x I) and risk acceptance criteria. |
| `SSS-DOC-ISMS-009` | Statement Of Applicability (SoA) | The master list of all 93 Annex A controls, justifications (Y/N), and implementation status. |

### Clause 8: Operation
| Document ID | Document Title | Purpose |
| :--- | :--- | :--- |
| `SSS-DOC-ISMS-006` | Asset Register | The inventory of all in-scope assets (systems, data, people, facilities), C-I-A scores, and owners. |
| `SSS-DOC-ISMS-007` | Risk Register | The output of the risk assessment, linking assets to 29 specific threats and vulnerabilities. |
| `SSS-DOC-ISMS-008` | Risk Treatment Plan (RTP) | The project plan for mitigating all identified risks, including owners, due dates, and residual risk. |


---

## To Do / Next Steps

This repository contains the "Plan" and "Do" phases of the ISMS. The next steps focus on the "Check" and "Act" phases.

* **Schedule & Run IR Tabletop Exercise:**
    * Simulate a P1 incident (e.g., `R-001 - Transaction Modification`) to test the `Incident Response Plan (SSS-DOC-ISMS-011)`.
    * Produce a `Lessons Learned` report.

* **Finalize & Test BCP/DR:**
    * Formalize the `Business Continuity Plan` (BCP) based on the `DR Procedure` in the manual.
    * Schedule and execute a full `DR Test` (failover to DR site).
    * Produce a `DR Test Report` with RTO/RPO results.

* **Build & Test SIEM Detection Rules:**
    * Implement the detection rules defined in the `Logging & Monitoring Procedure` (in SSS-DOC-ISMS-014).
    * Run "live fire" tests to ensure alerts are generated for risks like `R-020 (AD Compromise)`.

* **Create the Internal Audit Program:**
    * Draft the `Internal Audit Program (Schedule)`.
    * Create `Internal Audit Checklists` based on the SoA.
    * Execute a mock internal audit against a key domain (e.g., Access Control).
    * Produce a formal `Internal Audit Report` with findings.

* **Prepare for Management Review:**
    * Draft the `Management Review Meeting Agenda & Deck`.
    * Compile the ISMS metrics (from the ISMS Policy) into a KPI dashboard.
    * Present the results of the DR test and Internal Audit.

* **Compile Final Evidence Pack:**
    * Create an "Evidence Index" that links every control in the `SoA (SSS-DOC-ISMS-009)` to a specific piece of evidence (log, report, policy, or procedure).

---

## Disclaimer

This is a **fictional** body of work created for educational purposes. It is an example and should not be used as a direct, production-ready ISMS. All company names, roles, assets, and document IDs are part of a learning simulation.
