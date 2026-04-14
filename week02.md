
# Week02

## Overview

In this week, the focus was on configuring static IP addresses using different methods and testing network connectivity using the ping command. The activities helped in understanding both persistent and temporary IP configuration techniques as well as basic network troubleshooting.

-----

## Task 1: Setting Static IP Addresses

### Activities Performed
- Created a GNS3 project named: Setting-IP-12314173
- Added four Linux hosts and one Ethernet switch
- Connected all hosts to form a LAN
- Setting network for them 

### IP Configuration Methods

#### 1. Using GNS3 Configure Menu
- Assigned static IP addresses to two hosts before starting them
- Configuration applied automatically when nodes were started

#### 2. Using `/etc/network/interfaces`
- Opened console of third host
- Edited the file to manually assign IP address
- Restarted network service using:
commands are:
  
```bash
  
nano /etc/network/interfaces
ifdown eth0
ifup eth0

```
  
#### 3. Using `ip` Command
- Configured IP address on fourth host using:
Command used:

```bash

ip address add <ipaddress>/<mask> dev eth0

```
 
For my Host 4 IP address using

```bash

ip address add 10.10.2.4/24 dev eth0
```

## Testing Results (IP Verification)

Command used:

```bash
ip address show
```
### Observations
- All four hosts successfully received unique IP addresses
- Interfaces were active and correctly configured

---

## Screenshots

- Network topology  
![Network](images/Setting-IP-12314173-network.png)

- Host1 IP  
![Host1](images/Setting-IP-12314173-host1.png)

- Host2 IP  
![Host2](images/Setting-IP-12314173-host2.png)

- Host3 IP  
![Host3](images/Setting-IP-12314173-host3.png)

- Host4 IP  
![Host4](images/Setting-IP-12314173-host4.png)

---

## Reflection (Task 1)
This task improved my understanding of different methods to assign IP addresses in Linux systems. I learned the difference between permanent configuration using system files and temporary configuration using command-line tools.

---
## Task 2: Testing Network Connectivity using Ping

### Activities Performed
- Tested connectivity between hosts using ping command
- Ran ping without options and observed output
- Tested ping to an invalid IP address
- Used different options such as count, interval, and packet size

---
## Ping Testing 

### 1. Basic Ping
```
ping 10.10.1.2
```

- Successful communication between hosts
- Observed round-trip time 

---

### 2. Ping to Invalid Address
```
ping 10.10.1.99
```
- No response received
- 100% packet loss observed

---

### 3. Ping with Options

- Limited number of packets sent
- Modified packet size and interval
- Observed variation in delay

Limit the count of request messages to 5:

```
ping -c 5 10.10.2.2

```
Change the interval between request messages to 2 seconds:

```
ping -i 2 10.10.2.2

```
Change the size of the data sent in a request message to 100 Bytes:

```
ping -s 100 10.10.2.2
```

You can combine options, e.g.:
```
ping -c 3 -s 80 10.10.2.2
```
---

## 📸 Screenshots

- Basic ping  
![Ping Simple](images/Ping-Basics-12314173-simple.png)

- Ping error  
![Ping Error](images/Ping-Basics-12314173-error.png)

- Ping with options  
![Ping Options](images/Ping-Basics-12314173-options.png)

---

## Reflection (Task 2)
This task helped me understand how to verify connectivity and measure network performance using ping. I learned how different options affect the behavior of the command and how packet loss indicates connectivity issues.

---
## Key Concepts Learned

- Static IP configuration methods
- Persistent vs temporary network settings
- Use of ping for connectivity testing
- Packet loss and its meaning

---
