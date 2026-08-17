LAB 9 — DETECTING HTTP FLOOD / DoS ACTIVITY

OBJECTIVE

To monitor HTTP traffic to a web server and identify an unusual increase in HTTP requests using Splunk.

SCENARIO

A web server is running on Windows Server 2019 using IIS.

A large number of HTTP requests are sent to the web server. A SOC analyst monitors the activity in Splunk to identify whether the traffic shows signs of an HTTP flood or possible Denial-of-Service (DoS) activity.

WHY IIS IS USED

IIS stands for Internet Information Services.

It is Microsoft's web server software for Windows.

IIS allows the Windows Server to host websites and respond to HTTP requests.

In this lab, IIS is used as the target web server so that HTTP requests can be generated and monitored.

STEP 1 — IDENTIFY THE WINDOWS SERVER IP ADDRESS

On Windows Server 2019, open Command Prompt and type:

ipconfig

Identify the IPv4 address.

Example:

192.168.184.134

STEP 2 — INSTALL / ENABLE IIS

Where to type:
Windows Server 2019 → PowerShell as Administrator

Command:

Install-WindowsFeature -Name Web-Server -IncludeManagementTools

This installs IIS and the required management tools.

STEP 3 — VERIFY IIS

The IIS web server can be tested from Kali Linux.

Where to type:
Kali Linux → Terminal

Command:

curl -I http://192.168.184.134/

A successful response shows that the web server is reachable.

Example response:

HTTP/1.1 200 OK

This confirms that IIS is responding to HTTP requests.

STEP 4 — GENERATE HTTP REQUESTS

HTTP requests are generated toward the IIS web server to create traffic that can be monitored.

The requests are sent from Kali Linux to the Windows Server.

Example:

curl http://192.168.184.134/

Repeated HTTP requests create increased web traffic.

STEP 5 — CHECK IIS LOGS

IIS records web requests in its log files.

Default IIS log location:

C:\inetpub\logs\LogFiles\

The IIS logs contain information about HTTP requests received by the web server.

STEP 6 — SPLUNK ANALYSIS

Where to type:

Splunk Enterprise → Search & Reporting

Check whether events are available:

index=main

To count events over time:

index=main
| timechart span=1m count

The timechart groups events into one-minute intervals.

This helps the SOC analyst identify sudden increases in the number of events.

STEP 7 — ANALYZE THE RESULT

The SOC analyst looks for:

- Sudden increases in HTTP requests
- Large numbers of requests within a short period
- Unusual traffic patterns
- Repeated requests to the web server

A sudden and unusually high number of requests may indicate an HTTP flood or possible DoS activity.

DASHBOARD PANEL

Panel name:

HTTP Events Over Time

Visualization:

Line Chart

SPL:

index=main
| timechart span=1m count

RESULT

The lab demonstrates how a SOC analyst can monitor HTTP traffic and use Splunk to identify unusual increases in web requests.

KEY CONCEPT

Lab 9 demonstrates HTTP flood / DoS detection by monitoring web-server activity and analyzing event volume over time using Splunk.
