# SOC Threat Hunting Case Report – Operation Health Hazard

**Analyst:** Huldreich M.  
**Date:** 21 June 2025  
**TLP:** AMBER – Internal  

---

## 1. Executive Summary

A simulated threat hunting exercise identified a **supply chain compromise** via a malicious npm package. The stager was executed on **PAW-TOM**, triggering subsequent outbound connections on **PAW-TABITHA** and minor lateral movement to **PAW-PENNY**.  

**Key Findings:**

- **PAW-TOM**: Executed PowerShell stager  
- **PAW-TABITHA**: Beacon activity (outbound connections)  
- **PAW-PENNY**: Minor lateral movement  

This report highlights the **analytical process**, including Splunk queries used, log interpretation, and reasoning.

---

## 2. Investigation Hypothesis

**Hypothesis:**  
A compromised npm package allowed execution of a PowerShell stager, establishing a beacon and potential lateral movement.

**Analytical Approach:**  

1. Identify PowerShell executions triggered by npm postinstall scripts.  
2. Correlate **EventCode 1 and EventCode 3** across all hosts.  
3. Trace network connections to external domains.  
4. Validate sequence of execution using timestamps and host logs.

**Status:** Proven

---

## 3. Attack Chain Timeline

| Stage | MITRE Technique | Host | User | Queries & Reasoning | Evidence / IOCs | Timestamp |
|-------|----------------|------|------|-------------------|----------------|-----------|
| 1 | T1659 – Stager Execution | PAW-TOM | itadmin-tom | `index=main EventCode=1 Host=PAW-TOM | search "powershell.exe -EncodedCommand"`<br>Identified PowerShell stager execution triggered by npm package | `C:\Users\itadmin-tom\AppData\Roaming\SystemHealthUpdater.exe`<br>DNS query: `global-update.wlndows.thm`<br>NPM package: `compromised-package-name` | 21-Jun-2025 19:46:06 |
| 2 | T1071 – Application Layer Protocol | PAW-TABITHA | N/A | `index=main EventCode=3 Host=PAW-TABITHA | stats count by dest_ip,dest_port`<br>Outbound connections indicate beacon activity | HTTP GET: `http://global-update.wlndows.thm/SystemHealthUpdater.exe`<br>External IPs / ports | 21-Jun-2025 19:47:01 |
| 3 | T1021 – Remote Services / Lateral Movement | PAW-PENNY | N/A | `index=main EventCode=3 Host=PAW-PENNY | stats count by dest_ip,dest_port`<br>Minor connections indicate limited lateral spread | EventCode 3 connections, external IPs/ports | 21-Jun-2025 19:47:40 |

---

## 4. Assets Impacted

| Host | Role | Observations | Analytical Notes |
|------|------|--------------|-----------------|
| PAW-TOM | Initial Compromise | PowerShell stager executed, DNS C2 resolution | Confirmed EventCode 1 and npm package execution |
| PAW-TABITHA | Beacon Host | 19 outbound connections (EventCode 3) | Beacon activity correlates with PAW-TOM execution timestamp |
| PAW-PENNY | Secondary / Lateral | 6 outbound connections | Minor lateral movement, consistent with simulation |

---

## 5. Indicators of Compromise (IOCs)

**Host-Based IOCs**

- `C:\Users\itadmin-tom\AppData\Roaming\SystemHealthUpdater.exe`  
- `powershell.exe -NoP -W Hidden -EncodedCommand <Base64>`  
- NPM Package: `compromised-package-name`  

**Network-Based IOCs**

- Domain: `global-update.wlndows.thm`  
- URL: `http://global-update.wlndows.thm/SystemHealthUpdater.exe`  
- EventCode 3 outbound connections (Tabitha & Penny)  

Each IOC is **linked to host, stage, and reasoning**, showing correlation skills.

---

## 6. Analysis & Threat Narrative

1. **Initial Access (PAW-TOM):** Stager execution via npm package confirmed by EventCode 1 logs.  
2. **Command & Control (PAW-TABITHA):** Outbound connections consistent with beacon activity.  
3. **Lateral Movement (PAW-PENNY):** Minor outbound traffic indicates limited lateral propagation.  

**Note:** The report highlights **how each observation was tied to logs, queries, and hypotheses**, emphasizing investigative reasoning.

---

## 7. Recommendations

- Monitor npm / third-party package execution in developer environments.  
- Enable comprehensive Sysmon logging (EventCodes 1, 3, 11, 22).  
- Track all outbound connections from critical hosts.  
- Deploy host-based EDR for PowerShell encoded command execution.  
- Validate and whitelist dependencies in supply chain security programs.  

---

## 8. Conclusion

The investigation demonstrates:

- Initial compromise via npm package → PowerShell stager  
- Beacon activity on PAW-TABITHA  
- Minor lateral movement to PAW-PENNY  

This report showcases **log correlation, attack chain reconstruction, IOC mapping, and analytical reasoning**, suitable for a professional SOC portfolio.

---

## 9. Timeline Diagram

```text
PAW-TOM (stager execution)
       │
       ▼
PAW-TABITHA (beacon activity)
       │
       ▼
PAW-PENNY (minor lateral movement)
