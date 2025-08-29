# Charpter 5 LAN Design and Implementation

## Subtopics

* VLAN concept and benefits
* Creating and assigning VLANs
* Inter-VLAN routing
* Reducing broadcast domains

## Learning Objectives

* Understand VLANs and their role in network segmentation.
* Configure VLANs on switches and assign ports.
* Implement communication between different VLANs.
* Learn how VLANs limit broadcast domains and improve performance.

## Introduction to Cisco IOS

Cisco IOS (Internetwork Operating System) is the software that runs on Cisco routers and switches. It provides a command-line interface (CLI) used for configuring and managing network devices.

### Access Methods

* **Console:** Local access via serial cable, used for initial setup.
* **Telnet:** Remote access over the network (unencrypted, not recommended).
* **SSH:** Secure remote access using encryption, preferred for production.

### Command Modes

* **User EXEC Mode (`Switch>` )** – Basic commands, limited access.
* **Privileged EXEC Mode (`Switch#`)** – Access to all monitoring and config commands.
* **Global Configuration Mode (`Switch(config)#`)** – System-wide settings.
* **Interface Configuration Mode (`Switch(config-if)#`)** – Port/interface-specific settings.

### Basic Cisco IOS Command Explanation

This sequence configures a specific switch port (FastEthernet0/1) as an access port and assigns it to VLAN 10. This setup is commonly used to connect end devices such as PCs or printers to a specific VLAN.

* **enable**
  **Format:** `enable`
  **Meaning:** Enters Privileged EXEC mode from User EXEC mode.
  **Usage Example:**

  ```
  Switch> enable
  Switch#
  ```

* **configure terminal**
  **Format:** `configure terminal`
  **Meaning:** Enters Global Configuration mode to allow system changes.
  **Usage Example:**

  ```
  Switch# configure terminal
  Switch(config)#
  ```

* **interface FastEthernet0/1**
  **Format:** `interface [type][slot/port]`
  **Meaning:** Targets the specific interface for configuration.
  **Usage Example:**

  ```
  Switch(config)# interface FastEthernet0/1
  Switch(config-if)#
  ```

* **switchport mode access**
  **Format:** `switchport mode access`
  **Meaning:** Forces the port to operate in access mode (not trunk mode).
  **Usage Example:**

  ```
  Switch(config-if)# switchport mode access
  ```

* **switchport access vlan 10**
  **Format:** `switchport access vlan [vlan-id]`
  **Meaning:** Assigns the interface to VLAN 10, placing connected devices in that VLAN.
  **Usage Example:**

  ```
  Switch(config-if)# switchport access vlan 10
  ```

* **end**
  **Format:** `end`
  **Meaning:** Exits configuration mode and returns to Privileged EXEC mode.
  **Usage Example:**

  ```
  Switch(config-if)# end
  Switch#
  ```

**Complete Example:**

```
Switch> enable
Switch# configure terminal
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# end
Switch#
```

## Switch Configuration Concepts

### Hostname and Port Settings

This section explains how to configure a switch's hostname and a specific FastEthernet port with basic operational parameters such as description, speed, and duplex settings.

* **hostname SW1**
  **Format:** `hostname [device-name]`
  **Meaning:** Sets the device's name. Useful for identification in network environments.
  **Usage Example:**

  ```
  Switch(config)# hostname SW1
  SW1(config)#
  ```

* **interface FastEthernet0/1**
  **Format:** `interface [type][slot/port]`
  **Meaning:** Enters configuration mode for the specified port.
  **Usage Example:**

  ```
  SW1(config)# interface FastEthernet0/1
  SW1(config-if)#
  ```

* **description Connected to PC1**
  **Format:** `description [text]`
  **Meaning:** Adds a label to the interface for documentation purposes.
  **Usage Example:**

  ```
  SW1(config-if)# description Connected to PC1
  ```

* **speed 100**
  **Format:** `speed [10|100|1000]`
  **Meaning:** Sets the speed of the interface in Mbps.
  **Usage Example:**

  ```
  SW1(config-if)# speed 100
  ```

* **duplex full**
  **Format:** `duplex [half|full|auto]`
  **Meaning:** Sets the duplex mode for the interface.
  **Usage Example:**

  ```
  SW1(config-if)# duplex full
  ```

* **no shutdown**
  **Format:** `no shutdown`
  **Meaning:** Enables the port (brings it up administratively).
  **Usage Example:**

  ```
  SW1(config-if)# no shutdown
  ```

**Complete Example:**

```
Switch> enable
Switch# configure terminal
Switch(config)# hostname SW1
SW1(config)# interface FastEthernet0/1
SW1(config-if)# description Connected to PC1
SW1(config-if)# speed 100
SW1(config-if)# duplex full
SW1(config-if)# no shutdown
SW1(config-if)# end
SW1#
```

