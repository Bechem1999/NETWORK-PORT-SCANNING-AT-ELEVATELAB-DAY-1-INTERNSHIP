# 🔎 Local Network Port Scanning

![Kali Linux](https://img.shields.io/badge/Kali%20Linux-557C94?logo=kalilinux&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-4EAA25?logo=nmap&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?logo=wireshark&logoColor=white)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Project-red)
![Network Security](https://img.shields.io/badge/Network-Security-blue)
![Elevate Labs](https://img.shields.io/badge/Elevate%20Labs-Internship-purple)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview

This project was completed as **Task 1 of my Cybersecurity Internship at Elevate Labs**.

The objective was to scan an authorized local network, identify active devices, discover open TCP ports, identify services running on those ports, and assess potential security risks associated with exposed network services.

**Tools Used:** Kali Linux, Nmap and Wireshark.

---

## 🎯 Objectives

- Identify the local IP address and network range.
- Discover active devices on the local network.
- Identify open TCP ports.
- Identify services running on open ports.
- Understand potential security risks.
- Analyse network traffic using Wireshark.
- Save and document scan results.

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| 🐉 Kali Linux | Cybersecurity testing environment |
| 🔎 Nmap | Network discovery and port scanning |
| 🦈 Wireshark | Network traffic and packet analysis |

---

## 🔬 Methodology

### 1. Check Nmap Installation

First, I verified that Nmap was installed and working correctly.

```bash
nmap --version
```

If Nmap was not installed:

```bash
sudo apt update
sudo apt install nmap -y
```

---

### 2. Identify the Local IP Address

The local IP address and network interface were identified using:

```bash
ip -br addr
```

The routing table was then checked using:

```bash
ip route
```

These commands were used to determine the authorized local network range.

---

### 3. Discover Active Devices

After identifying the local network range, Nmap was used to discover active hosts.

```bash
nmap -sn <LOCAL_NETWORK>/24
```

Example:

```bash
nmap -sn 10.0.0.2/24
```

The actual network range used in the project was based on the local network configuration.

---

### 4. Perform TCP SYN Scan

A TCP SYN scan was performed to identify open TCP ports.

```bash
sudo nmap -sS 10.0.0.2/24/24
```

Example:

```bash
sudo nmap -sS 10.0.0.2/24/24
```

The `-sS` option performs a TCP SYN scan and is commonly used for TCP port discovery.

---

### 5. Identify Services and Versions

After identifying active hosts and open ports, service and version detection was performed against authorized hosts.

```bash
sudo nmap -sV <TARGET_IP>
```

Example:

```bash
sudo nmap -sV 10.0.0.2/24
```

This helped identify the services associated with the discovered ports.

---

### 6. Save the Nmap Scan Results

The scan results were saved as a text file using:

```bash
sudo nmap -sS 10.0.0.2/24/24 -oN nmap_scan.txt
```

The results can also be saved in multiple formats using:

```bash
sudo nmap -sS 10.0.0.2/24 -oA elevatelabs_task1
```

This generates:

```text
elevatelabs_task1.nmap
elevatelabs_task1.xml
elevatelabs_task1.gnmap
```

---

### 7. Analyse Network Traffic with Wireshark

Wireshark was used to capture and analyse network traffic generated during the Nmap scan.

Wireshark was started using:

```bash
wireshark
```

Useful display filters included:

```text
tcp
```

For a specific port:

```text
tcp.port == 80
```

For traffic involving a specific IP address:

```text
ip.addr ==10.0.0.2/24
```

The captured traffic helped demonstrate the TCP communication associated with network scanning.

---

## 📊 Scan Results

The Nmap scan was used to identify active hosts, open ports and associated services.

| IP Address | Port | Protocol | Service      | State |
|------------|------|----------|---------     |-------|
| 10.0.0.1   | 135  | TCP      | Msrpc        | Open |
| 10.0.0.1   | 445  | TCP      | Microsoft-ds | Open |

> **Note:** Replace the entries above with the actual results obtained from the Nmap scan.

---

## 🔐 Security Analysis

Open ports indicate that network services are accessible on a device.

An open port is not automatically a vulnerability. The security risk depends on the service, configuration, authentication mechanisms, software version and whether the service is actually required.

### Common examples

**Port 22 – SSH**

SSH is commonly used for remote administration.

Potential risks include:

- Unauthorized login attempts
- Weak authentication
- Password-guessing attacks
- Unnecessary remote access

Recommended controls include strong authentication and restricting SSH access to trusted devices or networks.

**Port 80 – HTTP**

HTTP is commonly used for web services.

Potential concerns include:

- Unencrypted communication
- Exposed administrative interfaces
- Outdated web applications
- Improper access controls

Where appropriate, HTTPS should be used to protect web communication.

**Port 443 – HTTPS**

HTTPS provides encrypted web communication using TLS.

However, the web server and application must still be securely configured and regularly updated.

---

## 📸 Project Evidence

### 1. Nmap Installation

![Nmap Version](screenshots/01-nmap-version.png)

<img width="1035" height="122" alt="nmap installed" src="https://github.com/user-attachments/assets/d62cb544-f163-4cec-9b89-b0a98a70e966" />

### 2. Local Network Information

![Network Information](screenshots/02-network-information.png)
<img width="912" height="436" alt="local network information" src="https://github.com/user-attachments/assets/97d94d1d-04ab-4d5e-b826-4a8fc3a1bcf5" />

### 3. Host Discovery

![Host Discovery](screenshots/03-host-discovery.png)
<img width="600" height="197" alt="network host discovery" src="https://github.com/user-attachments/assets/e695c5f6-79eb-449e-90d3-4cce4480d417" />


### 4. TCP SYN Scan

![Nmap SYN Scan](screenshots/04-syn-scan.png)

<img width="742" height="396" alt="NMAP SYN scan" src="https://github.com/user-attachments/assets/a08f5f8f-98be-44fd-957a-aa5cea39e381" />

### 5. Service Detection

![Service Detection](screenshots/05-service-detection.png)
<img width="910" height="170" alt="scan report" src="https://github.com/user-attachments/assets/73f6c4b3-abd9-4feb-b52a-f4f4481640bd" />

### 6. Wireshark Analysis

![Wireshark Analysis](screenshots/06-wireshark-analysis.png)
<img width="985" height="647" alt="wireshark" src="https://github.com/user-attachments/assets/cde1a50f-7c75-4d42-b03b-20277718be0b" />

---

## 🧠 Key Learning Outcomes

Through this project, I gained practical experience in:

- Network reconnaissance
- Host discovery
- TCP/IP networking
- TCP SYN scanning
- Open port identification
- Service identification
- Network attack surface analysis
- Packet analysis using Wireshark
- Security risk assessment
- Cybersecurity documentation

---

## 🛡️ Security Recommendations

Based on the findings and concepts demonstrated in this project:

- Disable unnecessary network services.
- Restrict administrative services to trusted hosts.
- Use firewalls to control network access.
- Keep network services and operating systems updated.
- Use strong authentication mechanisms.
- Monitor exposed network services.
- Regularly review network configurations.
- Segment sensitive systems where appropriate.

---

## ⚠️ Ethical Disclaimer

This project was performed in an authorized local/lab environment for educational and cybersecurity training purposes.

Network scanning should only be performed against systems and networks for which explicit permission has been granted.

---

## 🎓 Internship Context

This project was completed as **Task 1 of my Cybersecurity Internship at Elevate Labs**.

The project provided practical experience in network reconnaissance, port scanning, service identification, packet analysis and security assessment.

---



---

## ⭐ Acknowledgement

Special thanks to **Elevate Labs** for providing the opportunity to develop practical cybersecurity skills through hands-on internship projects.

---

### 🔗 Technologies

`Kali Linux` `Nmap` `Wireshark` `TCP/IP` `Network Security` `Cybersecurity`

