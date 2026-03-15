![Lab 1 in Eve-NG](/lab01.png)

# CCNA Networking Labs

Welcome! 👋

This repository contains the networking labs I built before and after studying for the **Cisco Certified Network Associate (CCNA)**. My goal here is to document hands-on practice with networking concepts and to build a portfolio that shows how I approach network design, configuration, and troubleshooting.

Most of these labs are based on scenarios that simulate small enterprise networks, the kind of environments a junior network engineer might encounter in real deployments.

I'm currently building practical networking experience through self-study, lab work, and real configuration practice.

---

## Lab Platforms 🥼

The labs in this repository were built using:

- Cisco Packet Tracer
- EVE-NG
- VPCS (Virtual PC Simulator)

Packet Tracer is useful for quickly testing ideas and learning concepts, while **EVE-NG** allows me to run more realistic Cisco images and build larger topologies.

---

## Repository Structure 🏗️

```
ccna-labs/
│
├── 00 jitl-megalab/
│
├── 01 enterprise-network-series/
│   ├── lab1-campus-network-segmentation/
│   ├── lab2-branch-network-ospf/
│   └── lab3-enterprise-edge-security/
│
└── additional-labs/ (future labs)
```

Each lab folder may include:

- topology files (Packet Tracer / EVE-NG)
- addressing tables
- lab documentation
- verification screenshots
- notes and troubleshooting observations

---

## Labs 🚀

### JITL MegaLab 📢

A large practice lab designed to bring together many CCNA topics in a single network.

Topics explored include:

- VLAN configuration
- Inter-VLAN routing
- Static routing
- DHCP
- NAT
- Access Control Lists
- Routing protocols

This lab helped reinforce how different technologies interact within a single network.

---

### Enterprise Network Deployment Series 💼

A progressive lab series simulating the deployment of a small enterprise network.

---

#### Lab 1 – Campus Network Segmentation

Platform: **EVE-NG**

Technologies practiced:

- VLANs
- Inter-VLAN routing
- Trunking
- EtherChannel
- DHCP
- Port security
- Spanning Tree concepts

This lab simulates a **headquarters campus network** where multiple departments are segmented into VLANs while still allowing communication through a multilayer switch.

---

#### Lab 2 – Branch Office Network _(In Progress)_

Technologies explored:

- OSPF
- WAN connectivity
- DHCP relay
- IPv6 dual-stack networking

This lab expands the enterprise network by connecting a **remote branch office** using dynamic routing.

---

#### Lab 3 – Enterprise Edge and Security _(Planned)_

Technologies planned:

- NAT / PAT
- Access Control Lists
- HSRP
- Edge routing
- Guest network isolation

This lab will simulate connecting the enterprise network to the **internet edge while implementing security policies and redundancy**.

---

## Skills Practiced 🎯

Through these labs I am actively practicing:

- Network segmentation with VLANs
- Layer 2 switching concepts
- Inter-VLAN routing
- Dynamic routing protocols
- WAN connectivity
- Network security policies
- Network verification and troubleshooting

---

## Future Labs 🔮

I plan to continue expanding this repository with additional labs covering topics like:

- advanced OSPF scenarios
- STP tuning and optimization
- network redundancy
- troubleshooting-focused labs
- larger enterprise network simulations

---

## Why This Repository Exists 📝

This repository serves as:

- a personal study archive
- a networking practice log
- a portfolio demonstrating hands-on networking experience

Networking is one of those skills where **actually configuring and breaking things in a lab teaches far more than just reading about it**, so this repo is where I keep track of that journey.

---

## Disclaimer ⚡

These labs are created for educational purposes and may simplify some aspects of real production network design.
