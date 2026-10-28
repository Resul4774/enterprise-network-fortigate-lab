# Enterprise Network & FortiGate Security Lab

## Project Overview

This project is an enterprise network lab built in EVE-NG to practice network engineering, network segmentation, routing, and firewall security.

The lab simulates a headquarters (HQ) network connected to an external WAN environment. It combines Cisco-style routing and access control lists (ACLs) with a FortiGate firewall to demonstrate how network traffic can be routed, filtered, and monitored.

## Technologies Used

- **EVE-NG** — Network emulation
- **Cisco IOS-style CLI** — VLAN routing and access control lists
- **FortiGate Firewall** — Firewall policies, source NAT, and traffic logging
- **Ubuntu Linux** — Network endpoints and connectivity testing
- **Nginx** — External HTTP test server

## Key Implementations

- Designed separate user and server VLANs.
- Configured inter-VLAN routing on the core router.
- Implemented IPv4 ACLs to restrict traffic between VLANs.
- Configured FortiGate WAN and LAN interfaces.
- Created outbound firewall policies with source NAT.
- Applied a temporary HTTP deny policy to validate firewall filtering.
- Tested connectivity between VLANs and to an external web server.
- Verified that HTTP access was blocked by the test policy and restored after the policy was disabled.

## Network Segmentation

The HQ network uses separate IP subnets for user and server traffic:

| Network | Subnet | Purpose |
|---|---|---|
| VLAN 10 | `192.168.10.0/24` | User network |
| VLAN 20 | `192.168.20.0/24` | Server network |
| VLAN 99 | Management subnet configured on the core router | Network management |
| WAN transit | `172.16.0.0/30` and `172.16.1.0/30` | Core-to-firewall and firewall-to-ISP connectivity |

The Linux endpoints also use a separate EVE-NG management network for administrative access.

## Security and Traffic Control

Router ACLs restrict selected traffic between the user and server VLANs. The FortiGate firewall controls permitted outbound traffic toward the simulated WAN and applies source NAT.

A dedicated test policy was used to block HTTP traffic from VLAN 10 to the external test server. Connectivity tests confirmed that HTTP requests timed out while the deny policy was enabled and succeeded after it was disabled.

## Learning Outcomes

This project provided hands-on practice with:

- Enterprise network topology design
- VLAN segmentation and inter-VLAN routing
- IPv4 ACL configuration and traffic filtering
- FortiGate firewall policies and NAT
- Routing and connectivity troubleshooting
- Security policy validation through practical testing

## Project Scope

This is an educational network lab designed for experimentation and portfolio demonstration. It represents a single HQ environment with a simulated WAN and external test server.

Inter-VLAN traffic is routed by the core router and controlled by router ACLs; it does not traverse the FortiGate in the current design. FortiGate firewall policies apply to traffic routed through the firewall.

## Disclaimer

This project was developed in a virtual lab environment. Configurations and results are specific to the lab design and should be reviewed before being adapted for production networks.
