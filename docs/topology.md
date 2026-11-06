# Topology Notes

Devices: R1 router, SW1 Layer 2 switch, PC-A (VLAN 10), PC-B (VLAN 20), and DNS server (VLAN 10).

| Link | Purpose |
|---|---|
| R1 G0/0 ↔ SW1 G0/1 | 802.1Q trunk |
| SW1 Fa0/1 ↔ PC-A | VLAN 10 access |
| SW1 Fa0/2 ↔ PC-B | VLAN 20 access |
| SW1 Fa0/3 ↔ DNS server | VLAN 10 access |

R1 uses subinterfaces G0/0.10 and G0/0.20 to route between VLANs.
