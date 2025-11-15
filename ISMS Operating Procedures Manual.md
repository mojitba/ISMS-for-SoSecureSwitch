| Document ID: | SSS-DOC-ISMS-014 |
| :---- | :---- |
| **Document Title:** | **ISMS Operating Procedures Manual** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-15\] |
| **Reference:** | \[ISO/IEC 27001:2022 Clause 8.1\]|
| **Owner:** | \[ISMS Manager\] |
| **Approved by:** | \[ISMS Owner\] |
| **Review Cycle:** | \[Annual, or after any P1/P2 incident\] |

**Scope**: All operational processes required to implement, operate and control SoSecureSwitch ISMS for the on-prem payment switching environment (transaction switch, back-office, HSMs, CI/CD, DC & DR, bank links, developer endpoints).

**Purpose**: provide concise, actionable operating procedures (SOPs) to ensure consistent implementation, evidence collection and auditability of ISMS controls across SoSecureSwitch.

**Document structure**

Change & Release Management Procedure

Access Provisioning & Privileged Access Procedure

Backup, Restore & Retention Procedure

Disaster Recovery (DR) & Business Continuity Procedure

Incident Response & Forensics Procedure

Vulnerability & Patch Management Procedure

CI/CD & Release Signing Procedure (HSM integration)

HSM & Key Management Procedure (summary / reference)

Logging, SIEM & Monitoring Procedure

Supplier & Contractual Security Procedure

Asset Management & Configuration Procedure

Onboarding / Offboarding (HR) Procedure

System Hardening & Secure Configuration Procedure

Change of Control / Exceptions & Risk Acceptance Procedure

Operational Review, Metrics & Audit Procedure

**Evidence & Records Management** (how to store evidence)

Each section contains: purpose, scope, roles, stepwise procedure, minimum evidence artifacts and review frequency.

**1\. Change & Release Management Procedure**

Purpose: Ensure controlled, auditable, and reversible changes to production and critical systems (A-class assets).  
Scope: All production changes including software releases, DB schema change, HSM policy changes, network/device config.  
Roles: Requestor (Asset Owner), Change Approver (CAB), Change Implementer (IT Ops Lead / Dev), QA, Build & Release Engineer, Change Coordinator (ISMS Manager).  
Procedure (summary):

Raise change ticket with description, business justification, rollback plan, test plan and impact analysis. (Tool: CAB\_Ticket\_\<id\>.md)

Classify change: Emergency / Standard / Major. Emergency changes require post-facto CAB review.

CAB approves or rejects; approvals recorded (CAB\_approvals\_YYYYMM.pdf).

If approved: schedule maintenance window, notify stakeholders (banks, ops).

Pre-deploy: run automated tests (unit, integration, SAST/DAST where applicable). Upload test reports.

Deploy using signed artifacts only (see CI/CD procedure). Record deployment logs and session recordings for privileged operations.

Post-deploy: run acceptance tests; update config & inventory; close CAB ticket with evidence.

Post-change review within 7 days for Major changes; lessons captured in Change\_Post\_Mortem\_\<id\>.md.  
Minimum evidence: CAB ticket, approval PDF, test reports, signed artifact record (Artifact\_Signing\_Records.csv), deployment logs, rollback proof.  
Review frequency: Quarterly CAB effectiveness review.  
Annex mapping: A.5.15, A.8.32, A.8.15.

**2\. Access Provisioning & Privileged Access Procedure**

Purpose: Grant, review and revoke access consistently (least privilege & SoD).  
Scope: User accounts, service accounts, privileged/admin accounts, repo access, CI/CD service identities.  
Roles: Requestor, Asset Owner (approver), IT Ops Lead (provisioner), HR (trigger for join/leave), ISMS Manager (oversight).  
Procedure (summary):

Access request via formal form or IAM portal; include justification and expiry. (IAM\_Provisioning\_Log.csv)

Asset Owner reviews and approves. Temporary access requires expiry and JIT justification.

IT Ops Lead provisions via SSO/IAM, assigns RBAC groups. Enforce MFA.

Privileged access only via PAM; sessions recorded. Quarterly privileged attestation by Asset Owners. (Privileged\_Access\_Attestations.csv)

Offboarding: HR notifies IT Ops Lead within 2 hours of termination; IT Ops disables/adjusts accounts within 4 hours for leavers and 8 hours for role changes.. Record in Offboarding\_Checklist.csv.  
Minimum evidence: Provisioning log, approval emails, PAM session logs, attestation spreadsheets.  
Review frequency: Quarterly access attestations; monthly orphan account check.  
Annex mapping: A.5.15, A.5.16, A.8.2, A.8.16.

