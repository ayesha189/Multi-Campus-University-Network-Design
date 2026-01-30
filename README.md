# Multi-Campus University Network Design
## 🌐 Project Overview
A comprehensive enterprise-level network infrastructure design for a multi-campus university environment, featuring six interconnected campuses with centralized management, high availability, and robust security. This project implements a complete network design consisting of six campuses interconnected through a central core network, providing secure, scalable, and high-performance connectivity supporting thousands of students, staff, servers, and wireless users.


### Key Features

- **Scalable Architecture**: Built on 10.0.0.0/8 private IP block with /16 allocation per campus
- **Dual Routing Protocols**: OSPF Multi-Area for intra-campus and EIGRP for inter-campus routing
- **Centralized Wireless Management**: Wireless LAN Controller (WLC) with Lightweight Access Points
- **VLAN Segmentation**: Secure departmental isolation across all campuses
- **High Availability**: Redundant links, dual routers, and loop-free Layer-2 design
- **Enterprise Security**: ACLs, WPA2 Enterprise, routing protocol authentication, and VLAN segmentation

## 🏗️ Network Architecture

### Campus Infrastructure

The network consists of six campuses (A through F) with Campus A serving as the central hub:

- **Campus A**: Core Router + Centralized Services (DHCP, WLC)
- **Campuses B-F**: Branch campuses connected to Campus A via dedicated WAN links

### Routing Design

#### Interior Routing (OSPF Multi-Area)
- Each campus runs OSPF internally
- Area 0 operates on the Core Router at Campus A
- Campus routers connect to Area 0 using point-to-point WAN links
- Ensures fast convergence and efficient routing within campuses

#### Exterior Routing (EIGRP)
- Autonomous System Number: AS 100
- Handles route exchange between campuses
- Load balancing across inter-campus links
- Redistribution between OSPF and EIGRP at Campus A Core Router

### WAN Design

Point-to-point connections using /30 subnets from 10.255.x.x/30:

```
Campus A ↔ Campus B: 10.255.1.0/30
Campus A ↔ Campus C: 10.255.2.0/30
Campus A ↔ Campus D: 10.255.3.0/30
Campus A ↔ Campus E: 10.255.4.0/30
Campus A ↔ Campus F: 10.255.5.0/30
```

## 📊 VLAN Structure

Common VLANs deployed across all campuses:

| VLAN ID | Department | Purpose |
|---------|-----------|---------|
| VLAN 10 | Admin | Administrative staff |
| VLAN 20 | Student | Student network |
| VLAN 30 | Faculty | Faculty members |
| VLAN 40 | Servers | Campus servers |
| VLAN 50 | Wireless | Wireless users |
| VLAN 60 | Guest WiFi | Guest network access |

## 📡 Wireless Network Design

### WLC Deployment
- **Location**: Campus A VLAN 50
- **Management**: Centralized control of all APs across six campuses
- **AP Mode**: Lightweight (CAPWAP protocol)

### SSID Configuration
- Staff/Student SSID with WPA2 Enterprise authentication
- Guest SSID with limited access and bandwidth controls

## 🔒 Security Measures

- **Access Control Lists (ACLs)**: Traffic filtering and policy enforcement
- **WPA2 Enterprise**: Secure wireless authentication
- **Routing Protocol Authentication**: OSPF and EIGRP MD5 authentication
- **VLAN Segmentation**: Network isolation by department
- **Port Security**: MAC address binding on access switches

## 🖥️ DHCP Design

Centralized DHCP servers located in Campus A provide IP addresses for:
- Admin department
- Student network
- Faculty network
- Server infrastructure
- Wireless clients
- Guest WiFi users

Router-on-a-Stick configuration with `ip helper-address` forwards DHCP requests from remote campuses.

## 📋 IP Addressing Plan

### Primary IP Block
**10.0.0.0/8**

### Per-Campus Allocation
Each campus receives a /16 subnet, supporting up to 65,536 IP addresses:

- Campus A: 10.1.0.0/16
- Campus B: 10.2.0.0/16
- Campus C: 10.3.0.0/16
- Campus D: 10.4.0.0/16
- Campus E: 10.5.0.0/16
- Campus F: 10.6.0.0/16

