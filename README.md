# SOC Detection & Incident Analysis Project

## 1. Context and Objective

This project aims to demonstrate a **Security Operations Center (SOC) mindset** through structured investigation questions, incident analysis logic, and escalation criteria.

The focus is not on specific tools, but on **how alerts are validated, investigated, documented, and escalated** in a risk-sensitive environment such as a financial institution.

This repository represents the **thinking framework** that will later be implemented in a hands-on SIEM lab.

---

## 2. SOC Operating Model (High-Level)

The operational flow followed in this project is:

1. Alert ingestion  
2. Initial validation (false positive vs potential incident)  
3. Context gathering (logs, asset criticality, user behavior)  
4. Risk and impact assessment  
5. Decision: continue investigation or escalate  
6. Documentation and handover  

This mirrors a **Tier 1 / Tier 2 SOC workflow**.

---

## 3. Core SOC Investigation Questions

These questions guide every analysis in this project:

- Is the alert legitimate or a false positive?
- Which asset is affected and what is its criticality?
- Is this an isolated event or part of a broader pattern?
- What is the potential business and security impact?
- Does this event violate internal security policies?
- Should this be escalated immediately or investigated further?

---

## 4. Incident Analysis by Category

### 4.1 Suspicious Authentication Activity

**Key Questions:**
- Is the login time consistent with the user’s normal behavior?
- Is the source IP known, trusted, or anomalous?
- Are there multiple failed attempts followed by a success?
- Were privileges changed after authentication?
- Are other accounts affected from the same source?

**Logs of Interest:**
- Authentication logs  
- VPN / remote access logs  
- Identity provider logs  

---

### 4.2 Phishing Attempts

**Key Questions:**
- Did the email pass SPF, DKIM, and DMARC checks?
- Did the user interact with links or attachments?
- Are there other internal recipients?
- Are indicators (URL, domain, hash) already known?
- Is blocking or takedown required?

**Logs of Interest:**
- Email gateway logs  
- User interaction logs  
- Web proxy logs  

---

### 4.3 Endpoint / Malware Alerts

**Key Questions:**
- Is the process legitimate or suspicious (living-off-the-land)?
- Was the execution performed with elevated privileges?
- Is there evidence of persistence or lateral movement?
- Is the endpoint associated with sensitive data?
- Should the host be isolated?

**Logs of Interest:**
- Endpoint detection logs  
- Process creation logs  
- Network connection logs  

---

### 4.4 Network Anomalies

**Key Questions:**
- Is the traffic expected for this host and service?
- Is communication occurring with unusual geolocations?
- Is the traffic volume consistent with baseline behavior?
- Could this indicate scanning, beaconing, or exfiltration?
- Should network or firewall teams be involved?

**Logs of Interest:**
- Firewall logs  
- NetFlow / traffic analysis  
- IDS/IPS alerts  

---

## 5. Risk Assessment Approach

Each event is evaluated based on:

- **Asset criticality** (user workstation vs core system)
- **Likelihood** of malicious activity
- **Potential impact** (data exposure, service disruption)
- **Regulatory and compliance considerations**

This ensures decisions are **risk-based**, not tool-driven.

---

## 6. Escalation Criteria

An incident should be escalated immediately if:

- A privileged or high-risk account is involved
- Critical systems are affected
- There is evidence of malware or lateral movement
- Sensitive or regulated data may be impacted
- Multiple correlated alerts indicate coordinated activity

Escalation should include:

- Clear timeline  
- Observed indicators  
- Actions already taken  
- Outstanding risks  

---

## 7. Documentation Principles

- Facts are documented separately from assumptions
- All actions are time-stamped
- Evidence is preserved
- Communication follows need-to-know principles

This aligns with audit and compliance expectations in regulated environments.

---

## 8. Lessons Learned

After each investigation:

- Could detection have been earlier?
- Were false positives avoidable?
- Are new detection rules or playbooks needed?
- Should procedures be updated?

---

## 9. Future Implementation

Planned next steps:

- Deploy a SIEM environment
- Simulate incidents aligned with the scenarios above
- Create detection rules and dashboards
- Produce incident reports and SOC playbooks

---

## 10. Final Note

This project emphasizes **process, judgment, and operational discipline**, which are core competencies for SOC roles, particularly in high-risk and regulated sectors such as banking.
