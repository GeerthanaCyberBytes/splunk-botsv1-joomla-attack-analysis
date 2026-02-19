Purpose: Explain the datasets you uploaded in Splunk.

Template content:

# Dataset Overview

## Sources

| Source | Count | Description |
|--------|-------|-------------|
| vendor_sales/vendor_sales.log | 60,488 | Business events (detect unusual actions) |
| www1-3/access.log | ~79,000 | Web server logs (detect brute force, 404s, reconnaissance) |
| www1-3/secure.log | ~60,000 | Linux auth logs (SSH logins, failures, escalations) |
| mailsv/secure.log | 19,658 | Mail server auth logs (detect brute force) |

## Notes

- All logs are human-readable and suitable for Splunk Add Data → Upload  
- Sourcetypes and indexes assigned for clarity
