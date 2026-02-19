# Command-and-Control Beaconing

## Overview

The compromised Joomla server initiated outbound HTTP requests to attacker IP 71.39.18.126:

http://71.39.18.126/?wNO=
...
http://71.39.18.126/?xC=
...
http://71.39.18.126/?BVw=
...


## Characteristics

- Obfuscated parameter names  
- High-entropy values  
- Repeated beacon intervals (minutes)  

## SPL Example



index=botsv1 sourcetype="data-2"
| search "71.39.18.126"
| stats count by _raw
| sort -count


## Analyst Notes

- Stage: Post-exploitation  
- Confirms active C2 beaconing from compromised host
