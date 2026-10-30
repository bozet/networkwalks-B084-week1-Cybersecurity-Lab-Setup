# networkwalks-B084-week1-Cybersecurity-Lab-Setup




<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for cybersecurity learning, network administration and ethical hacking practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Project-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Hypervisor-VirtualBox%207.1.8-0070C0?style=flat-square&labelColor=000000&logo=virtualbox&logoColor=white" />
  <img src="https://img.shields.io/badge/OS-Kali%20Linux-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Server-Ubuntu%20Server-E95420?style=flat-square&labelColor=000000&logo=ubuntu&logoColor=white" />
  <img src="https://img.shields.io/badge/Host-Windows%2011-0078D4?style=flat-square&labelColor=000000&logo=windows11&logoColor=white" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Network-Host--Only-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000&logo=linux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Focus-Network%20Security-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Internship-Networkwalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Platform-GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
</p>

---


## 📌 1. Project Overview

This project focuses on building a virtual cybersecurity laboratory using Oracle VirtualBox as the hypervisor.

The environment consists of Kali Linux and Ubuntu Server virtual machines running on a Windows 11 host.

The project provides practical exposure to virtualization, Linux administration, IP addressing, virtual networking and network troubleshooting.

## 🎯 2. Project Objectives

- Install and configure Oracle VirtualBox.
- Download and import Kali Linux.
- Configure a VirtualBox NAT Network.
- Configure a separate Host-Only network.
- Set up an Ubuntu Server virtual machine.
- Understand virtual machine network communication.
- Configure and troubleshoot IPv4 networking.
- Verify network interfaces and connectivity.
- Document technical challenges and troubleshooting procedures.

---

## 🏗️ 3. Lab Architecture

The laboratory consists of the following components:

| Component | Configuration |
|---|---|
| Host Machine | HP EliteBook 8770w |
| Host Operating System | Windows 11 |
| Hypervisor | Oracle VirtualBox 7.1.8 |
| Security Distribution | Kali Linux |
| Server Operating System | Ubuntu Server |
| Kali VM RAM | 3 GB |
| Kali VM CPU | 2 vCPUs |
| Ubuntu VM Name | ubuntu-server-lab |
| Virtual Networking | NAT Network and Host-Only |

### 3.1 Virtual Network Architecture

**NAT Network**

| Parameter | Configuration |
|---|---|
| Network Name | Kali-NAT |
| IPv4 Prefix | 10.0.0.0/24 |
| Gateway | 10.0.0.1 |
| DHCP | Enabled |

**Host-Only Network**

| Parameter | Configuration |
|---|---|
| Host IP Address | 192.168.56.1 |
| Subnet Mask | 255.255.255.0 |
| DHCP Server | 192.168.56.100 |
| DHCP Pool | 192.168.56.101 – 192.168.56.254 |

---

## ⚙️ 4. Tools and Technologies

| Tool | Purpose |
|---|---|
| Oracle VirtualBox | Virtualization |
| Kali Linux | Cybersecurity learning environment |
| Ubuntu Server | Linux server environment |
| Windows 11 | Host operating system |
| 7-Zip | Archive extraction |
| PowerShell | VirtualBox and system management |
| NetworkManager | Linux network configuration |

---

# 🚀 5. Implementation and Configuration

## Step 1: Prepare the Host Machine

The host computer used for this laboratory was an HP EliteBook 8770w running Windows 11.

System resources were considered before allocating memory and processing power to the virtual machines.


## Step 2: Install Oracle VirtualBox

Oracle VirtualBox version 7.1.8 was installed and configured as the hypervisor.

VirtualBox provides the virtualization platform required to create and manage the Kali Linux and Ubuntu Server virtual machines.

**Screenshot – VirtualBox Dashboard**

![VirtualBox Dashboard](screenshots/virtualbox-dashboard.png)

## Step 3: Download and Import Kali Linux

The official Kali Linux prebuilt VirtualBox image was downloaded and extracted.

The virtual machine was subsequently imported into Oracle VirtualBox.

The following resources were allocated:

- Memory: 3 GB
- Processors: 2 vCPUs
- Network Adapter: NAT Network

**Screenshot – Kali Linux Virtual Machine**

![Kali Linux Virtual Machine](screenshots/kali-linux-vm.png)

**Screenshot – Kali Linux Desktop**

![Kali Linux Desktop](screenshots/kali-linux-desktop.png)

## Step 4: Create and Configure the NAT Network

A dedicated NAT Network named `Kali-NAT` was created through the VirtualBox Network Manager.

The network was configured with the following parameters:

```text
Network Name: Kali-NAT
IPv4 Prefix: 10.0.0.0/24
Gateway: 10.0.0.1
DHCP: Enabled
```

The NAT Network was intended to provide outbound connectivity and communication between virtual machines connected to the same NAT Network.

**Screenshot – NAT Network Configuration**

![NAT Network Configuration](screenshots/nat-network-configuration.png)

## Step 5: Configure the Ubuntu Server Virtual Machine

An Ubuntu Server virtual machine named `ubuntu-server-lab` was configured.