**3\. Backup, Restore & Retention Procedure**

Purpose: Ensure recoverability and integrity of transaction data, repo snapshots and critical configs.  
Scope: Transaction DB, source code repo, configuration backups, HSM metadata where vendor allows.  
Roles: Backup & DR Coordinator, DBA, IT Ops Lead, Security Engineer.  
Procedure (summary):

Define RTO/RPO per asset (see Asset Register). Maintain RTO\_RPO\_Register.csv.

Backup schedule: continuous replication for DB \+ daily snapshots; daily repo backups; config backups daily.

Protect backups: encrypted at rest, at least one offline/air-gapped copy, dual-custodian access for key material(Requires IT Ops Lead and Security Engineer). (HSM\_Backup\_Register.csv)

Monthly automated restore verification for sample datasets; full restore drill quarterly with DR site. Record Restore\_Test\_Report\_YYYYMM.pdf.

On restore failure, escalate to IT Ops Lead and open RCA ticket.  
Minimum evidence: Backup logs, verification reports, restore drill reports.  
Review frequency: Weekly backup success check; quarterly full restore tests.  
Annex mapping: A.8.13, A.5.29.

**4\. Disaster Recovery (DR) & Business Continuity Procedure**

Purpose: Enable recovery of services meeting contractual SLAs and RTO/RPO.  
Scope: Primary DC, DR site, bank connectivity, transaction switch and supporting infra.  
Roles: Backup & DR Coordinator, IT Ops Lead, CTO, Deputy CEO.  
Procedure (summary):

Maintain DR runbooks per asset (DR\_Runbooks.md). Include failover steps, contact list, verification steps.

Monthly replication health checks; quarterly failover test to DR site. Record DR\_Test\_Summary\_YYYY.pdf.

Activate DR: follow runbook, notify banks & stakeholders, execute failback plan when stable.

Post-DR: post-incident review and update runbooks.  
Minimum evidence: DR runbooks, test reports, RTO/RPO register.  
Review frequency: Quarterly tests; annual DR plan review.  
Annex mapping: A.5.29, A.8.14.

**5\. Incident Response & Forensics Procedure**

Purpose: Detect, contain, eradicate and learn from security incidents with timely reporting to stakeholders and regulators.  
Scope: All security incidents impacting confidentiality, integrity or availability (including fraud, data breach, key compromise).  
IRT Lead (ISMS Manager), CTO (Escalation), CEO (Escalation), and an Incident Response Team composed of relevant SMEs (e.g., IT Ops Lead, DBA, Legal Counsel).  
Procedure (summary):

Detection: ingest SIEM alerts, user reports, monitoring. Triage per severity matrix. (SIEM\_Alert\_Report\_YYYYMM.csv)

Containment: isolate affected systems; preserve evidence (snapshots, logs). Follow Forensic\_Evidence\_Procedure.md.

Investigation: collect logs, HSM audit, DB transactions; document timeline. Store evidence immutably in SIEM/evidence store.

Eradication & Recovery: apply fixes, patch, rotate keys if needed, validate with tests.

Notification: inform affected banks, legal counsel, regulators per contract and law. Maintain Incident\_Notification\_\<date\>.pdf.

Lessons learned: create Post-Incident Report and update RTP/SoA.  
Minimum evidence: Incident ticket, timeline, forensic artifacts, notification records, post-incident report.  
Review frequency: After each incident; quarterly IR table-top exercises.  
Annex mapping: A.5.24–A.5.28, A.8.15.

**6\. Vulnerability & Patch Management Procedure**

Purpose: Identify, prioritise and remediate technical vulnerabilities across servers, network devices, appliances and endpoints.  
Scope: All in-scope systems (DB, OS, network gear, appliances, endpoints, build servers).  
Roles: IT Ops Lead, Security Engineer.  
Procedure (summary):

Regular scans (weekly for infra, monthly for apps) and triage via risk rating (CVSS \+ business impact). Vuln\_Scan\_Report\_YYYYMM.pdf.

Patch windows: Critical/High - apply within SLA (Critical: ASAP/24–72h; High: 7 days; Medium: 30 days). Emergency patches follow emergency CAB process.

Test patches in staging builds; maintain rollback plan.

Record patch status and exceptions in Patch\_Management\_Report.csv.  
Minimum evidence: Scan reports, patch logs, test evidence.  
Review frequency: Weekly vulnerability triage; monthly patch compliance report.  
Annex mapping: A.8.8, A.8.9.

