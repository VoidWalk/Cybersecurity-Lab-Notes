# 📁 Portfolio Project: Botium Toys Security Audit

## 📌 Project Overview
Botium Toys is a growing U.S. toy manufacturer expanding its global online presence. As part of an internal IT security audit, this assessment evaluates the company's current security posture against the **NIST Cybersecurity Framework (CSF)**, **PCI DSS**, **GDPR**, and **SOC 1 / SOC 2** standards to identify risks, missing controls, and regulatory compliance gaps.

---

## 🛠️ Controls Assessment Checklist

| Control Category | Control Name | Implemented (Yes/No) | Operational Status & Notes |
| :--- | :--- | :---: | :--- |
| **Administrative** | Least Privilege | **No** | Broad employee access to internal data, PII, and SPII. |
| **Administrative** | Separation of Duties | **No** | Lack of defined role-based access limits. |
| **Administrative** | Password Policies | **Yes** | Policy exists, but requirements are nominal and non-compliant. |
| **Administrative** | Disaster Recovery Plans | **No** | No business continuity or recovery plans established. |
| **Technical** | Firewall | **Yes** | Configured and filtering network traffic according to rules. |
| **Technical** | Antivirus (AV) Software | **Yes** | Active, installed, and monitored regularly by IT. |
| **Technical** | Intrusion Detection System (IDS) | **No** | No network intrusion detection deployed. |
| **Technical** | Critical Data Backups | **No** | No automated or scheduled backups of business data. |
| **Technical** | Data Encryption | **No** | Credit card data stored and transmitted in plaintext locally. |
| **Technical** | Centralized Password Manager | **No** | Missing centralized enforcement for password complexity. |
| **Technical** | Legacy System Maintenance | **Yes** | Manual monitoring present, but lacks regular scheduling. |
| **Physical** | Facility & Office Locks | **Yes** | Sufficient physical locks on office, storefront, and warehouse. |
| **Physical** | CCTV Surveillance | **Yes** | Up-to-date video monitoring active. |
| **Physical** | Fire Detection & Suppression | **Yes** | Functioning fire alarm and sprinkler systems present. |

---

## ⚖️ Regulatory Compliance Gaps

### 1. Payment Card Industry Data Security Standard (PCI DSS)
* ❌ **Failed:** Unrestricted internal access allows unauthorized employees to view cardholder data.
* ❌ **Failed:** Credit card numbers are stored and processed locally without data encryption.
* ❌ **Failed:** Password enforcement policies do not meet modern security requirements.

### 2. General Data Protection Regulation (GDPR)
* ❌ **Failed:** E.U. customer data lacks adequate privacy protection due to missing encryption.
* ❌ **Failed:** Assets are not fully inventoried or classified under NIST CSF *Identify* guidelines.
* ⚠️ **Passed:** A 72-hour E.U. customer breach notification plan is active and documented.

### 3. System and Organization Controls (SOC 1 / SOC 2)
* ❌ **Failed:** User access control policies fail to enforce confidentiality for PII/SPII.
* ⚠️ **Passed:** Data availability and data integrity controls remain functional.

---

## 🎯 Executive Recommendations
1. **Enforce Least Privilege & RBAC:** Immediately restrict employee data access so only authorized billing personnel can handle PII, SPII, and payment data.
2. **Deploy Encryption Standards:** Apply AES-256 encryption to stored and in-transit payment data to satisfy PCI DSS and GDPR mandates.
3. **Establish Backup & Recovery:** Build automated daily off-site backups and document a formal Disaster Recovery Plan (DRP) to guarantee business continuity.
4. **Deploy Intrusion Detection (IDS):** Install an network-based IDS alongside the existing firewall to monitor for active network threats.
5. **Modernize Password Governance:** Implement a centralized password manager to enforce complex password rules and reduce IT ticket overhead.
