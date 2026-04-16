<img width="783" height="548" alt="web browser test" src="https://github.com/user-attachments/assets/0084ec1a-eaff-4948-8df5-a45636cdafeb" /># Networking Fundamentals 🌐

## Lab 01: Basic Connectivity (Handshake)
In this lab, I established a connection between two PCs to test the basic networking concepts.

### Task Objectives:
* Use the correct cable type (**Copper Cross-over**).
* Assign Static IP addresses in the same subnet.
* Verify connectivity using the `ping` command.

### Results:
<img width="931" height="562" alt="01_Basic_PC_Connectivity" src="https://github.com/user-attachments/assets/dc392031-ec69-4106-a91f-a990c7317181" />


> **Note:** The ping was successful with 0% packet loss, confirming that Layer 1, 2, and 3 are working correctly.
------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Lab 02: Hub vs. Switch Comparison (Broadcast vs. Unicast)
In this lab, I compared the data transmission behavior of a **Hub** and a **Switch** using the Packet Tracer Simulation mode.

### Task Objectives:
* Build two separate networks: one using a **Hub** and another using a **Switch**.
* Observe how each device handles incoming data packets.
* Verify the difference between **Broadcast** and **Unicast** traffic.

### Simulation Results:
<img width="967" height="759" alt="02_Hub_vs_Switch_Comparison" src="https://github.com/user-attachments/assets/844763fd-80ef-4b7a-9826-a300bc693d43" />

### Key Observations:
* **The Hub (Left):** When PC0 sent a message, the Hub flooded it to **all connected devices** (Broadcast). Devices that were not the intended destination rejected the packet (indicated by the red X).
* **The Switch (Right):** After learning the MAC addresses via ARP, the Switch sent the message **directly to the target device** (Unicast), making the communication more efficient and secure.
* **Collision Domains (Hub):** Operates within a **single collision domain**; only one device can transmit at a time, or a collision occurs.
* **Collision Domains (Switch):** Each port is a **separate collision domain**, allowing simultaneous, interference-free communication.
> **Conclusion:** The Switch is "smarter" because it maintains a MAC Address Table, whereas the Hub simply repeats the signal to all ports.
------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Lab 03: Network Automation - Implementing DHCP Server
In this lab, I transitioned from manual IP configuration to dynamic management by implementing a **DHCP Server**. This approach minimizes errors and automates address assignment for all network hosts.

### Task Objectives:
* Deploy a dedicated **Server-PT** to act as the central authority for IP management.
* Configure a **DHCP Pool** with a specific address range and lease limits.
* Transition end-devices (PCs) from **Static** to **Dynamic** IP addressing.

### Server Configuration:
I configured the DHCP pool to start from `192.168.1.101`, reserving the lower range for infrastructure devices (like Routers and Switches).

<img width="743" height="453" alt="03_DHCP_Server_Configuration" src="https://github.com/user-attachments/assets/5caab964-855b-4602-ac4d-89120d1bda9d" />



### Key Configurations:
* **Start IP Address:** `192.168.1.101` (Reserved `1-100` for static management).
* **Subnet Mask:** `255.255.255.0` (Class C network).
* **Max Users:** `154` (Calculated based on the available range within the subnet: 254 - 101 + 1).

> **Technical Note:** While the default setting shows 254 or more users, I manually adjusted it to reflect the physical limits of a /24 subnet and my specific reservation plan, ensuring a clean and conflict-free IP environment.

### Results:
<img width="1038" height="541" alt="03_DHCP_Verification_PC0" src="https://github.com/user-attachments/assets/a1277c25-6ea4-4ea1-8b49-a17d0aaae76e" />

### Verification & Connectivity Test:
* Verified that **PC0** successfully leased the first available IP (`192.168.1.101`) from the server.
* Performed a **Ping test** between the dynamic hosts to ensure that internal routing within the VLAN is fully operational.

> **Final Result:** The implementation was successful, providing a reliable and automated addressing solution for the local network.
------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Lab 04: Full Network Services Integration (DHCP, DNS, & HTTP)
In this lab, I integrated three essential network services into a single server to simulate a real-world local network environment. The objective was to demonstrate how these services collaborate to provide a seamless user experience.

