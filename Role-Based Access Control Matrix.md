| Document ID: | SSS-DOC-ISMS-013 |
| :---- | :---- |
| **Document Title:** | **Role-Based Access Control Matrix** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-15\] |
| **Reference:** | \[ISO 27001:2022 controls A.5.15, A.5.16, A.8.2, A.8.3\]|
| **Owner:** | \[ISMS Manager\] |
| **Approved By:** | \[ISMS Owner\] |
| **Review Cycle:** | \[Annual, or after any P1/P2 incident\] | 


| **Role / Department**                    | **Business Function**               | **Key Systems & Assets Accessed**                                                                               | **Access Type (Read / Write / Admin)** | **Access Justification**                         | **Privileged Account? (Y/N)** | **Control Mapping (ISO 27001:2022)** | **Approval Authority** |
| :--------------------------------------- | :---------------------------------- | :-------------------------------------------------------------------------------------------------------------- | :------------------------------------- | :----------------------------------------------- | :---------------------------: | :----------------------------------- | :--------------------- |
| **CEO**                                  | Executive management                | Quarterly Financial Reports (A-DAT-004), Board Docs, HR Summaries,                                               | Read / Approve                        | Governance, strategy, decision-making            |               N               | A.5.4, A.5.36                        | Board Director         |
| **CTO**                                  | Technical leadership / Architecture | SoSecureSwitch Transaction Switch (A-SW-001), CI/CD Pipeline (A-SRV-001), Source Code Repo (A-DAT-002), DR Runbooks | Read / Approve                     | Design authority / security oversight            |               Y               | A.5.15, A.8.2, A.8.32                | CEO                    |
| **Deputy CEO / Board Director**          | Oversight & compliance              | Financial Reports, Audit Logs / Compliance Register                                                             | Read                                   | Oversight / management review                    |               N               | A.5.4, A.5.35                        | CEO                    |
| **ISMS Manager**                         | ISMS management / risk oversight    | Risk Register, RTP, SoA, SIEM (A-SRV-004), IAM (A-SRV-005), Logs                                                | Read / Write / Admin                   | Security governance and audit readiness          |               Y               | A.5.2, A.5.15, A.8.15, A.8.16        | CTO                    |
| **Security Engineer**                    | Monitoring / incident response      | SIEM (A-SRV-004), HSM (A-HW-001), Firewalls (A-HW-002), Load Balancers (A-HW-003)                               | Read / Write / Admin                   | Security operations and incident handling        |               Y               | A.8.7, A.8.8, A.8.15, A.8.24         | ISMS Manager           |
| **IT Ops Lead**                          | Infrastructure operations           | Email (A-SRV-002), IAM (A-SRV-005), Network (A-HW-002), Backups (A-SRV-007)                                     | Read / Write / Admin                   | System availability & identity services          |               Y               | A.8.2, A.8.16, A.8.20                | CTO                    |
| **System Administrator**                 | Day-to-day system admin             | DC Infra (A-FCY-001), Servers, Network Devices (A-HW-004)                                                       | Write / Admin                          | Operational maintenance / incident response      |               Y               | A.8.2, A.8.9, A.8.13                 | IT Ops Lead            |
| **DBA**                                  | Database administration             | Transaction Database (A-DAT-001), Backup System (A-SRV-007)                                                     | Write / Admin                          | Ensure data integrity and availability           |               Y               | A.8.8, A.8.13, A.8.32                | IT Ops Lead            |
| **Dev Manager**                          | Development lead                    | Source Code Repo (A-DAT-002), Build Servers (A-SRV-003), CI/CD Pipeline (A-SRV-001),Web Back-Office App (A-SW-002)| Read / Write / Admin                 | Manage code and release integrity                |               Y               | A.8.4, A.8.25, A.8.29                | CTO                    |
| **Developers (Team)**                    | Application development             | Source Code Repo (A-DAT-002), Dev/Test Environments (A-SW-002)                                                  | Read / Write                           | Implement and maintain SoSecureSwitch software   |               N               | A.8.25, A.8.28                       | Dev Manager            |
| **Build & Release Engineer**             | CI/CD processes                     | CI/CD Pipeline (A-SRV-001), Build Servers (A-SRV-003), HSM (A-HW-001)                                           | Write / Admin                          | Secure builds and artifact signing               |               Y               | A.8.24, A.8.25, A.8.29               | CTO                    |
| **Network & Infra Engineer**             | Network management                  | Firewalls (A-HW-002), Load Balancers (A-HW-003), Bank Connectivity Links (A-SRV-006)                            | Write / Admin                          | Maintain segmentation and link security          |               Y               | A.8.20, A.8.21, A.8.22               | IT Ops Lead            |
| **Backup & DR Coordinator**              | BC/DR operations                    | Backup System (A-SRV-007), DR Site (A-FCY-002)                                                                  | Read / Write / Admin                   | Ensure replication, recovery and test validation |               Y               | A.5.30, A.8.13, A.8.14               | IT Ops Lead            |
| **HR Manager**                           | HR records & personnel              | Employee PII (A-DAT-003), Offboarding Checklist Access                                                          | Read / Write                           | HR processes and GDPR compliance                 |               N               | A.5.34, A.6.1, A.6.5                 | CEO                    |
| **Legal Counsel**                        | Contracts / compliance              | Supplier Contracts (A-DAT-005), NDAs (A-DOC-001)                                                                | Read / Write                           | Legal governance / supplier risk control         |               N               | A.5.19, A.5.20, A.5.31               | CEO                    |
| **Cleaning Service / Facility Security** | Physical security                   | Office / Facility access only                                                                                   | Physical Entry                         | Support physical security of premises            |               N               | A.7.2, A.7.3                         | HR Manager             |


**Key Notes**
Privileged roles (Y) require MFA, PAM session logging, and quarterly access attestation.

Evidence of reviews: Privileged_Access_Attestations_Q4.csv, Access_Review_Reports_Q4.csv.

For each role, removal of access must occur within 8 hours of departure or reassignment.

All access logs are forwarded to SIEM per Logging Policy (A.8.15).