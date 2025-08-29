# Chapter 3 -  Network Devices

## Topics

* Introduction to network devices: switches, routers, PCs
* Network topologies and architecture

## Learning Outcomes

* Identify functions of common network devices
* Build a basic network using Packet Tracer
* Use `ipconfig` and Control Panel in Windows 11 to view network info

## Introduction to Network Devices

In any computer network, various devices work together to ensure the successful transmission, reception, and processing of data. Understanding the roles and functions of these devices is crucial for anyone entering the field of networking. Network devices are the building blocks that define how data travels from one point to another, how different segments of a network interact, and how services such as security, routing, and access are implemented. This section introduces the most common network devices, including switches, routers, personal computers (PCs), gateways, access points, and firewalls, providing a foundation for understanding both basic and intermediate networking concepts.

**PCs (Personal Computers)**
Personal computers serve as endpoints in a network, responsible for both generating and consuming data. Each PC is equipped with a Network Interface Card (NIC), which may be wired (Ethernet) or wireless (Wi-Fi). Network configuration settings include an IP address (either static or assigned via DHCP), subnet mask, default gateway, and DNS server information. PCs communicate using the TCP/IP model and rely on standard diagnostic tools such as `ping` for checking connectivity, `ipconfig` (on Windows) or `ifconfig`/`ip a` (on Linux) for viewing network configurations, and `tracert` or `traceroute` for examining packet travel paths. Multiple layers of the OSI model are relevant in PC networking: the physical layer for hardware and cabling, the data link layer for MAC addressing, the network layer for IP addressing, the transport layer for protocols like TCP and UDP, and the application layer for services like HTTP, FTP, and DNS. Security best practices on PCs include enabling firewalls, using antivirus software, and ensuring operating systems and applications are regularly updated with security patches.

![PC as a Network Endpoint in the OSI and TCP/IP Model](figure/03/PC_Network_Endpoint.png)

<!-- \label{fig:pc-network-endpoint} -->

**Switches**
Switches primarily operate at Layer 2 (Data Link Layer) of the OSI model, although some advanced switches also function at Layer 3 (referred to as multilayer switches). They use MAC (Media Access Control) addresses to forward frames to specific destination ports. Each connected device is placed in a separate collision domain, significantly improving performance in LAN environments. Switches support full-duplex communication, eliminating collisions. They maintain a MAC address table (or CAM table) to learn which devices are connected to which ports. Advanced switch features include support for VLANs (Virtual Local Area Networks), port security, link aggregation (EtherChannel), and Spanning Tree Protocol (STP) to prevent network loops. Managed switches allow configuration via command-line interface (CLI), Secure Shell (SSH), or web interfaces, while unmanaged switches operate in a plug-and-play fashion.

![Functions and Features of a Network Switch](figure/03/Functions_and_Features_of_a_Netw.png)

<!-- \label{fig:network-switch} -->

**Routers**
Routers operate at Layer 3 (Network Layer) of the OSI model and are responsible for routing packets between different networks. They use IP addressing and subnet information to determine the best path for packet forwarding, based on a routing table. This table can be populated manually through static routing or dynamically using routing protocols. Standard dynamic routing protocols include RIP (Routing Information Protocol), a simple distance-vector protocol with a maximum hop count of 15; OSPF (Open Shortest Path First), a link-state protocol using Dijkstra’s algorithm to determine shortest paths; and EIGRP (Enhanced Interior Gateway Routing Protocol), a Cisco proprietary protocol that combines the best of distance-vector and link-state characteristics. Routers separate broadcast domains and often perform Network Address Translation (NAT), allowing multiple devices on a local area network (LAN) to share a single public IP address. They can also function as DHCP relays, apply Access Control Lists (ACLs), and support basic firewall configurations. Routers are commonly used to connect local area networks (LANs) to wide area networks (WANs), such as the Internet or other remote networks.

![Functions and Features of a Router](figure/03/Functions_and_Features_of_a_Router.png)

<!-- \label{fig:router-functions} -->

