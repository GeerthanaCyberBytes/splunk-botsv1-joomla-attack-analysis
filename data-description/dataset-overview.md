Purpose: Explain the datasets you uploaded in Splunk.

Template content:

# Dataset Overview

## Sources

| Source       | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| data-2       | Web server activity logs (Joomla enumeration, webshell access, XSS attempts, C2 beaconing) |
| data-3       | Botnet / exploit scanning logs (admin/service path probing, automated reconnaissance)       |
| stream:http  | Reconnaissance HTTP streams (attacker probing Joomla endpoints)                           |


## Notes

- All logs are human-readable and suitable for Splunk Add Data → Upload  
- Sourcetypes and indexes assigned for clarity
