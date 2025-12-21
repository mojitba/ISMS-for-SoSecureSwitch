| Document ID: | SSS-DOC-ISMS-012 |
| :---- | :---- |
| **Document Title:** | **RACI Matrix** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-16\] |
| **Reference:** | \[ISO 27001:2022 Clause 5.3, Annex A.5.2\]|
| **Owner:** | \[ISMS Manager\] |
| **Approved By:** | \[ISMS Owner\] |
| **Review Cycle:** | \[Annual, or after any P1/P2 incident\] | 

RACI Key:

    R \= Responsible (The person/role who does the work)

    A \= Accountable (The one person ultimately answerable for the task)

    C \= Consulted (Provides input, two-way communication)

    I \= Informed (Kept up-to-date, one-way communication)

| ISMS Process | CEO | CTO (ISMS Owner) | ISMS Manager | IT Ops Lead | Dev Manager | Legal Counsel | HR Manager | Security Engineer | SMEs (DBA, Net, Build) |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| 1\. Leadership & Governance |  |  |  |  |  |  |  |  |  |
| Maintain ISMS Policy & Scope | C | A | R | C | C | C | C | C | C |
| Conduct Management Review | A | C | R | C | C | C | C | I | I |
| 2\. Risk Management |  |  |  |  |  |  |  |  |  |
| Perform Risk Assessment | I | A | R | C | C |  |  | C | C |
| Approve Risk Treatment Plan (RTP) | I | A | R | C | C |  |  | C | C |
| Accept High Residual Risk (e.g., R-021) | A | C | R |  |  |  |  |  |  |
| 3\. Control Implementation & Ops |  |  |  |  |  |  |  |  |  |
| Manage Access Control (Lifecycle) |  | A | I | R | C |  | C | I |  |
| Manage Privileged Access (PAM) |  | A | C | R |  |  |  | C | C |
| Manage Cryptography & HSMs |  | A | C | C |  |  |  | R |  |
| Manage Secure Development (SDLC) |  | A | C |  | R |  |  | C | R (Build) |
| Manage Change Control (CAB) |  | A | C | R | C |  |  | C | C |
| Manage Backup, Restore & DR |  | A | I | R | C |  |  |  | R (Backup) |
| 4\. Incident & Compliance |  |  |  |  |  |  |  |  |  |
| Respond to Security Incidents (P1) | I | C | A | R | C | C |  | R | R |
| Manage Supplier Security | I | A | C | R |  | R (Contracts) |  |  |  |
| Manage Security Awareness Training |  | A | R (Content) |  |  | C | R (Logistics) |  |  |
| 5\. Assurance |  |  |  |  |  |  |  |  |  |
| Conduct Internal Audits | A | I | I | I | I | I | I | I | I |
| Internal Audit Lead (Deputy CEO) | (I) | (C) | (C) | (C) | (C) | (C) | (C) | (C) | (C) |