**7\. CI/CD & Release Signing Procedure (HSM integration)**

Purpose: Ensure only approved, integrity-protected artifacts reach production.  
Scope: CI/CD pipeline, build servers, artifact registry, HSM signing.  
Roles: Build & Release Engineer, Dev Manager, Security Engineer, HSM Custodians.  
Procedure (summary):

Builds run on isolated build servers; artifacts stored in registry with metadata.

Artifact signing: CI authenticates to vault, requests HSM sign operation; signature and metadata recorded (Artifact\_Signing\_Records.csv). Private keys never leave HSM.

Deployment gates verify signature and key validity; deployment rejected on invalid/missing signature.

All build and signing events logged to SIEM.  
Minimum evidence: Build logs, signing records, verification logs.  
Review frequency: Monthly artifact integrity checks; quarterly pipeline security review.  
Annex mapping: A.8.24, A.8.32, A.8.25–8.29.

**8\. HSM & Key Management Procedure (summary/reference)**

Purpose: Protect and govern keys used for transaction signing and artifact signing.  
Scope: On-prem HSMs, key backups, rotation, custodial activities.  
Roles: Security Engineer (Crypto Lead), HSM Custodians, IT Ops Lead.  
Procedure (summary):

Follow the full Cryptography & Key Management Procedure. Key operations require dual control, recorded custody logs and quarterly rotation/backup tests.  
Minimum evidence: HSM\_Key\_Inventory.csv, Key\_Rotation\_Log.csv, HSM\_Backup\_Register.csv.  
Review frequency: Quarterly key inventory; annual HSM audit.  
Annex mapping: A.8.24, A.7.2.

**9\. Logging, SIEM & Monitoring Procedure**

Purpose: Capture, store, detect and alert on security-relevant events to support detection and forensics.  
Scope: Authentication, privileged sessions, application logs, network flows, HSM audit logs.  
Roles: SOC / Monitoring Engineer, ISMS Manager, IT Ops Lead.  
Procedure (summary):

Forward logs centrally (SIEM) with synchronized NTP timestamps.

Define alert rules for critical assets (switch errors, anomalous DB queries, failed privileged logins).

Triage alerts per playbooks and escalate to IR team.

Retain logs per retention policy (immutable storage for critical logs). Log\_Retention\_Policy.pdf.  
Minimum evidence: SIEM alert reports, log forwarding config, integrity checks.  
Review frequency: Weekly alert reviews; quarterly tuning of detection rules.  
Annex mapping: A.8.15, A.5.33.

**10\. Supplier & Contractual Security Procedure**

Purpose: Ensure suppliers meet security obligations and SLAs (HSM vendors, colo, carriers).  
Scope: All suppliers with access or impact to in-scope systems.  
Roles: Legal Counsel, IT Ops Lead, ISMS Manager.  
Procedure (summary):

Pre-engagement: supplier security questionnaire and risk assessment. Supplier\_Security\_QA\_Questionnaire\_responses.csv.

Contract: include security clauses, audit rights, IP & NDA terms. Store in Supplier\_Contracts\_Index.csv.

Onboarding: map supplier access, enforce least privilege, time-bound access. Supervised vendor sessions for HSM/colo.

Ongoing: periodic vendor performance & security review (quarterly).  
Minimum evidence: Contract copies, questionnaire responses, access logs.  
Review frequency: Quarterly supplier reviews.  
Annex mapping: A.5.19, A.5.20.

**11\. Asset Management & Configuration Procedure**

Purpose: Maintain an accurate inventory and configuration baseline for all in-scope assets.  
Scope: Hardware, software, systems, data, people (key persons), documents.  
Roles: Asset Owners, ISMS Manager, IT Ops Lead.  
Procedure (summary):

Maintain Asset Register with CIA ratings (6.asset\_register.csv). Assign owners and criticality.

Baseline configs for servers/routers/build servers; record in Baseline\_Config\_Images.zip.

Configuration changes logged and backed up. Periodic discovery to identify drift.  
Minimum evidence: Asset register, config baselines, change logs.  
Review frequency: Monthly automated discovery; annual full inventory audit.  
Annex mapping: A.5.9, A.8.9.

**12\. Onboarding / Offboarding (HR) Procedure**

Purpose: Ensure secure and timely provisioning and deprovisioning of accounts and assets.  
Scope: New hires, role changes, contractors, leavers.  
Roles: HR Manager, IT Ops Lead, Line Manager.  
Procedure (summary):

