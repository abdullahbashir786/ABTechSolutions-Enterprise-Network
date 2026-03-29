# ABTechSolutions Multi-Site Enterprise Network
### Cisco Packet Tracer | Network Design & Security Implementation

---

## 📋 Project Overview

A comprehensive multi-site enterprise network simulation built in Cisco Packet Tracer, demonstrating real-world network design, security, and high availability concepts. The project simulates a complete enterprise infrastructure with headquarters, two remote branch offices, DMZ architecture, and centralized monitoring.

---

## 🏗️ Network Architecture

```
                          [Internet]
                              |
                      [Internet Router]
                              |
                    [ISP Router Mesh]
                    /         |        \
            [HQ Routers]  [Branch A]  [Branch B]
            (HSRP Active/  Router      Router
             Standby)        |            |
                |          Switch       Switch
           [L3 Switch]     PCs          PCs
          /     |    \
      [SW1]  [SW2]  [DMZ SW]
       |       |        |
      PCs     PCs   DMZ Servers
                    (Web/Email/DNS)
```

**3 Sites:** Headquarters + Branch A + Branch B  
**50+ Devices:** 6 Routers, 6 Switches, 9 Servers, Wireless Infrastructure, 20+ End Devices

---

## ⚡ Technologies Implemented

**Routing & Switching**
- OSPF (Open Shortest Path First) — Area 0, dynamic routing across all sites
- HSRP (Hot Standby Router Protocol) — Router redundancy with sub-10 second failover
- 802.1Q VLAN Trunking — 8 VLANs with inter-VLAN routing
- EtherChannel (LACP) — Link aggregation for redundancy and bandwidth
- Layer 3 Switching — Hardware-based inter-VLAN routing

**Security**
- Extended ACLs — Perimeter filtering, blocking external to internal traffic
- Static NAT — DMZ public service exposure
- Port Security (Sticky MAC) — 34 ports secured against rogue devices
- SSH v2 — Encrypted management on all 13 network devices
- DMZ Segmentation — Isolated public-facing services
- 144+ Unused Ports Disabled — Reduced attack surface

**Services**
- DHCP — Centralized with 11 pools, DHCP relay for branches
- DNS — Internal (abtechsolutions.local) and public zones
- NTP — Time synchronization across 14 devices
- Syslog — Centralized logging from all network devices

**Wireless**
- Wireless LAN Controller (WLC 3504)
- Dual SSID: ABTech-Internal (employees) and ABTech-Guest (visitors)
- WPA2-PSK, complete guest isolation

---

## 🌐 Network Design

### VLAN Structure (Headquarters)

| VLAN | Name | Network | Purpose |
|------|------|---------|---------|
| 10 | HR | 192.168.10.0/24 | Human Resources |
| 20 | Finance | 192.168.20.0/24 | Finance & Accounting |
| 30 | IT | 192.168.30.0/24 | IT Department |
| 40 | Admin | 192.168.40.0/24 | Administration |
| 50 | Guest | 192.168.50.0/24 | Internal Guests |
| 90 | Wireless-Internal | 192.168.90.0/24 | Employee WiFi |
| 99 | Management | 192.168.99.0/24 | Servers & Infrastructure |
| 100 | Voice | 192.168.100.0/24 | VoIP Ready |

### High Availability (HSRP)

| Router | Role | Priority | IP |
|--------|------|----------|----|
| HQ Router 1 (Cisco 2911) | Active | 110 | 192.168.99.2 |
| HQ Router 2 (Cisco 2811) | Standby | 100 | 192.168.99.3 |
| Virtual IP | Shared | — | 192.168.99.254 |

Failover time: ~10 seconds | Preempt enabled

### DMZ Architecture

| Server | Private IP | Public IP (NAT) |
|--------|-----------|-----------------|
| Web Server | 192.168.200.10 | 200.0.0.10 |
| Email Server | 192.168.200.11 | 200.0.0.11 |
| DNS Server | 192.168.200.12 | 200.0.0.12 |

---

## 🔒 Security Implementation

**Multi-Layer Defense Strategy:**

1. **Perimeter** — Extended ACLs block all external → internal traffic
2. **DMZ** — Isolated network segment for public services
3. **Access Layer** — Port security with sticky MAC on 34 ports
4. **Management** — SSH v2 on all 13 devices, login banners
5. **Physical** — 144+ unused ports administratively shut down

**ACL Logic:**
```
External → DMZ Public IPs  ✅ ALLOWED
External → Internal VLANs  ❌ BLOCKED
External → Branch Offices  ❌ BLOCKED
External → Management      ❌ BLOCKED
```

---

## 📊 Testing Results

| Test | Description | Result |
|------|-------------|--------|
| Intra-VLAN | Same VLAN communication | ✅ PASS |
| Inter-VLAN | Routing between departments | ✅ PASS |
| Branch to HQ | OSPF multi-hop routing | ✅ PASS |
| Branch to Branch | Multi-site communication | ✅ PASS |
| NAT | External to DMZ via public IP | ✅ PASS |
| ACL | External blocked from internal | ✅ PASS |
| HSRP | Automatic failover ~10 seconds | ✅ PASS |
| Port Security | Rogue device blocked + logged | ✅ PASS |
| Guest Isolation | Guest cannot reach internal | ✅ PASS |
| NTP | All 14 devices synchronized | ✅ PASS |
| Syslog | Centralized logs from all devices | ✅ PASS |

**Overall: 15/15 Tests Passed (100%)**

---

## 📁 Repository Contents

```
├── ABTechSolutions_Final.pkt    # Cisco Packet Tracer topology file
├── Documentation.pdf            # Full project documentation with screenshots
└── README.md                    # This file
```

---

## 🛠️ Tools Used

- Cisco Packet Tracer
- Cisco IOS CLI

---

## 👤 Author

**Abdullah Bashir**  
BS Cybersecurity Student  
📧 [mabdullahbashir786@gmail.com]  
🔗 [linkedin.com/in/abdullah-bashir-1a3075342]  
🐙 [github.com/abdullahbashir786]

---

## 📅 Project Details

- **Course:** Computer Networks
- **Date:** December 2024
- **Status:** Complete ✅
