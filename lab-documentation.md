# Lab: Configure a NIC to Use DHCP in Windows
## Network Automation & Security Implications

### Executive Summary

This project demonstrates the configuration of Dynamic Host Configuration Protocol (DHCP) on a network interface card (NIC) in a Windows environment using Cisco Packet Tracer. The lab simulates a small business network where two client workstations automatically obtain IP addresses from a centralized router acting as a DHCP server.

**Key Outcomes:**
- Successfully configured DHCP server on Cisco 2621XM router with two separate IP pools
- Achieved automatic IP assignment to both client machines
- Validated network connectivity via ICMP ping tests (0% packet loss)

### Network Topology
Host A (192.168.1.2) <---> Router (2621XM) <---> Host B (192.168.2.2)
|
DHCP Server Enabled
Pool A: 192.168.1.0/24
Pool B: 192.168.2.0/24

text

### Lab Results

| Device | IP Address | Subnet Mask | Gateway |
|--------|------------|-------------|---------|
| Router Fa0/0 | 192.168.1.1 | 255.255.255.0 | - |
| Router Fa0/1 | 192.168.2.1 | 255.255.255.0 | - |
| Host A | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| Host B | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |

### Ping Test Results
C:>ping 192.168.2.2

Pinging 192.168.2.2 with 32 bytes of data:
Reply from 192.168.2.2: bytes=32 time<1ms TTL=127
Reply from 192.168.2.2: bytes=32 time<1ms TTL=127
Reply from 192.168.2.2: bytes=32 time<1ms TTL=127
Reply from 192.168.2.2: bytes=32 time<1ms TTL=127

Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)

text

### Cybersecurity Implications

| Risk | Mitigation |
|------|------------|
| Rogue DHCP Server | Enable DHCP snooping on switches |
| DHCP Starvation | Implement port security and rate limiting |
| DNS Spoofing | Use DHCP authentication |

### Business Value

| Metric | Without DHCP | With DHCP |
|--------|--------------|-----------|
| Time to onboard new device | 5-10 minutes | 30 seconds |
| IT support tickets for IP issues | High | Minimal |
| Human error rate | Significant | Eliminated |

### Author
Milton Silas

### License
MIT License - Educational Purpose Only