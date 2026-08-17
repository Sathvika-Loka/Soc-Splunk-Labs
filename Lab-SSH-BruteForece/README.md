LAB — MONITORING BRUTE-FORCE ATTEMPTS ON SSH PORT

OBJECTIVE

To monitor SSH authentication activity and identify repeated failed login attempts using Splunk.

SCENARIO

An SSH server is running on the target system.

An attacker attempts to log in using incorrect usernames or passwords multiple times.

A SOC analyst monitors the authentication logs in Splunk and investigates repeated failed SSH login attempts.

WHY SSH IS USED

SSH stands for Secure Shell.

It is a network protocol used to securely access and manage a remote computer.

SSH normally operates on port 22.

Repeated failed SSH login attempts can indicate a possible brute-force attack.

STEP 1 — IDENTIFY THE TARGET IP ADDRESS

Identify the IPv4 address of the system running the SSH server.

Command:

ipconfig

or, on Linux:

ip addr

Example:

192.168.XX.XX

STEP 2 — VERIFY SSH SERVICE

Check whether the SSH service is running on the target system.

The SSH server listens for incoming SSH connections.

Port 22 is the standard SSH port.

STEP 3 — TEST SSH CONNECTION

Where to type:

Kali Linux → Terminal

Example:

ssh fakeuser@192.168.XX.XX

An incorrect username or password produces a failed authentication attempt.

This activity can generate authentication events that can be monitored by the SOC.

STEP 4 — GENERATE FAILED SSH LOGIN ATTEMPTS

Multiple unsuccessful SSH login attempts are generated against the SSH server.

The purpose of this lab is to simulate suspicious authentication activity in a controlled lab environment.

Repeated failed attempts can represent a possible brute-force attack.

STEP 5 — COLLECT SSH AUTHENTICATION LOGS

The SSH server records authentication activity.

The logs contain information about successful and failed login attempts.

These logs are forwarded to Splunk for monitoring and analysis.

STEP 6 — SPLUNK ANALYSIS

Where to type:

Splunk Enterprise → Search & Reporting

First check whether events are available:

index=main

Search for SSH-related events:

index=main ssh

The SOC analyst examines the returned events for failed authentication attempts.

STEP 7 — IDENTIFY REPEATED FAILED ATTEMPTS

The SOC analyst looks for:

- Multiple failed SSH login attempts
- Repeated attempts from the same source IP address
- Attempts using invalid usernames
- A large number of authentication failures within a short period

A high number of failed login attempts may indicate a possible brute-force attack.

STEP 8 — ANALYZE EVENTS OVER TIME

Use a timechart to observe authentication activity:

index=main
| timechart span=1m count

The query groups events into one-minute intervals.

A sudden increase in authentication events can help the SOC analyst identify suspicious activity.

DASHBOARD PANEL

Panel name:

SSH Authentication Events

Visualization:

Line Chart

SPL:

index=main
| timechart span=1m count

RESULT

The lab successfully demonstrates how repeated failed SSH authentication attempts can be generated and monitored using Splunk.

The SOC analyst can use authentication logs to identify suspicious login activity and investigate possible brute-force attacks.

KEY CONCEPT

Lab demonstrates how a SOC can monitor SSH authentication activity, identify repeated failed login attempts, and use Splunk to investigate possible brute-force attacks.
