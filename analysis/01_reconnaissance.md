# Reconnaissance — Forced Browsing

## Overview

The attacker enumerated Joomla administrative paths and components:

/joomla/administrator/
/administrator/index.php
option=com_installer
option=com_extplorer


## SPL Example



index=botsv1 sourcetype="data-2"
| rex field=_raw "(?i)joomla|administrator|com_installer|com_extplorer"
| stats count by _raw


## Analyst Notes

- Automated directory enumeration  
- Goal: locate exploitable admin panels/components  
- Classic web reconnaissance activity
