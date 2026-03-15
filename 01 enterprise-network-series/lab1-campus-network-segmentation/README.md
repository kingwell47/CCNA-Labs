# Lab 1 – Campus Network Segmentation

## Overview

This lab simulates the deployment of a **small enterprise campus network**.  
The goal is to segment departments using VLANs while still allowing communication between them through a multilayer switch.

The lab was built in **EVE-NG** to emulate real Cisco IOS behavior rather than relying purely on simulation.

This was one of my first full topology builds outside of Packet Tracer, so it was also a good exercise in configuring switching infrastructure in a more realistic environment.

---

## Objectives

The main objectives of this lab were:

- Segment network traffic using **VLANs**
- Enable **inter-VLAN routing**
- Configure **trunk links between switches**
- Implement **EtherChannel** for link aggregation
- Deploy **centralized DHCP**
- Apply **port security** on access ports
- Observe **Spanning Tree behavior** in a switched network

---

## Network Topology

The network follows a simple **core-access design**.

Core Layer

- 1 multilayer switch responsible for routing between VLANs

Access Layer

- 3 access switches connecting user devices

End Devices

- 20 PCs
- 1 server

Each access switch represents a different area of the office building.

![Lab 1 Network Diagram in Eve-NG](./lab01.png)

---

## VLAN Design

| VLAN | Department | Network         | Gateway      |
| ---- | ---------- | --------------- | ------------ |
| 10   | Management | 192.168.10.0/24 | 192.168.10.1 |
| 20   | HR         | 192.168.20.0/24 | 192.168.20.1 |
| 30   | IT         | 192.168.30.0/24 | 192.168.30.1 |
| 40   | Sales      | 192.168.40.0/24 | 192.168.40.1 |
| 50   | Guest      | 192.168.50.0/24 | 192.168.50.1 |

The default gateways for all VLANs are configured on the **multilayer switch**.

---

## Device Layout

All switches are running the Cisco IOL image:

```
Cisco IOS Software, Solaris Software (I86BI_LINUXL2-ADVENTERPRISEK9-M)
Experimental Version 15.1
```

This platform supports the features required for the lab, including:

VLANs

802.1Q trunking

EtherChannel

Spanning Tree

Port security

Layer 3 routing (when IP routing is enabled)

This makes it suitable for building a core-access campus topology within EVE-NG.

Access Switch 1 – Administration

- Management PCs
- HR PCs

Access Switch 2 – Operations

- IT PCs
- Sales PCs

Access Switch 3 – Public Area

- Guest network devices
- Additional IT workstations

The **Server** is located in the IT VLAN.

---

## Interface Allocation Table

The following tables document the physical connections between devices in the topology.

### Core Switch (CSW1)

| Device | Interface | Connected To | Remote Interface | Purpose             |
| ------ | --------- | ------------ | ---------------- | ------------------- |
| CSW1   | E0/0      | ASW1         | E0/0             | EtherChannel uplink |
| CSW1   | E0/1      | ASW1         | E0/1             | EtherChannel uplink |
| CSW1   | E0/2      | ASW2         | E0/0             | EtherChannel uplink |
| CSW1   | E0/3      | ASW2         | E0/1             | EtherChannel uplink |
| CSW1   | E1/0      | ASW3         | E0/0             | EtherChannel uplink |
| CSW1   | E1/1      | ASW3         | E0/1             | EtherChannel uplink |
| CSW1   | E1/3      | Server       | Eth0             | Server connection   |

---

### Access Switch 1 (ASW1)

| Device | Interface | Connected To | Remote Interface | VLAN         |
| ------ | --------- | ------------ | ---------------- | ------------ |
| ASW1   | E5/0      | PC1          | Eth0             | Management   |
| ASW1   | E5/1      | PC2          | Eth0             | Management   |
| ASW1   | E4/0      | PC3          | Eth0             | HR           |
| ASW1   | E4/2      | PC4          | Eth0             | HR           |
| ASW1   | E4/1      | PC5          | Eth0             | HR           |
| ASW1   | E0/0      | CSW1         | E0/0             | EtherChannel |
| ASW1   | E0/1      | CSW1         | E0/1             | EtherChannel |

