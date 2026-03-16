# Laboratory Setup

## Virtualization Environment

The lab was set up using VMware Workstation with a Windows 11 host computer. All virtual machines were deployed in the same virtual network for communication among the attacker, the monitored endpoints, and the Wazuh server. The configuration of the lab was meant to simulate a small monitored infrastructure where various operating systems generate logs to be centralised within a SIEM.

## Virtual Machines Used

The lab consists of four virtual machines.

## Wazuh Server

Operating System: Ubuntu Server 22.04  
Role: Central SIEM Platform

Assigned Resources:

- 4 GB of RAM  
- 2 CPU Cores  
- 40 GB of Disk  

This system runs the Wazuh server, which is responsible for collecting logs, analyzing events, and generating alerts.

## Windows Endpoint

Operating System: Windows 10  
Role: Monitored Endpoint

Assigned Resources:

- 4 GB of RAM  
- 2 CPU Cores  
- 40 GB of Disk  

The Windows endpoint has Wazuh Agent installed; therefore, any security logs and system logs generated on the Windows system will be collected at the Wazuh server.

---

### Ubuntu Client

OS: Ubuntu Desktop  
Purpose: Monitored Linux Client

Resources:  
- 2 GB RAM  
- 2 CPU Cores  
- 30 GB Disk Space  

A Wazuh agent is installed on this machine to collect authentication logs and system events.

---

### Attacker Machine

OS: Kali Linux  
Purpose: Simulate Malicious Activities

Resources:  
- 4 GB RAM  
- 2 Cores CPU  
- 40 GB Disk Space  

The system will be used to perform various malicious activities such as brute force and network scanning.

---

## Wazuh Installation Process

The Wazuh server was installed using an official installation script on an Ubuntu Server machine,

```bash
curl -s -O https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a
```

## Installation of all the components required: 

Wazuh Manager 

Wazuh Indexer 

Wazuh Dashboard 

Wazuh's Web Interface will be reachable after installation via the IP of the server for the Wazuh Installation's web server.

## Installing Agents 

Log Collection from Other Operating Systems is enabled with the installation of Wazuh agents at the endpoints to be monitored. 

## Installing the Wazuh Windows Agent 

The Wazuh Windows agent was installed using the graphical installer.

While installing the agent, you configured two attributes:

Manager Address (Wazuh server IP) 

Agent's Authentication Key assigned from the Wazuh Manager. 

After Installation, you can restart Wazuh service and see the endpoint in the Wazuh Dashboard.

## Installing the Wazuh Ubuntu Agent 

The Wazuh agent was installed in the endpoint with Ubuntu using the installation package for Linux:

```bash
sudo apt install wazuh-agent
```

The Wazuh agent was then configured to use the Wazuh Server as the manager in the configuration file for the agent.

=======
# Laboratory Setup

## Virtualization Environment

The lab was set up using VMware Workstation with a Windows 11 host computer. All virtual machines were deployed in the same virtual network for communication among the attacker, the monitored endpoints, and the Wazuh server. The configuration of the lab was meant to simulate a small monitored infrastructure where various operating systems generate logs to be centralised within a SIEM.

## Virtual Machines Used

The lab consists of four virtual machines.

## Wazuh Server

Operating System: Ubuntu Server 22.04  
Role: Central SIEM Platform

Assigned Resources:

- 4 GB of RAM  
- 2 CPU Cores  
- 40 GB of Disk  

This system runs the Wazuh server, which is responsible for collecting logs, analyzing events, and generating alerts.

## Windows Endpoint

Operating System: Windows 10  
Role: Monitored Endpoint

Assigned Resources:

- 4 GB of RAM  
- 2 CPU Cores  
- 40 GB of Disk  

The Windows endpoint has Wazuh Agent installed; therefore, any security logs and system logs generated on the Windows system will be collected at the Wazuh server.

---

### Ubuntu Client

OS: Ubuntu Desktop  
Purpose: Monitored Linux Client

Resources:  
- 2 GB RAM  
- 2 CPU Cores  
- 30 GB Disk Space  

A Wazuh agent is installed on this machine to collect authentication logs and system events.

---

### Attacker Machine

OS: Kali Linux  
Purpose: Simulate Malicious Activities

Resources:  
- 4 GB RAM  
- 2 Cores CPU  
- 40 GB Disk Space  

The system will be used to perform various malicious activities such as brute force and network scanning.

---

## Wazuh Installation Process

The Wazuh server was installed using an official installation script on an Ubuntu Server machine,

```bash
curl -s -O https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a
```

## Installation of all the components required: 

Wazuh Manager 

Wazuh Indexer 

Wazuh Dashboard 

Wazuh's Web Interface will be reachable after installation via the IP of the server for the Wazuh Installation's web server.

## Installing Agents 

Log Collection from Other Operating Systems is enabled with the installation of Wazuh agents at the endpoints to be monitored. 

## Installing the Wazuh Windows Agent 

The Wazuh Windows agent was installed using the graphical installer.

While installing the agent, you configured two attributes:

Manager Address (Wazuh server IP) 

Agent's Authentication Key assigned from the Wazuh Manager. 

After Installation, you can restart Wazuh service and see the endpoint in the Wazuh Dashboard.

## Installing the Wazuh Ubuntu Agent 

The Wazuh agent was installed in the endpoint with Ubuntu using the installation package for Linux:

```bash
sudo apt install wazuh-agent
```

The Wazuh agent was then configured to use the Wazuh Server as the manager in the configuration file for the agent.
After starting the service, Wazuh agent registered successfully with Wazuh and began sending logs forward.