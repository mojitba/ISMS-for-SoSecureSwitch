Document ID: SSS-DOC-ISMS-003

Document Title: ISMS Scope Statement

Version: \[1.0\]

Status: \[Approved\]

Effective Date: \[2025-10-31\]

Owner: "\[ISMS Manager\]"

Review Cycle: "\[Annual\]"

**1\. Purpose**

This document defines the scope and boundaries of the Information Security Management System (ISMS) for SoSecureSwitch Ltd. in accordance with ISO/IEC 27001:2022 Clause 4.3. It states what is in-scope, what is out-of-scope, the rationale for inclusions/exclusions, the physical and logical boundaries, and the interested parties whose requirements drive the scope.

This scope has been determined based on the analysis of internal/external issues (documented in SSS-DOC-ISMS-001) and the requirements of interested parties (documented in SSS-DOC-ISMS-002).

**2\. Scope Statement**

The ISMS for SoSecureSwitch Ltd. covers the **design, development, deployment, operation, maintenance, and support** of the **SoSecureSwitch payment-switch platform** and associated back-office services used by our four bank customers. The scope includes SoSecureSwitch as a proprietary intellectual property asset ,production and disaster recovery transaction environments, cryptographic key management (HSM/KMS), transaction databases, the web-based back-office application, source control repositories, build and release pipelines (CI/CD), developer endpoints used to build and test the product, supporting network and infrastructure components (on-prem data centers and connectivity to bank customers), monitoring and logging systems used for detection and evidence, and supplier services that directly support the in-scope systems.

**3\. In-Scope**

**Departments**

IT, Developers Team, Information Security, HR, Legal, Management Board,

**Systems & Applications**

* SoSecureSwitch transaction switch (all production instances).  
* Transaction database(s) (production \+ DR replicas).  
* Web-based back-office application used by bank operators.  
* Key management systems (HSM or local KMS used for transaction cryptography and code signing).  
* Source-code repositories and version control systems that store SoSecureSwitch code and configuration.  
* CI/CD/build servers, artifact repositories, and release signing infrastructure.  
* Centralized logging and monitoring systems used for transaction, operational and security telemetry.  
* Authentication/SSO and IAM systems used to control access to in-scope systems.  
* HR (for processes supporting the ISMS, e.g., screening, onboarding/offboarding, awareness)  
* Legal (for processes supporting the ISMS, e.g., supplier contracts, IP protection, regulatory liaison)

**Infrastructure & Locations**

* Primary on-prem server room hosting production systems and the designated DR site.  
* Network devices and connectivity (firewalls, routers, load balancers) supporting bank-facing interfaces and internal segmentation.  
* Bank connectivity links (VPNs) and interconnects used to process customer transactions.

**People & Processes**

* Employees, contractors involved in design, development, deployment, operations, support and security of SoSecureSwitch (Dev, Ops, Support, Security, Product).  
* Operational processes that directly affect in-scope systems: change management, release management, incident response, backup & restore, privileged access management, secure SDLC activities.

**Suppliers (in scope function)**

HSM/KMS provider, network/ISP providers, and CI/CD tooling providers that host or manage artifacts used by SoSecureSwitch.

**Assets of special significance**

SoSecureSwitch product intellectual property: source code, design documentation, build artifacts, release signing keys and related derivates.

**4\. Out-of-Scope**

·       **Marketing website** that does not store or process transaction data and it hosted outside of our infrastructures. — *Rationale:* no technical or contractual interface to in-scope systems.

* **Bank customer internal systems** — *Rationale:* outside SoSecureSwitch operational control (interfaces remain in-scope).  
* **Personal BYOD devices** not authorized for development or admin access — *Rationale:* only corporate-managed developer endpoints and admin consoles are in-scope;  
* **Cloud-based office productivity services (Email, HR System)** — *Rationale: These systems do not store, process, or transmit client transaction data or SoSecureSwitch source code, and are logically segregated. They are managed via a separate Supplier Security Policy.*

**5\. Organizational chart**

**Top Management / Board**

* **Board of Directors**  
  * **Board Director (Chair)**  
  * **Deputy CEO**  
  * **Chief Executive Officer (CEO)** — *ISMS Sponsor / Top Management Representative*  
  * **Chief Technology Officer (CTO)** — *ISMS Owner / Technical Authority*  
  * **Company Secretary**

---

**Operational Departments**

**1\. Information Technology (IT Operations) – 6 persons**

**IT Operations Lead** *(reports to CTO)*

* **System Administrator (Production)**  
* **Database Administrator (DBA)**  
* **Network & Infrastructure Engineer**  
* **Backup & DR Coordinator**  
* **Monitoring & Support Engineer**  
* **Helpdesk / IT Support Technician**

*Main Responsibilities:* operate production switch environment, maintain servers, DR, backups, monitoring, patch management.

---

**2\. Software Development Department – 15 persons**

**Development Manager (Dev Manager)** *(reports to CTO)*

* **Lead Software Engineer (Switch Platform)**  
* **Lead Web Application Developer (Back Office)**  
* **Developers (x8)**  
* **QA/Test Engineer (x2)**  
* **Build & Release Engineer**  
* **Technical Writer / Documentation Specialist**

*Main Responsibilities:* maintain and enhance SoSecureSwitch software, follow secure SDLC, manage CI/CD, implement code signing and version control practices.

---

**3\. Information Security Department – 4 persons**