## VLAN Concept and Benefits

### What is a VLAN?

A **Virtual Local Area Network (VLAN)** is a logical grouping of network devices that allows them to communicate as if they were on the same physical LAN, even if they are connected to different switches. VLANs enable administrators to partition a single physical network into multiple distinct broadcast domains.

VLANs operate at **Layer 2 (Data Link Layer)** of the OSI model. They utilize frame tagging, typically through the IEEE 802.1Q standard, to identify and segregate traffic for different VLANs across trunk links.

### Benefits of VLANs

1. **Network Segmentation**
   VLANs enable the logical grouping of devices based on function or department, rather than physical location. For example:

   * VLAN 10: HR Department
   * VLAN 20: Finance Department
   * VLAN 30: IT Department

   This segmentation enhances traffic management and organizational clarity.

2. **Security**
   VLANs isolate broadcast traffic between groups. Devices in one VLAN cannot directly access those in another without explicit inter-VLAN routing, providing basic layer-2 level security. Sensitive departments (e.g., Finance) can be shielded from general access.

3. **Reduced Broadcast Traffic**
   Each VLAN is a separate broadcast domain. Broadcasts sent in one VLAN do not propagate to others, reducing unnecessary traffic and minimizing the risk of broadcast storms.

4. **Flexibility and Mobility**
   Network administrators can assign VLANs based on user roles, regardless of the user's physical location within the building. A user who moved from one desk to another can still belong to the same VLAN by reassigning the switch port.

5. **Improved Performance and Manageability**
   By reducing the size of broadcast domains and isolating traffic, VLANs improve switch performance and simplify troubleshooting. Network policies and Quality of Service (QoS) configurations are also easier to apply within distinct Virtual Local Area Networks (VLANs).

### Example Scenario

Consider a three-floor office building:

* Floor 1: HR — VLAN 10
* Floor 2: Sales — VLAN 20
* Floor 3: IT — VLAN 30

Without VLANs, all devices share the same broadcast domain, leading to congestion and potential data exposure. With VLANs configured, traffic is isolated per department, reducing overhead and enhancing security.

### VLAN Configuration

This command sequence is used to create VLAN 10 with the name "SALES" and assign interface `FastEthernet0/1` to it. VLANs (Virtual Local Area Networks) allow logical segmentation of network traffic within switches.

* **vlan 10**
  **Format:** `vlan [vlan-id]`
  **Meaning:** Creates VLAN 10 if it does not already exist and enters VLAN configuration mode.
  **Usage Example:**

  ```
  Switch(config)# vlan 10
  Switch(config-vlan)#
  ```

* **name SALES**
  **Format:** `name [vlan-name]`
  **Meaning:** Assigns a descriptive name "SALES" to VLAN 10.
  **Usage Example:**

  ```
  Switch(config-vlan)# name SALES
  ```

* **interface FastEthernet0/1**
  **Format:** `interface [type][slot/port]`
  **Meaning:** Selects the interface to configure.
  **Usage Example:**

  ```
  Switch(config)# interface FastEthernet0/1
  Switch(config-if)#
  ```

* **switchport mode access**
  **Format:** `switchport mode access`
  **Meaning:** Configures the interface to operate as an access port.
  **Usage Example:**

  ```
  Switch(config-if)# switchport mode access
  ```

* **switchport access vlan 10**
  **Format:** `switchport access vlan [vlan-id]`
  **Meaning:** Assigns the interface to VLAN 10.
  **Usage Example:**

  ```
  Switch(config-if)# switchport access vlan 10
  ```

**Complete Example:**

```
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name SALES
Switch(config-vlan)# exit
Switch(config)# interface FastEthernet0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# end
Switch#
```

### Verification Commands

The following commands help verify VLAN setup, interface states, MAC address learning, and the active configuration of a switch.

* `show vlan brief` – Displays all configured VLANs and associated ports.

  ```
  Switch# show vlan brief
  VLAN Name                             Status    Ports
  ---- -------------------------------- --------- -------------------------------
  1    default                          active    Fa0/1, Fa0/2, Fa0/3
  10   SALES                            active    Fa0/4
  20   HR                               active    Fa0/5
  ```

* `show interfaces status` – Lists each port’s current status, VLAN, duplex, speed, and type.

  ```
  Switch# show interfaces status
  Port    Name               Status       Vlan       Duplex  Speed Type
  Fa0/1                      connected    10         a-full  a-100 10/100BaseTX
  Fa0/2                      notconnect   1          auto    auto  10/100BaseTX
  ```

* `show mac address-table` – Displays the MAC address forwarding table.

  ```
  Switch# show mac address-table
            Mac Address Table
  -------------------------------------------
  Vlan    Mac Address       Type        Ports
  ----    -----------       --------    -----
    10    00E0.F7B2.3A6B    DYNAMIC     Fa0/1
    20    0012.D45E.8A0C    DYNAMIC     Fa0/5
  ```

