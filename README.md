# Cisco ASA Cluster – Spanned Mode (AS2)

#Project Overview
This project demonstrates the configuration and working of a **Cisco ASA Cluster (AS2)** in **spanned mode**.  
The design follows Cisco best practices where ASA data interfaces operate at **Layer 2**, while routing and gateway functionality is handled by external routers.

---

#Topology Summary

# Devices Used
- 2 × Cisco ASA (ASA1, ASA2) – Clustered
- 2 × Routers (R1 – Inside, R2 – Outside)
- 3 × Layer-2 Switches
- End hosts (for testing)

# Network Segments
| Segment | Subnet | Notes |
| Inside | 10.11.11.0/24 | Gateway on R1 |
| Outside | 192.1.20.0/24 | Gateway on R2 |
| CCL (Control Link) | 150.1.7.0/24 | Used for ASA cluster control |

---

# Key Design Concepts

- ASA cluster operates in **spanned mode**
- **No IP address on ASA data interfaces (inside / outside)**
- ASA behaves as a **Layer-2 firewall**
- Default gateways are configured on routers, not on ASA
- Control Link (CCL) is the only interface with an IP on ASA
- Identical configuration across all cluster members

---

# Configuration Highlights

# ASA Cluster
- Cluster type: AS2
- Interface mode: Spanned
- Control interface: `eth2`
- Data interfaces: `eth0 (inside)`, `eth1 (outside)`
- No failover, VPN, or DHCP (unsupported in clustering)

# Routers
- **R1 (Inside Gateway):** `10.11.11.1`
- **R2 (Outside Gateway):** `192.1.20.2`
- Routing handled entirely by routers

# Verification Commands

On ASA:
show cluster info
show cluster state
show conn

**Tools & Environment**
EVE-NG / GNS3
Cisco ASA Image
Cisco IOS Routers
Git & GitHub



