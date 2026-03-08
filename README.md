# Active Directory Home Lab

[![Platform](https://img.shields.io/badge/Platform-Windows%20Server-blue)](https://github.com)
[![Virtualization](https://img.shields.io/badge/Virtualization-VirtualBox-orange)](https://github.com)
[![Status](https://img.shields.io/badge/Status-Complete-success)](https://github.com)

> A complete Active Directory environment built from scratch in VirtualBox, featuring domain controller setup, DNS configuration, DHCP, RAS/NAT, bulk user provisioning via PowerShell, and domain-joined client connectivity.

## Table of Contents

- [Overview](#overview)
- [Network Architecture](#network-architecture)
- [Technologies Used](#technologies-used)
- [Build Process](#build-process)
  - [Phase 1: Network Interface Configuration](#phase-1-network-interface-configuration)
  - [Phase 2: Active Directory Domain Services](#phase-2-active-directory-domain-services)
  - [Phase 3: Admin Account Creation](#phase-3-admin-account-creation)
  - [Phase 4: RAS/NAT Configuration](#phase-4-rasnat-configuration)
  - [Phase 5: DHCP Server Setup](#phase-5-dhcp-server-setup)
  - [Phase 6: Bulk User Provisioning](#phase-6-bulk-user-provisioning)
  - [Phase 7: Client Domain Join](#phase-7-client-domain-join)
- [Skills Demonstrated](#skills-demonstrated)
- [Author](#author)

## Overview

The objective of this lab was to build a fully functional Active Directory environment from the ground up. This involved deploying a Windows Server domain controller with dual network interfaces, configuring core infrastructure services (DNS, DHCP, RAS/NAT), automating user creation with PowerShell, and joining a Windows 10 client to the domain.

**Final Result:** A working Active Directory domain with automated user provisioning and a domain-joined client with full internet connectivity through the domain controller.

## Network Architecture

```
Internet
    |
[NIC 1 - External]
    |
Domain Controller (Windows Server)
  - Active Directory Domain Services
  - DNS Server
  - DHCP Server
  - RAS / NAT
    |
[NIC 2 - Internal Network]
    |
Client1 (Windows 10)
  - Domain-Joined
  - DHCP-Assigned IP
  - Internet Access via DC
```

| Component | Details |
|-----------|---------|
| **Domain Controller** | Windows Server with 2 NICs |
| **NIC 1** | External — Internet-facing |
| **NIC 2** | Internal — Private network for clients |
| **Client** | Windows 10 — Domain-joined workstation |
| **Virtualization** | Oracle VirtualBox |

## Technologies Used

| Technology | Purpose |
|-----------|---------|
| **Windows Server** | Domain controller, DNS, DHCP, RAS/NAT |
| **Windows 10** | Client workstation |
| **Oracle VirtualBox** | Virtualization platform |
| **PowerShell** | Automated bulk user creation |
| **Active Directory Domain Services** | Centralized identity and access management |
| **DNS** | Domain name resolution |
| **DHCP** | Dynamic IP assignment for clients |
| **RAS/NAT** | Routing and remote access for internal network internet connectivity |

## Build Process

### Lab Architecture Overview

The diagram below shows the full lab design including both NICs on the domain controller, the internal network, and the client VM.

![Lab Overview](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/bd3dca70-41e0-4201-b037-818f7ce94c5c)

---

### Phase 1: Network Interface Configuration

Configured two network interfaces on the domain controller — one dedicated to the internet (external) and one for the internal private network where clients will reside.

![NIC Configuration](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/3f00606c-2c4c-4822-9346-7a2e993ad5a5)

The internal NIC was configured with a static IP address and DNS settings to support Active Directory and domain services on the private network.

![Internal Network Details](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/814886fc-82d9-4cb7-8d24-3f95ffc8974b)

---

### Phase 2: Active Directory Domain Services

Installed the Active Directory Domain Services (AD DS) role on Windows Server and promoted the server to a domain controller.

![AD DS Installation](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/acd95b21-f3a6-4110-ae22-37f20ad4525d)

After configuring the domain name, the domain was created and ready for deployment.

![Domain Creation](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/d28b79e7-4b01-4b27-810a-c992e43c6bfb)

---

### Phase 3: Admin Account Creation

Created a dedicated administrator account within Active Directory for domain management, following best practices of not using the default built-in administrator account.

![Admin User Creation](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/77c24c89-a926-4391-a02d-aa698d1059cd)

---

### Phase 4: RAS/NAT Configuration

Configured Remote Access Server (RAS) with Network Address Translation (NAT) on the domain controller. This allows clients on the internal private network to access the internet through the domain controller's external NIC.

![RAS/NAT Setup](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ea842309-940c-4998-a723-090f0e365372)

![RAS/NAT Complete](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/44a2a0b0-adb6-484e-b3f2-29d9ba4a7eb6)

---

### Phase 5: DHCP Server Setup

Installed and configured the DHCP server role to automatically assign IP addresses to clients joining the internal network. The DHCP scope was configured to hand out addresses on the internal subnet with the domain controller as the default gateway.

![DHCP Configuration](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ca1bd18f-0af3-4096-9a22-8d6189858f65)

![DHCP Scope](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/8e7a0d46-5194-470b-88b6-68fa51cceba3)

---

### Phase 6: Bulk User Provisioning

Created a PowerShell script to automate the creation of multiple user accounts in Active Directory. This simulates a real-world scenario where IT administrators need to onboard a large number of users efficiently.

![PowerShell Script Execution](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/a0479666-8acf-4df9-9e2d-a2876a3e6eef)

The script successfully created all user accounts, which are now visible in Active Directory Users and Computers.

![Users Created in AD](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/9a5e32f7-87cb-446b-a80b-ea0b0415479f)

---

### Phase 7: Client Domain Join

Deployed a Windows 10 client VM (CLIENT1) connected to the internal network. The client received an IP address from the DHCP server and has internet access through the domain controller's RAS/NAT configuration.

![Client Network Connectivity](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/ba8b2b08-30e7-456b-9f90-542313173b17)

CLIENT1 was successfully joined to the domain. Any user account created on the domain controller can now log in to this client machine, demonstrating centralized authentication and access management.

![Domain Join Verified](https://github.com/Jpouncil23/Active-Directory-Lab/assets/163768012/5a58b89c-80ec-44fe-b909-0d693f484e9a)

---

## Skills Demonstrated

- Deploying Active Directory Domain Services and promoting a domain controller
- Configuring dual-NIC networking for internal/external network separation
- Setting up DNS services for domain name resolution
- Configuring DHCP for automated IP address assignment
- Implementing RAS/NAT to provide internet access to internal clients
- Automating bulk user creation with PowerShell scripting
- Joining client workstations to a domain
- Troubleshooting authentication, DNS, and network connectivity issues

## Author

**Justin**
IT Professional

---

*Last Updated: June 2024*
