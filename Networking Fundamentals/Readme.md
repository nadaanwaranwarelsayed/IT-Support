
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

ip route 192.168.1.0 255.255.255.0 180.170.1.1  # Path to Subnet 0

ip route 172.16.0.0 255.255.255.0 160.150.1.9   # Path to Subnet 2

Router 2:

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
## 🚀 Lab 07: Site-to-Site Enterprise Network & OSPF Routing
Two-Branch Infrastructure with Dynamic OSPF Routing and VLSM Optimization

## 📌 Project Overview
This project involves the design and implementation of a scalable enterprise network connecting two main branches: Smouha Branch and the Head Office. The system is engineered using Cisco 2911 routers to ensure seamless data flow through the OSPF (Open Shortest Path First) dynamic routing protocol. The infrastructure focuses on VLSM (Variable Length Subnet Masking) to optimize IP address allocation, specifically using /30 subnets for point-to-point wide area network (WAN) links.

## 🏗 Network Topology (Architecture)
The network utilizes a Point-to-Point topology between the branches, ensuring a dedicated and efficient path for inter-branch communication.

<img width="402" height="412" alt="Site-to-Site OSPF Topology" src="https://github.com/user-attachments/assets/64937766-650c-4a60-a6d3-ee1c219bbf8e" />


Description: Diagram showing the interconnection between Smouha Branch (R1) and Head Office (R2).

## 🛠 Configuration Steps & Implementation

1. Local Area Network (LAN) Configuration
Two distinct subnets were established to represent the internal infrastructure of each branch:

Smouha Branch (LAN 0):

Subnet: 192.168.1.0/24

Host PC (PC0): 192.168.1.10

Default Gateway: 192.168.1.1 (Configured on R1 G0/0)

Head Office (LAN 1):

Subnet: 192.168.2.0/24

Host PC (PC4): 192.168.2.10

Default Gateway: 192.168.2.1 (Configured on R2 G0/0)

2. Router Interface Configuration (Point-to-Point WAN Link)
The WAN link was configured using a /30 subnet to maximize IP efficiency for the router-to-router connection:

Link (Smouha ↔ Head Office): Subnet 10.0.0.0/30

Interface IP (R1 G0/1): 10.0.0.1

Interface IP (R2 G0/1): 10.0.0.2

Subnet Mask: 255.255.255.252

3. Dynamic Routing Implementation (OSPF)
To automate route discovery and ensure network scalability, OSPF Area 0 was implemented on both routers:

Smouha Router (R1):
CLI :
router ospf 1

network 192.168.1.0 0.0.0.255 area 0

network 10.0.0.0 0.0.0.3 area 0

Head Office Router (R2):

CLI :
router ospf 1

network 192.168.2.0 0.0.0.255 area 0

network 10.0.0.0 0.0.0.3 area 0
 
<img width="770" height="480" alt="OSPF Routing Table Verification" src="https://github.com/user-attachments/assets/ee1e695a-0ef1-481d-8b1a-f8dcefc8ebdd" />

This screenshot verifies that the OSPF protocol is active. The entries marked with 'O' indicate that the router has successfully learned the remote networks from its neighbor. 


## 🔍 Troubleshooting & Validation
During the validation phase, the following tests were conducted to ensure network integrity:

Adjacency Check: Verified that OSPF neighbors reached the "FULL" state, allowing for successful routing table exchange.

Convergence: Used the "Fast Forward Time" feature in Packet Tracer to speed up OSPF Hello packet exchange and synchronization.

Route Verification: Confirmed that the remote LAN subnets were correctly injected into the routing table with the "O" designator.

Final Testing Results:

<img width="621" height="298" alt="ping dynamic routing" src="https://github.com/user-attachments/assets/6b7aee33-46f0-4a77-9b6f-c587a78a8f22" />


ICMP Connectivity (Ping): ✅ Successful replies from PC0 (Smouha) to PC4 (Head Office) with 0% loss.

<img width="504" height="158" alt="tracert dynamic routing" src="https://github.com/user-attachments/assets/71012d50-c722-4252-9b65-55076ae5d384" />


