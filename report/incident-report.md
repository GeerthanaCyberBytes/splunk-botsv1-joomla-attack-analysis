Incident Report — Joomla Webshell Compromise
Summary

A Joomla web server within the BOTS v1 dataset was compromised through web application exploitation.
The attacker deployed a PHP webshell and established persistent command-and-control communication.

Initial Access

Evidence shows forced browsing of Joomla administrative paths and component endpoints, followed by XSS payload delivery.

Persistence

A malicious file agent.php was uploaded into the Joomla directory, functioning as a remote webshell.

Command and Control

The compromised server repeatedly contacted attacker IP 71.39.18.126 using obfuscated HTTP parameters, consistent with beaconing behavior.

Post-Compromise Activity

Embedded malware strings indicate scanning of external IoT and web administration interfaces, suggesting botnet propagation capability.

Impact

Remote attacker control of web server

Persistent backdoor

Outbound malicious traffic

Potential lateral or external attacks

Detection Opportunities

Non-standard webroot files

High-entropy query parameters

Repeated outbound HTTP to single IP

Joomla admin enumeration patterns

Conclusion

The intrusion demonstrates a complete web application compromise lifecycle from reconnaissance to persistent C2 control and botnet-style propagation activity.
