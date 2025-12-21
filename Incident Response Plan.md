| Document ID: | SSS-DOC-ISMS-011 |
| :---- | :---- |
| **Document Title:** | **Incident Response Plan** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-15\] |
| **Reference:** | \[ISO/IEC 27001:2022 Clause 6.1.2, Annex A.5.24-A.5.28\]|
| **Owner:** | \[ISMS Manager\] |
| **Approved By:** | \[ISMS Owner\] |
| **Review Cycle:** | \[Annual, or after any P1/P2 incident\] | 


# **1\. Purpose**

This plan defines SoSecureSwitch Ltd.’s structured approach for identifying, reporting, responding to, and learning from information security incidents.  
 Its objectives are to:

* Detect incidents early

* Contain and eradicate threats quickly

* Restore services securely

* Meet regulatory and contractual obligations (banks, GDPR, regulators)

* Preserve forensic evidence

* Improve controls after every incident


# **2\. Scope**

This plan applies to:

* All incidents involving any asset in the **ISMS Scope Statement (SSS-DOC-ISMS-003)**

* All SoSecureSwitch employees, contractors, and third-party support

* All production systems, including:

  * Payment switch (A-SW-001)

  * Transaction database (A-DAT-001)

  * HSM/KMS appliances (A-HW-001)

  * Authentication/IAM (A-SRV-005)

  * Build servers & CI/CD (A-SRV-001, A-SRV-003)

  * Back-office interfaces (A-SW-002)

  * Network perimeter devices and bank connectivity



# **3\. Definitions (Mandatory ISO Requirement)**

## **3.1 Security Event**

Any observable system or network occurrence **that may indicate a potential security issue** but has not been confirmed.

Examples:

* SIEM alerts

* Multiple failed login attempts

* Suspicious outbound traffic

* Malware detection on an endpoint

## **3.2 Security Incident**

A **confirmed** event that results in (or has strong evidence of):

* Unauthorized access

* Loss of confidentiality, integrity, or availability

* Disruption of services

* Compromise of keys or credentials

* Data exfiltration

* Fraud or attempted fraud

## **3.3 Major Incident (P1/P2)**

Any incident with **Impact ≥ 4 (Major/Catastrophic)** or affecting:

* Transaction switching

* Transaction database

* HSMs

* Authentication / IAM

* Banks connectivity links

* Source code repository



# **4\. Incident Response Team (IRT)**

| Role | Responsibilities |
| ----- | ----- |
| **IRT Lead – ISMS Manager** | Overall command, classification, regulatory communication support, report approval |
| **Technical Lead – IT Ops Lead** | Directs technical containment, eradication, and recovery |
| **Security Engineer** | Forensics, SIEM analysis, malware analysis, HSM audit logs |
| **DBA** | Database integrity validation, recovery, replication |
| **Dev Manager / Build & Release Engineer** | CI/CD, code integrity, artifact signing |
| **Network & Infrastructure Engineer** | Firewall actions, segmentation, link isolation |
| **Backup & DR Coordinator** | Restore operations, DR failover |
| **CTO** | Executive decisions, authorization for P1 actions |
| **CEO** | Customer/regulator notifications |
| **Legal Counsel** | Regulatory and contractual obligations review |

# **5\. Classification & Escalation Criteria**


## **5.1 When an event becomes an incident**

A security **event** becomes an **incident** when ANY of the following is true:

* Unauthorized access confirmed

* Confidential data accessed or exfiltrated

* Malware infection confirmed

* System integrity compromised

* Payment transaction integrity impacted

* Signed artifact integrity failure

* Authentication/SSO compromise

* Ransomware detected

* HSM/KMS anomalies

* Regulator/bank SLA disruption likely


## **5.2 Incident Prioritization (P1–P4)**


| Priority | Definition | Examples | SLA |
| ----- | ----- | ----- | ----- |
| **P1 Critical** | Catastrophic impact (Impact=5) | R-001, R-002, R-003, R-020, R-021 | Detect \<30 min, Contain \<1h, Recover \<4h |
| **P2 High** | Major impact (Impact=4) | R-004, R-005 | Detect \<1h, Contain \<4h |
| **P3 Medium** | Moderate impact (Impact=3) | Developer malware, R-013 | Detect \<24h |
| **P4 Low** | Minor impact | Low-impact malware, scans | Best effort |

# **6\. Incident Response Process (PICERL)**


## **Phase 1-Preparation**

SoSecureSwitch maintains:

