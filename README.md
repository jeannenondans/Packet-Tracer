# Private Network Configuration with Subnets and VLANs
![image](https://github.com/user-attachments/assets/932c2d04-b7d0-44af-9b33-3bf377ab6787)

## 1. Network Design and Segmentation

The private **Class B** network `172.28.0.0/16` was used.  
From this network, subnets and VLANs were defined as follows:

### Subnets and VLANs
| **Subnet**  | **IP Range**           | **VLAN**          | **Gateway**           | **Devices and Assigned IPs**                  |
|-------------|------------------------|-------------------|-----------------------|-----------------------------------------------|
| Subnet 1    | 172.28.1.0 – 172.28.1.254 | VLAN 10 Users   | 172.28.1.1           | PCO: 172.28.1.10, PC1: 172.28.1.11            |
| Subnet 2    | 172.28.2.0 – 172.28.2.254 | VLAN 20 IT      | 172.28.2.1           | PC2: 172.28.2.10                              |
| Subnet 3    | 172.28.3.0 – 172.28.3.254 | VLAN 30 BILING  | 172.28.3.1           | PC3: 172.28.3.10, PC4: 172.28.3.11            |
| Subnet 4    | 172.28.4.0 – 172.28.4.254 | VLAN 40 Cservice | 172.28.4.1           | PC5: 172.28.4.11, PC6: 172.28.4.10            |
| Subnet 5    | 172.28.5.0 – 172.28.5.254 | VLAN 50 Server  | 172.28.5.1           | Server0: 172.28.5.100                         |

---

## 2. End Devices Configuration

Each device was configured with its respective IP address, subnet mask, and gateway:

| **Subnet**   | **Device**   | **Assigned IP**  | **Subnet Mask**       | **Gateway**          |
|--------------|--------------|------------------|-----------------------|----------------------|
| Subnet 1     | PCO          | 172.28.1.10      | 255.255.255.0         | 172.28.1.1          |
| Subnet 1     | PC1          | 172.28.1.11      | 255.255.255.0         | 172.28.1.1          |
| Subnet 2     | PC2          | 172.28.2.10      | 255.255.255.0         | 172.28.2.1          |
| Subnet 3     | PC3          | 172.28.3.10      | 255.255.255.0         | 172.28.3.1          |
| Subnet 3     | PC4          | 172.28.3.11      | 255.255.255.0         | 172.28.3.1          |
| Subnet 4     | PC5          | 172.28.4.11      | 255.255.255.0         | 172.28.4.1          |
| Subnet 4     | PC6          | 172.28.4.10      | 255.255.255.0         | 172.28.4.1          |
| Subnet 5     | Server0      | 172.28.5.100     | 255.255.255.0         | 172.28.5.1          |

---

## 3. Multilayer Switch Configuration

### Steps Performed:
1. **VLAN Creation**:  
   - VLAN 10 Users  
   - VLAN 20 IT  
   - VLAN 30 BILING  
   - VLAN 40 Cservice  
   - VLAN 50 Server  

2. **Port Assignment**:  
   The switch ports were configured to belong to their respective VLANs.

3. **Interface Configuration**:  
   Each VLAN was assigned an interface with an IP address to act as the gateway.

4. **IP Routing Enabled**:  
   IP routing was enabled on the multilayer switch to allow inter-VLAN communication and connectivity with the Router.

---

## 4. Router and Layer 2 Switch Configuration

### Router:
1. **Interface Configuration**:
   - The interface connected to the multilayer switch was configured with subinterfaces for each VLAN.
   - Each subinterface was assigned an IP address to serve as the gateway for the VLAN.

2. **IP Routing Enabled**:  
   Routing was enabled to facilitate communication between VLANs.

### Layer 2 Switch:
1. **VLAN Creation**:
   The required VLANs (10, 20, 30, 40, 50) were created.

2. **Port Assignment**:
   The Layer 2 switch ports were configured to match their corresponding VLANs for proper connectivity.

---

This repository documents the design and implementation of a segmented network with VLANs, detailing the configuration of end devices and network equipment.

