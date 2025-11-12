
| Document ID: | SSS-DOC-ISMS-010 |
| :---- | :---- |
| **Document Title:** | **Access Control Policy** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-09\] |
| **Reference:** | \[ISO/IEC 27001:2022 Annex A.5, A.6, A.8\]|
| **Owner:** | \[IT Ops Lead\] |
| **Approved by:** | \[CTO\] |
| **Review Cycle:** | \[Annual\] |

**1\. Purpose**

This Access Control Policy defines rules, responsibilities and controls to protect SoSecureSwitch information assets by ensuring that access to systems, networks, applications, data and administrative functions is granted on the basis of least privilege, need-to-know, and separation of duties. The policy supports confidentiality, integrity and availability requirements documented in the Statement of Applicability (SoA) and the ISMS.

**2\. Scope**

Applies to:

* All SoSecureSwitch employees, contractors and third parties with access to SoSecureSwitch systems.
* All information systems, services, applications, databases, network devices, developer endpoints, admin consoles, HSMs and cloud-free infrastructure in scope of the ISMS (see Scope Statement SSS-DOC-ISMS-003).
* All access types: local, network, administrative, API, service-to-service, CI/CD and human.

Exclusions: None (SoSecureSwitch uses no cloud services per scope).

**3\. Objectives**

1.Ensure access is granted, changed and revoked in a timely, auditable and consistent manner.

2.Enforce least privilege, role-based access and segregation of duties for sensitive functions.

3.Protect privileged accounts and administrative consoles using technical and procedural controls (PAM, admin workstations, session logging).

4.Secure authentication mechanisms (SSO + MFA) and enforce credential hygiene.

5.Control and protect access to source code, CI/CD pipelines and cryptographic keys (HSM).

6.Provide audit trails to demonstrate enforcement and to support detection & forensics.

**4\. Roles & Responsibilities**

1. **CEO / CTO:** Provide leadership and resources for access control enforcement; approve exceptions that materially affect risk.

2. **ISMS Manager:** Maintain this policy, report compliance to top management, coordinate periodic reviews.

3. **IT Ops Lead:** Implement technical access controls (IAM, AD, network ACLs, PAM), enforce account lifecycle processes.

4. **Security Engineer / InfoSec:** Define privileged access controls, review privileged activity logs, run periodic checks, approve HSM custodial processes.

5. **Asset Owners / Risk Owners:** Request, approve and periodically review access to their assets; justify access levels.

6. **HR:** Notify IT Ops of onboarding/offboarding and role changes; enforce employment terms relating to access.

7. **All users:** Comply with this policy, protect credentials and report suspected compromise.

**5\. Policy Statement**

5.1 **Access Principles**

 * Access is provisioned on least privilege and need-to-know.
 * Role-based access control (RBAC) is the default for production systems; temporary elevated access (JIT) is used where required.
 * Segregation of duties shall be enforced for critical processes (release approvals, key management, production changes).
 * All access actions must be logged and the logs retained per Logging & SIEM retention policy.

5.2 **Account Management (Provisioning & Deprovisioning)**

* All account requests must be submitted via the formal provisioning workflow and approved by the asset owner or delegated approver. Evidence: IAM_Provisioning_Log.csv.
* New accounts are assigned the minimum privileges required; group membership controls privilege.
* Accounts for contractors/third parties are time-limited and tied to contract terms; extension requires re-approval.
* HR must notify IT Ops within 4 business hours of termination/role change; IT Ops must revoke or adjust access within 8 business hours for leavers and 24 hours for role changes (exceptions approved by ISMS Manager). Audit evidence: Offboarding_Checklist.xlsx.

5.3 **Authentication & Identity Management**

* Centralized SSO/IAM (A-SRV-004) is the authoritative identity store. All interactive and privileged logins must use SSO where supported. Design: `Authentication_SSO_Design.md`.
* Multi-Factor Authentication (MFA) is mandatory for: all admin accounts, privileged users, remote access, and any external-facing application used for bank interaction. Evidence: MFA_Enrollment_Report.csv.
* Passwords or secrets used by services must follow the Secrets Management Standard and be stored in a centralized vault (HSM/KMS for crypto secrets). Evidence: KMS_Policy.pdf.

**5.4 Privileged Access Management**

* Privileged accounts (domain admin, DB admin, HSM custodians, release manager) must be controlled via a PAM solution with session recording, approval workflow and just-in-time (JIT) capability. Evidence: PAM_Config_Export.json.
* Use dedicated admin workstations / bastion hosts for all privileged administrative tasks; no general-purpose browsing or email on those workstations. Evidence: Admin_Workstation_Baseline.md.
* Privileged sessions must be recorded and retained as evidence for audits. Evidence: Privileged_Session_Recordings.zip.
* Privileged account reviews must occur quarterly; attestations stored in Privileged_Access_Policy.xlsx.

