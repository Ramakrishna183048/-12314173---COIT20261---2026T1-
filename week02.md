
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
  
               nano /etc/network/interfaces
               ifdown eth0
               ifup eth0

#### 3. Using `ip` Command
- Configured IP address on fourth host using:
  Command used: 

             ip address add <ipaddress>/<mask> dev eth0

  For my Host 4 IP address using

             ip address add 10.10.2.4/24 dev eth0

## Testing Results (IP Verification)

   Command used:

              ip address show
  












 
