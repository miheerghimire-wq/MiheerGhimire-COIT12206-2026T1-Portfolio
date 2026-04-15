
## Project Overview- Week 2
This project demonstrates a TCP/IP network setup using GNS3 with multiple hosts connected through a switch. Each host is configured with a static IP address and tested using ping commands.

---

## Network Topology
- 4 Hosts (Host1, Host2, Host3, Host4)
- 1 Switch
- Star topology connection

---

## IP Configuration

| Host  | IP Address |
|------|-----------|
| Host1 | 10.10.2.1 |
| Host2 | 10.10.2.2 |
| Host3 | 10.10.2.3 |
| Host4 | 10.10.2.4 |

Subnet Mask: 255.255.255.0

---

## Configuration Code

```bash
auto eth0
iface eth0 inet static
    address 10.10.2.X
    netmask 255.255.255.0
    up echo nameserver 192.168.0.1 > /etc/resolv.conf
```

---

## Screenshots

### Topology
![Topology](topology1.png)

### Host 1 Configuration
![Host1](Config-host 1.png)

### Host 2 Configuration
![Host2](Config-host 2.png)

### IP Address Host1
![IP1](ip-host1.png)

### IP Address Host2
![IP2](ip-host2.png)

### IP Address Host3
![IP3](ip-host3.png)

### IP Address Host4
![IP4](ip-host4.png)

### Console Host3
![Console3](console-host 3.png)

### Console Host4
![Console4](console-host 4.png)

### Ping Test (Success Host1 to Host2)
![Ping1](Ping-success-1to2.png)

### Ping Test (Success Host4 to Host2)
![Ping2](ping-sucess-4to2.png)

### Ping Test (Failure)
![Failure](ping-failure.png)
