# 🎓 Enterprise University Campus Network Simulation

A comprehensive multi-tier Cisco Packet Tracer project modeling an enterprise-grade university campus network. The architecture connects three dedicated campus zones—**Administration**, **Labs**, **Dorms**—to an ISP core with centralized authentication, VoIP, dynamic routing, and wireless infrastructure.

---

## 📌 Architecture Overview

```
                          +-------------------------+
                          |       ISP / Cloud       |
                          +------------+------------+
                                       |
                +----------------------+----------------------+
                |                                             |
   [ OSPF Area 60 ]                              [ OSPF Area 0 ]                              [ OSPF Area 2 ]
+-----------------------+                    +-----------------------+                    +-----------------------+
|  Administration Zone  | <================> |     Labs Building     | <================> |    Dormitory Zone     |
|  • VLANs: 10,20,30,   |   10.10.10.0/30    |  • VLANs: 10,20,30,   |    60.60.60.0/30   |  • VLANs: 10,20,30,   |
|           40,50,70    |   40.40.40.0/30    |           40,50       |                    |           40,50,1     |
|  • EtherChannel Ch1   |   50.50.50.0/30    |  • EtherChannel Ch2   |                    |  • Multi-AP WLAN      |
|  • RADIUS + DHCP/DNS  |                    |  • RADIUS + DNS       |                    |  • 172.16.0.0/16 Sub. |
+-----------------------+                    +-----------------------+                    +-----------------------+

```

---

## 🏢 Subnet & VLAN Allocation

### 1. Administration Building (`192.168.0.0/16`)



* **VLAN 10:** IT Department


* **VLAN 20:** Staff


* **VLAN 30:** Management & Native


* **VLAN 40:** IP Telephony (VoIP)


* **VLAN 50:** Network Printers


* **VLAN 70:** Central Servers


* **VLAN 999:** Unused / Blackhole



### 2. Labs Building (`172.168.0.0/16`)



* **VLAN 10:** Students


* **VLAN 20:** Security Cameras & Surveillance


* **VLAN 30:** Lab Workstations


* **VLAN 40:** Faculty / Staff


* **VLAN 50:** Management & Native


* **VLAN 999:** Unused / Blackhole



### 3. Dorms / Student Housing (`172.16.0.0/16`)



* **VLAN 1:** Server / Core Services


* **VLAN 10:** Resident Students


* **VLAN 20:** Staff


* **VLAN 30:** Guest Access


* **VLAN 40:** IoT Devices


* **VLAN 50:** Management


* **VLAN 999:** Unused / Blackhole



---

## ⚙ Core Network Implementations

* **Layer 3 Multi-Area OSPF:** Backbone (`Area 0`) interconnects edge building routers (`Area 60` for Admin, `Area 2` for Dorms) with static default routing directed to the simulated ISP.


* **Link Aggregation (EtherChannel):** Configured across core switches (`Channel 1` and `Channel 2`) for multi-link load balancing and bandwidth resilience.


* **Centralized Identity & AAA:** Integrated RADIUS servers handling centralized authentication across wireless clients and management planes.


* **Wireless Infrastructure:** Multi-SSID deployment with APs mapped directly to isolated user VLANs (Students, Staff, IoT, Guests).


* **Layer 2 Hardening:** Configured with DHCP Snooping, Dynamic ARP Inspection (DAI), PortFast, and BPDU Guard.


* **Edge Services:** IP Telephony routing on dedicated voice VLANs, multi-scope DHCP services, NAT/PAT translation, and standard/extended ACLs for inter-VLAN boundary enforcement.



---

## 🖼 Topologies

**Full Campus Topology**

| **Administration Building** | **Labs Building** | **Dorms Building** |
| --- | --- | --- |
|  |  |  |

---

## 🚀 Key Skills Demonstrated

* **Routing & Switching:** Multi-Area OSPF, Inter-VLAN Routing, EtherChannel (LACP/PAgP), 802.1Q encapsulation.


* **Network Security:** AAA with RADIUS, Layer 2 perimeter defenses, traffic filtering via ACLs.


* **Infrastructure Services:** Voice over IP (VoIP), DHCP scopes, dynamic NAT/PAT, SSH remote management.



---

## 🛠 Tools & Environment

* **Simulation Software:** Cisco Packet Tracer


* **Default Lab Credentials:** Passwords set to `cisco` across console/VTY/privileged EXEC (refer to embedded topology notes for role-based testing logins).
