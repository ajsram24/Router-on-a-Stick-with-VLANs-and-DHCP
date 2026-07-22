# Router-on-a-Stick with VLANs and DHCP

## 📌 Project Overview

This project demonstrates the implementation of Router-on-a-Stick (ROAS) to enable Inter-VLAN Routing using IEEE 802.1Q trunking. A Cisco 2911 router was configured as a DHCP server to automatically assign IP addresses to devices in different VLANs.

## 🎯 Objectives

- Configure multiple VLANs on a Layer 2 switch.
- Configure access and trunk ports.
- Implement Router-on-a-Stick.
- Configure DHCP pools for multiple VLANs.
- Verify Inter-VLAN communication.
- Troubleshoot DHCP connectivity issues.

## 🛠 Devices Used

- Cisco 2911 Router
- Cisco 2960 Switch
- PCs/Laptop/printer/smartphone
- Access Point
- Cisco Packet Tracer

## 🌐 Network Topology

<img width="1920" height="1080" alt="topology" src="https://github.com/user-attachments/assets/563c5777-8314-49be-abd6-7f66fd5bb540" />


## 📋 VLAN Configuration

| VLAN | Department | Network | Default Gateway |
|------|------------|------------------|----------------|
| 10 | Admin | 192.168.1.0/26 | 192.168.1.1 |
| 20 | Finance | 192.168.1.64/26 | 192.168.1.65 |
| 30 | CS | 192.168.1.128/26 | 192.168.1.129 |

## ⚙️ Features Implemented

- VLAN Configuration
- Access Port Configuration
- 802.1Q Trunking
- Router-on-a-Stick
- DHCP Server Configuration
- Inter-VLAN Routing
- Network Verification

## 📂 Project Files

```
configs/
├── router-running-config.txt
└── switch-running-config.txt

verification/
├── show-vlan-brief.txt
├── show-interfaces-trunk.txt
├── show-ip-interface-brief.txt
├── show-ip-dhcp-pool.txt
└── show-ip-dhcp-binding.txt
```

## ✅ Verification

### DHCP Address Assignment

<img width="1920" height="1021" alt="dhcp_success" src="https://github.com/user-attachments/assets/43016875-2456-4351-93ff-9b75bec669c1" />


### Inter-VLAN Connectivity

<img width="1920" height="1021" alt="inter_vlan_ping_test" src="https://github.com/user-attachments/assets/f88d932a-f760-4a80-aa38-30d83b24a55b" />


## 🔍 Troubleshooting

### Problem

The PCs were unable to obtain IP addresses from the DHCP server.

### Investigation

- Verified VLAN configuration.
- Verified trunk status.
- Verified router subinterfaces.
- Checked DHCP pools.
- Checked DHCP bindings.
- Used `show cdp neighbors detail` to verify the physical connection between the router and the switch.
- Checked the MAC address table.

### Root Cause

The PC was connected to a switch port configured as a trunk instead of an access port. End devices should always be connected to access ports.

### Solution

Configured the PC's switch port as an access port and assigned it to the appropriate VLAN. DHCP requests were then successfully processed by the router.

## 📚 Key Learnings

- Difference between access ports and trunk ports.
- Router-on-a-Stick configuration.
- IEEE 802.1Q VLAN tagging.
- DHCP operation across multiple VLANs.
- Using CDP for topology verification.
- Using MAC address tables to troubleshoot Layer 2 issues.
- Systematic network troubleshooting using Cisco IOS commands.

## 📖 Useful Verification Commands

```
show vlan brief
show interfaces trunk
show ip interface brief
show ip dhcp pool
show ip dhcp binding
show cdp neighbors detail
show mac address-table
```

## 🚀 Future Improvements

- Add DNS server.
- Configure NAT for Internet access.
- Implement ACLs between VLANs.
- Add Port Security.
- Configure SSH for secure device management.