**Gateways**
A gateway is a device or node that acts as an entry and exit point to another network, often translating communication between different network protocols or architectures. A typical example is a default gateway, typically a router that forwards packets from a local subnet to destinations beyond the local network. Gateways are essential for communication between networks that use different communication protocols, for example, IP to legacy systems or internal networks to the Internet.

![Network Gateway: Entry and Exit Point for Network Traffic](figure/03/Network_Gateway.png)

<!-- \label{fig:network-gateway} -->

**Firewalls**
A firewall is a network security device that monitors and controls incoming and outgoing traffic based on predefined security rules. Firewalls can be hardware-based, software-based, or a combination of both. They operate primarily at Layer 3 and Layer 4 (Network and Transport layers), but next-generation firewalls also provide deep packet inspection at Layer 7 (Application Layer). Firewalls are used to enforce policies that prevent unauthorized access and protect against threats such as malware, intrusion attempts, and denial-of-service (DoS) attacks. They support stateful inspection, packet filtering, and can be configured with access control lists (ACLs), port forwarding, and VPN pass-through settings.

![Firewall: Network Traffic Monitoring and Threat Protection](figure/03/Firewall_Diagram.png)

<!-- \label{fig:firewall} -->

**Access Points**
An access point (AP) is a network device that enables wireless-capable devices to connect to a wired local area network (LAN). It operates at Layer 2 of the OSI model and uses Wi-Fi (IEEE 802.11) standards to transmit data over the air. Access points are commonly used in home networks, enterprise wireless networks, and public hotspots. They extend the range of a wireless network and can be either standalone or controller-managed. Essential features include SSID broadcasting, encryption (e.g., WPA3), and support for multiple clients.

![Access Point: Layer 2 Wireless Bridge to Wired LAN (IEEE 802.11)](figure/03/Access_Point.png)

<!-- \label{fig:access-point} -->

## Network Topologies and Architecture

In computer networking, the arrangement of devices and their communication are defined by network topologies and architectures. A **network topology** refers to the physical or logical layout of devices and connections in a network. It determines how data flows and how efficiently devices communicate with each other. Understanding different types of topologies is essential for designing, troubleshooting, and optimizing networks.

On the other hand, **network architecture** defines the structure and design principles behind how network components operate and interact. It includes models such as peer-to-peer and client-server, as well as concepts like centralized versus distributed control. Together, topologies and architectures form the blueprint for network functionality, scalability, and resilience.

The following sections explain both physical and logical topologies, as well as network architecture models, highlighting their advantages, limitations, and typical use cases.

### Physical Topologies

A **bus topology** uses a single backbone cable to connect all devices in the network. It is inexpensive and straightforward to implement, especially in small environments. However, it is highly susceptible to collisions and network failure if the backbone cable is damaged, as all devices share the same communication line.

In a **star topology**, all devices are connected to a central switch or hub. This makes the network easy to manage and expand. If one cable fails, only the device it is connected to is affected. However, if the central device fails, the entire network goes down.

A **ring topology** forms a closed loop in which data travels in one direction from one device to the next until it reaches its destination. This design reduces the chances of collision, but can be disrupted if any device or connection in the ring fails.

![Common Physical Network Topologies: Bus, Star, Ring, Mesh, and Hybrid](figure/03/Network_Topologies.png)

<!-- \label{fig:network-topologies} -->

A **mesh topology** connects every device to every other device in the network. This provides high redundancy and reliability, as multiple paths exist for data to travel. It is often used in mission-critical environments, but is more complex and expensive to implement due to the number of connections required.

A **hybrid topology** combines two or more different types of topologies, such as star-bus or star-ring. It allows organizations to tailor the network design to their specific needs, offering flexibility and scalability while inheriting the strengths and weaknesses of the topologies it combines.

### Logical Topologies

A **broadcast topology** is commonly used in Ethernet LANs. In this topology, every device receives all network data, regardless of whether it is the intended recipient. Devices must filter out irrelevant data, which can lead to network inefficiency if traffic volume is high.

