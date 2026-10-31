# networkwalks-B084-week1-Cybersecurity-Lab-Setup





<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for cybersecurity learning, network configuration and ethical hacking practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Project-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Hypervisor-VirtualBox%207.1.8-0070C0?style=flat-square&labelColor=000000&logo=virtualbox&logoColor=white" />
  <img src="https://img.shields.io/badge/OS-Kali%20Linux-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Host-Windows%2011-0078D4?style=flat-square&labelColor=000000&logo=windows11&logoColor=white" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000&logo=linux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Focus-Network%20Security-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Internship-Networkwalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Platform-GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
</p>

---

## 📌 1. Project Overview

This project documents the setup and configuration of an isolated cybersecurity laboratory using Oracle VirtualBox and Kali Linux.

The objective was to establish a virtual environment for cybersecurity learning, network configuration, Linux administration and ethical hacking practice.

The project involved creating a custom NAT Network, importing Kali Linux, configuring its network interface and troubleshooting connectivity issues encountered during the setup.

## 🎯 2. Project Objectives

- Install and configure Oracle VirtualBox.
- Download and import Kali Linux.
- Create a custom NAT Network using the `10.0.0.0/24` subnet.
- Configure Kali Linux with the required static IP address.
- Establish internet connectivity within the virtual machine.
- Troubleshoot network activation and DHCP issues.
- Document the configuration process and solutions.

---

## 🖥️ 3. Lab Environment and Architecture

### 3.1 Host Machine Specifications

| Component | Configuration |
|---|---|
| Host Machine | HP EliteBook 8770w |
| Operating System | Windows 11 |
| Hypervisor | Oracle VirtualBox 7.1.8 |
| Virtual Machine | Kali Linux |
| Allocated RAM | 3 GB |
| Allocated CPU | 2 vCPUs |
| Network Mode | NAT Network |

### 3.2 Network Architecture

The laboratory uses a custom VirtualBox NAT Network.

| Parameter | Configuration |
|---|---|
| Network Name | Kali-NAT |
| IPv4 Prefix | 10.0.0.0/24 |
| Gateway | 10.0.0.1 |
| DHCP | Enabled |
| Required Kali IP | 10.0.0.2 |
| Subnet Mask | 255.255.255.0 |

The intended configuration assigns Kali Linux a static IP address within the custom NAT Network.

---

## ⚙️ 4. Tools and Technologies

| Tool | Purpose |
|---|---|
| Oracle VirtualBox | Virtualization |
| Kali Linux | Cybersecurity operating system |
| Windows 11 | Host operating system |
| 7-Zip | Archive extraction |
| PowerShell | VirtualBox management |
| NetworkManager | Linux network configuration |
| nmcli | Network configuration through the command line |

---

# 🚀 5. Implementation and Configuration

### Step 1: Prepare the Host Machine

The host computer used for this project was an HP EliteBook 8770w running Windows 11.

Available system resources were considered before allocating memory and processing power to the virtual machine.

**Screenshot – Host Machine Information**

![Host Machine Information](screenshots/host-machine-information.png)

### Step 2: Install Oracle VirtualBox

Oracle VirtualBox version 7.1.8 was installed and configured as the hypervisor.

VirtualBox provides the virtualization platform required to create and manage the Kali Linux virtual machine.

**Screenshot – VirtualBox Dashboard**

![VirtualBox Dashboard](screenshots/virtualbox-dashboard.png)

### Step 3: Download and Import Kali Linux

The official Kali Linux prebuilt VirtualBox image was downloaded and extracted.

The virtual machine was subsequently imported into Oracle VirtualBox.

The following resources were allocated:

- RAM: 3 GB
- Processors: 2 vCPUs
- Network Adapter: NAT Network

**Screenshot – Kali Linux Virtual Machine**

![Kali Linux Virtual Machine](screenshots/kali-linux-vm.png)

**Screenshot – Kali Linux Desktop**

![Kali Linux Desktop](screenshots/kali-linux-desktop.png)

### Step 4: Create and Configure the NAT Network

A dedicated NAT Network named `Kali-NAT` was created through the VirtualBox Network Manager.

The network was configured with the following parameters:

```text
Network Name: Kali-NAT
IPv4 Prefix: 10.0.0.0/24
Gateway: 10.0.0.1
DHCP: Enabled
```

This network was intended to provide internet connectivity to the Kali Linux virtual machine.

**Screenshot – NAT Network Configuration**

![NAT Network Configuration](screenshots/nat-network-configuration.png)

### Step 5: Configure Kali Linux Network Adapter

The Kali Linux virtual machine was connected to the custom `Kali-NAT` network.

