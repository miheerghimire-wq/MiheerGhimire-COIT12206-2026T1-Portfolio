# TCP/IP Configuration - Week 2

## Student Details
- Name: Miheer Ghimire
- Student ID: 12304055
- Course: COIT12206
- Term: 2026 T1

---

## Project Overview
This project demonstrates a TCP/IP network setup using GNS3 with multiple hosts connected through a switch. Each host is configured with a static IP address and tested using ping commands.

---

## Network Topology
- 4 Hosts (Host1, Host2, Host3, Host4)
- 1 Switch
- All devices connected in star topology

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

## Testing

- Verified IP using `ip address show`
- Used `ping` to test connectivity between hosts
- Successful communication between hosts confirms correct configuration

---

## Screenshots

### Topology
![Topology](topology.png)

### Configuration
![Config](config.png)

### Console Output
![Console](console.png)
