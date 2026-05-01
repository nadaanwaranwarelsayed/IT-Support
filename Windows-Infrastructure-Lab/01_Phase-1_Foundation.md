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

## Before launching the installation, here is a summary of the virtual hardware and system settings configured for the Domain Controller.

<img width="1036" height="500" alt="3" src="https://github.com/user-attachments/assets/914ba0b0-511b-4458-b10b-16d99e88ea48" />















