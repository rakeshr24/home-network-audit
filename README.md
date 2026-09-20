# Home Network Security Audit

## Overview
Used Nmap to scan my home network, identify connected devices, and assess my router for open ports and potential weak points.

## Tools Used
- Nmap 7.991
- macOS Terminal

## Steps
1. Identified local network range: `192.168.1.0/24`
2. Discovered live hosts: `nmap -sn 192.168.1.0/24`
3. Deep-scanned the router for open ports, services, and OS fingerprint: `sudo nmap -sV -O 192.168.1.1`

## Findings
- 2 active hosts on the network: router (192.168.1.1) and my Mac (192.168.1.150)
- Router (Sagemcom Broadband SAS) has 6 open ports: 53 (DNS), 80 (HTTP), 139 (NetBIOS), 443 (HTTPS), 445 (SMB), 49152 (UPnP)
- Port 80 (unencrypted HTTP) is open alongside 443 — if the admin panel is reachable over HTTP, credentials could be exposed in plaintext
- Ports 139/445 (NetBIOS/SMB) are open — these are common attack targets and often unnecessary to expose

## Recommendations
1. Disable HTTP admin access on the router, use HTTPS only
2. Disable NetBIOS/SMB on the router if not actively used for file sharing
3. Confirm router firmware is up to date
4. Change default admin credentials if not already done

## What I Learned
How to use Nmap for host discovery and service enumeration, and how to read scan results to flag real security misconfigurations on a home network.

## Disclaimer
All scanning performed on my own home network and devices I own.
