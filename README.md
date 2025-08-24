# Cyber Shield: Network Security Project

## Project Overview
This project is a practical network security simulation that demonstrates VLAN segmentation, inter-VLAN routing, HSRP, EtherChannel, DHCP, OSPF, ACLs, NAT, Port Security, Syslog, and NTP synchronization. The project is designed for Packet Tracer simulation and serves as a comprehensive final project.

## Configuration Summary

### VLANs & IPs
| VLAN | IP Address     | HSRP Virtual IP | HSRP Priority | Status       |
|------|---------------|----------------|---------------|--------------|
| 10   | 192.168.50.1  | 192.168.50.10  | 150 (MLS0)    | Active       |
| 20   | 192.168.60.1  | 192.168.60.10  | 100 (MLS0)    | Active       |
| 30   | 192.168.70.1  | 192.168.70.10  | 110 (MLS0)    | Active       |
| 40   | 192.168.80.1  | 192.168.80.10  | 150 (MLS2)    | Active/Standby |
| 50   | 192.168.90.1  | 192.168.90.10  | 80  (MLS2)    | Active/Standby |
| 60   | 192.168.99.1  | 192.168.99.10  | 110 (MLS2)    | Active/Standby |

### EtherChannel Summary
| Port-Channel | Protocol | Members       | Mode  |
|--------------|----------|---------------|-------|
| Po1          | LACP     | Fa0/3, Fa0/4  | Trunk |
| Po3          | LACP     | Fa0/5, Fa0/6  | Trunk |
| Po5          | LACP     | Fa0/7, Fa0/8  | Trunk |
| Po2          | LACP     | Fa0/7, Fa0/8  | Trunk |
| Po4          | LACP     | Fa0/5, Fa0/6  | Trunk |
| Po6          | LACP     | Fa0/3, Fa0/4  | Trunk |

### HSRP Configuration
- VLAN10: MLS0 Priority 150, MLS1 Priority 90  
- VLAN20: MLS0 Priority 100, MLS1 Priority 80  
- VLAN30: MLS0 Priority 110, MLS1 Priority 70  
- VLAN40: MLS2 Priority 150, MLS3 Priority 90  
- VLAN50: MLS2 Priority 80, MLS3 Priority 80  
- VLAN60: MLS2 Priority 110, MLS3 Priority 70  

### DHCP Pools
| VLAN | Pool Name | Network        | Default Gateway  | DNS       |
|------|-----------|----------------|-----------------|-----------|
| 10   | VLAN10    | 192.168.50.0/24| 192.168.50.10   | 8.8.8.8  |
| 20   | VLAN20    | 192.168.60.0/24| 192.168.60.10   | 8.8.8.8  |
| 30   | VLAN30    | 192.168.70.0/24| 192.168.70.10   | 8.8.8.8  |
| 40   | VLAN40    | 192.168.80.0/24| 192.168.80.10   | 8.8.8.8  |
| 50   | VLAN50    | 192.168.90.0/24| 192.168.90.10   | 8.8.8.8  |
| 60   | VLAN60    | 192.168.99.0/24| 192.168.99.10   | 8.8.8.8  |

### ACLs
**vlan10_filter**
```
permit ip 192.168.50.0 0.0.0.255 192.168.80.0 0.0.0.255
permit ip 192.168.50.0 0.0.0.255 192.168.90.0 0.0.0.255
deny ip 192.168.50.0 0.0.0.255 192.168.99.0 0.0.0.255
permit ip any any
```

### OSPF
- Process ID: 10  
- Router IDs: MLS0: 3.3.3.3, MLS1: 4.4.4.4, MLS2: 5.5.5.5, MLS3: 6.6.6.6  
- Networks Advertised:  
  - 192.168.10.0/24, 192.168.20.0/24, 192.168.30.0/24, 192.168.40.0/24  
  - 192.168.50.0/24 → 192.168.70.0/24, 192.168.80.0 → 192.168.99.0/24

### Port Security
- Most access ports (Fa0/2, Fa0/3) configured to **Shutdown** on violation.

### Syslog
- Logging Server: 192.168.10.100

### NTP
- Time synchronization configured for all MLS switches.

### NAT
- NAT configured on MLS0 for internal to external traffic.

## Summary
This project demonstrates a fully configured network with VLANs, Inter-VLAN Routing, HSRP, EtherChannel, DHCP, OSPF, ACLs, NAT, Port Security, Syslog, and NTP. Ready for Packet Tracer simulation with failover and network verification testing.

## Topology Diagram
*(Add network topology image here)*

## Verification Commands
- `show vlan brief`
- `show ip dhcp binding`
- `show standby brief`
- `show etherchannel summary`
- `show ip route ospf`
- `show access-lists`
- `show port-security`
- `ping` & `traceroute` tests for connectivity

---

*Prepared by Manar Hossam*

