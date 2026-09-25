# Network Design

## Design Goals

1. Segment users with VLANs.
2. Separate management traffic from user traffic.
3. Route between VLANs through controlled Layer 3 interfaces.
4. Protect routing adjacencies with authentication.
5. Restrict selected IPv6 traffic with ACLs.
6. Provide secure administrative access through SSH.
7. Apply traffic inspection policies at security boundaries.

## Segmentation Model

The lab uses VLANs as security boundaries. Management VLANs are kept separate from user VLANs so that administrative interfaces are not placed in the same broadcast domain as normal endpoints.

## Routing Model

Inter-VLAN routing is implemented using 802.1Q subinterfaces on the routing device. OSPF is used for dynamic routing and authentication is configured to reduce the risk of unauthorized routing adjacency formation.

## Management Plane

SSH version 2 is used for remote management. Local authentication is documented as the baseline, while AAA/parser views provide examples of role-based command access.
