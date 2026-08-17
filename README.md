# SOC Incident Detection & Monitoring — Labs 8–10

## Project Overview

This project contains hands-on SOC (Security Operations Center) labs focused on security monitoring, attack simulation, log collection, and analysis using Kali Linux, Windows Server 2019, Splunk Universal Forwarder, and Splunk Enterprise.

The labs demonstrate how a SOC analyst can:

- Identify exposed ports and services.
- Detect abnormal HTTP traffic.
- Monitor SSH authentication attempts.
- Collect logs from Windows systems.
- Analyze security events using Splunk.
- Create visualizations for security monitoring.

## Lab Environment

### Machines

- Kali Linux — used to generate controlled security/network activity.
- Windows Server 2019 — monitored/target server.
- Splunk Universal Forwarder — collects and forwards logs.
- Splunk Enterprise — central SIEM used for searching and visualization.

### Additional Software

- Nmap — port and service scanning.
- IIS — Windows web server used for Lab 9.
- cURL — generates HTTP requests for Lab 9.
- OpenSSH Server — required for Lab 10's SSH scenario.
- PowerShell / Windows Event Viewer — Windows administration and log verification.

## Labs

| Lab | Topic |
|---|---|
| 08 | Monitoring Insecure Ports and Services |
| 09 | Detecting HTTP Flood / DoS |
| 10 | Monitoring SSH Brute-Force Attempts |

## Lab Structure

- [Lab 08 — Monitoring Insecure Ports and Services](Lab-08-Insecure-Ports-Services/README.md)
- [Lab 09 — Detecting HTTP Flood / DoS](Lab-09-HTTP-Flood-DoS/README.md)
- [Lab 10 — Monitoring SSH Brute-Force Attempts](Lab-10-SSH-Brute-Force/README.md)

## Overall Architecture

Kali Linux
    |
    | Controlled test activity
    v
Windows Server 2019
    |
    | Windows / IIS / authentication logs
    v
Splunk Universal Forwarder
    |
    v
Splunk Enterprise
    |
    v
Search / Analysis / Visualization