---

### Access Switch 2 (ASW2)

| Device | Interface | Connected To | Remote Interface | VLAN         |
| ------ | --------- | ------------ | ---------------- | ------------ |
| ASW2   | E5/0      | PC6          | Eth0             | IT           |
| ASW2   | E5/1      | PC7          | Eth0             | IT           |
| ASW2   | E5/2      | PC8          | Eth0             | IT           |
| ASW2   | E3/0      | PC9          | Eth0             | Sales        |
| ASW2   | E3/1      | PC10         | Eth0             | Sales        |
| ASW2   | E3/2      | PC11         | Eth0             | Sales        |
| ASW2   | E3/3      | PC12         | Eth0             | Sales        |
| ASW2   | E0/0      | CSW1         | E0/0             | EtherChannel |
| ASW2   | E0/1      | CSW1         | E0/1             | EtherChannel |

---

### Access Switch 3 (ASW3)

| Device | Interface | Connected To | Remote Interface | VLAN         |
| ------ | --------- | ------------ | ---------------- | ------------ |
| ASW3   | E3/0      | PC13         | Eth0             | Guest        |
| ASW3   | E3/1      | PC14         | Eth0             | Guest        |
| ASW3   | E3/2      | PC15         | Eth0             | Guest        |
| ASW3   | E3/3      | PC16         | Eth0             | Guest        |
| ASW3   | E1/0      | PC17         | Eth0             | IT           |
| ASW3   | E1/1      | PC18         | Eth0             | IT           |
| ASW3   | E4/0      | PC19         | Eth0             | Guest        |
| ASW3   | E4/1      | PC20         | Eth0             | Guest        |
| ASW3   | E0/0      | CSW1         | E0/0             | EtherChannel |
| ASW3   | E0/1      | CSW1         | E0/1             | EtherChannel |

---

### Port Channel Allocation

| Port Channel   | Member Interfaces | Devices Connected |
| -------------- | ----------------- | ----------------- |
| Port-Channel 1 | E0/0, E0/1        | CSW1 ↔ ASW1       |
| Port-Channel 2 | E0/2, E0/3        | CSW1 ↔ ASW2       |
| Port-Channel 3 | E1/0, E1/1        | CSW1 ↔ ASW3       |

---

## Key Technologies Implemented

### VLAN Segmentation

Departments were separated into individual VLANs to reduce broadcast domains and improve network organization.

### Inter-VLAN Routing

The multilayer switch provides routing between VLANs so that departments can communicate when necessary.

### Trunk Links

Trunk ports allow multiple VLANs to travel between the core switch and access switches.

### EtherChannel

Two physical uplinks between switches were bundled together to create a single logical link, increasing bandwidth and providing redundancy.

### DHCP

A centralized DHCP server assigns IP addresses to devices across all VLANs.

### Port Security

Access ports were configured to restrict the number of allowed MAC addresses and automatically learn connected devices.

### Spanning Tree

Spanning Tree Protocol prevents switching loops and ensures a stable Layer 2 topology.

---

## Verification

After configuration, the following tests were performed:

- PCs successfully received IP addresses via DHCP
- Devices within the same VLAN could communicate
- Devices in different VLANs could communicate through the multilayer switch
- EtherChannel links formed correctly between switches
- Trunk links carried all required VLANs
- Spanning Tree selected the expected root bridge

Example verification commands used:

```
show vlan brief
show etherchannel summary
show spanning-tree
show ip interface brief
```

---

## Skills Practiced

This lab helped reinforce practical knowledge of:

- VLAN design and segmentation
- Layer 2 switching configuration
- Inter-VLAN routing
- Link aggregation
- DHCP deployment
- Network verification and troubleshooting

---

## Files Included

- EVE-NG topology file
- Lab documentation
- Verification screenshots

---

## Notes

This lab is part of the **Enterprise Network Deployment Series**, which gradually expands the network to include:

- Branch office connectivity
- Dynamic routing with OSPF
- Internet edge configuration
- Security policies and redundancy

Future labs will build on this topology.
