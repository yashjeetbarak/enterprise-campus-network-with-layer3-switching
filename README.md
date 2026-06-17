# Enterprise Campus Network with Layer 3 Switching

![Banner](/screenshots/Banner.jpeg)

## Project Overview
Designed and implemented a multi-floor enterprise campus network using Cisco Catalyst switches. The solution provides VLAN segmentation, centralized inter-VLAN routing, DHCP automation, EtherChannel redundancy, and Spanning Tree loop prevention.

## Business Scenario
A medium-sized enterprise occupies multiple office floors and requires secure departmental segmentation for HR, IT, Finance, and Sales while maintaining centralized management and high availability.

## Network Architecture

```text
                Core Layer
          +------------------+
          | Cisco 3560 MLS   |
          +------------------+
             ||        ||
        Po1==||        ||==Po2
             ||        ||

      Distribution Layer
   +------------+   +------------+
   | Floor-1 SW |   | Floor-2 SW |
   +------------+   +------------+

     /      \          /      \
   HR      IT      Finance   Sales
 VLAN10 VLAN20    VLAN30   VLAN40
```

The network follows a three-tier campus architecture consisting of Core, Distribution, and Access layers.

### Core Layer
- Cisco Catalyst 3560 Multilayer Switch
- Centralized Layer 3 routing between VLANs
- DHCP services for all departments
- STP Root Bridge for VLANs 10, 20, 30, and 40
- Aggregated uplinks using LACP EtherChannel

### Distribution Layer
- First Floor Distribution Switch
- Second Floor Distribution Switch
- Redundant uplinks to the Core Layer
- VLAN propagation through 802.1Q trunks
- Traffic aggregation from access switches

### Access Layer
- HR Department Access Switch (VLAN 10)
- IT Department Access Switch (VLAN 20)
- Finance Department Access Switch (VLAN 30)
- Sales Department Access Switch (VLAN 40)
- End-user connectivity and VLAN membership enforcement

## VLAN Design

| VLAN | Department | Gateway |
|------|------------|----------|
| 10 | HR | 192.168.10.1 |
| 20 | IT | 192.168.20.1 |
| 30 | Finance | 192.168.30.1 |
| 40 | Sales | 192.168.40.1 |

## Technologies
- VLANs
- 802.1Q Trunking
- Layer 3 Switching
- DHCP
- EtherChannel (LACP)
- Spanning Tree Protocol (STP)

## Verification Screenshots

### VLAN Verification
![VLAN](screenshots/02-vlan-verification.png)

The campus network was segmented into four logical broadcast domains using VLANs. Departments were isolated to improve security, reduce broadcast traffic, and simplify network management.

### Trunk Verification
![Trunk](screenshots/03-trunk-verification.png)

802.1Q trunk links were configured between the multilayer switch and distribution switches to allow VLAN traffic to traverse the campus network while maintaining VLAN separation.

### DHCP Services
![DHCP](screenshots/04-dhcp-bindings.png)

Centralized DHCP services were configured on the multilayer switch to automatically assign IP addresses, subnet masks, and default gateways to hosts across all VLANs.

### EtherChannel Verification

![EtherChannel](screenshots/06-etherchannel-floor1)

The core multilayer switch uses two LACP EtherChannels (Po1 and Po2) to provide redundant high-bandwidth uplinks to the distribution layer.

### STP Verification
![Root](screenshots/09-stp-root-bridge.png)

Spanning Tree Protocol (STP) was configured to prevent switching loops and ensure a stable Layer 2 topology.

The verification output confirms successful root bridge election and proper forwarding behavior.

### Layer 3 Routing
![Routing](screenshots/10-routing-table.png)

The Cisco Catalyst 3560 Multilayer Switch performs inter-VLAN routing through Switch Virtual Interfaces (SVIs).

The routing table confirms that all departmental networks are reachable and directly connected.

### SVI Interfaces
![SVI](screenshots/11-svi-verification.png)

SVIs were configured for each VLAN and serve as the default gateways for end devices.

The interface status confirms that all VLAN interfaces are operational and available for routing.

### End-to-End Connectivity
![Ping](screenshots/12-intervlan-connectivity.png)

End-to-end connectivity was successfully validated between devices located in different VLANs.

Successful ICMP replies confirm proper VLAN propagation, Layer 3 routing, DHCP operation, and overall network functionality.

## Folder Structure

```text
enterprise-campus-network-with-layer3-switching/
│
├── packet-tracer-file/
│   └── Enterprise-Campus-Network.pkt
│
├── screenshots/
│   ├── topology.png
│   ├── vlan-verification.png
│   ├── trunk-verification.png
│   ├── dhcp-bindings.png
│   ├── etherchannel-core.png
│   ├── etherchannel-floor1.png
│   ├── etherchannel-floor2.png
│   ├── stp-verification.png
│   ├── routing-table.png
│   ├── svi-verification.png
│   └── connectivity-test.png
│
└── README.md
```

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
