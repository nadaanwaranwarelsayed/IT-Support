## Section: Environment Setup & Virtualization
1. Virtual Machine Configuration (Windows Server 2022)
In this stage, I initialized the virtual environment using Oracle VirtualBox. The goal was to create a clean, manual installation to have full control over the configuration process.

VM Name: WinServer2022-DC (Dedicated as the Primary Domain Controller).

Installation Method: Manual (Skipped Unattended Installation) to ensure custom role deployment and security configuration from scratch.
<img width="1011" height="502" alt="1" src="https://github.com/user-attachments/assets/9a060f53-36eb-4cc8-9bdb-f6d4b406d556" />

## Hardware Resource Allocation
To ensure the stability of the Windows Server 2022 environment, I have allocated resources based on the recommended specifications for a Desktop Experience deployment:

Base Memory: 4096 MB (4 GB). This allows the OS to handle Active Directory Domain Services (AD DS) and DNS roles efficiently without performance bottlenecks.

Processors: 2 CPUs. Allocated to provide better responsiveness during multi-tasking and management console operations.

Virtual Disk Size: 50 GB. Sufficient for OS files, local databases, and future Active Directory objects (Users, Groups, OUs).
<img width="1034" height="417" alt="2" src="https://github.com/user-attachments/assets/8d36f3f7-783e-47ea-ac64-2ebc470019aa" />

## Before launching the installation
here is a summary of the virtual hardware and system settings configured for the Domain Controller.

<img width="1036" height="500" alt="3" src="https://github.com/user-attachments/assets/914ba0b0-511b-4458-b10b-16d99e88ea48" />


## Post-Creation Configuration: Network Isolation
After finishing the initial VM creation wizard, it is critical to configure the network architecture before the first boot. This ensures the environment is properly isolated and ready for domain services.

Steps Taken:

Accessing Settings: Right-clicked on the WinServer2022-DC virtual machine and selected Settings.

Network Adapter Setup: Navigated to the Network tab , expert tab to modify the default connectivity.

Configuring Internal Network: Changed the "Attached to" option from NAT to Internal Network.

Defining the Lab LAN: Named the internal network LabNetwork.

Why this step is mandatory:

Isolation: It prevents the virtual Windows Server from interacting with the physical home network (Host), avoiding potential conflicts with the local router's DHCP.

Connectivity: It creates a dedicated virtual switch (LAN) where the Domain Controller and future Client machines (Windows 10) can communicate securely using static IPs.

<img width="979" height="643" alt="4" src="https://github.com/user-attachments/assets/4fb9ea51-058c-45f0-8517-0f1966042b85" />