## 🎯 Design Benefits

✅ **Scalable**: 10.0.0.0/8 with /16 per campus supports significant population growth

✅ **Fast Convergence**: OSPF Multi-Area ensures efficient routing within campuses

✅ **Robust Connectivity**: EIGRP provides high performance and load balancing between campuses

✅ **Centralized Management**: WLC in Campus A reduces operational overhead

✅ **High Security**: Multi-layered security approach with ACLs, encryption, and segmentation

✅ **Easy Administration**: Campus A hosts all critical services for simplified management

## 🛠️ Technologies Used

- **Routing Protocols**: OSPF (Multi-Area), EIGRP
- **Layer-2 Protocols**: VLANs, STP, VLAN Trunking
- **Wireless**: Centralized WLC with CAPWAP
- **Services**: DHCP, DNS
- **Security**: ACLs, WPA2 Enterprise, MD5 Authentication

## 📁 Repository Structure

```
├── CN_Course_Project.docx    # Complete project documentation
├── CN_Course_Project.pkt     # Cisco Packet Tracer simulation file
├── README.md                  # This file

```

## 📖 Documentation

The complete network design documentation including:
- Detailed topology diagrams
- CLI configurations for all devices
- Security policies
- VLAN configurations
- Routing protocol setup
- Wireless controller configuration

See full documentation.

## 💻 Packet Tracer Simulation

This repository includes a fully functional Cisco Packet Tracer simulation file: **CN_Course_Project.pkt**

### Opening the Simulation
1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) (version 8.0 or higher recommended)
2. Download the `CN_Course_Project.pkt` file from this repository
3. Open the file in Cisco Packet Tracer
4. Explore the network topology and device configurations

### What's Included in the Simulation
- All six campus networks (A through F)
- Configured routers with OSPF and EIGRP
- Layer-2 switches with VLAN configurations
- Wireless LAN Controller (WLC) and Access Points
- DHCP servers
- End devices (PCs, laptops, servers)
- WAN interconnections between campuses

### Testing the Network
You can test various scenarios in the simulation:
- **Connectivity Testing**: Use ping and traceroute between different campuses and VLANs
- **DHCP Testing**: Check if devices receive IP addresses automatically
- **Routing Protocol Verification**: View OSPF and EIGRP routing tables
- **Wireless Connectivity**: Test wireless client connections
- **Failover Testing**: Disable links to test redundancy and convergence

## 🚀 Getting Started

### Prerequisites
- **Cisco Packet Tracer** (version 8.0 or higher) - [Download here](https://www.netacad.com/courses/packet-tracer)
- Basic understanding of networking concepts (TCP/IP, routing, switching)
- Familiarity with Cisco IOS commands
- Knowledge of VLAN, OSPF, and EIGRP concepts

### Quick Start
1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/multi-campus-network-design.git
   cd multi-campus-network-design
   ```

2. **Open the simulation**
   - Launch Cisco Packet Tracer
   - Open `CN_Course_Project.pkt`
   - The complete network topology will load with all configurations

3. **Explore the network**
   - Click on devices to view configurations
   - Use simulation mode to visualize packet flow
   - Test connectivity between different campuses and VLANs

### Building From Scratch (Optional)
If you want to recreate the network from scratch for learning purposes:

1. Set up the physical or virtual network topology
2. Configure IP addressing according to the addressing plan
3. Implement VLAN structure on all switches
4. Configure OSPF within each campus
5. Set up EIGRP between campus routers
6. Deploy and configure WLC for wireless management
7. Configure DHCP services
8. Implement security policies (ACLs, authentication)
9. Test connectivity and failover scenarios

**Tip**: Reference the provided `.pkt` file for complete device configurations!


## 📄 License

-This project is created for educational purposes as part of a university course assignment.

## 👤 Author

**Team Members:**
- **23f-0807** - [https://github.com/ayesha189]
-  **23f-0734** - [https://github.com/NIMRAH-S]

## 🙏 Acknowledgments

- Computer Networks Course Project
- Cisco Networking Academy
- University Faculty and Peers

## 📝 Academic Details

**Course**: Computer Networks
**Project Type**: Final Project  


---

⭐ If you found this project helpful, please consider giving it a star!
