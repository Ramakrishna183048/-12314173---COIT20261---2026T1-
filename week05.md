
# Week 05 – VLAN Configuration on Switch and Router

## Overview
In this week, I explored how Virtual LANs (VLANs) are configured on a switch and how a router can be used to enable communication between different VLANs. The tasks focused on segmenting a network and then restoring connectivity using routing techniques.

---

## Task 1: VLAN Configuration on Switch

### Objective
To divide a network into separate VLANs using a managed switch and observe how VLANs restrict communication.

###  Network Setup
- 4 Linux Hosts connected to an OpenvSwitch
- Hosts connected to ports: eth1 to eth4
- All hosts initially assigned IP addresses in the same subnet

###  Network Topology

![Network](images/Vlan-Basics-12314173-network.png)

IP Address are:
- Host1 → 10.10.1.73  
- Host2 → 10.10.1.74  
- Host3 → 10.10.1.75  
- Host4 → 10.10.1.76  

All hosts are connected to a single switch.

---
### VLAN 

The switch ports were divided into two VLANs:

- VLAN 10 → Host1, Host2 (eth1, eth2)
- VLAN 20 → Host3, Host4 (eth3, eth4)

Commands used:
```bash
ovs-vsctl set port eth1 tag=10
ovs-vsctl set port eth2 tag=10
ovs-vsctl set port eth3 tag=20
ovs-vsctl set port eth4 tag=20
```
For Verification

Command used
```baash
ovs-vsctl show
```