* `show running-config` – Shows the currently running configuration.

  ```
  Switch# show running-config
  !
  hostname SW1
  interface FastEthernet0/1
   switchport mode access
   switchport access vlan 10
  !
  vlan 10
   name SALES
  ```

## Creating and Assigning VLANs

### Creating VLANs on a Switch (Cisco CLI Example)

To define VLANs on a managed switch, use the following commands in global configuration mode:

```
Switch(config)# vlan 10
Switch(config-vlan)# name HR
Switch(config)# vlan 20
Switch(config-vlan)# name IT
```

Each VLAN is assigned a unique ID and an optional name for easier management and identification.

### Assigning Ports to VLANs

After creating VLANs, individual switch ports can be assigned to specific VLANs. This ensures that devices connected to those ports belong to the appropriate logical segment.

**Example:** Assign port FastEthernet 0/1 to VLAN 10:

```
Switch(config)# interface FastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

Repeat similar steps for other ports and VLANs as needed.

### Verifying VLAN Configuration

To check which VLANs are configured and which ports are assigned to each VLAN, use:

```
Switch# show vlan brief
```

This command displays a summary of all VLANs, including VLAN ID, name, and the ports associated with each.

### Trunk Port Setup

This configuration enables trunking on interface `FastEthernet0/24`, allowing it to carry traffic for multiple VLANs (in this case, VLANs 10 and 20). Trunk ports are typically used to connect switches to other switches or to routers performing inter-VLAN routing.

* **interface FastEthernet0/24**
  **Format:** `interface [type][slot/port]`
  **Meaning:** Selects the specified interface for configuration.
  **Usage Example:**

  ```
  Switch(config)# interface FastEthernet0/24
  Switch(config-if)#
  ```

* **switchport trunk encapsulation dot1q**
  **Format:** `switchport trunk encapsulation [isl|dot1q|negotiate]`
  **Meaning:** Specifies IEEE 802.1Q as the trunking encapsulation protocol.
  **Note:** This command may be required only on certain switch models that support multiple encapsulation types.
  **Usage Example:**

  ```
  Switch(config-if)# switchport trunk encapsulation dot1q
  ```

* **switchport mode trunk**
  **Format:** `switchport mode trunk`
  **Meaning:** Sets the interface to operate in trunk mode, allowing multiple VLANs.
  **Usage Example:**

  ```
  Switch(config-if)# switchport mode trunk
  ```

* **switchport trunk allowed vlan 10,20**
  **Format:** `switchport trunk allowed vlan [vlan-list]`
  **Meaning:** Restricts the trunk to carry only the specified VLANs (10 and 20).
  **Usage Example:**

  ```
  Switch(config-if)# switchport trunk allowed vlan 10,20
  ```

**Complete Example:**

```
Switch# configure terminal
Switch(config)# interface FastEthernet0/24
Switch(config-if)# switchport trunk encapsulation dot1q
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20
Switch(config-if)# end
Switch#
```

## Broadcast Domains

### Broadcast Domain Explained

A **broadcast domain** refers to a logical division of a computer network where any broadcast sent by one device is received by all other devices within the same domain. Broadcasts are used by devices to locate others (e.g., through ARP requests or DHCP discovery), but in large or flat networks, excessive broadcast traffic can lead to congestion and degraded performance.

In traditional Ethernet networks without segmentation, all devices connected to the same switch or set of interconnected switches belong to a single broadcast domain. This means that every broadcast frame is propagated to all devices, even if the broadcast is not relevant to them.

### How VLANs Reduce Broadcast Domains

VLANs address this issue by creating **separate broadcast domains at Layer 2**. When a VLAN is assigned to a switch port, the device connected to that port becomes part of a specific broadcast domain. Broadcasts are then limited to devices within that VLAN only.

* Devices in **VLAN 10** will only receive broadcasts from other devices in VLAN 10.
* Devices in **VLAN 20** are isolated from broadcasts in VLAN 10.

This segmentation significantly reduces the scope of broadcast traffic and prevents it from affecting the entire network.

### Benefits of Reducing Broadcast Domains

1. **Improved Network Performance**
   Smaller broadcast domains reduce unnecessary traffic on the network, conserving bandwidth and improving response times for applications.

2. **Enhanced Security and Isolation**
   Broadcast traffic from one department (e.g., HR) cannot be intercepted by another (e.g., Guest Wi-Fi), minimizing potential attack surfaces.

3. **Simplified Troubleshooting and Monitoring**
   With broadcast domains confined to VLANs, it becomes easier to pinpoint and isolate network issues to specific segments.

4. **Scalability**
   As organizations grow, VLANs help keep broadcast traffic manageable by dividing the network into well-defined zones.

### Example Scenario

Consider a network without VLANs where 100 devices share the same broadcast domain. Each broadcast frame is delivered to all 100 devices. As more devices are added, the number of broadcasts increases, creating congestion.

With VLANs:

* VLAN 10 (HR): 30 devices
* VLAN 20 (Sales): 30 devices
* VLAN 30 (IT): 40 devices

Now, a broadcast in VLAN 10 is only received by 30 devices instead of all 100. The result is more efficient communication, lower CPU usage on endpoints, and a more stable network.

## Example: Dumbbell Network Topology

### What is a Dumbbell Topology?

A **dumbbell topology** is a simple network design that illustrates segmentation and broadcast domain boundaries. It consists of two groups of devices (representing the “weights”) connected through a pair of switches (the “bar” of the dumbbell). This topology is particularly useful for demonstrating the impact of VLAN configuration on traffic isolation.

### Scenario Without VLANs

```
[PC1, PC2] --- Switch1 === Switch2 --- [PC3, PC4]
```

In this flat network:

* All four PCs are in the same broadcast domain.
* A broadcast sent by PC1 will reach PC4 and all other devices, even if they are not relevant to the communication.
* This setup can lead to congestion, increased CPU usage, and potential security risks.

### Scenario With VLANs

To segment the network, we configure VLANs as follows:

**Switch1:**

* Assign PC1 and PC2 to **VLAN 10**.

**Switch2:**

* Assign PC3 and PC4 to **VLAN 20**.

A trunk link between Switch1 and Switch2 allows VLAN-tagged traffic to pass between them while preserving VLAN separation.

```latex
\begin{figure}[h]
    \centering
    \begin{tikzpicture}[
        device/.style={draw, rectangle, minimum width=1.8cm, minimum height=1cm, align=center},
        vlan10/.style={fill=blue!20},
        vlan20/.style={fill=red!20},
        link/.style={-Latex, thick},
        trunk/.style={-Latex, thick, dashed},
        node distance=1cm and 1.5cm
    ]

    % Switches
    \node[device] (sw1) {Switch 1};
    \node[device, right=of sw1] (sw2) {Switch 2};

    % PCs on Switch 1 - VLAN 10
    \node[device, vlan10, above left=of sw1] (pc1) {PC1\\VLAN 10};
    \node[device, vlan10, below left=of sw1] (pc2) {PC2\\VLAN 10};

    % PCs on Switch 2 - VLAN 20
    \node[device, vlan20, above right=of sw2] (pc3) {PC3\\VLAN 20};
    \node[device, vlan20, below right=of sw2] (pc4) {PC4\\VLAN 20};

    % Connections to Switch 1
    \draw[link] (pc1) -- (sw1);
    \draw[link] (pc2) -- (sw1);

    % Connections to Switch 2
    \draw[link] (pc3) -- (sw2);
    \draw[link] (pc4) -- (sw2);

    % Trunk Link
    \draw[trunk] (sw1) -- node[above]{Trunk Link (VLAN 10, 20)} (sw2);

    \end{tikzpicture}