Path Tracing (Tracert): ✅ Confirmed the data path through 3 hops: Gateway ➡️ WAN Link ➡️ Remote Host.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🚀 Lab 08: Distributed Enterprise Mesh & Advanced OSPF Routing
Full-Mesh Triangle Infrastructure with Multi-Branch Services (DHCP, DNS, HTTP)

## 📌 Project Overview
This project demonstrates the design of a highly redundant enterprise network connecting three main branches in Alexandria (Smouha, Miami, and Centre). The architecture utilizes a Full-Mesh Triangle Topology to ensure multiple paths for data flow, managed by the OSPF dynamic routing protocol. The project focuses on "Distributed Services," where network functions (DNS and HTTP) are strategically placed across different branches to simulate a real-world enterprise environment.

## 🏗 Network Topology (Architecture)
The network is built using three Cisco routers connected in a triangle formation. This design ensures that if any single WAN link fails, OSPF will automatically reroute traffic through the alternative path.


<img width="690" height="651" alt="Triangle-Mesh-Topology-Overview" src="https://github.com/user-attachments/assets/2c711c58-e842-456f-9a54-68b17ee3c33d" />


Description: Full-Mesh interconnection between Smouha, Miami, and Centre routers with active OSPF adjacencies.

## 🛠 Configuration Steps & Implementation

1. VLSM & IP Addressing Scheme
To maximize efficiency, VLSM was applied using /30 subnets for the point-to-point WAN links, providing exactly 2 usable IPs per link:

Link Smouha ↔ Miami: 10.0.0.0/30 (IPs: .1, .2)

Link Miami ↔ Centre: 10.0.0.4/30 (IPs: .5, .6)

Link Centre ↔ Smouha: 10.0.0.8/30 (IPs: .9, .10)

2. Distributed Application Services
Unlike centralized designs, services were distributed across branches to optimize resource allocation:

Smouha Branch: Hosts the HTTP Web Server (192.168.10.50) containing the project's landing page.

Miami Branch: Hosts the Centralized DNS Server (192.168.20.50) responsible for resolving www.nada.com.

<img width="791" height="524" alt="DNS-Record-Configuration" src="https://github.com/user-attachments/assets/8a94129d-d9d9-4ab0-b3b5-13dd4691735d" />


All Branches: Each branch has a local DHCP Pool configured to provide Gateway and the global DNS IP (192.168.20.50) to all end-devices.

3. Dynamic Routing (OSPF Area 0)
OSPF was implemented to automate route discovery. Wildcard masks were carefully calculated to match the /30 WAN links (0.0.0.3) and /24 LANs (0.0.0.255).

Sample Configuration (Smouha Router):

CLI :

router ospf 1

network 192.168.10.0 0.0.0.255 area 0

network 10.0.0.0 0.0.0.3 area 0

network 10.0.0.8 0.0.0.3 area 0


<img width="801" height="508" alt="OSPF-Routing-Table-Verification" src="https://github.com/user-attachments/assets/7f42de51-760f-4420-8982-753398d34440" />



## 🔍 Troubleshooting & Validation

Several critical network challenges were addressed during the testing phase:

IP Conflict Resolution: Resolved a Duplicate Address error on the Miami-Smouha link by re-assigning unique IPs within the /30 range.

DNS Latency/Timeout: Fixed a "DNS Request Timed Out" issue by correcting the DNS server IP in the DHCP scopes from .100 to the actual server IP .50.

Routing Path Verification: Confirmed that traffic from the Centre Branch can reach the Smouha Web Server using the OSPF-learned paths.

Final Testing Results:


<img width="783" height="475" alt="DNS-Resolution-Test ,End-to-End-Connectivity-Ping " src="https://github.com/user-attachments/assets/8c5a4cac-42b9-4fc9-97fa-0d505f58ad5e" />

ICMP Connectivity: ✅ 100% success rate in Pings across all branches.
DNS Resolution: ✅ nslookup www.nada.com correctly resolves to the Smouha Server IP (192.168.10.50).


<img width="805" height="522" alt="Web-Service-Final-Verification" src="https://github.com/user-attachments/assets/2a24a8d7-8757-462e-bdc1-d80c038ead40" />


Web Services: ✅ The "Welcome to Nada's Network" HTML page loads successfully on all remote workstations.
































