# SOC Investigation Framework

This document describes the standard investigation approach applied across the security cases documented in this portfolio.

The objective is to ensure consistency, analytical clarity, and evidence-based conclusions.

---

## 1. Alert Triage

The investigation begins with validation of the alert:

- Confirm alert source (SIEM, EDR, Firewall, Email Gateway)
- Review rule logic and severity level
- Identify affected user, endpoint, and IP address
- Determine potential false positive indicators

If the alert demonstrates credible risk, the investigation proceeds.

---

## 2. Log Analysis & Correlation

Relevant logs are reviewed to establish context:

- SIEM event logs
- Firewall traffic logs
- Endpoint telemetry
- Email header authentication (SPF, DKIM, DMARC)
- DNS queries (if applicable)

The goal is to answer:

- What happened?
- When did it occur?
- Who was involved?
- Was malicious infrastructure contacted?

---

## 3. Threat Validation

If suspicious indicators are identified:

- Validate domain/IP reputation
- Check domain age and typosquatting patterns
- Look for execution or abnormal process activity
- Identify possible Indicators of Compromise (IOCs)

Findings are documented before proceeding.

---

## 4. Impact Assessment

The investigation evaluates whether:

- User interaction occurred
- Malware was executed
- Credentials may have been exposed
- Lateral movement occurred
- Additional systems were affected

Conclusions are based strictly on observable evidence.

---

## 5. MITRE ATT&CK Mapping

Observed activity is mapped to relevant MITRE ATT&CK techniques when applicable to:

- Understand adversary behavior
- Improve detection coverage
- Support defensive analysis

---

## 6. Risk Classification & Case Closure

Each case is classified as:

- True Positive (Compromised)
- True Positive (User Interaction – No Compromise)
- False Positive
- Informational

Final classification is supported by documented evidence.

---

## Guiding Principle

All investigations follow a structured and evidence-driven approach.

The objective is not only to close alerts, but to validate risk exposure and strengthen defensive posture.
