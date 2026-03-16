## Incident Response Playbooks

## Overview

Following the detection of suspicious activities via the Security Incident Event Management (SIEM), the Security Operations Center (SOC) has a responsibility to investigate the event and determine the appropriate response.

This section presents example incident response playbooks based on the simulated attacks performed in this laboratory.

Specifically. these example-playbooks will provide guidance to analysts for conducting their initial investigation and then subsequent responses to each alert generated within Wazuh.

---

## Playbook 1 - SSH Brute Force Attack

## Detection

Wazuh will generate an alert indicating multiple unsuccessful SSH authentication attempts to an Ubuntu endpoint. 

This type of activity could be an indication that there is a brute-force attack that is attempting to guess user credentials.

--- 

## Investigation

When performing the above-listed checks, SOC analysts must accomplish the following:

- Identify the Source IP Address of the SSH attempted login 
- Verify the Number of Login Attempts Failed
- Verify whether or not there were any Successful Login Attempts 
- Identify which user accounts were targeted
- Identify if the Login Attempts were from an Internal or External Host

--- 

## Response

The following are some of the possible response actions that an analyst could take: 

1. Block Attackers Source IP Address via Firewall 
2. Temporarily disable targeted user accounts
3. Enable SSH Key Authentication instead of Password Authentication 
4. Enable Rate Limiting or Fail2Ban (or similar program)

---

## Mitigation

Possible long-term mitigation measures include:

- Enforcing password policies that require complexity
- Using SSH keys for authentication
- Restricting SSH access to trusted networks
- Monitoring authentication activity to identify anomalies

---

# Playbook Part 2 - Port Scanning Detection

## Detection

Wazuh has detected multiple connection attempts that target the Windows endpoint.

This could indicate reconnaissance activities from an attacker, as they are likely scanning for open services.

---

## Investigation

The analyst should verify:

- The **source IP address** of the device doing the scan
- The **ports being scanned**
- The **number of connection attempts over time**
- If the host that conducted the scan has connected with any other systems on the network

---

## Response Action

Potential response actions include:

- Blocking the IP that was scanning
- Monitoring the host for further suspicious activity
- Reviewing the list of open services on the targeted system
- Hardening firewall rules to restrict access to only those needed by authorized users

---

## Mitigation

To reduce exposure to scanners and scanning activity:

- Close open ports that do not need to be open
- Limit the ability of anyone outside your organization from accessing critical services
- Use network segmentation (divide into multiple pieces with their own access requirements)
- Monitor for repeated connection attempts made by unknown hosts

---

## Role of Wazuh in Incident Response

Wazuh is used in the lab to gather all of the different types of security events from all of their endpoints so that they can have one central location where they can see security events and respond to them from that one area.

The Wazuh platform will collect logs from the different endpoints in real-time, which allows analysts to detect suspicious activity immediately and begin their investigation.

Wazuh not only has detection capabilities, but it offers features that allow the analyst to automate their responses to detected events. One example of this is the **Active Response** feature that Wazuh has; it can automatically perform security actions on malicious IP addresses, such as blocking them.

---

### XDR Understanding

Contemporary security systems offer capabilities of discovery and responding to incidents on several separate systems at once.

In a live system environment Wazuh can work with firewalls, endpoint protection software and orchestration solutions to automate a portion of the incident response ability.

Extended Detection and Response (XDR) enables companies to respond rapidly to an identified threat by detecting it more effectively and coordinating responses across their environment.