# Incident Report — Joomla Webshell Compromise

## Summary
Compromised Joomla server; PHP webshell deployed; C2 beaconing established.

## Initial Access
Forced browsing and XSS payload delivery.

## Persistence
agent.php uploaded; remote shell active.

## Command and Control
Repeated outbound HTTP to attacker IP 71.39.18.126.

## Post-Compromise
Malware strings indicate botnet propagation scanning.

## Impact
- Remote server control  
- Persistent backdoor  
- Outbound malicious traffic  

## Detection Opportunities
- Non-standard files  
- High-entropy query parameters  
- Repeated outbound HTTP to single IP  

## Conclusion
Complete attack lifecycle captured: reconnaissance → exploitation → webshell → C2 → botnet propagation.
