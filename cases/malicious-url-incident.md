# SOC Simulation Case Report

**Analyst:** Huldreich de Oliveira  
**Role:** SOC Analyst (Blue Team)  
**Simulation Platform:** TryHackMe SOC Simulator  
**Date:** 02/09/2026  
**Alert ID:** 8816  
**Alert Type:** Access to Blacklisted External URL Blocked by Firewall  
**Severity:** High  
**Source:** Firewall / SIEM  

---

## 1. Time of Activity
- **Start:** 02/09/2026 22:16:35  
- **End:** 02/09/2026 22:18:00  

---

## 2. List of Affected Entities
- **Source IP:** 10.20.2.17  
- **Destination IPs:**  
  - 67.199.248.11 (malicious URL)  
  - 142.250.64.78 (legitimate web activity)  
- **Destination Ports:** 80, 443  
- **Protocol:** TCP  
- **Application:** web-browsing  

### 2.1 Technical Event Metadata
- **Firewall Action:** Blocked (Deny)  
- **Rule Triggered:** URL Filtering – Threat Intelligence Feed  
- **URL Category:** Malicious / Phishing  
- **Session Duration:** < 5 seconds  
- **Bytes Sent:** Minimal (HTTP request only)  
- **Bytes Received:** 0 (connection terminated by firewall)  
- **NAT Translation:** Internal to External (10.20.2.17 → Public IP)  
- **User Identification:** Associated user mapped via firewall logs (if available)  

> The metadata confirms that the connection attempt was interrupted at the perimeter level before content retrieval.

---

## 3. Reason for Classifying as True Positive
- Alert corresponds to a known malicious URL blocked by the firewall.  
- Source IP previously performed normal web activity (payroll system search).  
- Attempt to access blacklisted URL confirms a genuine threat.  
- Firewall intervention prevented any compromise.  

### 3.1 Threat Intelligence Validation
- URL reputation categorized as **high-risk**  
- Associated with **phishing distribution infrastructure**  
- Observed in recent **threat intelligence feeds**  

> This confirms the alert as a genuine malicious indicator rather than a false positive.

---

## 4. Escalation Decision
- Escalation **not necessary** because:  
  - Connection successfully blocked by perimeter security  
  - No evidence of download, credential submission, or suspicious follow-up activity  
  - Event contained at firewall level  

- **Case Closure:** Tier 1 with monitoring recommendations  

### 4.1 Risk Assessment
- Severity classified as **High** due to:  
  - Confirmed malicious destination  
  - Potential phishing-related infrastructure  
  - User-initiated outbound connection attempt  

- **Final Risk Level:** Contained / No Compromise Observed

---

## 5. Recommended Remediation Actions
1. Monitor the source IP for additional suspicious activity.  
2. Educate the user about phishing, social engineering, and blacklisted URLs.  
3. Ensure firewall and threat intelligence feeds are updated.  
4. Optionally block the malicious URL at endpoint or proxy level.  
5. Document the incident and update SOC playbooks for similar alerts.  

---

## 6. List of Attack Indicators
- Blocked request to `http://bit.ly/3sHkX3da12340`  
- Source IP `10.20.2.17` attempted access to blacklisted domain  
- Protocol: TCP  
- Application: web-browsing  
- Timestamp: 02/09/2026 22:16:35  

### 6.1 MITRE ATT&CK Mapping
- **T1566 – Phishing**  
- **T1204 – User Execution**  
- **T1071.001 – Application Layer Protocol: Web Protocols**  

> Behavioral pattern aligns with early-stage phishing or user-driven web-based attack attempts.

---

## 7. Evidence / Prints

### Print 1 – SIEM Event Screenshot
![SIEM Event Screenshot](images/siem_event_screenshot.png)  
*Screenshot shows both the malicious blocked URL and previous normal web activity from the same source IP, providing context for investigation.*

### Print 2 – Alert Details Screenshot
![Alert Details Screenshot](images/alert_details_screenshot.png)  
*Full alert details captured in SIEM for incident documentation and verification.*

### Print 3 – Analyst Comment / Case Note
![Analyst Comment Screenshot](images/analyst_comment_screenshot.png)  
*Final SOC analyst comment summarizing True Positive determination and next steps for remediation.*

### Print 4 – Threat Validation (Try Detect This)
![Threat Validation Screenshot](images/threat_validation_screenshot.png)  
*Screenshot from Try Detect This confirming the blocked URL as malicious, supporting the True Positive classification in the SOC investigation.*

---

## 8. Post-Click Activity Investigation
- Reviewed firewall logs for subsequent allowed connections  
- Searched for repeated connection attempts to same/similar domains  
- Investigated file download attempts (`.exe`, `.zip`, `.js`, `.docm`, `.xlsm`, `.ps1`)  
- Reviewed traffic for unusual outbound connections (C2)  

**Findings:**  
- No successful connection to malicious IP observed  
- No additional suspicious domains contacted  
- No evidence of file downloads or abnormal traffic  
- No indicators of persistence or lateral movement  

### 8.1 Investigative Reasoning
- Validated absence of:  
  - Cached malicious content retrieval  
  - Secondary redirects  
  - Prior compromise before blacklist update  
  - Malware beaconing  

> Correlating firewall logs and outbound traffic patterns supports closure without escalation.

### 8.2 Detection & Prevention Recommendations
- Enable browser isolation or URL sandboxing  
- Implement DNS-layer filtering for malicious domains  
- Correlate firewall blocks with endpoint telemetry  
- Trigger automated user notifications on blocked high-risk domains  

> These improvements enhance proactive defense and user awareness.

---

## 9. Summary / Conclusion
- Incident confirmed as **True Positive**  
- Firewall blocked malicious attempt, preventing compromise  
- SOC analysts documented incident and recommended remediation actions  
- Monitoring both anomalous and normal activity is key to early threat detection  

---
