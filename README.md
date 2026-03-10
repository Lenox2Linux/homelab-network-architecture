# Home Network Segmentation & Home Lab Risk Mitigation

## Project Summary
This project documents improvements made to my home network to increase security while supporting an isolated cybersecurity home lab environment. The goal was to separate lab systems from personal devices to reduce the risk of lateral movement and unintended network exposure during testing.

The network design implements segmentation, stronger wireless security, and device monitoring practices while creating a scalable foundation for future VLAN-based segmentation.

---

## Goal
Improve home network security while isolating a cybersecurity home lab to reduce the risk of lab systems interacting with personal devices.

---

## Network Environment

**Primary Router**  
TP-Link Archer AX3200 (Home Network)

**Lab Router**  
TP-Link Archer AX50 (Isolated Lab Network)

**Lab Switch**  
Netgear GS308E Managed Switch (Lab Device Expansion)

**Future Expansion**  
Additional managed switches to support VLAN segmentation (802.1Q)

---

## Network Segmentation Design

The lab network is isolated from the primary home network using a router-behind-router architecture.


Internet
> ISP Modem
> TP-Link Archer AX3200 (Primary Home Router)
> Home Network Devices
> AX3200 LAN Port
> TP-Link Archer AX50 (Lab Router)
> Netgear GS308E (Managed Lab Switch)
> MacBook Pro 2012 - Kali Linux Attacker System
> MacBook Air - Ubuntu Endpoint
> Mac mini - Wazuh Server
> Additional Lab / IoT Devices

This design creates double NAT, which introduces an additional firewall boundary between the home network and the lab network.

Adding the GS308E managed switch allows wired expansion for lab devices and prepares the environment for potential VLAN-based segmentation in the future.

---

## Lab Devices and Roles

**Lenovo ThinkPad T14**  
Primary workstation used for lab administration, documentation, and virtualization.

**Mac mini**  
Ubuntu Server host running the Wazuh monitoring platform using Docker.

**MacBook Pro 2012**  
Kali Linux attacker system used for network scanning, testing, and packet analysis.

**MacBook Air**  
Ubuntu endpoint used as a monitored lab system that generates logs and security events.

**TP-Link Archer AX3200**  
Primary router responsible for managing the home network and internet connectivity.

**TP-Link Archer AX50**  
Secondary router used to isolate the cybersecurity lab network.

**Netgear GS308E Managed Switch**  
Provides wired connectivity for lab systems and enables future VLAN support for more granular segmentation.

---

## Implementation Steps

### 1. Replace ISP Router
Replaced restrictive ISP equipment by deploying a TP-Link Archer AX3200 as the primary router.

### 2. Reset and Configure Router
Performed a factory reset on the AX3200 and created a new SSID with a strong password.

### 3. Device Visibility
Added and labeled IoT devices in the TP-Link management app to improve network visibility and troubleshooting.

### 4. Guest Network Isolation
Created a guest network for visitors and non-trusted devices to limit cross-device interaction.

### 5. Wireless Security Hardening
Enabled strong wireless protections:

- WPA2/WPA3 encryption (AES)
- Disabled WPS to reduce brute-force and PIN attack risk

### 6. Lab Network Isolation
Implemented router-behind-router segmentation by connecting the AX3200 LAN port to the AX50 WAN port.

This creates:

- double NAT
- separate firewall boundary
- isolated lab network

### 7. Wired Lab Expansion
Connected the Netgear GS308E managed switch to the AX50 to support wired lab devices and prepare for future VLAN segmentation.

### 8. Lab Device Segmentation
Connected lab devices to the AX50 / GS308E infrastructure to ensure lab traffic remains separated from personal devices.

### 9. DHCP Reservation
Configured a DHCP reservation on the AX50 for a wired lab device to ensure:

- consistent IP addressing
- easier monitoring
- predictable network identification

### 10. Future Network Expansion
Prepared for wired expansion using managed switches to support 802.1Q VLAN segmentation for more granular network isolation.

---

## Security and Risk Mitigation Outcomes

These improvements significantly strengthened the home network security posture.

Key benefits include:

- Reduced risk of lab systems interacting with personal devices
- Improved device accountability through network labeling and monitoring
- Reduced wireless attack surface by disabling WPS and enforcing WPA2/WPA3
- Improved troubleshooting through stable DHCP reservations
- Created scalable infrastructure for future VLAN segmentation
- Added wired lab infrastructure for controlled device expansion

---

## Tools and Concepts Used

- Network segmentation
- Router-behind-router architecture
- Double NAT
- Guest network isolation
- WPA2/WPA3 wireless encryption
- WPS hardening
- DHCP reservation
- Ethernet segmentation
- Managed switches
- VLAN planning
- Device inventory management

---

## Skills Demonstrated

- Network architecture design
- Home network hardening
- Network segmentation
- Risk mitigation
- Infrastructure planning
- Wireless security configuration
- Technical documentation

---

## Future Improvements

Planned improvements to further strengthen the lab environment include:

- Deploy VLAN segmentation on the GS308E switch
- Expand the number of monitored endpoints
- Implement packet analysis using Wireshark
- Add additional security monitoring tools
- Simulate more advanced attack scenarios
- Build a fully segmented security testing network

---

## Related Projects

**SOC Lab Setup**  
https://github.com/Lenox2Linux/soclab-wazuh

**SOC Detection Lab – Nmap Scan Investigation**  
https://github.com/Lenox2Linux/soc-detect-nmap-wazuh
