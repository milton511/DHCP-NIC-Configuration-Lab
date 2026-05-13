# Cybersecurity Implications of DHCP Deployment

## Attack Vectors & Mitigations

### 1. Rogue DHCP Server Attack

**Description**: Attacker deploys unauthorized DHCP server to assign malicious network configurations.

**Mitigation Commands**:
```bash
# Enable DHCP snooping
ip dhcp snooping
ip dhcp snooping vlan 1-100

# Configure trusted port
interface FastEthernet0/24
 ip dhcp snooping trust

# Set rate limits
interface FastEthernet0/1
 ip dhcp snooping limit rate 10
2. DHCP Starvation Attack
Description: Attacker floods DHCP server with requests to exhaust IP address pool.

Mitigation:

bash
# Port security to limit MAC addresses
interface FastEthernet0/1
 switchport port-security
 switchport port-security maximum 2
NIST Compliance Mapping
NIST Control	Implementation	Evidence
CM-8 (Asset Inventory)	DHCP lease logs	show ip dhcp binding
SC-7 (Boundary Protection)	VLAN segmentation	Separate subnets
AU-2 (Audit Events)	DHCP logging	logging dhcp
IA-3 (Device ID)	MAC address tracking	Lease database
Incident Response
Detecting Rogue DHCP Server
Indicators:

Multiple DHCP offers from unknown servers

IP address conflicts

Unexpected gateway changes

Recovery Procedure
bash
# Clear DHCP bindings
clear ip dhcp binding *

# Reset DHCP server
no ip dhcp pool PoolA
ip dhcp pool PoolA
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1