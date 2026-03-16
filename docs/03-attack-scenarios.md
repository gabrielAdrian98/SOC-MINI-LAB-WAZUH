# Attack Scenarios

## Overview

In order to assess the monitoring capabilities of the Wazuh SIEM platform, a number of attack scenarios were simulated in the laboratory environment.

These attacks were launched from the Kali Linux machine against the monitored endpoints. The purpose was to create security events that could be detected and evaluated through the Wazuh system.

The attack scenarios chosen represent common activities that an SOC team may observe in real-world environments.

---

## Scenario 1 - SSH Brute Force Attack

### Description

The first scenario simulates a brute-force attack against the SSH service running on the Ubuntu endpoint.

Brute force attacks are examples of unauthorized access attempts that utilize multiple username and password combinations to successfully gain access to a system.

Even though the attack may not succeed, the attacker generates multiple authentication attempts that can be observed in the system logs.

### Attacker Machine

Kali Linux

### Target Machine

Ubuntu Desktop Endpoint

### Tool Being Used

Hydra

Hydra is a password-cracking tool commonly used to perform brute force attacks against services such as SSH, FTP, and HTTP.

### Sample Hydra Command

```bash
hydra -l testuser -P rockyou.txt ssh://TARGET_IP
```

## Objective

This attack's objective is to create many unsuccessful login attempts that would write to the authentication log file created by the Ubuntu OS and be sent to Wazuh.

These events trigger existing Wazuh detection rules related to repeated authentication failures.

---

## Scenario 2 - Network Port Scan

## Description

As the second type of synthetic attack, a network port scan simulates reconnaissance.

Network port scanning is commonly used by an attacker as part of their reconnaissance of an organization's environment and typically occurs early in an attempted intrusion to identify the open services running on a target.

By identifying open ports or the associated services where those open ports exist, an attacker can further assess which services may be vulnerable to an attack.

## Attacker's Machine

Kali Linux

## Target System

Windows 10 Endpoint

## Tool Being Used

Nmap

As one of the most widely used network scanning tools and a common choice for penetration testing and network discovery, Nmap will be utilized in the network port scanning portion of the exercise.

## Command Example

```bash
nmap -sT -p 445 TARGET_IP
```

## Objective: 
This scan is intended to create a connection attempt that could log in the Windows event log.

These events will then be sent to the Wazuh agent and forwarded to the Wazuh server, where they can be analyzed for suspicious activity.

---

## Events Expected: 
Both attack scenarios create different log types/methods that can be detected by Wazuh.

## Some examples are:

Multiple SSH authentication failures
Connection attempts made repeatedly from one source
Suspicious network behaviors/patterns

These are events to allow analysts to detect potential intrusions and start an investigation.

Further analysis on these alerts is found here: [Detection Analysis](docs/04-detection-analysis.md)