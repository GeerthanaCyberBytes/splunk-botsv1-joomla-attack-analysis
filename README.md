# Splunk BOTS v1 — Joomla Webshell & C2 Attack Analysis

This project documents a full SOC-style intrusion investigation using Splunk and the BOTS v1 dataset.  

The analysis traces the attack lifecycle from reconnaissance to exploitation, webshell deployment, C2 beaconing, and botnet propagation.

---

## Dataset

- Source: Splunk BOTS v1  
- Log types analyzed: IIS logs, HTTP artifacts (data-2), binary strings (data-3), authentication logs  

---

## Attack Overview

1. Joomla admin paths enumeration (Forced Browsing)  
2. Reflected XSS attempts  
3. Webshell upload (agent.php)  
4. Remote attacker command execution  
5. Outbound C2 beaconing  
6. Botnet propagation activity  

---

## Project Structure

data-description/
analysis/
spl/
dashboards/
report/


---

## Skills Demonstrated

- Splunk SPL threat hunting  
- Web attack detection  
- Webshell identification  
- C2 traffic analysis  
- Malware string interpretation  
- Intrusion timeline reconstruction
