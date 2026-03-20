# Snort IDS/IPS Deployment and Configuration Lab

## Overview

This project demonstrates the installation, configuration, and testing of Snort, an open-source Network Intrusion Detection and Prevention System (IDS/IPS), on an Ubuntu Linux environment.

The objective of this lab was to deploy Snort as a network monitoring and intrusion detection tool capable of analyzing packet traffic, generating alerts for suspicious activity, and logging network events for security analysis.

Throughout this project, Snort was configured to monitor a local network interface, detect ICMP traffic generated through testing, and apply custom detection rules. The system was also tested in multiple operational modes, including Intrusion Detection System (IDS), Intrusion Prevention System (IPS), and packet logger mode.

This project demonstrates foundational skills in:

* Linux system administration
* Network security monitoring
* Intrusion detection system deployment
* Security rule configuration
* Log monitoring and packet inspection

---

## Technologies Used

* Ubuntu Linux
* Snort Intrusion Detection and Prevention System
* GNU Nano Text Editor
* Linux Command Line Interface
* ICMP traffic testing using ping

---

## Lab Objectives

The primary objectives of this project were to:

1. Install and configure Snort on an Ubuntu system
2. Identify the correct network interface for packet monitoring
3. Modify the Snort configuration file to define the protected network
4. Deploy Snort in IDS mode to detect suspicious traffic
5. Generate network traffic to test detection capabilities
6. Configure and validate custom Snort detection rules
7. Monitor Snort alerts and logs in real time
8. Run Snort in packet logger mode for packet capture and analysis

---

## System Preparation

Before installing Snort, the Ubuntu system was updated to ensure the latest package lists and security updates were applied.

Example commands used:

sudo apt update
sudo apt upgrade

Updating the system helps prevent dependency issues and ensures compatibility with security tools.

---

## Installing Snort

Snort was installed using the Ubuntu package manager.

Command used:

sudo apt install snort

The installation process automatically installs the required dependencies and prepares the system to run Snort as a network intrusion detection tool.

After installation, Snort was executed to confirm that the program was successfully installed and accessible from the command line.

---

## Identifying the Network Interface

To configure Snort correctly, the active network interface and local IP address needed to be identified.

Command used:

ifconfig

The command output displayed the system's network interfaces and their assigned IP addresses. The interface used in this lab environment was:

Interface: enp0s3
Example IP Address: 10.0.2.15

This information was required for proper Snort configuration.

---

## Snort Configuration

The primary configuration file for Snort is:

/etc/snort/snort.conf

This file was opened using the Nano text editor:

sudo nano /etc/snort/snort.conf

One of the most important configuration variables modified in this lab was:

HOME_NET

This variable defines the local network that Snort should monitor and protect.

Example configuration:

var HOME_NET 10.0.2.15

Defining HOME_NET allows Snort to differentiate between internal and external network traffic during packet inspection.

---

## Running Snort in IDS Mode

Snort was first launched in Intrusion Detection System (IDS) mode to monitor network traffic and generate alerts when suspicious activity was detected.

Example command:

sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3

In this mode, Snort analyzes packets passing through the network interface and outputs alerts directly to the console.

---

## Generating Test Network Traffic

To verify that Snort was successfully detecting traffic, ICMP packets were generated using the ping command.

Example command:

ping <target IP>

These ICMP packets were detected by Snort and logged as network activity, confirming that the IDS was properly monitoring traffic.

---

## Running Snort in IPS Mode

Snort was also executed in Intrusion Prevention System (IPS) mode.

In this mode, Snort is capable of actively blocking or dropping malicious packets based on configured detection rules. This transforms Snort from a passive monitoring system into an active network defense mechanism.

---

## Creating Custom Snort Rules

Custom detection rules were written to allow Snort to identify specific types of network activity.

Rules were edited using Nano within the Snort rules configuration.

Example rule:

alert icmp any any -> $HOME_NET any (msg:"ICMP Detected"; sid:1000001; rev:1;)

This rule instructs Snort to generate an alert whenever ICMP packets are detected targeting the defined HOME_NET.

---

## Monitoring Snort Alerts

Snort generates alerts that are stored in log files located in:

/var/log/snort/

To monitor alerts in real time, the following command was used:

sudo tail -f /var/log/snort/alert

This command continuously displays new log entries as Snort detects network activity.

Real-time monitoring is commonly used in Security Operations Centers (SOCs) to identify suspicious network behavior.

---

## Packet Logger Mode

Snort was also executed in packet logger mode to capture and store network packets for later analysis.

Packet logging allows security analysts to perform deeper forensic investigations into suspicious traffic patterns or potential network intrusions.

---

## Project Structure

snort-ids-ips-lab
│
├── README.md
├── screenshots
│   ├── 01-ubuntu-system-update.png
│   ├── 02-snort-installation.png
│   ├── 03-snort-install-verification.png
│   ├── 04-network-interface-ifconfig.png
│   ├── 05-snort-config-open-nano.png
│   ├── 06-snort-home-net-config.png
│   ├── 07-snort-configuration-adjustments.png
│   ├── 08-snort-ids-mode-command.png
│   ├── 09-snort-icmp-detection.png
│   ├── 10-snort-ips-mode.png
│   ├── 11-snort-rule-edit.png
│   ├── 12-snort-rule-validation.png

---

## Skills Demonstrated

This project demonstrates practical experience with:

* Linux command line administration
* Network intrusion detection systems
* Security tool deployment
* Network interface configuration
* Packet analysis and monitoring
* Security rule creation
* Log analysis and security event monitoring

---

## Learning Outcome

Through this project, I gained hands-on experience deploying and configuring a network intrusion detection system within a Linux environment. The lab demonstrates how IDS tools analyze network packets, detect suspicious activity, and generate alerts for further investigation.

Understanding how to deploy and configure tools like Snort is an important skill for cybersecurity roles such as:

* SOC Analyst
* Security Analyst
* Network Security Engineer
* Cybersecurity Analyst

---

## Author

Quenten Conley

