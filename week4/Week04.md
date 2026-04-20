# WEEK 4 -Portfolio

## Course
**COIT12206 – TCP/IP Principles and Protocols**

## Student Details
- **Name:** Miheer Ghimire 
- **Student ID:** 12304055 
- **Term:** 2026 Term 1


---
- **Task-1** – View Routing Tables and
- **Task-2** Dynamic Routing with OSPF

## Tools Used
- GNS3
- Linux networking commands
- FRRouting (FRR)
- GitHub

---

# Task-1 – View Routing Tables:

## Objective of this project:

This task 1 illustrates how to set up a small routed network with Linux hosts and a Linux router, to enable forwarding on the router, to look at routing tables and verify connectivity between two subnets.

---

## Network Topology
The network contains:
- Host 1  and Host 2 on subnet `10.10.1.XY/24`
- Host 3 on subnet `10.10.2.XY/24`
- Router connecting between two subnets.
- A single switch connecting Host1, Host2, and the router interface in subnet A.

![Project Create](name.png)
![Task 1 Topology](outface.png)

---

## IP Addressing Used in this project :

| Device | Interface | IP Address | Netmask | Gateway |
|---|---|---:|---:|---:|
| Host1 | eth0 | 10.10.1.11 | 255.255.255.0 | 10.10.1.1 |
| Host2 | eth0 | 10.10.1.12 | 255.255.255.0 | 10.10.1.1 |
| Host3 | eth0 | 10.10.2.11 | 255.255.255.0 | 10.10.2.1 |
| Router | eth0 | 10.10.1.1 | 255.255.255.0 | – |
| Router | eth1 | 10.10.2.1 | 255.255.255.0 | – |

---

## Evidence of Configuration

### Router Configuration Setting Screenshot:

![Task 1 Router Configuration](router.png)
![ Router Configuration](week6router.png)


---

### Configuration of Host 1:
![Task 1 Host1 Configuration](ping.png)

### Configuration of Host 2:
![Task 1 Host2 Configuration](host2.png)

### Configuration of Host 3:
![Task 1 Host3 Configuration](hhost3.png)

## Forwarding
- Forwarding was disabled on hosts.
- Router was turned on forwarding to allow the router to forward packets between the two subnets.

---

## Routing Table Evidence

### Router Routing Table Screenshots:
![Task 1 Router ip route show](pingh1-router.png)

## Ping Test Connectivity:
A successful ping from Host1 to hosts and router addresses shows that routing worked correctly across subnets.

---

### Results of Host 1 in Console:
![Task 1 Host1 Ping](pingh1-router.png)

## Summary
Task 1 was completed by:
1. Building a two ubnet topology
2. Static IP addresses
3. Forwarding on the router enabled.
4. Viewing routing tables
5. Ping subnet confirmation Checking the subnet to subnet communication.


---

# Task-2 – Dynamic Routing with OSPF

## Objective
This task-2 exercise shows the dynamism of OSPF in sharing routes between FRR routers and the dynamic nature of the path which changes automatically in case of a link failure.

---

## OSPF Topology
The topology contains:
- Host 1 on network `10.10.1.0/24`
- Host 2 on network `10.10.6.0/24`
- FRR1, FRR2, FRR3, and FRR4
- There are two possible paths between the hosts
- NETem nodes used to simulate path failure in the task 2.

![Create project](2.png)

![Task 2 Topology](TopologyOSPF.png)

---

## OSPF Verification:

### OSPF Neighbor Output Screenshot:
This confirms that FRR1 formed OSPF adjacencies with neighboring routers.

![Task 2 OSPF Neighbor](frr1showipospf.png)

### IP Route Table Output:
This shows the routes installed in the router forwarding table.

![Task 2 IP Route](ipospfroute.png)

---


## Traceroute Before Link Failure Output:
Before disconnecting the path, traceroute from Host1 to Host2 followed the current preferred route.
![Task 2 Traceroute Before](Neterm2stop.png)
![Task 2 Traceroute Before](h1-traceroute-before.png)

## Traceroute After Link Failure Output:
After stopping the relevant NETem node, the route changed and traffic used the alternate path.

![Task 2 Traceroute After](after-result-stopping.png)

---

## Routing Summary Table

| Router | Destination Network | Next Node / Interface |
|---|---|---|
| FRR1 | 10.10.1.0/24 | directly connected (eth0) |
| FRR1 | 10.10.2.0/24 | directly connected (eth1) |
| FRR1 | 10.10.3.0/24 | directly connected (eth2) |
| FRR1 | 10.10.4.0/24 | via 10.10.2.2 |
| FRR1 | 10.10.5.0/24 | via 10.10.3.3 |
| FRR1 | 10.10.6.0/24 | via 10.10.2.2 or 10.10.3.3 depending on topology state |


---

## Key Observation of Week 4:

OSPF automatically updated the path in case of a link failure. which demonstrates the utility of dynamic routing in larger networks: it reduce manual reconfigurability, and adapts to changes in topology.

## Conclusion
In Week 4 successfully demonstrated:
- Concepts of static routing and viewing routing table in Task 1.
- Task 2: OSPF neighboring processes and dynamic learning of routes.
- Automatic change of path in case of unavailable link.
