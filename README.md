# Network Configuration & Troubleshooting

**Tools:** Cisco Packet Tracer, Cisco IOS CLI, IPv4, VLAN, DHCP, DNS, TCP/IP

A documented networking lab for practising VLAN segmentation, IP addressing, router-on-a-stick inter-VLAN routing, DHCP, DNS, and basic troubleshooting.

> **Status:** Reference configurations and documentation are provided. They have not been deployed or verified on physical Cisco equipment. Build and test the topology in Packet Tracer before describing it as completed.

## Objectives
- Create VLAN 10 and VLAN 20 for separate user groups.
- Configure switch access ports and an 802.1Q trunk.
- Configure inter-VLAN routing on a router.
- Assign client IP addresses using DHCP.
- Configure and test DNS name resolution.
- Troubleshoot using common IOS and client commands.

## Topology
```text
                 R1 - Router
          G0/0.10: 192.168.10.1
          G0/0.20: 192.168.20.1
                    |
                802.1Q trunk
                    |
                 SW1 - 2960
             /       |       \
         VLAN 10  VLAN 20   VLAN 10
          PC-A     PC-B     DNS Server
                            192.168.10.10
```

## IP addressing plan

| Device/interface | VLAN | IPv4 address |
|---|---:|---|
| R1 G0/0.10 | 10 | 192.168.10.1/24 |
| R1 G0/0.20 | 20 | 192.168.20.1/24 |
| DNS server | 10 | 192.168.10.10/24 |
| PC-A | 10 | DHCP |
| PC-B | 20 | DHCP |

## Repository structure
```text
├── README.md
├── .gitignore
├── configs/
│   ├── router-r1.txt
│   └── switch-sw1.txt
├── docs/
│   ├── addressing-plan.md
│   ├── topology.md
│   └── troubleshooting-guide.md
└── tests/
    └── verification-checklist.md
```

## Build and configure in Packet Tracer
1. Add a router, 2960 switch, two PCs, and one server.
2. Connect R1 G0/0 to SW1 G0/1; use the switch uplink as an 802.1Q trunk.
3. Connect PC-A to Fa0/1 (VLAN 10), PC-B to Fa0/2 (VLAN 20), and the DNS server to Fa0/3 (VLAN 10).
4. Apply the reference configurations in `configs/`. Adjust interface names if your device model differs.
5. Set the DNS server to `192.168.10.10/24`, gateway `192.168.10.1`. Enable DNS and add `lab.example` → `192.168.10.10`.
6. Set both PCs to obtain IP addresses using DHCP.
7. Run the checks in `tests/verification-checklist.md` and record actual results.

## Useful commands
Router:
```text
show ip interface brief
show ip route
show ip dhcp binding
show running-config
```
Switch:
```text
show vlan brief
show interfaces trunk
show mac address-table
```
PC:
```text
ipconfig
ping 192.168.10.1
ping 192.168.20.1
ping 192.168.10.10
nslookup lab.example
```

## Expected outcomes
- PC-A receives an address in `192.168.10.0/24`; PC-B receives an address in `192.168.20.0/24`.
- Both clients can reach their default gateways.
- Inter-VLAN routing works through R1.
- Clients can reach the DNS server and resolve the configured test hostname.

These are expected lab outcomes, not claims of completed testing. Record observed results in the checklist.

## Learning outcomes
IPv4 addressing, VLANs, access ports, trunking, DHCP, DNS, router-on-a-stick routing, and systematic network troubleshooting.
