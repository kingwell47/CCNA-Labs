# Enterprise Network Deployment Series

## Overview

This lab series simulates the deployment of a small enterprise network from the ground up.  
Each lab builds on the previous one, gradually expanding the network and introducing new technologies.

The goal of this series is to practice **realistic network design, configuration, and troubleshooting**, similar to tasks a junior network engineer might encounter when deploying or expanding an enterprise network.

These labs are built primarily using **EVE-NG** to emulate real Cisco IOS behavior.

---

## Series Goals

The labs in this series focus on developing practical experience with:

- enterprise VLAN design
- Layer 2 switching technologies
- inter-VLAN routing
- WAN connectivity
- dynamic routing protocols
- network security policies
- redundancy and high availability

Each lab introduces additional complexity while keeping the topology manageable.

---

## Lab Structure

```
01 enterprise-network-series/
│
├── lab1-campus-network-segmentation/
├── lab2-branch-network-ospf/
└── lab3-enterprise-edge-security/
```

Each lab folder contains:

- topology files
- addressing tables
- configuration documentation
- verification screenshots
- notes and observations

---

## Labs

### Lab 1 – Campus Network Segmentation

The first lab focuses on building a **headquarters campus network** using a core-access design.

Technologies practiced:

- VLANs
- Inter-VLAN routing
- Trunking
- EtherChannel
- DHCP
- Port security
- Spanning Tree

This lab establishes the base network that later labs will expand.

---

### Lab 2 – Branch Office Network

This lab extends the enterprise network by connecting a **remote branch office**.

Technologies introduced:

- WAN routing
- OSPF
- DHCP relay
- IPv6 dual-stack networking

The branch network will dynamically exchange routes with the headquarters network.

---

### Lab 3 – Enterprise Edge and Security

The final lab simulates connecting the enterprise network to the **internet edge**.

Technologies introduced:

- NAT / PAT
- Access Control Lists
- HSRP redundancy
- guest network isolation

This lab focuses on **network security and high availability**.

---

## Design Philosophy

This series follows a simplified **enterprise network model**:

```
Core Layer
│
Access Layer
│
User Devices
```

As the series progresses, additional components such as **branch routers, WAN links, and internet edge devices** are introduced.

---

## Future Expansions

Additional labs may be added to this series covering topics such as:

- advanced OSPF scenarios
- spanning tree optimization
- network redundancy
- troubleshooting scenarios
- larger enterprise topologies

---

## Purpose of This Series

This project serves as:

- a hands-on CCNA study resource
- a networking portfolio
- a record of practical lab work

Networking concepts become much clearer when they are implemented in a working topology, so this series focuses heavily on **building and validating real configurations rather than just studying theory**.
