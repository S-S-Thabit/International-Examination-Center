# International Examination Center

An enterprise network design and documentation project for an **International Examination Center** consisting of a main site and a secondary branch.

The project focuses on designing a secure, scalable, redundant, and well-structured network infrastructure using Cisco networking technologies and enterprise networking concepts.

---

## 📌 Project Overview

The International Examination Center network is designed to support examination laboratories, administration, IT staff, CCTV systems, printers, servers, network management, and Internet/WAN connectivity across two sites:

- **Main Building (HQ)**
- **Branch 2 (Secondary Branch)**

The network follows a hierarchical architecture with dedicated Access and Layer 3 Core/Distribution layers, security boundaries, redundant WAN connectivity, and centralized network services.

---

## 🏗️ Network Architecture

The project uses a structured enterprise network architecture:

```text
                    Internet / ISP 1
                         |
                    Internet / ISP 2
                         |
                  +---------------+
                  |   WAN Routers |
                  +---------------+
                         |
                      Firewall
                         |
                    Core Layer
                  +------------+
                  | L3 Core 1  |
                  | L3 Core 2  |
                  +------------+
                         |
                  Access Switches
                         |
        +----------------+----------------+
        |                |                |
       PCs            Cameras          Printers
