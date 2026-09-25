# Security Architecture

## Threats Addressed

### VLAN hopping

Mitigation approach: explicit VLAN assignments and controlled trunk configuration. Production deployments should also disable unused switch ports, avoid unnecessary native VLAN exposure, and explicitly configure trunk behavior.

### Unauthorized management access

Mitigation approach: SSH v2, local authentication, AAA concepts, and management VLAN separation.

### Routing attacks

Mitigation approach: OSPF authentication to reduce the chance of unauthorized routing peers participating in the routing domain.

### Unauthorized IPv6 traffic

Mitigation approach: IPv6 ACLs can explicitly deny selected source/destination traffic while permitting other traffic according to policy.

### Uncontrolled inter-zone traffic

Mitigation approach: Zone-Based Firewall policies define which traffic classes can be inspected between security zones.

## Defense-in-Depth Model

```text
Endpoint
   ↓
VLAN Segmentation
   ↓
Switch Security
   ↓
ACL / Routing Controls
   ↓
OSPF Authentication
   ↓
Firewall / Security Zones
   ↓
External Network
```

The controls are complementary rather than interchangeable: segmentation limits exposure, routing controls constrain paths, authentication protects control-plane relationships, and firewall policy controls traffic between trust zones.
