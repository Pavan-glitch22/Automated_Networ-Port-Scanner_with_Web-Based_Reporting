# Automated_Networ-Port-Scanner_with_Web-Based_Reporting

##  Introduction

In cybersecurity, network scanning is one of the first and most important steps in penetration testing. Before attacking any system, it is necessary to understand what devices are present in the network, which ports are open, and what services are running.

In this project, I built an automated port scanning system using tools like Nmap and Masscan. The main idea was to automate the scanning process and display the results in a web page that updates automatically.

The project was done in a virtual lab using Kali Linux and Metasploitable 2 to ensure safe testing.

---
##  Objective

* To perform network scanning and identify live hosts
* To scan open ports and running services
* To automate scanning using bash scripting
* To display results in a web-based dashboard
* To schedule automatic scans using cron jobs
* To understand real-world network monitoring

---

##  Project Overview

This project automates the process of scanning a network and displaying results in a browser.

* Target Network: 192.168.56.0/24
* Target Machine: Metasploitable 2
* Scan Tools: Nmap & Masscan
* Output: Web page (Apache server)
* Automation: Cron job every 10 minutes

---

##  Tools Used

* Kali Linux
* Nmap
* Masscan
* Netdiscover
* Apache2
* VirtualBox

---

##  Lab Setup

* Host Machine: Windows 11
* Attacker Machine: Kali Linux
* Target Machine: Metasploitable 2
* Network: Host-Only Network

Both machines were connected in the same network for communication. The setup was isolated to avoid affecting real systems.

---

## 🔍 Methodology

### 1. Network Identification

Used `ip a` to identify network interfaces and IP range.

### 2. Device Discovery

Used:

```
nmap -sn 192.168.56.0/24
```

to find live hosts in the network.

### 3. Port Scanning

Used Nmap for service detection:

```
nmap -sV 192.168.56.101
```

Used Masscan for fast scanning:

```
masscan 192.168.56.101 -p1-10000 --rate=10000
```

### 4. Automation Script

Created a bash script to:

* Run Nmap scan
* Generate HTML file
* Add timestamp
* Save results in web directory

### 5. Cron Job

Scheduled script using:

```
*/10 * * * * /home/pavan/scan_script.sh
```

This runs the scan every 10 minutes automatically.

### 6. Web-Based Reporting

Results were displayed on:

```
http://<kali-ip>/scan_results.html
```

---

##  Screenshots
![Afterautomation1](screenshota_sn/Afterautomation1.png)

![Afterautomation2](screenshota_sn/Afterautomation2.png)
---

##  Key Findings

* Multiple open ports detected on Metasploitable 2
* Critical backdoor on port 1524
* FTP vulnerable to backdoor attack
* Telnet sending plaintext credentials
* Samba vulnerable to exploits
* Apache Tomcat with default credentials

---

##  Possible Attacks

* Root access via bind shell (port 1524)
* FTP backdoor exploitation
* Credential sniffing via Telnet
* Brute force attacks on SSH
* Web attacks on Apache server

---

##  Remediation

* Disable unused ports
* Replace insecure services (Telnet → SSH)
* Use strong passwords
* Update outdated software
* Implement firewall rules

---

##  What I Learned

* Network scanning concepts
* Difference between Nmap and Masscan
* Bash scripting for automation
* Using cron jobs for scheduling
* Hosting results using Apache

---

##  Disclaimer

This project was performed in a controlled lab environment using intentionally vulnerable systems.
For educational purposes only.

---

##  Author

Pavan N
Cybersecurity Student | CEH Candidate
