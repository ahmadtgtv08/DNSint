# DNSint
A professional DNS reconnaissance and OSINT tool for comprehensive domain analysis.

**Created by wh0xac**

---

## ✨ Features

- **DNS Records** - Query A, AAAA, MX, TXT, NS, SOA, SRV, CAA, DNSKEY, DS, NAPTR
- **Email Security** - Analyze SPF, DMARC, DKIM configurations
- **WHOIS Lookup** - Extended domain registration information
- **Security Audit** - Zone transfer tests, DNSSEC validation, misconfiguration detection
- **Technology Detection** - Identify web servers, CMS, frameworks, CDN, analytics
- **DNS Propagation** - Check consistency across global resolvers
- **OSINT Enrichment** - Certificate Transparency logs and passive DNS
- **Export Reports** - Save results in JSON and TXT formats

---

## 🚀 Installation

```bash
# Install dependencies
pip install -r requirements.txt

# Run DNSint
python3 dnsint.py example.com -a
```

---

## 📖 Usage

```bash
python3 dnsint.py example.com -a -e
```

---

## ⚠️ Disclaimer

This tool is intended for educational and legal security testing purposes only. The author is not responsible for any misuse of this script.

---

**wh0xac** | DNSint 