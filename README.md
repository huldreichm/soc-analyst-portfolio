# SOC Incident Analysis Portfolio

## Overview

This repository contains documented incident investigations performed in a simulated Security Operations Center (SOC) environment.

The objective of this portfolio is to demonstrate:

- Structured security event investigation methodology
- SIEM log analysis (Splunk & Elastic)
- Windows Security Event Log analysis
- RDP and VPN activity investigation
- Phishing detection and validation
- MITRE ATT&CK technique mapping
- Incident documentation and reporting standards
- Analytical reasoning and false positive validation

---

## Tools & Technologies

- Splunk (SPL)
- Elastic Stack (KQL)
- Windows Security Event Logs
- Firewall Log Analysis
- VPN Log Investigation
- MITRE ATT&CK Framework
- Threat Intelligence Validation

---

## Investigation Methodology

Each case follows a structured workflow:

1. Alert identification  
2. Initial triage and scope definition  
3. Log correlation across multiple data sources  
4. Event validation and evidence collection  
5. Behavioral analysis  
6. Threat classification  
7. MITRE ATT&CK mapping  
8. Risk assessment and final determination  

Full methodology details are available in the `methodology/` directory.

---

## Case Studies

### VPN Brute Force Analysis
Investigation of abnormal VPN authentication spikes, identification of source IP behavior patterns, and validation of credential abuse attempts.

### RDP Logon Investigation
Analysis of Windows Logon Types, failed authentication patterns, and detection of potential lateral movement activity within a controlled lab environment.

### Phishing – User Click Investigation
Inbound phishing email analysis including header authentication validation (SPF/DKIM/DMARC), domain reputation analysis, firewall correlation, and endpoint impact assessment following confirmed user interaction.

### Ransomware Incident Response Simulation
End-to-end investigation of a simulated ransomware attack including initial phishing vector identification, lateral movement analysis, impact assessment, containment strategy, and MITRE ATT&CK mapping.

### False Positive Validation Case
Investigation of a medium-severity alert initially flagged as suspicious but determined to be legitimate administrative activity after log correlation and contextual validation.

---

## Documentation & AI Usage Disclosure

AI tools were used exclusively to refine documentation structure, improve formatting consistency, and enhance clarity of written reports.

All investigative analysis, log review, technical validation, and incident classification were performed independently based on evidence evaluation.

AI assistance was utilized as a documentation support tool, not as a substitute for analytical reasoning or technical investigation.

---

## Disclaimer

All investigations were performed in a controlled lab environment.  
Certain telemetry values may reflect simulated data for educational and demonstration purposes.

---

## Author

Huldreich M.  
Security Operations Center (SOC) Analyst – Entry Level  
Focused on detection engineering development and incident response skill progression.
