# IP Addressing Plan

| Network | VLAN | Subnet | Gateway | Assignment |
|---|---:|---|---|---|
| Department A | 10 | 192.168.10.0/24 | 192.168.10.1 | DHCP |
| Department B | 20 | 192.168.20.0/24 | 192.168.20.1 | DHCP |

DNS server: `192.168.10.10/24`, gateway `192.168.10.1`.

The DHCP configuration excludes `192.168.10.1–192.168.10.20` and `192.168.20.1–192.168.20.20` for gateways, servers, and static infrastructure.