**Token passing topology** is typically used in older ring networks. In this logical layout, a token — a small data packet — is passed around the network. A device must possess the token to transmit data, which helps avoid collisions. However, it may introduce delays and is considered outdated compared to modern Ethernet switching.

![Logical Topologies: Broadcast (used in Ethernet LANs) and Token Passing (used in older ring networks)](figure/03/Logical_Topologies.png)

<!-- \label{fig:logical-topologies} -->

### Network Architectures

In a **peer-to-peer (P2P)** network architecture, each device has equal status and can both provide and consume resources without the need for a central server. This setup is simple and cost-effective, suitable for minor or temporary networks, but it lacks centralized control and scalability.

A **client-server** architecture uses one or more central servers to manage resources and services for client devices. This model supports centralized administration, scalability, and security, making it ideal for business and enterprise networks. However, it depends on server availability and typically requires more maintenance and setup.

![Network Architectures: Peer-to-Peer vs. Client-Server Models](figure/03/Network_Architectures.png)

<!-- \label{fig:network-architectures} -->

The **centralized vs. distributed** model compares two broader approaches. In a **centralized network**, one central point manages all operations, making control and security easier but also creating a single point of failure. In a **distributed network**, power and resources are spread across multiple nodes, increasing resilience and fault tolerance, but often requiring more complex coordination.

![Comparison of Centralized and Distributed Network Architectures](figure/03/Centralized_vs_Distributed.png)

<!-- \label{fig:centralized-distributed} -->

### Broadcast Domains

A broadcast domain is a logical segment of a network in which all other devices receive any broadcast packet sent by a device within the same segment. In simpler terms, it is the set of all devices that will receive a broadcast frame originating from any one of them. Broadcast domains play a crucial role in network traffic management and performance, as broadcast messages can lead to congestion if they are not properly segmented.

Switches operate at Layer 2 of the OSI model and, by default, forward broadcast traffic to all ports within the same VLAN, except the port that originated the broadcast. This means that all devices connected to the switch will receive the broadcast unless specific configurations, such as VLANs or access control mechanisms, are applied.

![Broadcast Domains Separated by a Router: Each Switch Represents a Distinct Broadcast Domain](figure/03/Broadcast_Domains.png)

<!-- \label{fig:broadcast-domains} -->

Routers, on the other hand, function at Layer 3 and do not forward broadcast traffic across different interfaces. This makes routers natural boundaries for broadcast domains. When a broadcast frame reaches a router, it is dropped unless the router is specifically configured to relay it (e.g., in DHCP relay scenarios).

### Virtual LANs (VLANs)

A Virtual Local Area Network (VLAN) is a logical grouping of devices within a network that appear to be on the same local area network (LAN), even if they are not physically connected to the same switch or segment. VLANs are used to segment broadcast domains at the data link layer (Layer 2) of the OSI model. This allows network administrators to partition a single physical switch into multiple logical networks, improving performance, security, and manageability.

When devices are assigned to different VLANs, they cannot directly communicate with each other unless routing is enabled between the VLANs, typically through a router or a Layer 3 switch. This segmentation ensures that broadcast traffic remains within the VLAN, preventing it from flooding the entire switch and affecting unrelated devices.

VLANs are configured using VLAN IDs, and network ports on switches can be statically assigned to specific VLANs or dynamically assigned through protocols such as VLAN Management Policy Server (VMPS). Trunk ports are used to carry traffic for multiple VLANs between switches, utilizing tagging protocols such as IEEE 802.1Q.

![VLAN segmentation: Devices are separated into distinct broadcast domains](figure/03/VLAN_Diagram.png)

<!-- \label{fig:vlan-segmentation} -->

**Key benefits of VLANs include:**

* Enhanced network segmentation and traffic isolation
* Improved security by separating sensitive departments or systems
* Simplified network management and flexibility
* Reduced broadcast traffic within each VLAN

Overall, VLANs are a foundational tool in modern network design, particularly in enterprise environments, enabling efficient and scalable network segmentation without the need for physical device separation.

---
