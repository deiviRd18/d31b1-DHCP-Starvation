# 💀 DHCP Starvation Attack Tool

**Course:** Network Security (Seguridad Informática)  
**Student:** Junior (ID: 2024-2015)  
**Framework:** Python 3 + Scapy

## ⚠️ Disclaimer
This tool is for **educational purposes only**. It was developed to demonstrate network vulnerabilities in a controlled laboratory environment. Unauthorized use against systems you do not own is illegal.

## 🎥 Video Demonstration
[PASTE YOUR YOUTUBE/DRIVE LINK HERE]

---

## 1. Objective
The main objective of this script is to perform a **Denial of Service (DoS)** attack against a legitimate DHCP server. The tool generates thousands of DHCP DISCOVER packets using randomized spoofed MAC addresses. This exhausts the server's IP address pool (DHCP Binding Table), preventing legitimate clients from obtaining an IP address and connecting to the network.

## 2. Network Topology & Scenario
* **Network Segment:** 20.24.20.0/24 (Based on Student ID).
* **Victim Server:** Cisco Router (20.24.20.15).
* **Attacker:** Kali Linux (20.24.20.2).
* **Interface:** eth0 (VMnet3 Isolated Network).

![Topology Screenshot](img/topology.png)

## 3. Requirements & Usage
* **OS:** Kali Linux / Debian-based Linux.
* **Dependencies:** Python 3, Scapy.
* **Privileges:** Root access is required to inject raw packets.

### Installation
bash
`git clone [https://github.com/deiviRd18/d31b1-DHCP-Starvation.git](https://github.com/deiviRd18/d31b1-DHCP-Starvation.git)
cd D31B1-DHCP-Starvation
pip3 install scapy`

Execution
Bash
`sudo python3 d31b1_dhcp_starvation.py`

4. Proof of Concept (PoC)
Script Execution
The script flooding the network with fake MAC addresses.

Impact on the Router
The command `show ip dhcp binding` reveals the IP pool is fully exhausted.

5. Mitigation Strategies
To defend against this attack in enterprise environments:

Port Security: Limit the number of MAC addresses allowed on a single switch port (e.g., max 2 MACs).

DHCP Snooping: Configure the switch to rate-limit DHCP packets and validate that requests come from trusted sources.

