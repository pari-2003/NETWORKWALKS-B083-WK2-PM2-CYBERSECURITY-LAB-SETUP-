# NETWORKWALKS-B083-WK2-PM2-CYBERSECURITY-LAB-SETUP
the second week project for the networkwalks pentesting online intern - Enumeration and Scanning

# Penetration Testing Report — Enumeration & Network Scanning

A documented penetration testing exercise covering Phase 1 (Enumeration & Footprinting) and Phase 2 (Network Scanning). All activities were performed with explicit written permission from the target or on personally owned devices.

---

## Target Scope

| Target | Type | Permission |
|---|---|---|
| networkwalks.com | Public domain — enumeration | Written permission obtained |
| 192.168.1.0/24 | Personal LAN — host discovery | Own network |

---

## Tools Used

| Tool | Phase | Purpose |
|---|---|---|
| `whois` | Enumeration | Domain registration info — registrar, dates, name servers |
| `whatweb` | Enumeration | Web technology fingerprinting — CMS, plugins, server, JS libraries |
| `nslookup` | Enumeration | DNS resolution of target domain to server IP |
| `curl -I` | Enumeration | HTTP response header inspection |
| `wafw00f` | Enumeration | WAF detection |
| `dnsrecon` | Enumeration | Full DNS record enumeration — SOA, NS, A, MX, TXT, SPF, SRV |
| `Zenmap (Nmap 7.991)` | Network Scanning | Ping scan for live hosts, IPs, MACs, and hostnames on LAN |

All enumeration tools were run inside **Kali Linux on Oracle VirtualBox**. Zenmap was run on **Windows**.

---

## Key Findings

### Enumeration — networkwalks.com

- WordPress 7.1 + WP Download Manager 3.3.58 publicly fingerprinted via WhatWeb
- WordPress REST API endpoint `/wp-json/` exposed in HTTP Link header
- WAF detected: **ModSecurity (SpiderLabs)**
- Hosting provider identifiable: **HostGator / cPanel** via NS and SRV records
- SPF record uses `~all` (softfail) — email spoofing may reach inboxes
- DNSSEC not enabled
- Mail server shares IP with web server (192.232.216.135)

### Network Scanning — Personal LAN

- 9 live hosts discovered on 192.168.1.0/24
- Hosts include: Zyxel gateway, 4 mobile devices, TP-Link RE200, 1 Windows desktop, scanning machine
- Multiple devices using MAC address randomization
- Network topology map exported from Zenmap

---

## Report

The full penetration testing report is available in this repository:

📄 [`pentest_report_ahmed.docx`][(./pentest_report_ahmed.docx)](https://github.com/AhmaqAhmed/NETWORKWALKS-B083-WK2-PM2-CYBERSECURITY-LAB-SETUP/blob/main/pentest_report_ahmed.pdf)

It covers:
- Liability disclaimer
- Introduction and methodology
- Per-tool findings with exact commands and observations
- Risk analysis table with risk levels
- Recommendations
- Evidence index

---

## Screenshots (Evidence)

All screenshots are in the `/screenshots` folder:

```
screenshots/
├── Screenshot_156.png   # WHOIS output
├── Screenshot_157.png   # WhatWeb fingerprint
├── Screenshot_158.png   # Nslookup DNS resolution
├── Screenshot_159.png   # Curl -I HTTP headers
├── Screenshot_160.png   # Wafw00f WAF detection
├── Screenshot_161.png   # DNSRecon DNS records
├── Screenshot_170.png   # Zenmap ping scan results
└── net-top.pdf          # Zenmap network topology map
```

---

## Phases

| Phase | Description | Status |
|---|---|---|
| Phase 1 | Enumeration & Footprinting | ✅ Complete |
| Phase 2 | Network Scanning | ✅ Complete |
| Phase 3 | Vulnerability Scanning | 🔄 In Progress |
| Phase 4 | Exploitation | 🔄 In Progress |
| Phase 5 | Post-Exploitation & Reporting | 🔄 In Progress |

This repo will be updated as each phase is completed.

---

## Disclaimer

All activities documented in this repository were conducted strictly on systems and networks for which prior written authorization was obtained, or on personally owned devices. This project is for educational and professional development purposes only.

Unauthorized access to computer systems is illegal. Do not reproduce any technique from this repository against systems you do not own or have explicit written permission to test.

---

## Author

**PARIVALLAL**
Cybersecurity Intern | September 2026
