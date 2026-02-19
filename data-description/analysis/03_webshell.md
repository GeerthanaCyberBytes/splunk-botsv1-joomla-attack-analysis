# Webshell Detection — Joomla agent.php

## Overview

Multiple HTTP requests were identified targeting a non-standard Joomla file:

/joomla/agent.php

This file does not exist in the default Joomla installation and is therefore considered malicious.

Traffic patterns indicate the file functions as a PHP webshell providing remote command execution on the compromised server.

---

## Evidence

Observed requests contain randomized high-entropy parameters:

/joomla/agent.php?ge=ABpb4tK4Qf2GvZaLICnCKT6DO2iyRj  
/joomla/agent.php?pZ=XMab8QzhefmnwSIHmoV_xGbUpCjA5F  
/joomla/agent.php?wVz=b6cS6hz_3GtG7BjQ4678Kh8Txocdbs  

Characteristics:

- Parameter length 20–32 characters  
- Mixed upper/lowercase letters  
- Numbers and symbols (`_ -`)  
- No readable words  
- Rotating parameter names  

These traits match encoded command/data blobs commonly used in PHP webshell communication.

---

## Behavioral Indicators

The request sequence shows:

- Repeated access to the same non-standard file  
- Parameter entropy typical of obfuscated payloads  
- Multiple requests within seconds  

This burst timing pattern is consistent with interactive attacker command execution via HTTP webshell.

---

## SPL Detection Query
index=botsv1 sourcetype="data-2"
| search "agent.php"
| stats count by _raw
| sort -count

This query identifies repeated requests to the malicious webshell endpoint.

---

## Analyst Assessment

The presence and repeated execution of `/joomla/agent.php` confirms:

- Successful exploitation of the Joomla web application  
- Upload of a malicious PHP webshell  
- Active attacker interaction with the compromised host  

This represents post-exploitation remote control capability.

---

## Conclusion

A persistent PHP webshell (`agent.php`) was deployed on the Joomla server and actively used for remote command execution.  
This establishes confirmed compromise and attacker control of the web application host.
