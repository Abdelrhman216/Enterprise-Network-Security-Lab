# Subnetting Reference

The addressing plan uses small point-to-multipoint / user subnets to limit broadcast domains and conserve address space.

## /29 Networks

A `/29` provides 8 total addresses, 6 usable host addresses in a conventional IPv4 subnet.

Examples documented in this lab include:

- `172.16.1.112/29` → gateway `172.16.1.113`
- `172.16.1.120/29` → gateway `172.16.1.121`
- `172.16.1.128/29` → gateway `172.16.1.129`
- `172.16.1.136/29` → management network with gateway `172.16.1.141`

## /28 Network

`172.16.1.64/28` provides 16 total addresses and 14 conventional usable host addresses. It is used for VLAN 10 in the documented configuration.
