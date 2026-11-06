# Troubleshooting Guide

| Symptom | Checks | Possible correction |
|---|---|---|
| PC has no DHCP address | `ipconfig`, `show ip dhcp binding`, `show vlan brief` | Check DHCP pool, access VLAN, and trunk |
| PC cannot reach gateway | `ipconfig`, `show ip interface brief` | Check IP, mask, gateway, interface state |
| VLANs cannot communicate | `show interfaces trunk`, `show ip route` | Check allowed VLANs and router subinterfaces |
| IP ping works but hostname fails | `nslookup lab.example` | Check DNS address, service, and A record |
| Trunk does not carry VLANs | `show interfaces trunk` | Check trunk mode and allowed VLAN list |

## Diagnostic sequence
1. Check physical links and interface state.
2. Confirm client IP, subnet mask, gateway, and DNS.
3. Ping the local gateway.
4. Ping a host in the other VLAN.
5. Ping the DNS server by IP.
6. Test DNS with `nslookup`.

Change one setting at a time and repeat the relevant test.
