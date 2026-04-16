# VLAN Configuration and Inter-VLAN Routing using GNS3

##  Course

COIT12206 – TCP/IP Principles and Protocols


---

#  Project Overview

This project demonstrates VLAN configuration and inter-VLAN routing using Open vSwitch and a Linux Router in GNS3.

Two tasks were performed:

* Task 1: VLAN configuration and network isolation
* Task 2: Inter-VLAN communication using a router

---

#  Task 1: VLAN Configuration on Switch
![Task1 Network](projectcreate.png)
##  Network Topology

![Task1 Network](topology.png)

📌 The topology shows 4 hosts connected to a switch without a router.

---

## ⚙️ Configuration

* Host1 → 10.10.1.101
* Host2 → 10.10.1.102
* Host3 → 10.10.1.103
* Host4 → 10.10.1.104

![Configuration](h1.png)
![Configuration](h2.png)
![Configuration](h3.png)
![Configuration](h4.png)

### VLAN Setup
![VLAN Setup](Setport.png)
```
ovs-vsctl set port eth1 tag=10
ovs-vsctl set port eth2 tag=10
ovs-vsctl set port eth3 tag=20
ovs-vsctl set port eth4 tag=20
```

📌 VLAN 10 → Host1, Host2
📌 VLAN 20 → Host3, Host4

---

## 📸 Switch Configuration

![Task1 Ports](tag.png)

![Task1 Ports](tag2nd.png)

📌 Shows VLAN tagging on switch ports using Open vSwitch.

---

## 📊 Connectivity Testing

![Task1 Ping](h1pingtoall.png)

![Task1 ping](h4.png)

1. Same VLAN → ping works
2. Different VLAN → ping fails (Isolation working)

---

##  ARP Observation
![Task1 Ports](h1pingtoall.png)
![Task1 Ports](h4.png)
* Same VLAN → MAC resolved

* Different VLAN → incomplete
![Task1 Ports](DifferentVLAN.png)

*Result of ARP using arp -n 
![Task1 Ports](arp-a.png)

---

## Conclusion (Task 1)

VLAN successfully isolates traffic between different groups.

---

#  Task 2: Inter-VLAN Routing

##  Network Topology

![Task2 Network](topologyweek5.png)

📌 Router connected to switch via trunk link.

---

##  Configuration

### VLAN Setup

```
ovs-vsctl set port eth1 tag=10
ovs-vsctl set port eth2 tag=10
ovs-vsctl set port eth3 tag=20
ovs-vsctl set port eth4 tag=20
```

---

![Task VLAN Setup](Tagsetandlist.png)

### Trunk Port

```
ovs-vsctl set port eth0 trunks=[]
```

📌 Allows all VLAN traffic to router.

---

### Router Configuration

```
ip link add link eth0 name eth0.10 type vlan id 10
ip link add link eth0 name eth0.20 type vlan id 20

ip addr add 10.10.1.1/24 dev eth0.10
ip addr add 10.10.2.1/24 dev eth0.20

ip link set eth0 up
ip link set eth0.10 up
ip link set eth0.20 up

echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

##  IP Addressing

| Host  | IP Address  | VLAN |
| ----- | ----------- | ---- |
| Host1 | 10.10.1.101 | 10   |
| Host2 | 10.10.1.102 | 10   |
| Host3 | 10.10.2.103 | 20   |
| Host4 | 10.10.2.104 | 20   |

---

##  Router Configuration

![Router Config](routeripaddress1.png)

📌 Shows VLAN interfaces and gateway setup.

---

##  Connectivity Testing

![Task2 Ping](gatewaysamepingsuccessful.png)
![Task2 Ping](h3-ping.png)
![Task2 Ping](h4-ping.png)
![Task2 Ping](pingfailedh1with2.104.png)

📌 Inter-VLAN communication successful.

---

##  Conclusion (Task 2)

Router enables communication between VLANs successfully.

---

#  Tools Used

* GNS3
* Open vSwitch
* Linux Router

---

#  Final Summary

* VLAN isolates traffic 
* Trunk carries VLANs 
* Router connects VLANs 
* Network fully working 
