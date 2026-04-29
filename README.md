# DNS Zone Configuration: GitHub Pages + DNS.com

This repository contains a reference DNS zone file configuration for mapping a custom domain (managed via DNS.com) to a GitHub Pages site.

## ⚠️ Disclaimer
**FOR TESTING PURPOSES ONLY.** This configuration is provided "as-is" without any warranty of any kind. I assume **no liability** for any downtime, loss of service, or security misconfigurations. Use at your own risk.

## Overview
This setup ensures that both the apex domain (`example.com`) and the `www` subdomain correctly resolve to GitHub's infrastructure using standard BIND formatting.

## Implementation Guide
1. **Customize:** Replace all instances of `example.com.` with your actual domain and `your-username` with your GitHub username.
2. **Serial Number:** Every time you update the zone file, you **must** increment the serial number in the `SOA` record (e.g., `2026042901` → `2026042902`).
3. **Verification:** Ensure you have added the required `_github-pages-challenge` TXT record found in your GitHub repository's **Settings > Pages** dashboard.

## Validation Commands
You can verify your DNS settings using the following terminal commands:

```bash
# Check A Records
dig +short example.com

# Check CNAME Alias
dig +short [www.example.com](https://www.example.com)

# Check Ownership Verification
dig -t txt _github-pages-challenge-your-username.example.com
