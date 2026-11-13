# NETWORKWALKS — Week 2 Cybersecurity Projects

## Project Overview

This repository documents my work for Week 2 of the Networkwalks Cybersecurity & Ethical Hacking Internship.

The completed modules are:

- **W2-PM1:** Footprinting of `networkwalks.com`
- **W2-PM5:** Network scanning and host discovery in my own UTM/Kali Linux lab environment

The repository contains project documentation, command outputs, screenshots, and the final report.


## Environment

- Host machine: MacBook (Apple Silicon)
- Virtualization: UTM/QEMU
- Operating system: Kali Linux (ARM64)
- Lab subnet: `10.0.0.0/24`

## Project Evidence

- [W2-PM1 Footprinting — Screenshots](W2-PM1-Footprinting/Screenshots/)
- [W2-PM1 Footprinting — Command Outputs](W2-PM1-Footprinting/Outputs/)
- [W2-PM5 Network Scanning — Screenshots](W2-PM5-Network-Scanning/Screenshots/)
- [W2-PM5 Network Scanning — Command Outputs](W2-PM5-Network-Scanning/Outputs/)
- [W2-PM5 Network Topology](W2-PM5-Network-Scanning/Topology/)
---


## W2-PM1 — Footprinting

### Objective

To collect publicly available information about `networkwalks.com` using six Kali Linux footprinting tools.

### Tools and Observations

| Tool | Purpose | Observation |
|---|---|---|
| WHOIS | Retrieve domain registration information | GoDaddy registrar; domain created on 2019-11-06 |
| WhatWeb | Identify web technologies | Apache, WordPress 7.1.4, and other detected technologies |
| nslookup | Query DNS records | Domain resolved to `192.232.216.135` through Cloudflare DNS |
| curl | Inspect HTTP response headers | Successful `HTTP/1.1 200 OK` response |
| WAFW00F | Identify possible WAF presence | Detected ModSecurity (SpiderLabs) |
| DNSRecon | Attempt general DNS enumeration | Enumeration timed out, including when explicitly using `1.1.1.1` |

### DNSRecon Limitation

DNSRecon enumeration was unsuccessful because the requests timed out in my environment. However, independent DNS queries using `nslookup` successfully retrieved the domain's IP address and name-server records. The reason for the DNSRecon timeouts could not be established.

---

## W2-PM5 — Network Scanning

### Objective

To identify responsive hosts on my own lab network using Zenmap (Nmap GUI).

### Environment Adaptation

The original task instructions were written for Windows. I used Kali Linux ARM64 in UTM/QEMU instead.

- `ip -br addr` — identified the network interface and IP address.
- `ip route` — identified the local subnet and gateway.
- Zenmap Ping Scan — performed host discovery on `10.0.0.0/24`.

### Scan Command

```bash
nmap -sn 10.0.0.0/24
```

The `-sn` option performs host discovery without port scanning.

### Results

Two hosts responded to the scan:

| IP Address | Device | MAC Address |
|---|---|---|
| `10.0.0.1` | UTM host-side interface | `52:55:0A:00:00:01` |
| `10.0.0.2` | Kali Linux VM | `72:a9:70:94:15:b0` |

Nmap completed the scan of 256 IP addresses and reported two hosts up.

### Network Topology

A network topology graphic was generated using Zenmap's Topology tab. The legend was enabled in the Zenmap interface, but it did not appear in the exported PDF. The PDF contains the topology diagram.

## Conclusion

During Week 2, I completed footprinting of `networkwalks.com` using six Kali Linux tools and performed host discovery on my own UTM lab network. This work helped me practice information gathering, DNS troubleshooting, network scanning, and documenting technical evidence.
