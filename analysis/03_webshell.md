Webshell Detection — Joomla agent.php

Multiple HTTP requests targeted a non-standard Joomla file:

/joomla/agent.php


This file does not exist in Joomla core and is therefore malicious.

Indicators

High-entropy parameters

Rotating parameter names

Repeated execution bursts

Example event:

/joomla/agent.php?pZ=XMab8QzhefmnwSIHmoV_xGbUpCjA5F


These parameters represent encoded command data typical of PHP webshells.

SPL
index=botsv1 sourcetype="data-2"
| search "agent.php"
| stats count by _raw

Conclusion

The presence of agent.php confirms successful exploitation and webshell deployment enabling remote command execution.