The required static IPv4 configuration was:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
```

The network interface was configured through Kali Linux NetworkManager.

**Screenshot – Kali Linux Network Settings**

![Kali Linux Network Settings](screenshots/kali-network-configuration.png)

---

# 🔎 6. Network Troubleshooting and Resolution

During the configuration process, Kali Linux encountered a network activation failure.

This section documents the issue, the troubleshooting process and the alternative configuration that restored network connectivity.

### 6.1 Initial Network Activation Error

When attempting to activate the connection using NetworkManager, the following command was executed:

```bash
sudo nmcli connection up "Wired connection 1"
```

However, the connection failed to activate.

The terminal returned the following error:

```text
Error: Connection activation failed:
IP configuration could not be reserved
(no available address, timeout, etc.).
```

The network interface appeared as UP, but it did not successfully obtain an IPv4 address.

**Screenshot – Kali Linux Network Activation Error**

![Kali Linux Network Activation Error](screenshots/kali-network-activation-error.png)

### 6.2 Troubleshooting Approach

The initial troubleshooting process involved checking the network configuration and attempting to restore connectivity.

The following possibilities were considered:

- Incorrect IPv4 configuration.
- DHCP address allocation failure.
- NetworkManager connection activation issues.
- VirtualBox NAT Network configuration.

The initial static IP configuration did not establish connectivity, and subsequent DHCP activation attempts also failed.

### 6.3 Alternative Configuration and Resolution

An alternative approach was used to reset the IPv4 configuration of the NetworkManager connection and switch it to automatic addressing.

The following command was executed:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.method auto ipv4.addresses "" ipv4.gateway "" ipv4.dns ""
```

This configuration changed the IPv4 method to automatic (DHCP) and cleared the previously configured static address, gateway and DNS values.

The connection was then restarted:

```bash
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

**Result:** The alternative configuration restored network connectivity.

**Screenshot – Successful Network Activation**

![Successful Network Activation](screenshots/network-activation-success.png)


---

## 🧪 7. Network Verification

After restoring network connectivity, the following commands can be used to inspect the network configuration and verify the connection.

### 7.1 Check Network Interfaces

```bash
ip a
```

Displays available network interfaces and their assigned IP addresses.

**Screenshot – Network Interface Output**

![Network Interfaces](screenshots/network-interfaces.png)

### 7.2 Display Routing Information

```bash
ip route
```

Displays the routing table and default gateway information.

**Screenshot – Routing Table**

![Routing Table](screenshots/routing-table.png)

### 7.3 Check NetworkManager Device Status

```bash
nmcli device status
```

Displays the status of network devices managed by NetworkManager.

**Screenshot – NetworkManager Status**

![NetworkManager Status](screenshots/networkmanager-status.png)

### 7.4 Test Gateway Connectivity

```bash
ping 10.0.0.1
```

Tests connectivity to the configured NAT Network gateway.

### 7.5 Test Internet Connectivity

```bash
ping -c 4 8.8.8.8
```

Tests outbound connectivity using Google's public DNS IP address.

### 7.6 Test DNS Resolution

```bash
ping -c 4 google.com
```

Checks whether DNS resolution and network connectivity are working.

*Only report verification tests as successful when their actual command outputs confirm success.*

---

## 🐞 8. Challenges and Lessons Learned

The major technical challenge encountered during this project was the Kali Linux network activation failure.

The issue demonstrated the importance of understanding the relationship between:

- VirtualBox NAT Network configuration.
- Static IPv4 addressing.
- DHCP address allocation.
- Linux NetworkManager.
- Network interface activation.

The successful alternative configuration demonstrated how resetting an incorrect or problematic IPv4 configuration and switching to automatic addressing can restore connectivity.

### Key Learning Outcomes

Through this project, I gained practical experience in:

1. Virtual machine installation and management.
2. Configuring Kali Linux in VirtualBox.
3. Virtual networking and NAT configuration.
4. IPv4 addressing and subnet masks.
5. Static and automatic IP configuration.
6. DHCP troubleshooting.
7. Linux NetworkManager administration.
8. Command-line network troubleshooting.
9. Technical documentation and problem resolution.

---

## 🔐 9. Security and Ethical Considerations

This laboratory is intended for educational purposes and authorized cybersecurity practice.

All security testing should be conducted within systems owned by the student or systems for which explicit permission has been granted.

---

## 🔗 10. Tools and References

- [Oracle VirtualBox](https://www.virtualbox.org/)
- [Kali Linux](https://www.kali.org/get-kali/)
- [7-Zip](https://www.7-zip.org/)
- [Networkwalks](https://networkwalks.com/)

---

## 👤 11. Author

**Bryan Ntangju Ache**

Cybersecurity Internship  
Networkwalks

**Project:** Cybersecurity Lab Environment Setup

**Technologies:** Kali Linux | VirtualBox | Windows 11 | NetworkManager

---

*This repository documents my practical experience in setting up, configuring and troubleshooting a virtual cybersecurity laboratory.*