### Task Objectives:
* **DHCP:** Automate IP assignment and distribute DNS server information to clients.
* **DNS:** Map the domain `nada.com` to the server's static IP address.
* **HTTP:** Host a custom web page accessible via the domain name.

### Implementation & Verification:
The following image captures the complete integrated setup:
1. **Infrastructure:** A central switch connecting the server and three PCs.
2. **DNS Configuration:** An `A Record` was created for `nada.com` pointing to `192.168.1.100`.
3. **End-to-End Success:** The Web Browser on **PC0** successfully loads the custom page using the domain name instead of the IP address.

<img width="1500" height="502" alt="04_Integrated_Network_Services" src="https://github.com/user-attachments/assets/c554c37a-a9e5-44f5-bb72-15dfead47b0b" />

> **Final Outcome:** This lab proves the transition from basic connectivity to a functional service-based network. The integration allows users to access resources intuitively without needing to know the underlying technical IP addresses.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Lab 05: Inter-Networking with a Single Router and DHCP

## Project Overview
This project demonstrates the fundamental concepts of connecting two distinct Local Area Networks (LANs) using a Cisco Router. The goal was to enable communication between different IP subnets while automating IP address assignment using dedicated DHCP servers for each network.

## Network Topology
- **Network A:** `192.168.1.0/24` (Subnet for PCs and Local Server)
- **Network B:** `10.0.0.0/24` (Subnet for PCs and Local Server)
- **Central Router:** Cisco 2911 ISR, acting as the Default Gateway for both networks.

## Key Features & Configurations
1. **Multi-Subnet Connectivity:** Established a physical and logical link between two different network addresses using a router.
2. **Default Gateway Implementation:** Configured specific router interfaces to act as the "exit point" for each network.
    - `GigabitEthernet 0/0`: 192.168.1.1
    - `GigabitEthernet 0/1`: 10.0.0.1
3. **Dynamic IP Assignment (DHCP):** Configured two DHCP servers to automatically provide IP addresses, Subnet Masks, and Default Gateway info to end devices.
4. **CLI Configuration:** Utilized the Cisco Command Line Interface (CLI) to manage interfaces and bring the ports up using the `no shutdown` command.
<img width="651" height="565" alt="router-cli-config" src="https://github.com/user-attachments/assets/353fb930-6321-43ba-bd4f-edfe03fe2493" />

## Verification
- Successfully performed a **Ping** test from a PC in Network A (`192.168.1.x`) to a PC in Network B (`10.0.0.x`).
- Initial packet loss (ARP resolution) followed by 100% successful ICMP replies.
<img width="1474" height="471" alt="Routing-Between-Two-Networks" src="https://github.com/user-attachments/assets/0655cf40-75fe-43cf-a6ce-3dba56dfa3e5" />

## Skills Learned
- Configuring Cisco Router Interfaces via CLI.
- Understanding the role of the Default Gateway in routing.
- Troubleshooting APIPA (169.254.x.x) issues by refreshing DHCP leases.


------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🚀 Lab 06: Multi-Network Infrastructure & Services Design
Three-Router Mesh Topology with Static Routing, DHCP, DNS, and HTTP Services

## 📌 Project Overview
This project involves the design and implementation of a comprehensive network infrastructure connecting three distinct local area networks (LANs) using Cisco 2911 routers. The system is engineered to provide automated IP addressing (DHCP), domain name resolution (DNS), and web hosting (HTTP), ensuring seamless end-to-end connectivity across all subnets through manually configured Static Routes.

## 🏗 Network Topology (Architecture)
The network utilizes a Full Mesh Triangle Topology between the routers to ensure high availability and redundant paths.

<img width="838" height="606" alt="Static Routing" src="https://github.com/user-attachments/assets/6bb6d691-1dd1-4815-9b3c-7e60e101351a" />

Description: Diagram showing the 3-router interconnection with all links active (green).

