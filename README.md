![JITL Megalab Completed Topology](/jitl-megalab-topology.png)

# **🚀 The JITL CCNA Mega Lab: Full Enterprise Deployment**

Welcome to the "final boss" of my CCNA preparation. This repository contains my completed **JITL Cisco Packet Tracer Mega Lab**, a comprehensive project that touches nearly every configuration topic required for the **Cisco CCNA 200-301** exam.

## **📖 Project Overview**

This isn't just a simple lab; it’s a simulation of a multi-site enterprise network featuring a **Core, Distribution, and Access** layer hierarchy. The project involved configuring everything from the ground up, starting with basic device hardening and ending with complex IPv6 routing and Wireless LAN Controller (WLC) setups.

Shoutout to **[Jeremy's IT Labs](https://www.youtube.com/playlist?list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ)** for providing a great (not to mention FREE) resource!

### **Key Network Highlights:**

- **Dual-Office Architecture:** Integrated two distinct office campuses (Office A and Office B) with a central Core layer.
- **Redundancy & High Availability:** Implemented **HSRPv2** across all VLANs and **EtherChannels** (both L2 and L3) to ensure no single point of failure.
- **Dynamic Routing:** Orchestrated **OSPF Area 0** across all Layer-3 switches and routers, including manual Router ID (RID) assignments and passive interface tuning.
- **Secure Infrastructure:** Hardened the network using **SSHv2**, **DHCP Snooping**, **Dynamic ARP Inspection (DAI)**, and **Port Security**.

## **🛠️ Technical Deep Dive**

### **Layer 2: Switching & Logic**

- **VLAN/VTP Management:** Managed a multi-VLAN environment (PCs, Phones, Wi-Fi, Servers, and Management) using **VTPv2** to ensure consistency across the access layer.
- **Spanning Tree (Rapid PVST+):** Fine-tuned STP priorities so the **Root Bridge** always aligns with the **HSRP Active router** for optimal traffic flow.
- **Trunking:** Manually configured 802.1Q trunks, disabled DTP for security, and utilized a non-default native VLAN (VLAN 1000).

### **Layer 3: Routing & Services**

- **Hybrid Routing:** Combined OSPF for internal reachability with **floating static routes** for redundant Internet edge failover.
- **Network Services:** Configured the head-end router (R1) as a **DHCP Server** for seven different pools and an **NTP Stratum 5 server**.
- **NAT/PAT:** Implemented static NAT for server access and pool-based PAT (overloading) for internal host internet access.

### **Security & Administration**

- **Access Control:** Deployed **Standard and Extended ACLs** to restrict SSH management access and control inter-office traffic.
- **Device Hardening:** Used **Type 9 (scrypt)** hashing for all passwords, configured synchronous logging, and set 30-minute inactivity timeouts on all console lines.

## **🎓 What I Learned (The "Aha\!" Moments)**

Completing a lab of this scale taught me that networking is 10% typing commands and 90% planning and troubleshooting. Here are the biggest takeaways from the process:

### **1\. The Power of Pre-Staging Configs**

- I learned that entering commands directly into the CLI is a recipe for typos in a large environment.
- I shifted to building my configurations in **Notepad** first. This is a more practical "real-world" approach that reduced my error rate and made it easier to audit my own work.

### **2\. Strategic Traffic Flow with STP and HSRP**

- I learned how to align Layer 2 and Layer 3 redundancy. By configuring the **STP Root Bridge** priority to match the **HSRP Active router**, I ensured that traffic doesn't take an inefficient "scenic route" through the standby switch.
- I practiced using **preemption** to ensure that once a primary switch recovers, it automatically reassumes its role as the active gateway.

### **3\. Managing Service Dependencies**

- I realized how many services rely on a rock-solid **IP Helper Address**. I had to configure these on the SVI interfaces so that broadcast DHCP requests from PCs could actually reach the DHCP server (R1) across different subnets.
- I learned the importance of **NTP synchronization** for logging; without a consistent time source across all routers and switches, your Syslog data becomes nearly impossible to correlate during an audit.

### **4\. Security is a Layered Effort**

- It’s not just about one firewall at the edge. I learned to implement **Defense in Depth** by using **Port Security** at the access port, **DHCP Snooping** to block rogue servers, and **DAI** to prevent ARP poisoning.
- I also learned the "Best Practice" for ACLs: applying **Extended ACLs** as close to the source as possible to save network bandwidth.

### **5\. Troubleshooting "Quirky" Infrastructure**

- This lab taught me to trust my configurations but verify the hardware. I encountered Packet Tracer "bugs" where domain names or ACLs wouldn't save correctly, which taught me to use show commands to double-check the actual state of the device regardless of what I just typed.

## **📁 Repository Contents**

- jitl-mega-lab-completed.pkt: The final, 100% completed Packet Tracer file.
  - username: cisco
  - password: ccna
  - enable secret: jeremysitlab
- /configs: Individual .txt files containing the show run for every Router and Switch.
