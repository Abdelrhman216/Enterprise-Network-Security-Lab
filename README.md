# Enterprise Network Security Lab

![Cisco](https://img.shields.io/badge/Cisco-Packet%20Tracer-1BA0D7?logo=cisco&logoColor=white)
![Security](https://img.shields.io/badge/Focus-Network%20Security-critical)
![Routing](https://img.shields.io/badge/Routing-OSPF-blue)
![IPv6](https://img.shields.io/badge/IPv6-ACLs-informational)

> **Academic cybersecurity / networking lab** — enterprise network segmentation, secure management, routing protection, access control, and traffic inspection using Cisco technologies.

## Author

**Abdelrhman Ali Saleh**

## Project Overview

This project demonstrates a segmented enterprise network designed with security controls at both Layer 2 and Layer 3. The lab uses Cisco Packet Tracer and documents the configuration patterns used for:

- VLAN-based network segmentation
- Inter-VLAN routing using 802.1Q router-on-a-stick
- DHCP address assignment
- Secure device administration using SSH
- OSPF authentication
- IPv6 traffic filtering with ACLs
- AAA / parser-view based administrative separation
- Zone-Based Firewall policy concepts
- Security-oriented network documentation and verification

The repository includes the original Packet Tracer topology plus cleaned, organized configuration references and documentation.

## Architecture

```text
                         +----------------------+
                         |   WAN / OUTSIDE      |
                         +----------+-----------+
                                    |
                             +------+------+
                             | Security /  |
                             | Edge Layer   |
                             +------+------+
                                    |
                         +----------+-----------+
                         |   Core / Routing    |
                         | OSPF + ACL + DHCP   |
                         +-----+----------+-----+
                               |          |
                         802.1Q Trunks    |
                         +-----+----+   +--+-----+
                         | Access   |   | Access |
                         | Switches |   | Switch |
                         +--+--+--+-+   +--+--+--+
                            |  |  |          |  |
                          VLANs / Segments  VLANs
```

See [`topology/network-topology.png`](topology/network-topology.png) for the Packet Tracer topology and [`topology/subnetting-table.png`](topology/subnetting-table.png) for the subnetting reference.

## Security Controls

| Control | Purpose | Status |
|---|---|---|
| VLAN segmentation | Separate user / management networks | Documented |
| 802.1Q trunking | Carry multiple VLANs between devices | Documented |
| SSH v2 | Secure remote administration | Documented |
| OSPF authentication | Protect routing adjacency | Documented |
| IPv6 ACL | Restrict selected IPv6 traffic | Documented |
| AAA / parser views | Administrative access separation | Documented |
| Zone-Based Firewall | Stateful traffic inspection policy | Documented |
| DHCP | Centralized address assignment | Documented |

> **Important:** The `.pkt` file is the authoritative lab artifact. The configuration files in this repository are reference/documentation files and should be verified against the topology in Packet Tracer before being used on real equipment.

## VLAN & Addressing Reference

### Network A

| VLAN | Role | Gateway | Mask |
|---:|---|---|---|
| 50 | User segment | 172.16.1.113 | /29 |
| 60 | User segment | 172.16.1.121 | /29 |
| 70 | User segment | 172.16.1.129 | /29 |
| 80 | Management | 172.16.1.141 | /29 |

### Network B

| VLAN | Role | Gateway | Mask |
|---:|---|---|---|
| 10 | User segment | 172.16.1.65 | /28 |
| 20 | User segment | 172.16.1.81 | /29 |
| 30 | User segment | 172.16.1.89 | /29 |
| 40 | User segment | 172.16.1.97 | /29 |
| 50 | Management | 172.16.1.105 | /29 |

## Project Structure

```text
Enterprise-Network-Security-Lab/
├── README.md
├── LICENSE
├── .gitignore
├── topology/
│   ├── Enterprise_Network_Security.pkt
│   ├── network-topology.png
│   └── subnetting-table.png
├── configurations/
│   ├── routers/
│   ├── switches/
│   └── security/
├── documentation/
│   ├── network-design.md
│   ├── subnetting.md
│   ├── security-architecture.md
│   └── testing.md
└── screenshots/
    └── topology.png
```

## How to Run

1. Install Cisco Packet Tracer.
2. Open `topology/Enterprise_Network_Security.pkt`.
3. Inspect the topology and device configurations.
4. Use the verification commands in `documentation/testing.md`.
5. Compare the live Packet Tracer configuration with the reference configuration files in `configurations/`.

## Verification Checklist

Use the following commands inside Packet Tracer where supported:

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show ip ospf neighbor
show ip protocols
show ip dhcp binding
show access-lists
show ipv6 access-list
show running-config
show ip ssh
```

## Security Notes

Credentials and cryptographic keys are intentionally represented as placeholders in the cleaned reference configurations. Do **not** publish real passwords, private keys, API tokens, or production secrets in a public repository.

This is an educational lab. It is not a production-ready enterprise security baseline without additional hardening, validation, logging, monitoring, redundancy, and change-control procedures.

## Future Improvements

- Add centralized Syslog and NTP.
- Add SNMPv3 monitoring.
- Add stronger management-plane ACLs.
- Add DHCP Snooping / Dynamic ARP Inspection where supported by the selected Packet Tracer devices.
- Add Port Security and BPDU Guard to access ports.
- Expand IPv6 security coverage.
- Add a documented IPsec site-to-site VPN scenario.
- Add a dedicated DMZ and explicitly documented trust boundaries.
- Add repeatable attack/defense verification scenarios.

## License

See `LICENSE`.
