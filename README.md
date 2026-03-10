# Home Network Segmentation & Home Lab Risk Mitigation

## Project Summary
This project documents improvements made to my home network to increase security while supporting an isolated cybersecurity home lab environment. The goal was to separate lab systems from personal devices to reduce the risk of lateral movement and unintended network exposure during testing.

The network design implements segmentation, stronger wireless security, and device monitoring practices while creating a scalable foundation for future VLAN-based segmentation.

## Goal
Improve home network security while isolating a cybersecurity home lab to reduce the risk of lab systems interacting with personal devices.

## Network Environment

**Primary Router**  
TP-Link Archer AX3200 (Home Network)

**Lab Router**  
TP-Link Archer AX50 (Isolated Lab Network)

**Future Expansion**  
Managed switches to support VLAN segmentation (802.1Q)

## Network Segmentation Design

The lab network is isolated from the primary home network using a router-behind-router architecture.

```text
Internet
   │
ISP Modem
   │
TP-Link Archer AX3200 (Primary Home Router)
   │
Home Network Devices
   │
AX3200 LAN Port
   │
TP-Link Archer AX50 (Lab Router - WAN)
   │
Cybersecurity Lab Network
   │
 ├ Kali Linux Attacker System
 ├ Ubuntu Endpoint
 ├ Wazuh Server
 └ Lab / IoT Testing Devices
