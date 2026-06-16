# Enterprise Campus Network with Layer 3 Switching

## Network Topology
![Topology](screenshots/01-topology.png)

## Project Overview
Designed and implemented a multi-floor enterprise campus network using Cisco Catalyst switches. The solution provides VLAN segmentation, centralized inter-VLAN routing, DHCP automation, EtherChannel redundancy, and Spanning Tree loop prevention.

## Business Scenario
A medium-sized enterprise occupies multiple office floors and requires secure departmental segmentation for HR, IT, Finance, and Sales while maintaining centralized management and high availability.

## Technologies
- VLANs
- 802.1Q Trunking
- Layer 3 Switching
- DHCP
- EtherChannel (LACP)
- Spanning Tree Protocol (STP)

## VLAN Design

| VLAN | Department | Gateway |
|------|------------|----------|
| 10 | HR | 192.168.10.1 |
| 20 | IT | 192.168.20.1 |
| 30 | Finance | 192.168.30.1 |
| 40 | Sales | 192.168.40.1 |

## Verification Screenshots

### VLAN Verification
![VLAN](screenshots/02-vlan-verification.png)

### Trunk Verification
![Trunk](screenshots/03-trunk-verification.png)

### DHCP Services
![DHCP](screenshots/04-dhcp-bindings.png)

### EtherChannel Verification
![Core](screenshots/05-etherchannel-core.png)
![Floor1](screenshots/06-etherchannel-floor1.png)
![Floor2](screenshots/07-etherchannel-floor2.png)

### STP Verification
![Root](screenshots/09-stp-root-bridge.png)

### Layer 3 Routing
![Routing](screenshots/10-routing-table.png)

### SVI Interfaces
![SVI](screenshots/11-svi-verification.png)

### End-to-End Connectivity
![Ping](screenshots/12-intervlan-connectivity.png)

## Key Achievements
- Built a segmented enterprise campus network.
- Implemented centralized Layer 3 inter-VLAN routing.
- Configured DHCP for automatic host provisioning.
- Deployed LACP EtherChannel for redundancy and bandwidth aggregation.
- Implemented STP to eliminate switching loops.
- Validated end-to-end inter-VLAN communication.

## Lessons Learned
- EtherChannel consistency is critical across all member interfaces.
- STP root bridge placement affects forwarding paths.
- DHCP failures are often caused by VLAN or trunk propagation issues.
- Layer 3 switching simplifies campus routing design.

## Author
Yashjeet Barak
