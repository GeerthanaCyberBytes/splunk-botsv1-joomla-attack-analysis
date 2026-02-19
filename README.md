# Splunk BOTS v1 — Joomla Webshell & C2 Attack Analysis

This project documents a full intrusion investigation conducted in Splunk using the BOTS v1 dataset.  
The analysis traces the attack lifecycle from reconnaissance to exploitation, webshell deployment, and command-and-control (C2) beaconing.

---

## Dataset

Source: Splunk BOTS v1  

Log types analyzed:

- IIS web logs  
- HTTP artifacts (data-2)  
- Binary strings (data-3)  
- Authentication logs  

---

## Attack Overview

The Joomla web server was compromised through web exploitation leading to persistent remote control.

Attack stages identified:

1. Forced browsing of Joomla admin paths  
2. Reflected XSS attempts  
3. Webshell upload (agent.php)  
4. Interactive attacker control  
5. Outbound C2 beaconing  
6. Botnet scanning activity  

---

## Key Evidence

### Joomla Enumeration
/joomla/administrator/
/administrator/index.php
option=com_installer
option=com_extplorer


Indicators:

- Non-standard Joomla file  
- High-entropy parameters  
- Rotating keys  
- Burst requests  

---

### C2 Beaconing

Indicators:

- Repeated outbound traffic  
- Random parameters  
- Persistent callbacks  

---

### Botnet Targets (data-3)
/admin/login.jsp
/scgi-bin/platform.cgi
/MSWSMTP/Common/Authentication/Logon.aspx
/tmui/


---

## Skills Demonstrated

- Splunk SPL threat hunting  
- Web attack detection  
- Webshell identification  
- C2 analysis  
- Malware string analysis  
- Intrusion timeline reconstruction  

---

## SPL Examples

**Webshell**

index=botsv1 sourcetype="data-2" "agent.php"


**C2**



index=botsv1 sourcetype="data-2" "71.39.18.126"


**XSS**



index=botsv1 sourcetype="data-2" "<script>"


---

## Project Structure



analysis/
report/
spl/
dashboards/


---
## Conclusion

The Joomla server was fully compromised via web exploitation.  
A PHP webshell enabled persistent remote access and outbound command-and-control communication, followed by botnet-style propagation activity.

