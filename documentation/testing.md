# Testing & Verification

## Layer 2

```text
show vlan brief
show interfaces trunk
```

Expected checks:
- Required VLANs exist.
- Access ports belong to the intended VLAN.
- Trunks carry only the required VLANs.

## Layer 3

```text
show ip interface brief
show ip route
```

Expected checks:
- Required interfaces are up/up.
- Connected networks appear in the routing table.

## DHCP

```text
show ip dhcp binding
```

Expected checks:
- Clients receive addresses from the intended subnet.
- Default gateways match the VLAN gateway.

## OSPF

```text
show ip ospf neighbor
show ip protocols
```

Expected checks:
- Intended neighbors reach the FULL state.
- Authentication configuration is consistent between peers.

## IPv6 ACL

```text
show ipv6 access-list
```

Expected checks:
- The intended deny rule exists.
- Permitted traffic follows the documented policy.

## SSH

```text
show ip ssh
show running-config | section line vty
```

Expected checks:
- SSH version 2 is enabled.
- VTY access is restricted to SSH where supported.

## Final Validation

Run end-to-end pings and traceroutes between approved VLANs, then verify that intentionally restricted traffic is denied. Record the results in a test matrix before treating the topology as complete.
