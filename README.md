
## Overview
This project demonstrates the design and implementation of a complete enterprise network environment using Oracle VirtualBox. It replicates a real‑world infrastructure for Campbell & Starr Super Bread‑Makers, focusing on:

- Secure communications
- Centralized management
- Redundant connectivity
- Automated IP assignment
- Controlled user access

## Technologies Used
- **Virtualization Tool**: Oracle VirtualBox
- **Operating Systems**:
  - Windows Server 2022 (Domain Controller, DHCP, DNS, File Server)  
  - Windows 11 Pro (Client PCs)

## Networking
- **Main Network**: 192.168.100.0/24
- **Redundant Network**: 192.168.200.0/24

## Components
| Machine       | Roles                                                          |
|----------------|----------------------------------------------------------------|
| DC01           | AD DS, DNS, DHCP, File Server                                 |
| DC02           | Secondary Domain Controller, Redundant AD/DNS                |
| ClientPC01     | Domain‑joined Client                                          |
| ClientPC02     | Domain‑joined Client                                          |

## Key Features Implemented

### 1. Network Connectivity
- Static IP configuration for servers.
- Verified connectivity:
  - Ping by IP
  - Ping by hostname
  - Domain Name Resolution (`nslookup`)

### 2. Redundancy
- Dual NIC configuration across **DC01** and **DC02**.
- Created a backup network (`192.168.200.0/24`).
- Tested failover links and AD replication across both IP ranges.

### 3. User Creation & Automation
- Created AD Users.
- Assigned Home Directory Paths.
- Verified access from Client PCs.
- Created Group Policy Objects (GPO) for role‑based access.

### 4. DHCP Configuration
- DHCP Scope: `192.168.100.50–192.168.100.100`.
- Assigned IP addresses, configured exclusions, and set options:
  - DNS: `192.168.100.10`
  - Gateway: `192.168.100.1`
- Authorized DHCP services and verified IP assignment.

### 5. NTFS & Shared Folders
- Created department‑level shared folders:
  - `C:\Shared\Accounting`
  - `C:\Shared\Baking`
- Assigned group‑level access using **icacls**.
- Verified access from Client PCs:
  - Emily: `\\DC01\Shared\Baking`
  - Restricted access for other departments.

### 6. Credentials & Domain Usage
- Created test user accounts and avoided relying on the built‑in Administrator.
- Verified user profiles and access to resources.
- Confirmed role‑based access and NTFS permission enforcement.

## Issue Resolution
- **DNS Unreachable**: Fixed by setting manual DNS IP.
- **AD Service Errors**: Resolved by restarting AD services.
- **Network Adapter Conflicts**: Fixed by verifying MAC and adapter settings.
- **NTFS Permission Errors**: Adjusted using `icacls` settings.

## Conclusion
This project showcases an enterprise‑level, redundant, and secure Windows network built within a virtual environment. It delivers:
- High Availability (Redundant DC/DHCP/DNS)
- Centralized User Management (AD DS)
- Controlled File and Resource Access (NTFS, GPO)
- Automated IP Management (DHCP)

It provides a strong foundation for understanding enterprise network design and administration.

## Additional Resources
- **PDF Documentation**