**Information Security Manager (ISMS Manager)** *(reports to CTO, dotted line to CEO)*

* **Security Engineer (Infrastructure & Hardening)**  
* **ISMS Analyst / Compliance Officer**  
* **SOC / Incident Response Analyst**

*Main Responsibilities:* implement and maintain ISMS; perform risk assessments, internal audits, vulnerability management, and awareness training; coordinate compliance with ISO 27001 and regulatory obligations.

---

**4\. Human Resources (HR) – 4 persons**

**HR Manager** *(reports to Deputy CEO)*

* **Recruiter / Onboarding Specialist**  
* **Training & Development Officer**  
* **Payroll & Benefits Administrator**

*Main Responsibilities:* screening and background checks, onboarding/offboarding, awareness programs, disciplinary processes, HR policy updates, and HR records.

---

**5\. Legal Department – 2 persons**

**Legal Counsel (Head of Legal)** *(reports to CEO)*

* **Legal Assistant / Contract Officer**

*Main Responsibilities:* manage NDAs, contracts, intellectual property rights, supplier agreements, regulatory compliance, and data-protection legal obligations.

---

**6\. Physical Security – 1 person**

**Physical Security Officer** *(reports to Deputy CEO)*  
 *Main Responsibilities:* control data-centre and office access, maintain CCTV, visitor logs, access badges, and coordinate with building management for physical protection.

---

**7\. Cleaning & Facility Services – 2 persons**

**Facilities & Cleaning Staff (x2)** *(report to Physical Security Officer or HR Manager depending on structure)*  
 *Main Responsibilities:* maintain cleanliness and support facility hygiene standards in secure zones.

---

**6\. Dependencies and Interfaces:**

 

| Interface / Dependency | Description (what flows / why important) | Owner (responsible) |
| ----- | ----- | ----- |
| **Bank connectivity (VPNs / leased lines / APIs to each bank customer)** | Real-time transaction messages, settlement exchanges and operational APIs across dedicated links. Highest availability and integrity requirement. | IT Ops Lead / Dev Manager |
| **HSM / KMS provider (on-prem appliance)** | Storage and use of cryptographic keys for transaction encryption and signing of releases. Critical for confidentiality and non-repudiation. | IT Ops Lead / Security Engineer |
| **Source-code repositories (on-prem git) & artifact stores** | Storage of SoSecureSwitch source, branches, commit history and build artifacts. Contains IP. | Dev Manager / Build & Release Engineer |
| **CI/CD / Build servers & pipeline (on-prem)** | Automated builds, tests, artifact generation and release pipelines. Controls the release process and artifact integrity. | Build & Release Engineer / Dev Manager |
| **Logging & monitoring (centralized on-prem SIEM / log store)** | Central collection of logs for detection, alerting, investigation and evidence for customers/regulators. | Monitoring & Support Engineer / SOC Analyst |
| **Backup & restore systems (on-prem backup appliances)** | Backups of DBs, configs, source-code snapshots and artifacts. Needed for recovery & evidence. | Backup & DR Coordinator / IT Ops Lead |
| **Data center / colocation provider** | Physical facility hosting production & DR hardware (power, cooling, access control). | IT Ops Lead / Vendor Manager |
| **Network/ISP provider (internet & carrier links)** | WAN connectivity that supports bank links and remote staff access. | IT Ops Lead / Procurement |
| **Supplier: HSM / hardware / vendor support** | On-site support, firmware updates, spare parts, emergency access. | Vendor Manager / Legal |
| **Bank test & certification environments (customer testbeds)** | Test transactions for integration/QA; sometimes contain sanitized data. | Dev Manager / Lead Software Engineer (Switch Platform) |
| **Payment networks / clearing houses (downstream processors)** | Settlement, clearing and message exchange to payment networks. | IT Ops Lead / Dev Manager |
| **Legal / Regulatory interfaces (regulators, data protection authority)** | Regulatory reporting, audits, compliance requests and notifications. | Compliance Officer / Legal Counsel |
| **Internal identity/SSO & HR systems (on-prem)** | User onboarding/offboarding; authentication & role provisioning for staff and contractors. | HR Manager / IT Ops Lead |
| **Time synchronization service (NTP / time servers)** | Central time source for logs/signatures (critical for evidence & non-repudiation). | IT Ops Lead / Monitoring Engineer |
| **Physical security & facilities (access control, CCTV)** | Physical controls for DC & secure areas, badge access, escorted vendor visits. | Physical Security Officer |
| **Incident response escalation contacts (legal, PR, banks)** | Formal communication paths for incidents (banks/regulator/press/legal). | ISMS Manager / IR Lead |
| **Insurance / risk transfer (cyber / IP insurance)** | Financial recovery and contractual coverage; insurer obligations for evidence. | CFO / Risk Owner |

 

**7\. Responsibilities**

* **ISMS Sponsor / CEO:** approve the scope and provide resources.  
* **ISMS Owner / InfoSec Lead (CTO):** maintain scope, coordinate SoA and evidence collection.  
* **Product Owner / Service Owners:** asset/service owners for SoSecureSwitch components — ensure inventory, classification, owners and evidence.  
* **IT Ops Lead / Dev Manager:** implement technical controls, change management and operational evidence.  
* **Procurement / Vendor Manager:** ensure supplier contracts contain required security and IP clauses.  
* **Internal Audit Lead:** audit compliance to scope and SoA.

 

 

 

