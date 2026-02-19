# Sourcetypes Mapping

# BOTSv1 Source Type Mapping

| Source Type      | Description                                                                                     | Example Fields / Use Case                                        |
|-----------------|-------------------------------------------------------------------------------------------------|------------------------------------------------------------------|
| data-2           | Web server activity logs                                                                         | `_raw`, `host`, `cs_uri_stem`, `cs_uri_query`, detect Joomla enumeration, webshell access, XSS attempts, C2 beaconing |
| data-3           | Botnet / exploit scanning logs                                                                   | `_raw`, `host`, automated scanning of admin/service endpoints, brute-force attempts |
| stream:http      | Reconnaissance HTTP streams                                                                      | `src_ip`, `dest_ip`, `uri`, status, early attacker probing of Joomla endpoints |

Notes:

- Sourcetypes ensure SPL queries are simple and meaningful  
- Indexes are optional but portfolio-friendly for clarity
