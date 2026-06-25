# Virtualized SOC for Security Monitoring and Incident Response

## Project Overview

This project presents the design and implementation of a virtualized Security Operations Center (SOC) for security monitoring, threat detection, incident management and automated response.

The solution was implemented in a laboratory environment inspired by a real enterprise network. It integrates several open-source security tools to centralize logs, detect suspicious activities, manage incidents and automate response actions.

## Objectives

The main objectives of this project are:

* Design a segmented virtual network architecture.
* Centralize security logs and alerts using Wazuh.
* Detect network and endpoint threats.
* Automate incident response using Shuffle.
* Manage security alerts and cases using TheHive.
* Enrich indicators of compromise using Cortex, VirusTotal and MISP.
* Perform endpoint investigation and response using Velociraptor.
* Validate the SOC through practical attack scenarios.

## Network Architecture

The virtual infrastructure is divided into several network zones:

* WAN
* DMZ
* LAN USERS
* LAN AD
* LAN ADMIN
* LAN SOC

The network segmentation is managed through pfSense, which provides routing, firewall rules, NAT, VPN access and Suricata IDS integration.

## Tools Used

* VMware Workstation
* pfSense
* Suricata
* Wazuh
* Shuffle
* TheHive
* Cortex
* MISP
* Velociraptor
* VirusTotal
* Docker
* NGINX
* Flask API

## Implemented Attack Scenarios

### Scenario 1: SSH Brute Force Attack

An SSH brute force attack is simulated against the DMZ server. Wazuh detects the suspicious authentication attempts, then Shuffle triggers the response workflow, creates an incident in TheHive and blocks the attacker IP address through pfSense.

### Scenario 2: Network Reconnaissance

A network scan is performed using Nmap. Suricata detects the scan, Wazuh correlates the alert and Shuffle launches the response workflow. The incident is created in TheHive and the source IP address is blocked.

### Scenario 3: Malware Incident

A suspicious file is analyzed using VirusTotal. When the file is detected as malicious, Wazuh triggers an alert, Shuffle creates the incident in TheHive, enriches the observable using Cortex and MISP, and isolates the compromised endpoint using Velociraptor.

## Repository Structure

```text
docs/                 Project report, diagrams and documentation
configs/              Sanitized configuration files
scripts/              Python, Flask and response automation scripts
docker/               Docker Compose files
shuffle-workflows/    Exported Shuffle workflows
screenshots/          Screenshots of the implementation and results
tests/                Documentation of attack scenarios and validation
```

## Security Notice

All credentials, API keys, tokens, private IP addresses, public IP addresses and sensitive information have been removed or anonymized.

This repository is for academic and educational purposes only.
