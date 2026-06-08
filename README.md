# 🛡️ Secure Enterprise Infrastructure Network

## 📌 Project Overview
This project focuses on designing and deploying a highly secure, redundant, and scalable enterprise network infrastructure. The architecture spans across three main sites: **Cairo Branch, Alexandria Branch, and a Centralized Data Center**, simulating a real-world corporate environment.

Built upon **Cisco’s Three-Tier Hierarchical Model** (Access, Distribution, and Core layers), the network serves as a robust foundation that seamlessly integrates advanced security appliances, including Next-Generation Firewalls (FortiGate NGFW) and Centralized Monitoring Systems (IBM QRadar SIEM).

> 💡 **My Role:** I served as the **Network Infrastructure Engineer**, responsible for designing the topology, implementing Layer 2 & Layer 3 security protocols, ensuring High Availability (HA), and configuring dynamic routing across all branches using the **PNETLab** emulation environment.

---

## 🏗️ Network Topology & Architecture
*(The network is logically segmented to isolate corporate departments such as HR, IT, and Sales, simplifying management and enforcing strict security policies).*

![Enterprise Network Topology](images/topology.png)

---

## ⚙️ Tech Stack & Implemented Protocols

Industry-standard networking protocols were deployed to ensure maximum performance, redundancy, and security. Below are the core implementations:

### 1️⃣ High Availability & Redundancy
* 🔄 **Hot Standby Router Protocol (HSRP):** Configured at the Distribution layer to provide a highly available Default Gateway for all VLANs. In the event of an active switch failure, the standby switch assumes control with zero service interruption.
* 🔗 **EtherChannel (LACP / PAgP):** Aggregated multiple physical links into single logical connections to increase bandwidth capacity and provide link-level redundancy.
* 🌳 **Rapid-PVST+ (Spanning Tree Protocol):** Implemented to prevent Layer 2 bridging loops while ensuring ultra-fast convergence during topology changes. Bridge priorities were optimized for efficient load distribution.

### 2️⃣ Routing & Logical Segmentation
* 🗂️ **VLANs & VTP v3:** Programmatically segmented the network to isolate departmental traffic. VTP version 3 was utilized for secure, encrypted synchronization of the VLAN database across the domain.
* 🛤️ **OSPF (Open Shortest Path First):** Configured dynamic routing (Area 0) to interconnect remote branches and effectively share routing tables with the edge network.

### 3️⃣ Infrastructure Security (Layer 2 & Layer 3)
*(Strict security policies were applied at the Access and Distribution layers to mitigate internal threats).*

![Security Configuration Snippet](images/security-config.png)

* 🛡️ **Port Security (Sticky MAC):** Restricted unauthorized access at the switchport level by limiting the number of allowed MAC addresses and enforcing violation actions (Shutdown).
* 🚫 **DHCP Snooping:** Mitigated Rogue DHCP Server attacks by explicitly defining "Trusted Ports" that are permitted to forward DHCP replies from the legitimate corporate server.
* 🕵️ **Dynamic ARP Inspection (DAI):** Validated ARP packets to protect the network against ARP Spoofing/Poisoning and Man-in-the-Middle (MitM) attacks.
* 🛑 **BPDU Guard & PortFast:** Bypassed the STP listening/learning states for end-user devices to provide immediate network access, while protecting the STP topology from unauthorized rogue switches using BPDU Guard.

---

## 🎯 Business Value & Impact
Engineering a project of this scale demonstrates a deep understanding of enterprise environments and delivers the following business values:
1. **Solid Cybersecurity Foundation:** The heavily secured Layer 2 & Layer 3 infrastructure streamlined the integration with FortiGate and IBM QRadar SIEM, allowing for accurate log collection and threat detection.
2. **Zero-Downtime Operations:** Through HSRP and EtherChannel, the network can sustain the loss of core links or distribution switches seamlessly without impacting the end-user experience.
3. **Future-Proof Scalability:** The Three-Tier hierarchical design ensures that the organization can easily expand by adding new building floors or remote branches without redesigning the core architecture.

---
*This infrastructure was built as part of a comprehensive engineering graduation project aimed at deploying a fully secured network from the ground up, culminating in advanced SIEM monitoring.*