The server was assigned a Host-Only network connection for communication within the virtual laboratory.

The following SSH connection details were recorded during the setup:

```text
Virtual Machine: ubuntu-server-lab
Hostname/User: darkhub
Host-Only IP: 192.168.56.101
NAT IP: 10.0.2.15
```

**Screenshot – Ubuntu Server Virtual Machine**

![Ubuntu Server](screenshots/ubuntu-server.png)

## Step 6: Configure the Host-Only Network

A separate Host-Only network was configured in VirtualBox.

This network provides a private communication environment between the host operating system and connected virtual machines.

Configuration:

```text
Host IP: 192.168.56.1
Subnet Mask: 255.255.255.0
DHCP Server: 192.168.56.100
DHCP Pool: 192.168.56.101 - 192.168.56.254
```

The Host-Only network was maintained separately from the NAT Network.

**Screenshot – Host-Only Network Configuration**

![Host-Only Network Configuration](screenshots/host-only-network.png)

## Step 7: Configure Kali Linux Network Settings

The intended static IPv4 configuration for Kali Linux was:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
```

During configuration, Kali Linux encountered a network activation issue.

The static configuration did not establish connectivity, and subsequent DHCP activation attempts also failed to obtain an IPv4 address.

The issue was investigated using NetworkManager and Linux networking utilities.

**Screenshot – Kali Linux Network Configuration**

![Kali Linux Network Configuration](screenshots/kali-network-configuration.png)

**Screenshot – Network Activation Error**

![Network Activation Error](screenshots/network-activation-error.png)

---

# 🔎 6. Network Verification and Troubleshooting

The following Linux commands were used or identified for inspecting network interfaces, routing information and connectivity.

### 6.1 Check Network Interfaces

```bash
ip a
```

Displays available network interfaces and their assigned IP addresses.

**Screenshot – Network Interface Output**

![Network Interfaces](screenshots/network-interfaces.png)

### 6.2 Display Routing Information

```bash
ip route
```

Displays the system's routing table and default gateway information.

**Screenshot – Routing Table**

![Routing Table](screenshots/routing-table.png)

### 6.3 Check NetworkManager Connections

```bash
nmcli connection show
```

Displays configured NetworkManager connections.

### 6.4 Check NetworkManager Device Status

```bash
nmcli device status
```

Displays the status of network devices managed by NetworkManager.

**Screenshot – NetworkManager Status**

![NetworkManager Status](screenshots/networkmanager-status.png)

### 6.5 Test Gateway Connectivity

```bash
ping 10.0.0.1
```

Tests connectivity to the intended NAT Network gateway.

### 6.6 Check DNS Configuration

```bash
cat /etc/resolv.conf
```

Displays the configured DNS resolver information.

### 6.7 Verify SSH Connectivity

```bash
ssh username@192.168.56.101
```

Tests SSH connectivity to the Ubuntu Server using its Host-Only IP address.

*Note: Commands are included for documentation and verification. Only tests actually performed should be reported as successful.*

---

## 🐞 7. Challenges Encountered

### 7.1 Kali Linux Network Activation Failure

During the configuration of the Kali Linux NAT Network adapter, NetworkManager returned an IP configuration activation error.

The network interface appeared as UP, but it did not receive an IPv4 address.

**Troubleshooting observations:**

- The NAT Network was created in VirtualBox.
- DHCP was enabled.
- The Kali network interface was enabled.
- DHCP activation did not successfully assign an IPv4 address.
- Static IPv4 configuration did not establish connectivity.
- The issue required further investigation.

**Status:** Further troubleshooting required.

### 7.2 Virtual Network Configuration

Different VirtualBox network modes were explored to understand how virtual machines communicate.

The NAT Network and Host-Only configurations were maintained separately to avoid interfering with the Host-Only communication environment.

---

## 📚 8. Key Learning Outcomes

Through this project, I gained practical experience in:

1. Virtualization and virtual machine management.
2. Installing and configuring Kali Linux.
3. Working with Ubuntu Server.
4. Understanding NAT Network and Host-Only networking.
5. IPv4 addressing and subnet masks.
6. DHCP and static IP configuration.
7. Linux network troubleshooting.
8. Using command-line networking utilities.
9. Identifying network activation issues.
10. Technical documentation and troubleshooting.

---

## 🔐 9. Security and Ethical Considerations

This laboratory is intended for educational purposes and authorized cybersecurity practice.

All security testing should be conducted within systems owned by the student or systems for which explicit permission has been granted.

---

## 🔗 10. Tools and References

- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Kali Linux](https://www.kali.org/get-kali/)
- [Ubuntu Server](https://ubuntu.com/download/server)
- [7-Zip](https://www.7-zip.org/)

---

## 👤  Author

**Bryan Ntangju Ache**

Cybersecurity Internship  
Networkwalks

**Project:** Cybersecurity Virtual Lab Setup

**Technologies:** Kali Linux | Ubuntu Server | VirtualBox | Windows 11

---

*This repository documents my practical experience in building, configuring and troubleshooting a virtual cybersecurity laboratory.*