\end{figure}
```

**Result:**

* PC1's broadcast traffic remains within VLAN 10 and does not reach VLAN 20.
* PC3 and PC4 do not receive broadcasts from PC1 or PC2.
* This improves performance and limits the scope of broadcast domains.

### Cisco CLI Configuration Steps

**Step 1: Create VLANs on both switches**

```
Switch(config)# vlan 10
Switch(config-vlan)# name HR
Switch(config)# vlan 20
Switch(config-vlan)# name IT
```

**Step 2: Assign switch access ports**

**On Switch1 (PC1 and PC2 on ports Fa0/1 and Fa0/2):**

```
Switch(config)# interface FastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Switch(config)# interface FastEthernet 0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

**On Switch2 (PC3 and PC4 on ports Fa0/1 and Fa0/2):**

```
Switch(config)# interface FastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
Switch(config-if)# exit

Switch(config)# interface FastEthernet 0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20
```

**Step 3: Configure the trunk link between the switches**

**Assume trunk link is on port Fa0/24 on both switches:**

**On Switch1:**

```
Switch(config)# interface FastEthernet 0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20
```

**On Switch2:**

```
Switch(config)# interface FastEthernet 0/24
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan 10,20
```

**Step 4: Verify Configuration**

```
Switch# show vlan brief
Switch# show interfaces trunk
```

These commands verify VLAN memberships and the status of trunk ports.

### Summary

The dumbbell topology helps visualize VLAN segmentation:

* VLANs prevent unnecessary traffic from flooding the entire network.
* Broadcasts are limited to their assigned VLANs, forming separate broadcast domains.
* Using trunk ports, switches can pass multiple VLANs while maintaining separation.

VLANs in dumbbell topologies improve **efficiency**, **security**, and **manageability** of modern enterprise networks.
