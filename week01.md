
# week01 – Introduction to GNS3 and Network Setup

## Overview
This lab introduces the GNS3 network simulator. The objective was to create a simple network project with a single Linux host and understand how network simulation environments work. GNS3 allows users to design, configure, and test network topologies without using physical hardware.

## Tasks Performed

### Section A
- Installed required tools:
  - VirtualBox
  - GNS3
- Created private GitHub repository:
  - Format: studentID-COIT20261-2026T1(12314173-COIT20261-2026T1)
- Created initial portfolio file (week01.md)

### Section B: GNS3 Basics
- Created a new project: GNS3-Intro-12314173
- Added a Linux Host node
- Added annotations
- Assigned static IP address 
- Configured IP using 
- Started node and opened console
- Verified IP using command


## Host Configuration

| **Step** | **Task** | **Description** | **Status** |
|---|---|---|---|
| 1 | Create New Project | Created project named `GNS3-Intro-<studentid>` in GNS3 |  Done |
| 2 | Add Linux Host | Dragged a single Linux Host node onto the workspace |  Done |
| 3 | Add Project Info Text | Added text showing project title, name, student ID, date, unit code, campus, and teacher |  Done |
| 4 | Select IP Address | Selected static IP address `10.10.1.1` for the host |  Done |
| 5 | Add IP Label | Added text near the node displaying the IP address `10.10.1.1` |  Done |
| 6 | Configure Static IP | Edited `/etc/network/interfaces` to set static IP before starting the node |  Done |
| 7 | Start the Node | Started the Linux host node in GNS3 |  Done |
| 8 | Open Web Console | Opened a web console in a new browser tab |  Done |
| 9 | Verify IP Address | Ran `ip address show` to confirm the IP address configuration | Done|
| 10 | Close Project | Verified all outputs, documented commands and learnings, then closed the project | Done|

---

## Network Interface Configuration

### File: `/etc/network/interfaces`

The following configuration was applied to the `/etc/network/interfaces` file **before** starting the node:

```bash

# Static config for eth0
auto eth0
iface eth0 inet static
    address 10.10.1.1
    netmask 255.255.255.0
    up sysctl net.ipv4.ip_forward=0
```

### Configuration
```
auto eth0
```
→ Automatically brings up the eth0 interface during system boot.
```
iface eth0 inet static
```
→ Specifies that the eth0 interface is configured with a static IPv4 address.
```
address 10.10.1.1
```
→ Assigns the IP address 10.10.1.1 to the eth0 interface.
```
netmask 255.255.255.0
```
→ Defines the subnet mask, indicating the network range (/24 network).
```
up sysctl net.ipv4.ip_forward=0
```
→ Disables IP forwarding, ensuring the system behaves as a host (not a router).

## Commands Used
```
ip address show
```
→ Displays the current IP addresses and detailed network interface configuration of the system.
```
cat /etc/network/interfaces
```
→ Outputs the contents of the network configuration file, allowing verification of the static IP settings.
```
sysctl net.ipv4.ip_forward
```
→ Checks the status of IP forwarding, indicating whether the system is configured to route packets between interfaces.

>  **Project Files**
>  
> 🔗 [Download GNS3 Project](./GNS3-Intro-12314173.gns3project)
## Week 01 – Project Files

The complete GNS3 project file for Week 01 can be accessed using the link below.
It includes the configured Linux host, static IP setup, and required annotations for the lab task.

![GNS3 NETWORK PROJECT FILE](./)

### Output: `ip address show`

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever

6: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN qlen 1000
    link/ether 02:42:a2:84:36:00 brd ff:ff:ff:ff:ff:ff
    inet 10.10.1.1/24 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:a2ff:fe84:3600/64 scope link
       valid_lft forever preferred_lft forever
```

## Screenshots 

### Screenshot 1: GNS3 Network Topology

> This screenshot shows the GNS3 workspace with the Linux host node, project title, student details, and IP address label.

![Network Topology](images/GNS-Intro-12314173-network.png.png)

---

### Screenshot IP Address

![IP Address Console](images/GNS-Intro-12314173-ipaddress.png.png)

---

## Key Knowledge & Skills Developed

### Networking Concepts

| **S.N.** | **Concept** | **Learning Outcomes** |
|---|---|---|
| 1 | Static IP Configuration | How to manually assign an IP address to a Linux network interface using `/etc/network/interfaces` |
| 2 | Subnet Mask | Understanding how a subnet mask defines the network and host portions of an IP address. |
| 3 | IP Forwarding | Understanding how IP forwarding allows a system to route packets between networks and how to enable or disable it. |
| 4 | Network Interfaces |  Understanding how network interfaces (like `eth0`) allow a system to connect and communicate within a network. |

### Technical Skills

| **S.N.** | **Skill** | **Description** |
|---|---|---|
| 1 | GNS3 Project Setup | Creating new projects and configuring simple network topology |
| 2 | Linux CLI | Using commands like `ip address show` to inspect network interfaces |
| 3 | File Editing | Editing the `/etc/network/interfaces` file to configure static IP settings |
| 4 | Network Verification | Confirming IP settings by reading and interpreting `ip address show` output |
| 5 | Documentation | Documenting configuration steps, commands, and outputs clearly in the GitHub README file. |

---

## Reflection

### Key Success 

- Successfully configured a static IP address on a Linux host within GNS3
- Gained practical experience using the GNS3 network simulator  
- Learned how to configure network interfaces using the `/etc/network/interfaces` file
- Verified network configuration using Linux CLI commands such as `ip address show`
- Improved understanding of basic networking concepts such as subnet masks and IP forwarding

### Challenges faced 

- The configuration changes did not appear immediately. Restarting the node in GNS3 helped apply the network configuration successfully.
- I initially found it difficult to understand the output of the `ip address show` command. After reviewing the interface details, I was able to identify the IP address, MAC address, and interface status.
- At first, I was not sure where to edit the network configuration file. I solved this by checking the correct path `/etc/network/interfaces` and editing it in the Linux node.

---
