# Networking Project — Cisco Packet Tracer

## Overview
This repository contains my final networking project implemented in Cisco Packet Tracer. The design simulates a small-to-medium enterprise environment with structured segmentation, secure remote access (VPN), redundancy, per-site logging, QoS, and hands-on exercises for access control.

## Topology
- Layered design: core/edge routers, distribution and access switches
- Multiple VLANs for department segmentation (e.g., Sales VLAN 10, Administration 20, Legal 30, Production 40, ServerRoom 100, Guest 70)
- Wireless access points with separate SSIDs for employees and guests
- On-site server rooms with shared services (DHCP, application/data servers, printing)
- VPN tunnel(s) for secure site-to-site / remote access
- Per-site dedicated **syslog** servers for centralized logging and diagnostics

## Key features implemented
- **VLAN segmentation & trunking** to separate broadcast domains and enforce policy boundaries
- **Inter-VLAN routing** (SVIs or router-on-a-stick where applicable)
- **DHCP** scopes and relay (`ip helper-address`) for distributed addressing
- **NAT/PAT** at the edge for Internet access
- **Site-to-site / remote-access VPN** (IPsec/IKE) with traffic selectors and ACLs defining interesting traffic
- **Distributed ACLs** to control inter-VLAN access and protect management and server resources
- **Redundancy & HA approach** for critical links/gateways (redundant links, gateway failover strategies)
- **Spanning Tree (STP)** configured for loop prevention and link resilience
- **Per-site Syslog**: each site logs to its local syslog server for improved fault isolation and retention
- **QoS policies** configured to prioritize latency-sensitive traffic (e.g., voice, critical print/print-queue traffic) and to shape/limit bulk flows
- **Access control exercises**: practical scenarios demonstrating controlled use of shared printers and servers (ACL-based rulesets, role separation)

## Security & Operational notes
- VPN policies include encryption/authentication parameters and ACLs that explicitly define which subnets traverse the tunnel.
- ACLs are applied directionally to limit traffic from guest/employee VLANs to sensitive server VLANs and to restrict management access to specific admin hosts/VLANs.
- NAT exemptions are applied where VPN traffic must avoid translation.
- Syslog servers per site enable local log aggregation and make forensic correlation and VPN troubleshooting easier.

NOTE: The complete project is included in this repository and can be exported and tested directly in a Cisco Packet Tracer environment.