Onboard: HR provides role and start date; IT provisions accounts and issues devices per least privilege. Deliver security orientation. Record in Onboarding\_Record\_\<user\>.csv.

Offboard: HR triggers offboarding checklist; IT revokes access, collects assets and updates asset register. Evidence: Offboarding\_Checklist.csv.  
Minimum evidence: Onboard/offboard checklists, asset receipts, training completion.  
Review frequency: Monthly audit of onboarding tickets.  
Annex mapping: A.6.1–A.6.6.

**13\. System Hardening & Secure Configuration Procedure**

Purpose: Apply secure baselines to reduce attack surface.  
Scope: Servers, network devices, developer endpoints, build servers.  
Roles: System Administrator, Network Engineer, Dev Manager, IT Ops Lead.  
Procedure (summary):

Maintain hardened baselines for each system type (System\_Baseline\_\<type\>.md).

Enforce automated configuration management (IaC, config management tools).

Periodic compliance scans against baseline; remediate drift within SLA.  
Minimum evidence: Baseline images, compliance scan reports.  
Review frequency: Quarterly baseline review.  
Annex mapping: A.8.9, A.8.25.

**14\. Change of Control / Exceptions & Risk Acceptance Procedure**

Purpose: Manage documented exceptions and temporary compensating controls.  
Scope: Any deviation from standard procedure/policy.  
Roles: ISMS Manager, CTO, Asset Owner, Risk Owner.  
Procedure (summary):

Raise exception request with justification and compensating controls. Exception\_Request\_\<id\>.md.

ISMS Manager assesses and CTO approves; time-boxed approvals only. Record in Access\_Policy\_Exceptions\_Register.csv.

Reassess monthly until closed.  
Minimum evidence: Exception request, approval, compensating control evidence.  
Review frequency: Monthly review of open exceptions.  
Annex mapping: A.5.15, Clause 6.1.

**15\. Operational Review, Metrics & Audit Procedure**

Purpose: Verify operation effectiveness and continual improvement.  
Scope: All procedures listed above.  
Roles: ISMS Manager, Internal Auditor, CTO, CEO.  
Procedure (summary):

Define KPIs and metrics: patch compliance %, backup success %, mean time to detect (MTTD), mean time to recover (MTTR), privileged attestation completion %.

Monthly operations meeting to review metrics and open items.

Quarterly management review (management minutes). Annual internal audit against SoA and Annex A.

Track corrective actions in RTP and evidence repository.  
Minimum evidence: KPI dashboards, meeting minutes, internal audit reports.  
Review frequency: Monthly operational; quarterly management; annual internal audit.  
Annex mapping: Clause 9 & A.5.36.

**16\. Evidence & Records Management (how to store evidence)**

Evidence store: centralized, access-controlled evidence repository on secure file server (path: /evidence/SoSecureSwitch/ISMS/).

Naming convention: \<ControlID\>\_\<ArtifactType\>\_\<YYYYMMDD\>\_\<owner\>.\<ext\> (e.g., A8.13\_RestoreTest\_20260104\_BackupCoordinator.pdf).

Retention: follow retention schedule in SoA; critical logs retained immutably per Log\_Retention\_Policy.pdf.

Immutable logs: SIEM for critical logs; snapshots of artifacts kept as read-only archives.

Linking: each RTP/control record must include Evidence filename(s) and link in SoA.

**Appendices**  

* A: Key templates & referenced documents

	* SSS-DOC-ISMS-006 (Asset Register)

	* ISMS-Roles-Responsibilities-Matrix.md

	* SSS-DOC-ISMS-010 (Access Control Policy.md)

	* SSS-DOC-ISMS-011(Incident\_Response\_Plan.md)

	* DR\_Runbooks.md

	* Artifact\_Signing\_Records.csv

	* CAB\_approvals\_Q4.csv

	* Privileged\_Access\_Attestations.csv

	* Backup\_Verification\_Report\_Q4.md
	
	* SIEM\_Alert\_Report\_Q4.csv

	* Supplier\_Security\_QA\_Questionnaire\_responses.csv

* B: Roles quick contact

	*CEO: ceo@SoSecureSwitch.local

	*CTO: cto@SoSecureSwitch.local

	*ISMS Manager: ops@SoSecureSwitch.local

	*Backup & DR Coordinator: backup@SoSecureSwitch.local

	*Build & Release: releases@SoSecureSwitch.local

	*SOC: soc@SoSecureSwitch.local