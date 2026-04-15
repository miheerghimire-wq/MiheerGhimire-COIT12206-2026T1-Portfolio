# VLAN Configuration and Inter-VLAN Routing using GNS3


#  Project Overview

This project demonstrates the implementation of VLANs and inter-VLAN routing using Open vSwitch and a Linux Router in GNS3. 

The project is divided into two main tasks:
- Task 1: VLAN configuration and isolation
- Task 2: Inter-VLAN communication using a router

---

#  Task 1: VLAN Configuration on Switch

##  Network Topology

![Task1 Network](Task1/network.png)

📌 **Description:**
The topology consists of four Linux hosts connected to an Open vSwitch. Each host is connected to different switch ports (eth1–eth4). No router is used in this task.

---

##  Configuration

All hosts were assigned IP addresses in the same subnet:

- Host1 → 10.10.1.101  
- Host2 → 10.10.1.102  
- Host3 → 10.10.1.103  
- Host4 → 10.10.1.104  

### VLAN Setup on Switch

```bash
ovs-vsctl set port eth1 tag=10
ovs-vsctl set port eth2 tag=10
ovs-vsctl set port eth3 tag=20
ovs-vsctl set port eth4 tag=20
