# Networking Fundamentals 🌐

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