**5.5 Service & Machine Accounts**

* Service accounts must be non-interactive, tied to a single service/process, use managed secrets and have expiry/rotation schedules. Secrets are stored in centralized vaults; access to vaults is managed separately. Evidence: Service_Account_Register.csv.

**5.6 Remote Access and Third-Party Access**

* Remote access to production systems is allowed only through approved VPN or bastion solutions, with MFA. Bank connectivity links must use mutual TLS/IPSec and per-bank authentication. Evidence: Bank_Link_Design.md.
* Third-party access is limited, time-boxed, supervised where appropriate (e.g., HSM vendor sessions) and requires a signed contract/NDAs and supplier security approval. Evidence: Vendor_Security_SLA_signed.pdf, NDA_Register.xlsx.

**5.7 Application, Database and Source Code Access**

* Access to source code repositories (A-DAT-002) is granted on RBAC; direct local copies are permitted only following the Source Code Handling guideline. Repos must enforce MFA and signed commits where possible. Evidence: Source_Code_Access_Policy.md.
* CI/CD pipelines must validate artifact integrity and require artifacts to be signed (HSM-backed) prior to deployment. Evidence: Artifact_Signing_Records.csv.
* Database access for transaction DBs is strictly controlled, monitored and only available from designated admin workstations or via PAM.

**5.8 Developer Endpoints & Build Infrastructure**

* Developer endpoints must have disk encryption, EDR, enforced patching and restricted local storage of critical IP. Evidence: EDR_Deployment_Report.pdf.
* Build servers and CI/CD hosts must be on isolated build networks, hardened and subject to configuration management and integrity checks. Evidence: Baseline_Config_Images.zip; Build_Server_Baseline.md.

**5.9 Network & Perimeter Access Controls**

* Network segmentation is required between management, development, production, bank links and DMZs. Firewall rules are subject to change control and quarterly review. Evidence: Network_Segmentation_Design.pdf; Firewall_Rule_Review_Log.csv.
* Load balancers, carrier links and bank connectivity must implement secure transport and high-availability design. Evidence: Carrier_SLA_Index.xlsx.

**5.10 Access Reviews, Audit and Monitoring**

* Access reviews: asset owners and HR must perform access attestation for their assets/accounts at least quarterly; records saved in Access_Attestation_HR_YYYY.xlsx.
* Authentication and access events must be forwarded to SIEM; anomalous access triggers SOC triage. Evidence: SIEM_Alert_Report_YYYYMM.csv.
* Failed/suspicious access attempts must be investigated and escalated per Incident Response Plan.

**5.11 Logging, Retention and Evidence**

* All access to critical systems (transaction switch, DB, HSM, admin consoles, CI/CD, SSO) must be logged with synchronized timestamps. Logs must be retained per the Logging & Retention policy and stored immutably in SIEM. Evidence: Log_Retention_Policy.pdf; Log_Integrity_Checks_YYYYMM.csv.

**5.12 Exceptions**

* Exceptions to this policy require an explicit written risk acceptance approved by the ISMS Manager and the respective asset owner; all exceptions must include compensating controls and a sunset date. Record: Access_Policy_Exceptions_Register.xlsx.

**5.13 Non-Compliance**

* Violations of this policy may result in disciplinary action, contract termination or legal action as appropriate. The disciplinary process is defined in Disciplinary_Policy.md.

**6. Implementation & Controls (Summary mapping to SoA)**

* This policy implements access control requirements referenced in the SoA and maps to Annex A controls. Key mappings:
* Account & access lifecycle → A.5.15, A.5.16, A.8.2, A.8.3
* Privileged access & PAM → A.8.16, A.8.15, A.5.15
* Authentication & MFA → A.5.16, A.8.5
* Source code & CI/CD signing → A.8.24, A.8.32, A.8.25–8.29
* Developer endpoints & EDR → A.8.7, A.8.8
* Refer to the SoA and RTP for detailed control assignments and treatment evidence.

**7. Evidence & Records (examples)**

`Access_Control_Policy.pdf` (this document)

`IAM_Provisioning_Log.csv`

`Privileged_Access_Policy.xlsx`

`PAM_Config_Export.json`

`MFA_Enrollment_Report.csv`

`Source_Code_Access_Policy.md`

`Artifact_Signing_Records.csv`

`SIEM_Alert_Report.md`

**8. Review & Exceptions**

This policy is reviewed annually by the ISMS Manager and CTO or after any major incident, audit finding or organizational change.
Any exception must be documented, approved and reviewed at least monthly until closed.