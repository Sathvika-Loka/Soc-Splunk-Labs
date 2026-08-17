LAB — MONITORING INSECURE PORTS AND SERVICES

STEP 1 — IDENTIFY THE WINDOWS SERVER IP ADDRESS

Identify the IPv4 address of the Windows Server.

STEP 2 — SCAN THE SERVER

Where to type: Kali Linux → Terminal

Command:
nmap <WINDOWS_SERVER_IP>

Example:
nmap 192.168.XX.XX

The scan identifies ports that respond on the target server.

STEP 3 — ANALYZE THE RESULT

The SOC analyst examines:

- Which ports are open?
- Which services are running?
- Are the services expected?
- Is any unnecessary service exposed?

An open port is not automatically malicious. It indicates that a service is accessible and should be investigated according to the organization's security requirements.

SPLUNK ANALYSIS

Where to type:
Splunk Enterprise → Search & Reporting

Check whether events are available:

index=main

GENERAL EVENT COUNT SEARCH

index=main
| stats count by host
| sort - count

DASHBOARD PANEL

Panel name: Events by Host

Visualization: Bar Chart

SPL QUERY:

index=main
| stats count by host
| sort - count

RESULT

The lab demonstrates how network reconnaissance can reveal exposed services and how SOC analysts can use SIEM data to investigate activity associated with monitored systems.

KEY CONCEPT

Lab demonstrates how a SOC can identify exposed ports and services and investigate related activity using Splunk.
