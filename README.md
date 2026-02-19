# Splunk BOTS v1 — Joomla Webshell & C2 Attack Analysis

This project documents a full intrusion investigation conducted in Splunk using the BOTS v1 dataset.  
The analysis traces the attack lifecycle from reconnaissance to exploitation, webshell deployment, and command-and-control (C2) beaconing.

The objective is to demonstrate SOC-level detection, log analysis, and threat-hunting methodology.

---

## Dataset

Source: Splunk BOTS v1 dataset  

Log types analyzed:

- IIS web logs  
- Extracted HTTP artifacts (data-2)  
- Binary string extraction (data-3)  
- Authentication logs  

---

## Attack Overview

The investigation identified a compromise of a Joomla web server involving:

- Forced browsing of Joomla admin paths  
- Reflected XSS attempts  
- Upload of malicious webshell (agent.php)  
- Interactive attacker control via HTTP  
- Outbound C2 beaconing to attacker IP  
- Botnet propagation scanning  

---

## Key Findings

### 1. Reconnaissance — Forced Browsing

The attacker enumerated Joomla administrative and component paths:

/joomla/administrator/
/administrator/index.php
option=com_installer
option=com_extplorer

yaml
Copy code

This activity matches automated web directory enumeration used to locate exploitable components.

---

### 2. Exploitation — XSS Injection Attempts

Reflected XSS payloads were observed:

searchword="><script>GP4l(9294)</script>

yaml
Copy code

Characteristics:

- Attribute break-out (`">`)
- Script injection
- Scanner markers (random function names)

---

### 3. Webshell Deployment

Repeated requests were identified to a non-standard Joomla file:

/joomla/agent.php

diff
Copy code

Indicators of compromise:

- File not present in Joomla core  
- High-entropy parameters  
- Rotating parameter names  
- Burst command timing  

Example:

/joomla/agent.php?ge=ABpb4tK4Qf2GvZaLICnCKT6DO2iyRj

yaml
Copy code

This confirms a deployed PHP webshell used for remote command execution.

---

### 4. Command-and-Control Beaconing

The compromised server initiated outbound callbacks to:

71.39.18.126

css
Copy code

Observed pattern:

"http://71.39.18.126/?wNO=..."
"http://71.39.18.126/?xC=..."
"http://71.39.18.126/?BVw=..."

yaml
Copy code

Characteristics:

- Random parameter keys  
- High-entropy values  
- Repeated beacon interval  
- Persistent communication  

This behavior matches webshell C2 polling.

---

### 5. Botnet Propagation Activity

Binary string extraction (data-3) revealed embedded scan targets:

/admin/login.jsp
/scgi-bin/platform.cgi
/MSWSMTP/Common/Authentication/Logon.aspx
/tmui/

yaml
Copy code

These correspond to IoT and web admin endpoints, indicating the malware contains a propagation target list.

---

## Attack Timeline

1. Joomla directory enumeration  
2. XSS exploitation attempts  
3. Webshell upload (agent.php)  
4. Interactive attacker commands  
5. Outbound C2 beaconing  
6. Botnet scanning activity  

---

## Skills Demonstrated

- Splunk SPL threat hunting  
- Web attack detection  
- Webshell identification  
- C2 traffic analysis  
- Malware string interpretation  
- Intrusion timeline reconstruction  

---

## SPL Queries

All detection queries are provided in `/spl`.

**Webshell detection**

index=botsv1 sourcetype="data-2" "agent.php"

markdown
Copy code

**C2 detection**

index=botsv1 sourcetype="data-2"
| search "71.39.18.126"

markdown
Copy code

**XSS detection**

index=botsv1 sourcetype="data-2"
| search "<script>"

yaml
Copy code

---

## Screenshots

See `/dashboards` for visual evidence of:

- Webshell traffic  
- C2 beaconing  
- Attack timeline  
- Joomla exploitation activity  

---

## Incident Assessment

The analyzed host was fully compromised via a Joomla web application attack.  
The attacker deployed a persistent PHP webshell and established outbound command-and-control communication, followed by botnet-style scanning behavior.
