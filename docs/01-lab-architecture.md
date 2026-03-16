# Lab Architecture

## Description

The testing laboratory is a small SOC that uses Wazuh to monitor its environment.  
The environment includes several monitored endpoints that generate system and security events. These events are forwarded to a centralized Wazuh server where they are analyzed and correlated to detect potential security incidents.
This lab simulates a basic enterprise monitoring system where multiple operating systems generate various event logs, and those logs are sent to an enterprise-level platform for detection, analysis, and investigation.

## Virtualized Components

This lab consists of four virtual machines running in VMware Workstation.

### Wazuh Central Site Server (Wazuh)

OS: Ubuntu Server 22.04  
Role: Centralized SIEM

Responsibilities:

- Collect logs from monitored endpoints
- Analyze logs utilizing event detection rules
- Generate alerts for suspicious activity
- Visualize findings on the Wazuh dashboard

---

### Windows Endpoint Device (Workstation)

OS: Windows 10  
Role: Monitored Workstation

The Windows endpoint contains **Wazuh Agent**, which collects system logs and monitors the operating system. The agent forwards these logs to the Wazuh server for processing, and any event detected that indicates a breach will generate an alert from the server to the appropriate response team.

---

### Endpoint - Ubuntu

Operating System: Desktop Ubuntu
Type of Machine: A Linux endpoint monitored

The Wazuh agent runs on the Linux endpoint and enables the collection of both system activity logs and authentication logs.

---

### Attacking Machine - Kali Linux

Operating System: Kali Linux
Role: Attack simulation system

This machine simulates attack activity such as:

- Attempting to brute force over SSH
- Scanning the network for open ports

These simulated attacks generate security events to be collected by Wazuh.

---

## Network Design

All virtual machines are part of the same virtual network in VMware.

The attacker machine can interact with the monitored Linux endpoint, and the Wazuh server can collect all logs from the various virtual machines/agents.

## Architecture Diagram
                    ┌─────────────────┐
                    │   Kali Linux    │
                    │   (Attacker)    │
                    └────────┬────────┘
                             │
                       Simulated
                        Attacks
                             │
              ┌──────────────┴──────────────┐
              │                              │
              ▼                              ▼
    ┌─────────────────┐            ┌─────────────────┐
    │   Windows 10    │            │ Ubuntu Desktop  │
    │  Wazuh Agent    │            │  Wazuh Agent    │
    └────────┬────────┘            └────────┬────────┘
             │                              │
             │       Security Logs          │
             └──────────────┬───────────────┘
                            │
                            ▼
                   ┌─────────────────┐
                   │  Wazuh Server   │
                   │   SIEM Engine   │
                   └─────────────────┘

## Log Collection Flow

1. Endpoints generate system and security events.
2. Wazuh agents collect those logs locally.
3. The agents send the logs to Wazuh server.
4. Wazuh analyzes the events using detection rules.
=======
# Lab Architecture

## Description

The testing laboratory is a small SOC that uses Wazuh to monitor its environment.  
The environment includes several monitored endpoints that generate system and security events. These events are forwarded to a centralized Wazuh server where they are analyzed and correlated to detect potential security incidents.
This lab simulates a basic enterprise monitoring system where multiple operating systems generate various event logs, and those logs are sent to an enterprise-level platform for detection, analysis, and investigation.

## Virtualized Components

This lab consists of four virtual machines running in VMware Workstation.

### Wazuh Central Site Server (Wazuh)

OS: Ubuntu Server 22.04  
Role: Centralized SIEM

Responsibilities:

- Collect logs from monitored endpoints
- Analyze logs utilizing event detection rules
- Generate alerts for suspicious activity
- Visualize findings on the Wazuh dashboard

---

### Windows Endpoint Device (Workstation)

OS: Windows 10  
Role: Monitored Workstation

The Windows endpoint contains **Wazuh Agent**, which collects system logs and monitors the operating system. The agent forwards these logs to the Wazuh server for processing, and any event detected that indicates a breach will generate an alert from the server to the appropriate response team.

---

### Endpoint - Ubuntu

Operating System: Desktop Ubuntu
Type of Machine: A Linux endpoint monitored

The Wazuh agent runs on the Linux endpoint and enables the collection of both system activity logs and authentication logs.

---

### Attacking Machine - Kali Linux

Operating System: Kali Linux
Role: Attack simulation system

This machine simulates attack activity such as:

- Attempting to brute force over SSH
- Scanning the network for open ports

These simulated attacks generate security events to be collected by Wazuh.

---

## Log Collection Flow

1. Endpoints generate system and security events.
2. Wazuh agents collect those logs locally.
3. The agents send the logs to Wazuh server.
4. Wazuh analyzes the events using detection rules.
5. Alerts are generated and displayed in the dashboard for investigation.