# International Examination Center

An enterprise network design and documentation project for an **International Examination Center** consisting of two interconnected sites:

- **Main Building (HQ)**
- **Branch 2 (Secondary Branch)**

The project focuses on designing a secure, scalable, redundant, and well-structured enterprise network infrastructure using Cisco networking technologies and enterprise networking concepts.

---

## 📌 Project Overview

The International Examination Center network is designed to support the operational and technical requirements of both sites, including:

- Examination laboratories
- Administration departments
- IT and employee workstations
- IP phones and VoIP services
- CCTV and IP cameras
- Network printers
- Servers and network services
- Network management
- Internet and WAN connectivity

The network follows a hierarchical architecture with dedicated **Access** and **Layer 3 Core/Distribution** layers, security boundaries, redundant WAN connectivity, VLAN segmentation, and centralized network services.

Both sites are interconnected through a secure WAN/IPsec VPN architecture while maintaining local infrastructure and selected local services at the secondary branch.

---

# 🏢 Network Sites

## Main Building (HQ)

The Main Building is the primary and central site of the International Examination Center.

It contains:

- 2 × Layer 3 Core/Distribution Switches
- 13 × Access Switches
- 2 × WAN/Edge Routers
- 2 × Firewalls
- Central server infrastructure
- Examination laboratories
- Administration area
- IT and employee area
- IP phones / VoIP infrastructure
- CCTV system
- Network printers
- Central network management services
- DMZ services
- Internet connectivity through two ISP paths

The HQ hosts the main centralized infrastructure and provides core network services for the organization.

---

## Branch 2 (Secondary Branch)

Branch 2 is the secondary site of the International Examination Center and is connected to the Main Building through the enterprise WAN.

It contains:

- 2 × Layer 3 Core/Distribution Switches
- 10 × Access Switches
- 2 × WAN/Edge Routers
- 1 × Firewall
- Local DHCP Server
- Local Camera Server
- Examination laboratories
- Administration area
- IT and employee area
- IP phones / VoIP infrastructure
- CCTV system
- Network printers
- Internet connectivity through two ISP paths

The branch provides selected local services while also using centralized services available from the Main Building.

---

# 🏗️ Network Architecture

The project follows a hierarchical enterprise network architecture consisting of:

- Access Layer
- Layer 3 Core/Distribution Layer
- Security Layer
- WAN/Edge Layer
- Server and DMZ Infrastructure

## Main Building Architecture

