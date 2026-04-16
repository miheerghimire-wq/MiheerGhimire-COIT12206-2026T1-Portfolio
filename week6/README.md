# Week 6 – Address Resolution and Management
 
## Overview
This week focused on ARP and basic address resolution in a routed network. The task involved configuring hosts and routers, checking interface settings, and testing connectivity using ping and ARP-related commands.
 
---
 
## Topology
![Topology](image.png)
 
This topology shows two LANs connected through two routers. The left side contains HostA to HostD and the right side contains Host1 to Host4.
 
---
 
## Left LAN Host Configurations
 
### HostA
![HostA](hostA.png)
 
HostA was configured with a static IP address in the 10.10.10.0/24 network and used Router1 as the default gateway.
 
### HostB
![HostB](hostB.png)
 
HostB was configured in the same subnet as HostA with a different host address.
 
### HostC
![HostC](hostC.png)
 
HostC was configured with a static IP in the same left-side network and used the same gateway.
 
### HostD
![HostD](hostD.png)
 
HostD was also configured in the 10.10.10.0/24 subnet.
 
---
 
## Right LAN Host Configurations
 
### Host1
![Host1](host1.png)
 
Host1 was configured in the 10.10.20.0/24 network.
 
### Host2
![Host2](host2.png)
 
Host2 was configured with a static IP in the same subnet as Host1.
 
### Host3
![Host3](host3.png)
 
Host3 was configured in the right-side LAN and used Router2 as the default gateway.
 
### Host4
![Host4](host4.png)
 
Host4 was also configured in the same subnet and checked using interface commands.
 
---
 
## Router Configuration
 
### Router1
![Router1 Config](router1.png)
 
Router1 connects the left LAN to the inter-router network. IP forwarding was enabled so packets could move between networks.
 
![Router1 Check](router1.1.png)
 
This screenshot shows interface checking after configuration.
 
### Router2
![Router2 Config](router2.png)
 
Router2 connects the inter-router network to the right LAN. IP forwarding was also enabled here.
 
![Router2 Check](router2.2.png)
 
This screenshot shows the active interface details after setup.
 
---
 
## Testing and Verification
 
The screenshots show interface checks using `ifconfig`, connectivity checks using `ping`, and ARP checking using `arp -a` or related commands. This matches the main ideas from the Week 6 lecture, where ARP is used to map IP addresses to MAC addresses inside a local network before frames can be delivered. :contentReference[oaicite:1]{index=1}
 
From the lecture, ARP is used when a device knows the destination IP address but still needs the matching MAC address on the LAN. The ARP request is broadcast and the ARP reply is sent back as unicast. :contentReference[oaicite:2]{index=2}
 
---
 
## Result
The network devices were configured with static IP addresses, routers were set to forward packets, and connectivity tests were used to verify communication. ARP-related checks helped confirm how devices resolved addresses on the local network.