## 🛠 Configuration Steps & Implementation
1. Local Area Network (LAN) & DHCP Setup
Three distinct subnets were created, each managed by a dedicated DHCP server to automate IP distribution for host devices:

Subnet 0 (192.168.1.0/24):

Server 0 (DNS/HTTP): 192.168.1.50 (Static)

DHCP Range: 192.168.1.51 - 192.168.1.254

Default Gateway: 192.168.1.1

Subnet 1 (10.0.0.0/24):

Server 1 (DHCP): 10.0.0.50 (Static)

DHCP Range: 10.0.0.51 - 10.0.0.254

Default Gateway: 10.0.0.1

Subnet 2 (172.16.0.0/24):

Server 2 (DHCP): 172.16.0.50 (Static)

DHCP Range: 172.16.0.51 - 172.16.0.254

Default Gateway: 172.16.0.1

Note: All end-devices (PCs) were toggled from Static to DHCP mode to refresh their IP leases and receive the updated Gateway and DNS parameters.

2. Router Interface Configuration (Point-to-Point Links)
The router interfaces were configured to establish the "highways" between the branches:

Link (R0 ↔ R1): Subnet 180.170.1.0/24 | Interface IPs: .1 & .2

Link (R0 ↔ R2): Subnet 150.140.0.0/24 | Interface IPs: .5 & .6

Link (R1 ↔ R2): Subnet 160.150.1.0/24 | Interface IPs: .8 & .9

3. Static Routing Implementation
To enable inter-VLAN communication, static routes were manually added to each router's routing table:

Router 0:
ip route 10.0.0.0 255.255.255.0 180.170.1.2    # Path to Subnet 1
ip route 172.16.0.0 255.255.255.0 150.140.0.6  # Path to Subnet 2
Router 1:
Bash
ip route 192.168.1.0 255.255.255.0 180.170.1.1  # Path to Subnet 0
ip route 172.16.0.0 255.255.255.0 160.150.1.9   # Path to Subnet 2
Router 2:
Bash
ip route 192.168.1.0 255.255.255.0 150.140.0.5  # Path to Subnet 0
ip route 10.0.0.0 255.255.255.0 160.150.1.8     # Path to Subnet 1
4. Application Layer Services (DNS & HTTP)
Web Hosting: HTTP and HTTPS services were enabled on Server 0 to host the www.nada.com domain.

Centralized DNS: Server 0 was configured as the primary DNS resolver for the entire infrastructure.

Global Configuration: The DNS IP 192.168.1.50 was propagated via DHCP across all three subnets, allowing any PC in the mesh to resolve the domain name.

## 🔍 Troubleshooting & Validation
During the implementation phase, several network issues were identified and resolved:

Inconsistent Addressing: Corrected subnet masks and network IDs to align with routing logic.

Default Gateway Omission: Fixed "Request Timeout" issues by assigning the proper router interface IP as the Default Gateway in the DHCP pools.

DNS Reachability: Resolved "DNS Request Timed Out" by ensuring Server 0 had a proper return path to all subnets and updating the DNS server field in remote DHCP scopes.

Service Sync: Toggled PCs from Static to DHCP to ensure they received updated DNS and Gateway settings.

Content Customization: Successfully edited the index.html file on Server 0 to display personalized project content via the Web Browser.

Final Testing Results:
ICMP Connectivity (Ping): ✅ Successful replies between all remote hosts.
<img width="939" height="513" alt="ping from PC0 to subnets PCs" src="https://github.com/user-attachments/assets/787fe8c4-f607-47aa-8c87-a411c2bb6c48" />

DNS Resolution (nslookup): ✅ www.nada.com successfully resolves to 192.168.1.50.
<img width="911" height="572" alt="DNS test from PC2" src="https://github.com/user-attachments/assets/5aa77a30-db2a-4ea8-9c74-ed5dc82698a9" />

Web Browser Verification: ✅ Website content successfully loads from all remote workstations.
<img width="783" height="548" alt="web browser test" src="https://github.com/user-attachments/assets/9d5d08f5-6cef-4a10-a286-5daf0398fb49" />

------------------------------------------------------------------------------------------------------------------------------------------------------------------