```text
                         ISP 1
                           |
                         ISP 2
                           |
                  +------------------+
                  |  HQ WAN Routers  |
                  |   HQ-R1 / HQ-R2  |
                  +------------------+
                           |
                    +-------------+
                    |    ASA1     |
                    | HQ Firewall |
                    +-------------+
                           |
                    +-------------+
                    |    ASA3     |
                    | HQ Firewall |
                    +-------------+
                           |
             +---------------------------+
             |       Core Layer          |
             |                           |
             |  HQ-CORE1   HQ-CORE2      |
             +---------------------------+
                    |           |
                    |           |
              Access Layer / Floor Switches
                    |
        +-----------+-----------+-----------+
        |           |           |           |
       PCs       IP Phones    Cameras    Printers
        |
   Examination /
   Administration /
   IT Users
Branch 2 Architecture
                         ISP 1
                           |
                         ISP 2
                           |
                +-------------------+
                | Branch WAN Routers|
                |  BR-R1 / BR-R2    |
                +-------------------+
                           |
                      +----------+
                      |  ASA22   |
                      | Firewall |
                      +----------+
                           |
             +---------------------------+
             |       Core Layer          |
             |                           |
             |  BR-CORE1   BR-CORE2      |
             +---------------------------+
                    |           |
                    |           |
              Access Layer / Floor Switches
                    |
        +-----------+-----------+-----------+
        |           |           |           |
       PCs       IP Phones    Cameras    Printers
        |
   Examination /
   Administration /
   IT Users
🔗 Inter-Site Connectivity

The Main Building and Branch 2 are interconnected through redundant WAN infrastructure.

                    MAIN BUILDING
                   +-------------+
                   | HQ-R1 / R2  |
                   +-------------+
                          ||
                    IPsec VPN / WAN
                          ||
                   +-------------+
                   | BR-R1 / R2  |
                   +-------------+
                    BRANCH 2

The WAN design includes:

Two WAN routers per site
Two ISP paths per site
Site-to-site IPsec VPN
Redundant connectivity
OSPF-based routing
Controlled inter-site communication
🧰 Technologies Used

The network design incorporates the following technologies:

VLAN Segmentation
Inter-VLAN Routing
Layer 3 Switching
EtherChannel / Port-Channel
OSPFv2
IPv4
IPv6
ACLs
NAT / PAT
DMZ
IPsec Site-to-Site VPN
QoS
DHCPv4
DHCPv6
DNS
NTP
Syslog
SNMPv3
Network Monitoring
Backup Services
Firewall Security
VoIP / IP Telephony
🔐 VLAN Structure

The network uses dedicated VLANs to logically separate different types of network traffic.

VLAN	Name	Purpose
10	ADMIN	Administration users
20	EMPLOYEES	IT and employee users
30	TEST_CENTER	Examination systems
40	CCTV	IP cameras
50	VOICE	IP phones and VoIP
60	SERVERS	Server infrastructure
70	MANAGEMENT	Network management
80	GUEST	Guest network
90	PRINTERS_IOT	Printers and IoT devices
100	DMZ	Public-facing services
999	NATIVE	Native / unused-port VLAN
🌐 IP Addressing

The project uses structured IPv4 and IPv6 addressing for both sites.

Main Site IPv4
10.10.0.0/16
Branch 2 IPv4
10.20.0.0/16
IPv6

The project uses the documentation IPv6 prefix:

2001:db8:acad::/48

IPv6 subnetting is organized according to VLAN and site requirements.

🖥️ Network Services
Main Building

The centralized infrastructure provides:

Active Directory Domain Services
DNS
DHCPv4
DHCPv6
NTP
Network Monitoring / Zabbix
Syslog
SNMPv3
Database Services
Web Services
IP-PBX / FreePBX-Asterisk
Backup Services
CCTV / NVR Services
SFTP
Branch 2

Branch 2 provides selected local services including:

Local DHCPv4
Local DHCPv6
Local CCTV / Camera Server

The branch also communicates with centralized services hosted at the Main Building.

📡 VoIP and IP Phones

The network includes an independent VOICE VLAN (VLAN 50) for IP phones and VoIP traffic.

The VoIP infrastructure is supported by:

IP Phones
IP-PBX / FreePBX-Asterisk
Dedicated Voice VLAN
QoS traffic prioritization
Network connectivity between the two sites

Voice traffic is separated from regular user and examination traffic to provide better traffic management and QoS control.

🔄 Routing and Redundancy

OSPFv2 is used as the internal dynamic routing protocol.

The design includes:

OSPF Area 0
Redundant core infrastructure
Layer 3 EtherChannel between core switches
Two WAN routers per site
Two ISP paths per site
Redundant WAN connectivity
Inter-site IPsec VPN
Structured IPv4 and IPv6 addressing
🛡️ Security Architecture

Security is implemented through multiple layers:

Firewalls
VLAN segmentation
Access Control Lists
DMZ
NAT/PAT
IPsec VPN
Management network separation
Restricted network management access
Secure network services

The Main Building contains two firewall/security layers:

Core Layer
    |
  ASA3
    |
  ASA1
    |
WAN / Internet

Branch 2 uses:

Core Layer
    |
  ASA22
    |
WAN / Internet
🌍 DMZ

The Main Building includes a dedicated DMZ network for externally accessible services.

The DMZ uses:

VLAN 100
10.10.100.0/24

The DMZ Web Server is:

10.10.100.10

The DMZ is separated from internal network resources through firewall security policies.

🔥 NAT and ACL

The design includes:

NAT
PAT / NAT Overload for internal users accessing the Internet
Separate NAT policies for HQ and Branch 2
Static NAT for the DMZ Web Server
ACL

ACL policies are used to control:

Network management access
DMZ access
Web traffic
Secure HTTPS traffic
ICMP reachability
Access to protected services
🔐 IPsec VPN

A site-to-site IPsec VPN connects the Main Building and Branch 2.

HQ Internal Network
10.10.0.0/16
        ||
     IPsec VPN
        ||
Branch Internal Network
10.20.0.0/16

The VPN provides secure communication between the two sites while using the redundant WAN infrastructure.

🚦 Quality of Service

QoS is implemented to prioritize important network traffic.

Class	Traffic	QoS Treatment
REALTIME	VoIP / IP-PBX	Strict Priority / LLQ
WEB	HTTP / HTTPS	Best Effort
MGMT	SSH / SNMP / Syslog	Guaranteed Bandwidth

VoIP traffic receives priority treatment to reduce latency and jitter.

🏢 Physical Infrastructure

The physical network design includes:

Network racks
Core switches
Access switches
WAN routers
Firewalls
Servers
Patch panels
Cat6 UTP cabling
Fiber optic uplinks
UPS systems
Floor distribution racks
Server infrastructure

The physical design represents the actual equipment distribution across the floors and network rooms of both sites.

🖥️ Logical Network Design

The logical network design was developed using Cisco Packet Tracer.

It represents:

VLANs
IP addressing
Core switches
Access switches
Routers
Firewalls
Servers
WAN connectivity
IPsec VPN
End devices
Network segmentation
Routing architecture
🗺️ Physical Network Design

The physical network design was developed using Microsoft Visio.

It represents:

Building topology
Floor distribution
Network racks
Switch placement
Router placement
Firewall placement
Server placement
Patch panels
Cabling
Fiber uplinks
Physical connectivity
📊 Project Scale
Component	Main Site	Branch 2	Total
PCs	191	137	328
IP Cameras	203	143	346
Printers	9	9	18
Core Switches	2	2	4
Access Switches	13	10	23
WAN Routers	2	2	4
Firewalls	2	1	3
IP Phones / VoIP	Supported	Supported	VLAN 50
📦 Network Equipment
Main Building
Equipment	Quantity
Layer 3 Core Switches	2
48-Port Access Switches	10
24-Port Access Switches	3
WAN Routers	2
Firewalls	2
Servers	5
Branch 2
Equipment	Quantity
Layer 3 Core Switches	2
48-Port Access Switches	7
24-Port Access Switches	3
WAN Routers	2
Firewall	1
Local Servers	2
🎯 Design Objectives

The main objectives of the project are:

Secure network segmentation
Reliable inter-site connectivity
Redundant WAN infrastructure
Scalable IP addressing
Centralized network services
Local branch services
Controlled access to network resources
Secure DMZ architecture
Traffic prioritization
Network monitoring and management
Support for future expansion
Structured physical and logical network design
🛠️ Design and Documentation Tools

The project was designed and documented using:

Tool	Purpose
Cisco Packet Tracer	Logical network topology and configuration
Microsoft Visio	Physical network design
Microsoft Word	Technical documentation
Microsoft PowerPoint	Project presentation
PDF	Final documentation and exported designs
📂 Repository Contents

The public repository contains the final exported project materials.

International-Examination-Center/
│
├── README.md
│
├── Presentation/
│   └── International-Examination-Center-Presentation.pdf
│
├── Documentation/
│   ├── Network-Documentation.pdf
│   └── Physical-Network-Design.pdf
│
└── Logical-Design/
    └── Logical-Network-Design.png
📚 Documentation Structure

The final documentation covers:

Project Overview
Site and Building Overview
Physical Network Design
Network Architecture
Logical Network Design
VLAN and Network Segmentation
IP Addressing Plan
Layer 2 Technologies
Layer 3 Routing
WAN and Internet Connectivity
Security Architecture
Quality of Service
Network Services
Conclusion
📄 Public Repository

This repository is intended to provide the final public version of the International Examination Center network project.

The public repository contains:

Final presentation
Final PDF documentation
Physical network design
Logical network design
Project overview and technical information
🔒 Private Project Repository

The original editable project files are maintained separately in a private repository.

The private repository may contain:

Cisco Packet Tracer .pkt files
Microsoft Visio .vsdx files
Editable Word .docx files
Editable PowerPoint .pptx files
Original diagrams
Working configurations
Project source files
Other internal working materials

The public repository intentionally contains exported/final versions rather than the original editable working files.

📖 Academic Purpose

This project was developed as an academic enterprise networking project demonstrating the design and documentation of a realistic multi-site network infrastructure.

It combines network architecture, switching, routing, security, WAN connectivity, network services, QoS, physical infrastructure, and technical documentation into one integrated enterprise network design.

👨‍💻 Project

International Examination Center

Enterprise Network Infrastructure Design

Main Site: HQ
Secondary Site: Branch 2

Core Technologies
Cisco Networking
VLAN
IPv4 / IPv6
OSPFv2
Layer 3 Switching
EtherChannel
ACL
NAT / PAT
DMZ
IPsec VPN
QoS
DHCPv4 / DHCPv6
DNS
NTP
Syslog
SNMPv3
VoIP
CCTV
Network Monitoring

 📜 License

This project is shared for **educational and academic purposes**.

You are welcome to view the project and use it as a reference for learning and study.

Please do not copy, reproduce, redistribute, or present this project or substantial parts of it as your own work without permission.

**Please respect the original work and give proper credit when referencing it.**
