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

> **Conclusion:** The Switch is "smarter" because it maintains a MAC Address Table, whereas the Hub simply repeats the signal to all ports.
