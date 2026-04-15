# Week 04 – Routing Tables and OSPF

## Overview
This week focused on understanding how routing works in networks. The first task involved configuring a router and hosts across two subnets and analysing routing tables. The second task explored dynamic routing using OSPF, where routers automatically exchange routing information and adapt to network changes.

---

# Task 1: View Routing Tables

## Aim
To understand how routing tables work and how a router forwards packets between different subnets.

---
## Activities Performed
- Created project: View-Routes-12314173
- Added:
  - 3 Linux Hosts
  - 1 Linux Router
  - 1 Ethernet Switch
- Designed network with two subnets:
  - Subnet 1: 10.10.1.0/24
  - Subnet 2: 10.10.2.0/24
- Configured static IP addresses for all devices
- Set gateway (router IP) for hosts
- Enabled IP forwarding on router
- Disabled IP forwarding on hosts
- Started all nodes and verified routing tables
- Tested connectivity using ping

---

## ⚙️ Configuration Details

###  Host 1 Configuration

```bash
auto eth0
iface eth0 inet static
   address 10.10.1.11
   netmask 255.255.255.0
   gateway 10.10.1.1
   up sysctl net.ipv4.ip_forward=0
```
### Host 2 Configuration

```bash
auto eth0
iface eth0 inet static
	address 10.10.1.12
	netmask 255.255.255.0
	gateway 10.10.1.1
        up sysctl net.ipv4.ip_forward=0
```
### Host 3 Configuration

```bash
auto eth0
iface eth0 inet static
	address 10.10.2.2
	netmask 255.255.255.0
	gateway 10.10.2.1
        up sysctl net.ipv4.ip_forward=0
```

### Router Configuration

```bash
auto eth0
iface eth0 inet static
   address 10.10.1.1
   netmask 255.255.255.0

auto eth1
iface eth1 inet static
   address 10.10.2.1
   netmask 255.255.255.0
   up sysctl net.ipv4.ip_forward=1
```
### Routing Table Command

```bash
ip route show
```
### Observations
-Hosts used router as default gateway
-Router had routes for both subnets
-Communication between subnets was successful
---
## Screenshots

#### Screenshot Network Topology

This screenshot shows the network with three hosts and one router forming two subnets.

![Network Topology](./images/View-Routes-12314173-network.png)

#### Screenshot Routing Table Output

This screenshot shows routing tables of hosts and router.

![Routing Table](./)

#### Screenshot Ping Test

This screenshot shows successful communication between hosts across different subnets.

![Ping Test](./)

---
