# W2-PM5 — Network Scanning Outputs

This folder contains the saved command-line output from the network discovery scan performed in my Kali Linux ARM64 virtual machine under UTM/QEMU.

## Nmap Ping Scan

**File:** `07-ping-scan-results.rtf`

The output records the results of the host discovery scan against my own lab subnet (`10.0.0.0/24`).

**Command:**
```bash
nmap -sn 10.0.0.0/24
```

The scan identified two responsive hosts:

- `10.0.0.1` — UTM host-side interface
- `10.0.0.2` — Kali Linux virtual machine
