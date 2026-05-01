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

Promiscuous Mode was set to "Deny" to ensure network security and data privacy within the virtual LAN, preventing the adapter from capturing packets intended for other virtual machines.
Why this step is mandatory:

Isolation: It prevents the virtual Windows Server from interacting with the physical home network (Host), avoiding potential conflicts with the local router's DHCP.

Connectivity: It creates a dedicated virtual switch (LAN) where the Domain Controller and future Client machines (Windows 10) can communicate securely using static IPs.

<img width="979" height="643" alt="4" src="https://github.com/user-attachments/assets/4fb9ea51-058c-45f0-8517-0f1966042b85" />

## Initializing Windows Server Installation
Booting the ISO: After clicking Start, a black screen appeared. I quickly pressed Space to boot from the attached ISO file.

Regional Settings: In the first setup screen, I kept the default settings (English US) for Language, Time, and Keyboard to ensure maximum compatibility with future Active Directory services.

Initiating Setup: Clicked Install Now to begin the operating system deployment.


## Operating System Installation & Edition Selection
After the initial boot, I proceeded with the manual installation of the operating system to ensure full control over the environment.

Version Selection: I chose Windows Server 2022 Standard Evaluation (Desktop Experience).

Why Standard? It is the ideal edition for physical or minimally virtualized environments. For this lab, it provides all the necessary roles (Active Directory, DNS, DHCP) required to build and manage a professional domain environment.

Why Desktop Experience? This is crucial as it installs the full Graphical User Interface (GUI). Without this selection, the server would install as a "Server Core" (Command-line only), which is not ideal for this initial learning phase where visual management tools are needed.

<img width="847" height="688" alt="5" src="https://github.com/user-attachments/assets/0cd78cde-06a3-4a3b-b7fc-fb122ec15518" />


2. Installation Type
When prompted, I selected Custom: Install Microsoft Server Operating System only (advanced).

Justification: Since this is a fresh installation on a new virtual hard drive (50GB), we are not performing an upgrade. The "Custom" option allows us to verify the disk partition and ensure a clean state for our Domain Controller.

<img width="679" height="462" alt="6" src="https://github.com/user-attachments/assets/7b94e6a2-1f6a-48ee-b4dc-d5d7e06cee7c" />

## Disk Partitioning
I allocated the entire 50 GB of virtual disk space to the primary partition.

Action taken: Selected "Drive 0 Unallocated Space" and clicked Next.

Result: Windows Setup automatically creates the necessary system partitions (System Reserved and Primary) to proceed with the installation.
The full 50GB was allocated to a single partition (Drive C:) to provide ample space for Windows Server 2022 system files and the Active Directory database, ensuring optimal performance for this Domain Controller lab.

<img width="682" height="535" alt="7" src="https://github.com/user-attachments/assets/efc5f538-cff7-4918-88df-bbd97ea6377f" />


## OS Installation & File Expansion
After configuring the disk partition and clicking Next, the formal installation process began.

Process Initiation: The system started copying the core operating system files from the ISO image to the virtual hard drive.

File Expansion: The setup entered the "Getting files ready for installation" stage, where the compressed system files within the ISO are expanded and extracted to the allocated 50GB partition.

Hardware Utilization: During this phase, the system utilizes the assigned 2 CPU cores and 4GB RAM to ensure a smooth deployment. 

<img width="694" height="552" alt="8" src="https://github.com/user-attachments/assets/2e86c8e6-126b-4730-ad5b-189223fd73d6" />



## Post-Installation: Administrator Account Setup
After the system rebooted, the Out-of-Box Experience (OOBE) phase began.

Customizing Settings: The system prompted to set a password for the built-in Administrator account.

Security Requirements: I configured a complex password that meets the default Windows Server password policy requirements (including uppercase, lowercase, numbers, and symbols).

Verification: Re-entered the password to confirm and finalized the setup.

<img width="747" height="518" alt="9" src="https://github.com/user-attachments/assets/f1458f33-3de5-454e-bc4b-b9467fea50ea" />

























