# Orion Health Services – Ransomware Incident Response

**Incident ID:** 1441  
**Date:** February 10, 2026  
**Prepared by:** Huldreich M. – Cybersecurity Analyst  

---

## Executive Summary

On February 10, 2026, Orion Health Services experienced a ransomware incident initiated through a phishing email delivered to a member of the Finance team. The email contained a malicious Excel attachment which, once opened, enabled unauthorized access to internal systems.

The attacker successfully established persistence and performed lateral movement across portions of the internal network before deploying ransomware. This resulted in encryption of files across multiple internal systems.

The incident caused temporary operational disruption affecting Finance, HR, and shared infrastructure services.

While sensitive data such as payroll records and patient appointment information may have been accessible during the attacker’s dwell time, no confirmed evidence of data exfiltration has been identified at this stage. Investigation remains ongoing.

Swift containment actions significantly reduced further impact and prevented organization-wide encryption.

---

## Incident Timeline

**08:12 AM** – Phishing email delivered to Finance employee  
**08:27 AM** – Malicious Excel attachment opened  
**09:05 AM** – Suspicious outbound traffic detected (C2 beaconing behavior)  
**11:40 AM** – Multiple failed login attempts and lateral authentication activity observed  
**12:15 PM** – Users reported inability to access shared drives  
**12:22 PM** – Ransom note discovered on network share  
**12:30 PM** – Incident Response Plan activated  
**12:35 PM** – Affected systems isolated  

The inclusion of a structured timeline demonstrates investigative clarity and response coordination.

---

## Technical Overview

Initial analysis indicates:

- Phishing email bypassed existing email filtering controls
- Malicious macro execution established reverse command-and-control communication
- Attacker leveraged valid credentials to perform lateral movement
- Ransomware deployed following internal reconnaissance
- Backup server partially encrypted; however, core backup repositories remained intact

### MITRE ATT&CK Mapping (Preliminary)

- T1566 – Phishing  
- T1059 – Command Execution  
- T1078 – Valid Accounts  
- T1486 – Data Encrypted for Impact  

Mapping observed behaviors to MITRE ATT&CK supports defensive improvement planning and threat modeling alignment.

---

## Business Impact

### Operational Impact

- Temporary unavailability of file services
- Disruption to payroll processing
- Delayed patient appointment scheduling workflows

### Data Exposure Risk

Potential exposure included:

- Payroll records
- Patient appointment schedules
- Internal credential artifacts

No confirmed data exfiltration was detected based on:

- Firewall log analysis
- NetFlow review
- Endpoint Detection & Response (EDR) telemetry

Forensic validation remains ongoing to confirm findings with high confidence.

---

## Actions Taken

Upon confirmation of ransomware activity:

- Incident Response Plan activated
- Network segmentation enforced
- Compromised accounts disabled and credentials reset
- EDR sweep conducted across affected endpoints
- Forensic image acquisition initiated
- Backup restoration from verified clean snapshots started
- Executive and Legal teams formally notified

A structured containment strategy limited further lateral expansion and prevented full environmental encryption.

---

## Risk and Regulatory Considerations

As Orion Health Services manages healthcare-related information and employee financial data, this incident presents potential:

- Regulatory implications (healthcare and data protection laws)
- Legal notification obligations
- Reputational exposure risks

Legal counsel has been engaged to assess reporting and compliance requirements.

---

## Root Cause Analysis (Preliminary)

Primary contributing factors identified:

- Email security controls failed to block phishing payload
- Macro execution was not restricted by organizational policy
- Lack of strict least-privilege enforcement enabled lateral movement
- Insufficient network segmentation between departments

The incident resulted from a chain of control weaknesses rather than a single failure point.

---

## Lessons Learned & Strategic Recommendations

This incident reinforces that ransomware attacks are typically progressive — consisting of multiple detection opportunities before final impact.

### Immediate Improvements

- Enforce organization-wide macro restrictions
- Implement stricter conditional access policies
- Enhance monitoring of outbound traffic anomalies
- Increase phishing simulations and awareness training

### Mid-Term Improvements

- Deploy advanced email sandboxing solutions
- Strengthen network segmentation architecture
- Implement Privileged Access Management (PAM)
- Conduct ransomware tabletop simulation exercises

### Long-Term Strategy

- Expand SOC detection engineering capabilities
- Regular adversary simulation and red team assessments
- Establish formalized threat hunting program

---

## Current Status

- Ransomware contained
- Core systems restoring from verified clean backups
- Forensic investigation ongoing
- Heightened monitoring maintained across environment
- No ransom payment issued

Operations are progressively returning to normal under increased security oversight.

---

## Closing Statement

Although this incident caused temporary operational disruption, coordinated response efforts between IT, Security, and Executive leadership significantly reduced overall impact.

This event serves as a catalyst to strengthen Orion Health Services’ cybersecurity posture, enhance resilience, and reinforce protection of patient and employee data.

The organization remains committed to continuous improvement and proactive risk management.
