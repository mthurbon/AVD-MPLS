# MPLS_CORE

## Table of Contents

- [Fabric Switches and Management IP](#fabric-switches-and-management-ip)
  - [Fabric Switches with inband Management IP](#fabric-switches-with-inband-management-ip)
- [Fabric Topology](#fabric-topology)
- [Fabric IP Allocation](#fabric-ip-allocation)
  - [Fabric Point-To-Point Links](#fabric-point-to-point-links)
  - [Point-To-Point Links Node Allocation](#point-to-point-links-node-allocation)
  - [Loopback Interfaces (BGP EVPN Peering)](#loopback-interfaces-bgp-evpn-peering)
  - [Loopback0 Interfaces Node Allocation](#loopback0-interfaces-node-allocation)
  - [ISIS CLNS interfaces](#isis-clns-interfaces)
  - [VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)](#vtep-loopback-vxlan-tunnel-source-interfaces-vteps-only)
  - [VTEP Loopback Node allocation](#vtep-loopback-node-allocation)

## Fabric Switches and Management IP

| POD | Type | Node | Management IP | Platform | Provisioned in CloudVision | Serial Number |
| --- | ---- | ---- | ------------- | -------- | -------------------------- | ------------- |
| MPLS_CORE | ce | CE-01 | 192.168.0.101/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | ce | CE-02 | 192.168.0.102/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | p | PE-04 | 192.168.0.104/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | p | PE-06 | 192.168.0.106/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | pe | PE-07 | 192.168.0.107/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | pe | PE-08 | 192.168.0.108/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | pe | PE-09 | 192.168.0.109/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | pe | PE-10 | 192.168.0.110/24 | vEOS-lab | Provisioned | - |
| MPLS_CORE | rr | RR-03 | 192.168.0.103/24 | vEOS-lab | Provisioned | - |

> Provision status is based on Ansible inventory declaration and do not represent real status from CloudVision.

### Fabric Switches with inband Management IP

| POD | Type | Node | Management IP | Inband Interface |
| --- | ---- | ---- | ------------- | ---------------- |

## Fabric Topology

| Type | Node | Node Interface | Peer Type | Peer Node | Peer Interface |
| ---- | ---- | -------------- | --------- | ----------| -------------- |
| p | PE-04 | Ethernet3/1 | rr | RR-03 | Ethernet4/1 |
| p | PE-04 | Ethernet6/1 | p | PE-06 | Ethernet4/1 |
| p | PE-04 | Ethernet7/1 | pe | PE-07 | Ethernet4 |
| p | PE-04 | Ethernet8/1 | pe | PE-08 | Ethernet4 |
| p | PE-04 | Ethernet9/1 | pe | PE-09 | Ethernet4/1 |
| p | PE-04 | Ethernet10/1 | pe | PE-10 | Ethernet4/1 |
| p | PE-06 | Ethernet10/1 | pe | PE-10 | Ethernet6/1 |
| pe | PE-07 | Ethernet3 | rr | RR-03 | Ethernet7/1 |
| pe | PE-07 | Ethernet8 | pe | PE-08 | Ethernet7 |
| pe | PE-08 | Ethernet3 | rr | RR-03 | Ethernet8/1 |
| pe | PE-09 | Ethernet3/1 | rr | RR-03 | Ethernet9/1 |
| pe | PE-09 | Ethernet10/1 | pe | PE-10 | Ethernet9/1 |
| pe | PE-10 | Ethernet3/1 | rr | RR-03 | Ethernet10/1 |

## Fabric IP Allocation

### Fabric Point-To-Point Links

| Uplink IPv4 Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ---------------- | ------------------- | ------------------ | ------------------ |

### Point-To-Point Links Node Allocation

| Node | Node Interface | Node IP Address | Peer Node | Peer Interface | Peer IP Address |
| ---- | -------------- | --------------- | --------- | -------------- | --------------- |
| PE-04 | Ethernet3/1 | 192.168.12.15/31 | RR-03 | Ethernet4/1 | 192.168.12.14/31 |
| PE-04 | Ethernet6/1 | 192.168.12.16/31 | PE-06 | Ethernet4/1 | 192.168.12.17/31 |
| PE-04 | Ethernet7/1 | 192.168.12.3/31 | PE-07 | Ethernet4 | 192.168.12.2/31 |
| PE-04 | Ethernet8/1 | 192.168.12.7/31 | PE-08 | Ethernet4 | 192.168.12.6/31 |
| PE-04 | Ethernet9/1 | 192.168.12.18/31 | PE-09 | Ethernet4/1 | 192.168.12.19/31 |
| PE-04 | Ethernet10/1 | 192.168.12.20/31 | PE-10 | Ethernet4/1 | 192.168.12.21/31 |
| PE-06 | Ethernet10/1 | 192.168.12.22/31 | PE-10 | Ethernet6/1 | 192.168.12.23/31 |
| PE-07 | Ethernet3 | 192.168.12.0/31 | RR-03 | Ethernet7/1 | 192.168.12.1/31 |
| PE-07 | Ethernet8 | 192.168.12.4/31 | PE-08 | Ethernet7 | 192.168.12.5/31 |
| PE-08 | Ethernet3 | 192.168.12.8/31 | RR-03 | Ethernet8/1 | 192.168.12.9/31 |
| PE-09 | Ethernet3/1 | 192.168.12.11/31 | RR-03 | Ethernet9/1 | 192.168.12.10/31 |
| PE-09 | Ethernet10/1 | 192.168.12.24/31 | PE-10 | Ethernet9/1 | 192.168.12.25/31 |
| PE-10 | Ethernet3/1 | 192.168.12.13/31 | RR-03 | Ethernet10/1 | 192.168.12.12/31 |

### Loopback Interfaces (BGP EVPN Peering)

| Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------- | ------------------- | ------------------ | ------------------ |
| 10.1.0.0/25 | 128 | 7 | 5.47 % |
| 10.10.0.0/25 | 128 | 2 | 1.57 % |

### Loopback0 Interfaces Node Allocation

| POD | Node | Loopback0 |
| --- | ---- | --------- |
| MPLS_CORE | CE-01 | 10.10.0.1/32 |
| MPLS_CORE | CE-02 | 10.10.0.2/32 |
| MPLS_CORE | PE-04 | 10.1.0.4/32 |
| MPLS_CORE | PE-06 | 10.1.0.6/32 |
| MPLS_CORE | PE-07 | 10.1.0.7/32 |
| MPLS_CORE | PE-08 | 10.1.0.8/32 |
| MPLS_CORE | PE-09 | 10.1.0.9/32 |
| MPLS_CORE | PE-10 | 10.1.0.10/32 |
| MPLS_CORE | RR-03 | 10.1.0.3/32 |

### ISIS CLNS interfaces

| POD | Node | CLNS Address |
| --- | ---- | ------------ |
| MPLS_CORE | CE-01 | 49.0001.0100.1000.0001.00 |
| MPLS_CORE | CE-02 | 49.0001.0100.1000.0002.00 |
| MPLS_CORE | PE-04 | 49.0001.0100.0100.0004.00 |
| MPLS_CORE | PE-06 | 49.0001.0100.0100.0006.00 |
| MPLS_CORE | PE-07 | 49.0001.0100.0100.0007.00 |
| MPLS_CORE | PE-08 | 49.0001.0100.0100.0008.00 |
| MPLS_CORE | PE-09 | 49.0001.0100.0100.0009.00 |
| MPLS_CORE | PE-10 | 49.0001.0100.0100.0010.00 |
| MPLS_CORE | RR-03 | 49.0001.0100.0100.0003.00 |

### VTEP Loopback VXLAN Tunnel Source Interfaces (VTEPs Only)

| VTEP Loopback Pool | Available Addresses | Assigned addresses | Assigned Address % |
| ------------------ | ------------------- | ------------------ | ------------------ |

### VTEP Loopback Node allocation

| POD | Node | Loopback1 |
| --- | ---- | --------- |
