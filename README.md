# Enterprise Network Security Lab

A segmented enterprise network designed and implemented in Cisco Packet Tracer with VLANs, DHCP, inter-VLAN routing, and router-based access control to enforce network security policies.

## Objective

The objective of this project was to design and implement a small enterprise network that provides both connectivity and network segmentation while restricting unauthorized communication between different areas of the network.

The network separates **Employees, Servers, and Guests** into dedicated VLANs and uses router-based inter-VLAN routing to control communication between these networks. An extended Access Control List (ACL) was then implemented to enforce security policies and prevent unauthorized access.

The completed environment was tested to verify that:

* Employees can communicate with authorized server resources.
* Employee devices cannot communicate directly with the Guest network.
* Guest devices cannot communicate with the Employee network.
* Guest devices cannot access the Server network.
* Authorized traffic continues to function normally.

The project demonstrates how **VLAN segmentation, DHCP, inter-VLAN routing, and ACLs** can be combined to create a more controlled and secure enterprise network environment.

## Skills Learned

* Enterprise network design and topology planning
* VLAN creation and network segmentation
* IP addressing and subnet organization
* DHCP configuration and address assignment
* Router-on-a-stick inter-VLAN routing
* Cisco IOS configuration and verification
* Extended Access Control List (ACL) configuration
* Network security policy implementation
* Traffic filtering and network isolation
* ICMP connectivity testing
* Cisco Packet Tracer Simulation Mode
* Troubleshooting network connectivity and security policies
* Interpreting ACL match counters and packet behavior
* Network documentation and security evidence collection

## Technologies & Tools Used

* **Cisco Packet Tracer** — Network design, configuration, simulation, and security testing
* **Cisco IOS** — Router and switch configuration
* **VLANs** — Network segmentation
* **DHCP** — Automated IP address assignment
* **802.1Q / Router-on-a-Stick** — Inter-VLAN routing
* **Extended ACLs** — Traffic filtering and access control
* **ICMP** — Connectivity and security testing

## Network Architecture

The network was designed using a segmented enterprise architecture consisting of one router, one managed switch, employee workstations, a server, and a guest workstation.

The network is divided into three primary VLANs:

| VLAN | Name      | Network         | Purpose                     |
| ---- | --------- | --------------- | --------------------------- |
| 10   | EMPLOYEES | 192.168.10.0/24 | Internal employee devices   |
| 20   | SERVERS   | 192.168.20.0/24 | Enterprise server resources |
| 30   | GUEST     | 192.168.30.0/24 | Guest and untrusted devices |

The router provides the default gateway for each VLAN and handles inter-VLAN routing through a router-on-a-stick configuration. The switch connects the endpoint devices to their respective VLANs while the router provides controlled communication between network segments.

### Topology

The completed topology is shown below.

![Enterprise Network Topology](screenshots/01-network-topology.png)

## VLAN Segmentation

VLAN segmentation was used to separate users and resources into distinct logical networks. This reduces the need for all devices to share the same broadcast domain and provides a foundation for applying different security policies to each group.

The switch was configured with three primary VLANs:

| VLAN | Name      | Assigned Devices | Network         |
| ---- | --------- | ---------------- | --------------- |
| 10   | EMPLOYEES | PC-EMP1, PC-EMP2 | 192.168.10.0/24 |
| 20   | SERVERS   | Server           | 192.168.20.0/24 |
| 30   | GUEST     | PC-GUEST         | 192.168.30.0/24 |

### VLAN Purpose

**VLAN 10 — Employees**

This VLAN contains internal employee workstations. It represents the trusted user network and is permitted to access authorized server resources.

**VLAN 20 — Servers**

This VLAN isolates server resources from end-user and guest devices. Server resources can be accessed by authorized internal devices while remaining protected from the Guest network.

**VLAN 30 — Guest**

The Guest VLAN is treated as an untrusted network. Guest devices are isolated from both the Employee and Server VLANs through ACL policies implemented on the router.

This segmentation provides the foundation for the security controls implemented later in the project.

### VLAN Configuration

The following screenshot shows the VLAN configuration on the network switch, including the assignment of endpoint ports to their respective VLANs.

![VLAN Configuration](screenshots/02-vlan-configuration.png)

