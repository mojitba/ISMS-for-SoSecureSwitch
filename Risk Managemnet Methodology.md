| Document ID: | SSS-DOC-ISMS-005 |
| :---- | :---- |
| **Document Title:** | **Risk Management Methodology** |
| **Version:** | 1.0 |
| **Status:** | \[Approved\] |
| **Effective Date:** | \[2025-11-03\] |
| **Reference:** | \[ISO/IEC 27001:2022 Clauses 6.1.2, 8.2\]|
| **Owner:** | \[CTO (ISMS Manager)\] |
| **Review Cycle:** | \[Annual\] |


**1\. Purpose**

This document describes the methodology used by SoSecureSwitch to identify, analyze, and evaluate information security risks. This process aligns with the requirements of ISO 27001:2022 (Clause 6.1.2).

**2\. Risk Assessment Process**

The risk assessment process is conducted annually and follows these steps:

1. **Asset-based Risk Identification:** Identify threats and vulnerabilities for each critical asset in the Asset Register (SSS-DOC-ISMS-005).  
2. **Risk Analysis:** Analyze risks by determining the **Impact** of a risk event and the **Likelihood** of it occurring.  
3. **Risk Evaluation:** Calculate the final **Risk Score** and compare it against the defined Risk Acceptance Criteria to determine risk priority.

**3\. Risk Analysis: Impact Criteria**

The Impact of a risk event is based on the Confidentiality (C), Integrity (I), and Availability (A) scores defined in the Asset Register.

The final **Impact Score (1-5)** is the **highest (MAX) value** of the C, I, or A scores for that asset.

* **Example:** Asset A-DAT-001 (Source Code) is C=5, I=5, A=3.  
* The **Impact Score** for *any* risk to this asset (e.g., theft, modification) is **5**.

| Impact Category | Operational Description | Reputational Scope | Regulatory Consequences | Business Value Impact |
| ----- | ----- | ----- | ----- | ----- |
| **Catastrophic (5)** | Complete outage or loss of critical systems (e.g., payment switch, transaction DB, HSM). Immediate service failure for all banks; extended downtime (\>24 hours). Irrecoverable data or key loss. | Severe and public loss of trust among all banking clients; extensive negative media coverage; long-term brand damage. | Significant legal penalties or loss of license; data-protection authority investigation; possible contractual termination by multiple banks. | \> 20 % annual revenue loss or permanent damage to business viability; potential insolvency. |
| **Major (4)** | Severe disruption to essential operations; partial service outage (6–24 hours); integrity of critical data at risk but recoverable. | Temporary but wide reputational impact across customer banks; formal incident notifications required. | Regulatory reporting required (e.g., GDPR Art. 33); contractual penalties triggered; increased audit scrutiny. | 5–20 % revenue loss; major cost to restore systems or compensate customers. |
| **Moderate (3)** | Noticeable service degradation or short outage (\<6 hours); limited subset of customers affected; incident contained. | Reputational impact limited to affected customers; internal or confidential disclosure only. | Minor regulatory attention; internal reporting or customer notification at bank’s request. | \< 5 % revenue loss; moderate cost and resource use to remediate. |
| **Minor (2)** | Localized issue (single system, short duration); limited productivity impact; no breach of contractual SLAs. | Minimal visibility outside SoSecureSwitch; managed internally. | No regulatory action; minor internal documentation. | Negligible financial loss (\< 1 % revenue) or one-time operational delay. |
| **Insignificant (1)** | Brief or negligible interruption; quickly corrected by standard procedures; no data or service impact. | No external awareness; no reputational impact. | No compliance implications. | No measurable financial or operational impact. |

   

**4\. Risk Analysis: Likelihood Criteria**

The Likelihood is the estimated frequency of a risk event occurring *in the context of existing controls*.

| Likelihood Category | Probability Range | Annual Frequency Range (Events per Year) | Statistical Definition | Business Examples (Contextual to SoSecureSwitch) |
| ----- | ----- | ----- | ----- | ----- |
| **Very High (5)** | \> 80 % probability of occurrence | More than 10 times / year | Expected to occur multiple times annually under normal operating conditions; almost certain. | Routine malware probes, phishing emails targeting staff, minor operational alerts triggered weekly, frequent patching or configuration changes introducing small errors. |
| **High (4)** | 51 % – 80 % | 2 – 10 times / year | Likely to occur several times per year; consistent or recurring trend. | Supplier delay in patch delivery, user account lockouts, recurring log or backup job failures, minor system misconfigurations detected in audits. |
| **Moderate (3)** | 21 % – 50 % | Once every 1–2 years | Could occur in the foreseeable future; realistic and not exceptional. | Network device failure requiring replacement, data-center power incident, internal policy violation by employee, low-impact security vulnerability exploited. |
| **Low (2)** | 6 % – 20 % | Once every 3–5 years | Unlikely under current controls, but plausible during adverse circumstances. | Major database corruption requiring restore, extended ISP outage, unauthorized internal access attempt detected and stopped, isolated HSM malfunction. |
| **Very Low (1)** | ≤ 5 % | Less than once every 5 years | Rare or unprecedented; would require multiple control failures or extraordinary conditions. | Catastrophic data-center fire, full cryptographic key compromise, insider collusion causing customer data breach, simultaneous failure of DR and backup systems. |

 

**5\. Risk Evaluation: Risk Score & Matrix**

The final Risk Score is calculated: **Risk Score \= Impact x Likelihood**

|  | Impact \= 1 | Impact \= 2 | Impact \= 3 | Impact \= 4 | Impact \= 5 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **Likelihood \= 5** | 5 (Low) | 10 (Med) | 15 (High) | 20 (High) | 25 (High) |
| **Likelihood \= 4** | 4 (Low) | 8 (Med) | 12 (Med) | 16 (High) | 20 (High) |
| **Likelihood \= 3** | 3 (Low) | 6 (Med) | 9 (Med) | 12 (Med) | 15 (High) |
| **Likelihood \= 2** | 2 (Low) | 4 (Low) | 6 (Med) | 8 (Med) | 10 (Med) |
| **Likelihood \= 1** | 1 (Low) | 2 (Low) | 3 (Low) | 4 (Low) | 5 (Low) |

**6\. Risk Acceptance Criteria & Treatment**

Risks are evaluated against the following criteria to determine the required treatment.

| Risk Score | Risk Level | Required Action |
| :---- | :---- | :---- |
| **15 \- 25** | **High** | **Mitigate.** Must be treated immediately. Requires a formal Risk Treatment Plan (RTP) and ISMS Manager approval. |
| **6 \- 12** | **Medium** | **Mitigate or Accept.** Treatment is required unless formally accepted by the Asset Owner and ISMS Manager. |
| **1 \- 5** | **Low** | **Accept.** No further treatment required. Risk is accepted by the Asset Owner. |

**7\. Risk Treatment Options**

* **Mitigate:** Apply controls (from Annex A or elsewhere) to reduce the Likelihood or Impact.  
* **Accept:** Formally acknowledge the risk and take no action (only for Low/Medium risks).  
* **Transfer:** Share the risk with a third party (e.g., insurance, outsourcing).  
* **Avoid:** Stop the activity that is causing the risk.

 

