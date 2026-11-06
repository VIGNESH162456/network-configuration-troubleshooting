# Verification Checklist

Run these checks after building the topology. Mark an item only after observing the result.

- [ ] Router interfaces/subinterfaces are up/up (`show ip interface brief`).
- [ ] VLAN 10 and VLAN 20 exist (`show vlan brief`).
- [ ] Trunk carries VLANs 10 and 20 (`show interfaces trunk`).
- [ ] PC-A receives a `192.168.10.x` DHCP address.
- [ ] PC-B receives a `192.168.20.x` DHCP address.
- [ ] PC-A can ping `192.168.10.1`.
- [ ] PC-B can ping `192.168.20.1`.
- [ ] Clients can communicate across VLANs.
- [ ] Clients can ping DNS server `192.168.10.10`.
- [ ] `nslookup lab.example` resolves to `192.168.10.10`.

## Results log

| Test | Actual result | Notes/date |
|---|---|---|
| DHCP - PC-A | Not tested | |
| DHCP - PC-B | Not tested | |
| Gateway reachability | Not tested | |
| Inter-VLAN ping | Not tested | |
| DNS resolution | Not tested | |
