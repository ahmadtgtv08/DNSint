<div align="center">

<img src="DNSint.png" alt="DNSint Logo" width="400"/>

# DNSint

### 🔍 Professional DNS Reconnaissance & OSINT Toolkit

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/who0xac/DNSint?style=social)](https://github.com/who0xac/DNSint/stargazers)

**A comprehensive DNS intelligence and security analysis tool for domain reconnaissance**

Created by **[wh0xac](https://github.com/who0xac)**

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Examples](#-examples) • [Documentation](#-documentation)

</div>

---

## 🎯 Overview

DNSint is a powerful, all-in-one DNS reconnaissance and OSINT tool designed for security professionals, penetration testers, and system administrators. It combines multiple DNS analysis techniques with OSINT data sources to provide comprehensive domain intelligence.

### Why DNSint?

- ✅ **Comprehensive** - 10+ analysis modules in one tool
- ✅ **Fast** - Parallel queries and optimized performance
- ✅ **Beautiful** - Rich terminal UI with colored output
- ✅ **Flexible** - Modular design, use only what you need
- ✅ **Export Ready** - JSON and TXT reports for documentation
- ✅ **Split-Brain DNS** - Custom DNS server support
- ✅ **Auto-Update** - Stay current with latest features

---

## ✨ Features

### 🔎 DNS Analysis
- **DNS Records Discovery** - Query all major record types (A, AAAA, MX, TXT, NS, SOA, SRV, CAA, DNSKEY, DS, NAPTR)
- **Reverse PTR Lookups** - Discover reverse DNS mappings for all IPs
- **Zone Transfer Testing** - Attempt AXFR on discovered nameservers
- **DNSSEC Validation** - Check DNSKEY and DS records

### 📧 Email Security
- **SPF Analysis** - Parse SPF records, count lookups, detect issues
- **DMARC Policy** - Check DMARC configuration and policy strength
- **DKIM Detection** - Probe common DKIM selectors

### 🛡️ Security Auditing
- **Misconfiguration Detection** - Identify common DNS security issues
- **Zone Transfer Vulnerabilities** - Test all nameservers for AXFR leaks
- **DNS Propagation** - Check consistency across global resolvers
- **Security Headers** - Analyze HTTP security headers (CSP, HSTS, etc.)

### 🌐 Infrastructure Analysis
- **Nameserver Analysis** - SOA serial checks, ASN lookups, geolocation
- **Technology Detection** - Identify web servers, CMS, frameworks, CDN, WAF
- **Network Intelligence** - ASN, organization, and country mapping

### 🔬 OSINT Enrichment
- **Certificate Transparency** - Discover subdomains from CT logs
- **Passive DNS** - Historical DNS data (when available)
- **Related Domains** - Find associated domains and wildcards

### 📊 WHOIS Intelligence
- **Extended WHOIS** - Registrar, registrant, dates, status
- **Privacy Detection** - Identify privacy protection services
- **Expiration Tracking** - Days until domain expiration with warnings

### 🛠️ Advanced Features
- **Custom DNS Server** - Query specific DNS resolvers (split-brain DNS support)
- **Auto-Update** - One-command updates via git
- **Export Reports** - Save results in JSON and TXT formats
- **Quiet Mode** - Minimal output for scripting
- **Verbose Logging** - Detailed debug information

---

## 🚀 Installation

### Prerequisites
- Python 3 or higher

### Quick Install

```bash
# Clone the repository
git clone https://github.com/who0xac/DNSint.git
cd DNSint

# Install dependencies
pip install -r requirements.txt

# Run DNSint
python DNSint.py example.com -a
```

---

## 📖 Usage

### Basic Syntax

```bash
python DNSint.py <domain> [options]
```

### Command-Line Options

```
Positional Arguments:
  domain                Target domain (e.g., example.com)

Module Selection:
  -a, --all            Run full DNS + OSINT + Technology scan (default)
  -r, --records        Query DNS record types
  -z, --zone           Perform reverse PTR & AXFR checks
  -m, --mail           Analyze SPF, DKIM, DMARC
  -w, --whois          Perform extended WHOIS lookup
  -n, --nsinfo         Analyze nameserver info & DNSSEC
  -p, --propagation    Check global DNS propagation
  -s, --security       Run DNS misconfiguration checks
  -o, --osint          Enrich with passive DNS & CT data
  -t, --tech           Detect web technologies, CMS, servers

Advanced Options:
  --dns-server <ip>    Custom DNS server to use (e.g., 8.8.8.8)
  --timeout <seconds>  Set DNS query timeout (default: 5)
  -u, --update         Update DNSint to the latest version
  -e, --export         Export JSON + TXT reports to Desktop
  -v, --verbose        Show detailed logs
  -q, --quiet          Minimal console output
```

---

## 💡 Examples

### Full Scan
```bash
# Complete analysis with all modules
python DNSint.py example.com -a
```

### Email Security Analysis
```bash
# Check SPF, DMARC, and DKIM
python DNSint.py example.com -m
```

### Security Audit
```bash
# Run security checks and export report
python DNSint.py example.com -s -e
```

### Custom DNS Server (Split-Brain DNS)
```bash
# Use Google DNS
python DNSint.py example.com --dns-server 8.8.8.8

# Use internal DNS server
python DNSint.py internal.company.com --dns-server 192.168.1.53

# Use Cloudflare DNS
python DNSint.py example.com --dns-server 1.1.1.1
```

### OSINT Gathering
```bash
# Certificate Transparency and passive DNS
python DNSint.py example.com -o
```

### Multiple Modules
```bash
# DNS records + WHOIS + email security
python DNSint.py example.com -r -w -m
```

### Technology Detection
```bash
# Detect web stack and security headers
python DNSint.py example.com -t
```

### Quiet Mode for Scripting
```bash
# Minimal output, export to files
python DNSint.py example.com -a -e -q
```

### Update Tool
```bash
# Update to latest version
python DNSint.py -u
```

---

## 📋 Output Examples

### DNS Records
```
┌────────────┬──────────────────────────────┬──────────┬──────────────────────┐
│ Type       │ Value                        │ TTL      │ Extra                │
├────────────┼──────────────────────────────┼──────────┼──────────────────────┤
│ A          │ 93.184.216.34                │ 3600     │                      │
│ MX         │ mail.example.com.            │ 3600     │ Priority: 10         │
│ TXT        │ "v=spf1 include:_spf..."     │ 3600     │                      │
└────────────┴──────────────────────────────┴──────────┴──────────────────────┘
```

### Email Security
```
📧 Email Security Analysis
├── SPF (Sender Policy Framework)
│   ├── ✓ SPF Record Found
│   ├── Record: v=spf1 include:_spf.google.com ~all
│   └── DNS Lookups: 3 (limit: 10)
├── DMARC (Domain-based Message Authentication)
│   ├── ✓ DMARC Record Found
│   └── Policy: reject
└── DKIM (DomainKeys Identified Mail)
    └── ✓ Found selectors: google, default
```

### Security Audit
```
🔒 Security Audit Results
├── Critical Issues (0)
├── Warnings (2)
│   ├── ⚠ DNSSEC not enabled
│   └── ⚠ Wildcard certificate detected
└── Informational (3)
    ├── ℹ SPF record configured
    ├── ℹ DMARC policy set to quarantine
    └── ℹ CAA records configured
```

---

## 🔧 Advanced Usage

### Split-Brain DNS Testing

Test how your domain resolves from different DNS servers:

```bash
# Internal DNS
python DNSint.py internal.company.com --dns-server 10.0.0.53

# External DNS (Google)
python DNSint.py company.com --dns-server 8.8.8.8

# Compare results
python DNSint.py company.com --dns-server 8.8.8.8 > external.txt
python DNSint.py company.com --dns-server 10.0.0.53 > internal.txt
diff external.txt internal.txt
```

### Automated Monitoring

```bash
#!/bin/bash
# Monitor domain DNS changes
python DNSint.py example.com -a -e -q
# Reports saved to Desktop with timestamp
```

### CI/CD Integration

```bash
# Check DNS before deployment
python DNSint.py staging.example.com -s --dns-server 10.0.0.53
if [ $? -eq 0 ]; then
    echo "DNS checks passed"
else
    echo "DNS issues detected"
    exit 1
fi
```

---

## 📁 Export Formats

DNSint can export results in two formats:

### JSON Export
```json
{
  "domain": "example.com",
  "scan_timestamp": "2025-11-23T10:30:00",
  "records": {
    "A": [{"value": "93.184.216.34", "ttl": 3600}]
  },
  "whois": {
    "registrar": "Example Registrar",
    "creation_date": "1995-08-14"
  }
}
```

### TXT Export
```
DNSint Report - example.com
Generated: 2025-11-23 10:30:00
==================================

DNS RECORDS:
A: 93.184.216.34 (TTL: 3600)
MX: mail.example.com (Priority: 10, TTL: 3600)

WHOIS:
Registrar: Example Registrar
Created: 1995-08-14
```

Files are saved to your Desktop with timestamp:
- `example.com_2025-11-23_103000.json`
- `example.com_2025-11-23_103000.txt`

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to fork the repository and submit a pull request with your improvements.

---

## ⚠️ Disclaimer

**DNSint is intended for educational and legal security testing purposes only.**

- Only test domains you own or have explicit permission to test
- Unauthorized reconnaissance may be illegal in your jurisdiction
- The author is not responsible for any misuse of this tool
- Always follow responsible disclosure practices
- Respect rate limits and DNS server resources

---

<div align="center">

**Made with ❤️ by wh0xac**

[⬆ Back to Top](#dnsint)

</div>