* SIEM ingesting logs from all critical assets

* Jump bag with approved tools (FTK Imager, Sysinternals, tcpdump)

* Privileged Access Monitoring (PAM)

* Forensic workstation

* Contacts for banks and regulators

* Quarterly IR tabletop exercises

* Annual simulation of P1 incident


## **Phase 2-Identification & Triage**

1. **Detect incident** via SIEM, monitoring, or user reports

2. **Record event** in `IR_Ticket_<ID>.md`

3. **IRT Lead classifies** P1–P4

4. **Incident bridge** opened for P1/P2

5. **Check linked risks** from Risk Register (R-XXX)

**Evidence required:**

* SIEM alert (`/evidence/IR/alerts/`)

* Event logs

* Screenshots

* Reporter notes


## **Phase 3-Containment**

### **Short-term containment**

* Isolate affected machines

* Disable affected accounts

* Block malicious IP/domains

* Pause transaction switch (P1)

* Disable compromised bank link

### **Long-term containment**

* Review segmentation

* Validate isolation by checking firewall logs

**Evidence required:**

* Firewall actions

* Access disable logs

* Isolation confirmation



## **Phase 4-Eradication**

* Identify root cause

* Remove malware/persistence

* Patch vulnerabilities

* Re-image compromised servers using trusted baseline

* Rotate exposed credentials or keys

* Remove malicious artifacts from CI/CD pipeline

* Validate DB integrity

**Evidence required:**

* Forensic images

* Malware results

* Fix logs


## **Phase 5-Recovery**

* Restore services using **validated, clean** systems

* Validate integrity before reconnecting

* Monitor for recurrence for minimum **48 hours**

* Re-enable production traffic only after Technical Lead approval

**Evidence required:**

* Recovery logs

* Validation test results

* Monitoring screenshots



## **Phase 6-Lessons Learned**

Performed within **5 business days** for P1/P2:

* Executive summary

* Timeline

* Impact analysis

* Root cause

* Corrective actions

* Evidence of fixes

* Required updates to SOA, RTP, procedures

Corrective actions tracked in:  
 `Corrective_Action_Log.xlsx`


# **7\. Evidence Requirements (Mandatory ISO Section)**


| Phase | Evidence Required | Location |
| ----- | ----- | ----- |
| Identification | SIEM alert, event record | `/evidence/IR/alerts/` |
| Containment | Logs, screenshots, commands, IP blocks | `/evidence/IR/containment/` |
| Eradication | Forensic images, patched systems, removed malware | `/evidence/IR/eradication/` |
| Recovery | Service validation, DB checks, switch health | `/evidence/IR/recovery/` |
| Lessons Learned | Post-incident report, RCA | `/evidence/IR/reports/` |

# **8\. External Communications Requirements**

Only the **CEO or CTO** may contact:

* Banks

* Regulators

* Law enforcement

* Media

**No employee** may make external statements.

Contractual obligations with banks require reporting:  
 **Within 1 hour** of confirmed P1 incident affecting transactions.

Legal Counsel must review all breach notifications.



# **9\. Integration with Business Continuity & DR (ISO Required)**

If the incident causes service degradation exceeding:

* RTO

* RPO

* SLA

* Bank contract obligations

→ **Activate Disaster Recovery Plan**

IRT Lead must inform DR Coordinator and CTO.


# **10\. Training & Exercises**

* Annual IR training for all employees (A.6.8)

* Specialized IR training for IRT members

* Quarterly tabletop exercises

* Annual P1 simulated incident test

* Training evidence stored in `/evidence/training/IR/`


# **11\. Incident Metrics & KPIs**

| Metric | Target |
| ----- | ----- |
| Mean Time to Detect (MTTD) | P1 \< 30 min / P2 \< 1 hour |
| Mean Time to Respond (MTTR) | As per SLA table |
| % Incidents with RCA within 5 days | ≥ 90% |
| % Incidents detected by SIEM | ≥ 80% |
| % IR exercises completed | 100% |

# **12\. Reporting & Documentation Templates**

Templates stored under:  
 `/evidence/templates/IR/`

Includes:

* Incident Report Template (ISO 27035-compliant)

* Lessons Learned Template

* RCA form

* Incident Notification Form (banks)

* Chain of Custody Form (evidence)



# **13\. No-Blame Reporting Culture**

SoSecureSwitch enforces a **no-blame culture** for reporting security incidents.  
 Employees are encouraged to report immediately without fear of punishment unless intentional misconduct is proven.