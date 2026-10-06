# FinServe India Pvt. Ltd. — NIST CSF 2.0 Cybersecurity Assessment Report

|                 |                                                                     |
| --------------- | ------------------------------------------------------------------- |
| **Report type** | Portfolio learning project (fictional organization)                 |
| **Framework**   | NIST Cybersecurity Framework (CSF) 2.0, published February 26, 2024 |
| **Prepared by** | Deepak Chaudhary                                                    |
| **Report date** | October 2026                                                        |

> **Disclaimer:** FinServe India is a fictional FinTech company created for a learning exercise. This report is a scenario-based assessment, not a certification audit. No technical testing was performed, and controls that are not described in the scenario are not treated as confirmed controls.

## Contents

1. [Executive Summary](#1-executive-summary)
2. [Organization Overview](#2-organization-overview)
3. [Assessment Scope](#3-assessment-scope)
4. [Methodology](#4-methodology)
5. [Asset Inventory](#5-asset-inventory)
6. [Risk Assessment](#6-risk-assessment)
7. [Current Profile](#7-current-profile)
8. [Target Profile](#8-target-profile)
9. [Gap Analysis](#9-gap-analysis)
10. [NIST CSF 2.0 Mapping](#10-nist-csf-20-mapping)
11. [Top Security Findings](#11-top-security-findings)
12. [Remediation Roadmap](#12-remediation-roadmap)
13. [Conclusion](#13-conclusion)

---

## 1. Executive Summary

This report assesses the cybersecurity posture of FinServe India Pvt. Ltd., a fictional FinTech company with about 250 employees and about 100,000 customers, running on AWS. The assessment follows the NIST CSF 2.0 Profile approach: document the Current Profile, define a Target Profile, analyze the gaps, and build a prioritized action plan.

**Key results**

| Measure | Result |
|---|---|
| Assets in scope | 9 (7 Critical, 2 High) |
| Risks registered | 5 (3 Critical, 2 High) |
| Security areas assessed | 10 (5 Weak, 5 Partial, none rated higher) |
| Remediation actions | 10 (4 Critical, 4 High, 2 Medium) |

**Overall assessment:** FinServe has some foundations in place (security policies, daily backups, annual training), but none of the ten areas assessed is rated above Partial. The weakest areas are identity and access management, vulnerability management, security monitoring, incident response, and risk management.

**Most urgent issues**

1. Administrator accounts are not protected by MFA and some employees retain unnecessary access.
2. Vulnerability scanning is irregular, while the internet-facing web application is exposed to serious risks such as SSRF/RCE.
3. There is no centralized security monitoring, so attacks may go undetected.
4. There is no formal incident-response plan.

**Recommendation:** Execute the 10-item remediation plan over 90 days, starting with privileged-account MFA (30 days), then vulnerability management, risk methodology and incident response (45 days). See [Section 12](#12-remediation-roadmap).

---

## 2. Organization Overview

| Attribute | Detail |
|---|---|
| Organization | FinServe India Pvt. Ltd. (fictional) |
| Industry | FinTech |
| Size | About 250 employees |
| Customers | About 100,000 |
| Hosting | AWS |
| Data handled | Sensitive customer data and payment data |
| Key platforms | Web and mobile applications, customer database, payment system (third-party), internal admin portal, Microsoft 365 |

As a FinTech handling customer financial data and payments, FinServe faces high impact from any breach: data exposure, fraudulent transactions, regulatory consequences, and reputational damage.

---

## 3. Assessment Scope

**In scope (9 assets):** web application, mobile application, customer database, AWS infrastructure, employee laptops, payment system, internal admin portal, backup system, and Microsoft 365.

**Security areas assessed (10):** governance, asset management, risk management, identity and access management, data protection, vulnerability management, security monitoring, incident response, backup and recovery, and security awareness.

**Limitations and assumptions**

- The assessment is based only on the learning scenario. No interviews, evidence review, scanning, or penetration testing were performed.
- Where the scenario is silent, a control is not assumed to exist. Several "Partial" ratings reflect missing evidence rather than confirmed failures.
- This is a portfolio assessment. It makes no claim of compliance or certification.

---

## 4. Methodology

**Workflow**

```
Asset Inventory → Threats & Vulnerabilities → Risk Register → Current Profile
→ Target Profile → Gap Analysis → Action Plan → NIST CSF Mapping
```

**Risk scoring:** Risk Score = Likelihood × Impact.

| Likelihood | Score | | Impact | Score |
|---|---|---|---|---|
| Low | 1 | | Low | 1 |
| Medium | 2 | | Medium | 2 |
| High | 3 | | High | 3 |
| | | | Critical | 4 |

| Risk Score | Rating | Meaning |
|---|---|---|
| 1–3 | Low | Monitor and manage through normal processes |
| 4–6 | Medium | Plan remediation and monitor |
| 7–9 | High | Prioritize remediation |
| 10–12 | Critical | Immediate/urgent management attention |

**Current Profile status labels:** *Partial* means some controls or practices exist but are incomplete or unverified. *Weak* means the capability is missing or clearly insufficient.

**Framework alignment:** Findings are mapped to NIST CSF 2.0 Functions, Categories, and Subcategories. The Current Profile, Target Profile, and gap analysis follow NIST's guidance on Organizational Profiles.

**Sources:** NIST CSF 2.0 (February 26, 2024); NIST CSF 2.0 Reference Tool; NIST Organizational Profiles guidance.

---

## 5. Asset Inventory

| ID | Asset | Type | Criticality | Why it matters |
|---|---|---|---|---|
| A001 | Web Application | Application | Critical | Internet-facing; flaws such as SSRF or RCE could give attackers a path to backend systems and internal resources. |
| A002 | Mobile Application | Application | Critical | Gives customers account access; authentication or authorization weaknesses could lead to account takeover and unauthorized transactions. |
| A003 | Customer Database | Database | Critical | Stores sensitive customer data; a breach could cause data exposure, business impact, and regulatory consequences. |
| A004 | AWS Infrastructure | Cloud | Critical | Hosts critical applications; misconfiguration or compromise could cause data exposure or production outages. |
| A005 | Employee Laptops | Endpoint | High | Compromised endpoints enable credential theft, malware, and lateral movement. |
| A006 | Payment System | Third-Party | Critical | Processes financial transactions; compromise could cause fraud, financial loss, and regulatory impact. |
| A007 | Internal Admin Portal | Application | Critical | Provides privileged management functions; compromise could allow modification or deletion of accounts and business data. |
| A008 | Backup System | Infrastructure | Critical | Needed to recover from ransomware, deletion, or failure; compromised backups raise recovery time and risk permanent data loss. |
| A009 | Microsoft 365 | SaaS | High | Corporate email and collaboration; account compromise can lead to phishing, data exposure, and further compromise. |

---

## 6. Risk Assessment

### Risk Register

| Risk | Asset | Threat | Vulnerability | Potential impact | Likelihood | Impact | Score | Rating | Recommended treatment |
|---|---|---|---|---|---|---|---|---|---|
| R001 | Web Application | External attacker | Vulnerable application code / insufficient input validation | Application compromise, unauthorized access to internal resources, data exposure | High (3) | Critical (4) | **12** | **Critical** | Secure coding, SAST/DAST, vulnerability scanning, penetration testing |
| R002 | Customer Database | External attacker | Unnecessary direct network access from external-facing systems; insufficient segmentation | Unauthorized access, customer data exposure, modification, or loss | High (3) | Critical (4) | **12** | **Critical** | Network segmentation, least privilege, database access controls |
| R003 | Employee Laptops | Cybercriminal / malware attacker | Outdated or unpatched software | Malware, credential theft, data loss, lateral movement, disruption | High (3) | High (3) | **9** | **High** | Patch management, EDR, vulnerability management |
| R004 | Backup System | Ransomware attacker / accidental deletion | Backups not sufficiently isolated or protected from modification/deletion | Loss of recovery capability, prolonged disruption, permanent data loss | Medium (2) | Critical (4) | **8** | **High** | Immutable/offline backups, access controls, recovery testing |
| R005 | AWS Infrastructure | External attacker | Overly permissive IAM permissions; insecure cloud configuration | Unauthorized access, data exposure, resource compromise, disruption | High (3) | Critical (4) | **12** | **Critical** | IAM least privilege, MFA, cloud configuration monitoring |

### Risk Heat Map

Cell values are the risk score. Registered risks are shown in brackets.

| Likelihood ↓ / Impact → | Low (1) | Medium (2) | High (3) | Critical (4) |
|---|---|---|---|---|
| **High (3)** | 3 | 6 | 9 **[R003]** | 12 **[R001, R002, R005]** |
| **Medium (2)** | 2 | 4 | 6 | 8 **[R004]** |
| **Low (1)** | 1 | 2 | 3 | 4 |

**Observations:** Three of five risks are Critical, and all three involve external attackers targeting internet-facing or cloud-exposed systems (web application, customer database, AWS). The remaining two risks (endpoint patching and backup protection) rate High.

---

## 7. Current Profile

| # | Security area | Current situation | Status |
|---|---|---|---|
| 1 | Governance | Security policies exist but are not regularly reviewed. | Partial |
| 2 | Asset Management | Major assets are known, but there is no evidence of a formal, continuously maintained inventory. | Partial |
| 3 | Risk Management | No formal cybersecurity risk-assessment process is described. | Weak |
| 4 | Identity & Access Management | MFA is not enforced for administrators, and some employees retain unnecessary access. | Weak |
| 5 | Data Protection | Sensitive customer and payment data exists, but evidence of comprehensive protection controls is insufficient. | Partial |
| 6 | Vulnerability Management | Vulnerability scanning is performed irregularly rather than through a consistent process. | Weak |
| 7 | Security Monitoring | No centralized SIEM or security monitoring capability is described. | Weak |
| 8 | Incident Response | No formal incident-response plan or documented process exists. | Weak |
| 9 | Backup & Recovery | Daily backups are maintained, but isolation and recovery testing are not indicated. | Partial |
| 10 | Security Awareness | Annual training exists, but there is no evidence of continuous training or phishing simulations. | Partial |

**Summary:** 5 areas Weak, 5 areas Partial, 0 areas rated higher.

---

## 8. Target Profile

| # | Security area | Target state |
|---|---|---|
| 1 | Governance | Regular policy review and update process |
| 2 | Asset Management | Centralized, maintained asset inventory |
| 3 | Risk Management | Formal risk assessment process and risk register |
| 4 | Identity & Access Management | MFA, least privilege, and regular access reviews |
| 5 | Data Protection | Data classification, encryption, and access controls |
| 6 | Vulnerability Management | Regular scanning with risk-based remediation |
| 7 | Security Monitoring | Centralized logging, monitoring, and alerting |
| 8 | Incident Response | Documented and tested incident-response plan |
| 9 | Backup & Recovery | Protected backups and tested recovery |
| 10 | Security Awareness | Continuous awareness program |

---

## 9. Gap Analysis

| Area | Current state | Target state | Gap | Priority |
|---|---|---|---|---|
| Governance | Policies not regularly reviewed | Regular policy review and update process | No formal policy-review process | Medium |
| Asset Management | Basic/uncertain inventory | Centralized, maintained inventory | Inventory not formally maintained | High |
| Risk Management | No formal process | Formal risk assessment and risk register | No documented risk-assessment process | High |
| Identity & Access Management | Incomplete MFA, excessive access | MFA, least privilege, regular access reviews | Missing admin MFA and access reviews | **Critical** |
| Data Protection | Controls unclear | Classification, encryption, access controls | Controls need verification and improvement | High |
| Vulnerability Management | Irregular scanning | Regular scanning, risk-based remediation | No consistent vulnerability-management process | **Critical** |
| Security Monitoring | No centralized SIEM | Centralized logging, monitoring, alerting | No centralized security monitoring | **Critical** |
| Incident Response | No formal plan | Documented and tested IR plan | IR capability not formalized | **Critical** |
| Backup & Recovery | Daily backups | Protected backups and tested recovery | Backup isolation and recovery testing missing | High |
| Security Awareness | Annual training | Continuous awareness program | Awareness program is limited | Medium |

---

## 10. NIST CSF 2.0 Mapping

### CSF 2.0 Core Functions

| Function | Meaning |
|---|---|
| GOVERN (GV) | Cybersecurity risk management strategy, expectations, and policy are established, communicated, and monitored |
| IDENTIFY (ID) | Cybersecurity risk to the organization, assets, and individuals is understood |
| PROTECT (PR) | Safeguards to manage cybersecurity risks are used |
| DETECT (DE) | Possible cybersecurity attacks and compromises are found and analyzed |
| RESPOND (RS) | Actions regarding a detected cybersecurity incident are taken |
| RECOVER (RC) | Assets and operations affected by a cybersecurity incident are restored |

### Findings mapped to CSF outcomes

| Finding | Area | Function | Category | Subcategories | Outcome (simplified) | Current | Priority |
|---|---|---|---|---|---|---|---|
| RA-01 | Governance | GOVERN | GV.PO (Policy) | GV.PO-02 | Cybersecurity risk policy is reviewed, updated, communicated, and enforced as requirements, threats, and technology change | Partial | Medium |
| RA-02 | Asset Management | IDENTIFY | ID.AM (Asset Management) | ID.AM-01, ID.AM-02 | Inventories of hardware, software, services, and systems are maintained | Partial | High |
| RA-03 | Risk Management | IDENTIFY | ID.RA (Risk Assessment) | ID.RA-04, ID.RA-05 | Impacts and likelihoods are recorded; threats, vulnerabilities, likelihoods, and impacts inform risk prioritization | Weak | High |
| RA-04 | Identity & Access Management | PROTECT | PR.AA (Identity Management, Authentication, and Access Control) | PR.AA-03, PR.AA-05 | Users, services, and hardware are authenticated; access permissions are managed and reviewed using least privilege and separation of duties | Weak | Critical |
| RA-05 | Data Protection | PROTECT | PR.DS (Data Security) | PR.DS-01, PR.DS-02 | Data at rest and in transit is protected | Partial | High |
| RA-06 | Vulnerability Management | IDENTIFY / PROTECT | ID.RA (Risk Assessment); PR.PS (Platform Security) | ID.RA-01, PR.PS-02 | Vulnerabilities are identified, validated, and recorded; software is maintained securely | Weak | Critical |
| RA-07 | Security Monitoring | DETECT | DE.CM (Continuous Monitoring) | DE.CM-01, DE.CM-03 | Networks and personnel technology activity are monitored to find potentially adverse events | Weak | Critical |
| RA-08 | Incident Response | RESPOND | RS.MA (Incident Management); RS.CO (Incident Response Reporting and Communication); RS.MI (Incident Mitigation) | RS.MA-01, RS.CO-02, RS.MI-01 | Incidents are managed, communicated, and contained | Weak | Critical |
| RA-09 | Backup & Recovery | PROTECT / RECOVER | PR.DS (Data Security); RC.RP (Incident Recovery Plan Execution) | PR.DS-11, RC.RP-01 | Backups are created, protected, maintained, and tested; the recovery plan is executed after an incident | Partial | High |
| RA-10 | Security Awareness | PROTECT | PR.AT (Awareness and Training) | PR.AT-01 | Personnel receive awareness training so they can perform tasks with cybersecurity risks in mind | Partial | Medium |


---

## 11. Top Security Findings

| #   | Finding                                                                                                                                                          | Related risk     | NIST reference               | Business impact                                                                   | Priority |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | ---------------------------- | --------------------------------------------------------------------------------- | -------- |
| 1   | **Administrator accounts lack MFA and some users retain excessive access.** A stolen admin credential could compromise the admin portal, AWS, or customer data.  | R005             | PR.AA-03, PR.AA-05           | Unauthorized access, data exposure, or modification of accounts and business data | Critical |
| 2   | **Vulnerability management is irregular.** The internet-facing web application and employee laptops are not scanned or patched on a consistent schedule.         | R001, R003       | ID.RA-01, PR.PS-02           | Application compromise (SSRF/RCE), malware, and credential theft                  | Critical |
| 3   | **Customer database has unnecessary direct network access from external-facing systems.** Weak segmentation means a web-tier compromise can reach customer data. | R002             | PR.AA-05, PR.DS-01           | Customer data exposure, modification, or loss                                     | Critical |
| 4   | **No centralized security monitoring.** Without logging and alerting, attacks against critical systems may go undetected.                                        | R001, R002, R005 | DE.CM-01, DE.CM-03           | Delayed detection and larger breach impact                                        | Critical |
| 5   | **No formal incident-response plan.** Roles, escalation, and containment steps are undefined.                                                                    | All              | RS.MA-01, RS.CO-02, RS.MI-01 | Slower, uncoordinated response and higher business impact                         | Critical |
| 6   | **Backups may not be isolated or tested.** Daily backups exist, but protection against ransomware or deletion and restore testing are unconfirmed.               | R004             | PR.DS-11, RC.RP-01           | Prolonged outage or permanent data loss                                           | High     |

---

## 12. Remediation Roadmap

### Action plan

| ID | Remediation | Addresses gap | Priority | Owner | Target |
|---|---|---|---|---|---|
| RA-04 | Enforce MFA for privileged accounts and least-privilege access; perform access reviews | Admin MFA missing, excessive access | Critical | IAM/Security | 30 days |
| RA-06 | Establish recurring vulnerability scanning and risk-based remediation | Irregular scanning | Critical | Security | 30–45 days |
| RA-03 | Establish risk methodology and maintain a risk register | No formal risk assessment | High | GRC/Security | 45 days |
| RA-08 | Develop, approve, communicate, and test an incident-response plan | No IR plan | Critical | Security/IR | 45 days |
| RA-02 | Create a centralized asset inventory and assign asset owners | Inventory not maintained | High | IT + Security | 60 days |
| RA-09 | Protect backups, isolate where appropriate, and test restoration | Backup isolation/testing unclear | High | IT Infrastructure | 60 days |
| RA-01 | Establish annual policy review and update process | No policy-review process | Medium | GRC/Security | 60 days |
| RA-05 | Classify sensitive data; implement access controls and encryption | Data-protection controls unverified | High | Data Security/IT | 90 days |
| RA-07 | Implement centralized logging/SIEM and alerting for critical systems | No centralized monitoring | Critical | SOC/Security | 90 days |
| RA-10 | Establish onboarding, recurring awareness, and phishing exercises | Annual training only | Medium | Security + HR | 90 days |

### Phased timeline

| Phase | Timeframe | Actions | Focus |
|---|---|---|---|
| 1 | Days 0–45 | RA-04, RA-06, RA-03, RA-08 | Close the most urgent exposure: privileged access, vulnerabilities, risk method, incident response |
| 2 | Days 46–60 | RA-02, RA-09, RA-01 | Build foundations: inventory, backup protection, policy review |
| 3 | Days 61–90 | RA-05, RA-07, RA-10 | Mature controls: data protection, centralized monitoring, awareness |

### Risk-to-action traceability

| Risk | Addressed by |
|---|---|
| R001 Web Application | RA-06 (scanning and remediation); secure coding, SAST/DAST, and penetration testing are recommended treatments |
| R002 Customer Database | RA-05 (access controls) in part; **network segmentation is not yet covered by a dedicated action** and is recommended as an addition |
| R003 Employee Laptops | RA-06 (vulnerability and patch management) |
| R004 Backup System | RA-09 |
| R005 AWS Infrastructure | RA-04 (MFA and least privilege); cloud configuration monitoring supported by RA-07 |

---

## 13. Conclusion

FinServe India has basic security practices in place, but its posture is foundational: half of the assessed areas are Weak and none is rated above Partial. The risk register shows three Critical risks, all tied to externally exposed systems. The most important improvements are protecting privileged access with MFA, establishing consistent vulnerability management, centralizing monitoring, and formalizing incident response.

Completing the 10-item roadmap over 90 days would move every area toward its Target Profile and give the organization a repeatable, framework-aligned risk process.

**Limitations**

- The assessment is scenario-based and relies on the information provided. Areas rated Partial or Weak because of missing evidence should be recorded as "Not Assessed/Unknown" until validated in a real engagement.
- The risk register covers five of nine in-scope assets. The mobile application, payment system, admin portal, and Microsoft 365 have not yet been risk-assessed.

**Recommended next steps**

1. Extend the risk register to all nine assets, including the third-party payment system.
2. Add a dedicated action for network segmentation (R002).
3. Re-assess after the 90-day plan and compare the new Current Profile against the Target Profile.
4. Broaden GOVERN coverage (roles and responsibilities, risk strategy, supply-chain risk).

---

*This report is a fictional portfolio exercise based on NIST CSF 2.0. It is not a compliance or certification assessment.*
