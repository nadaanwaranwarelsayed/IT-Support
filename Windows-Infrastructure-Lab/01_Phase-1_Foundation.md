# Phase 1: Lab Foundation & Environment Setup

In this phase, I established the base infrastructure for my IT Support lab by configuring the virtualization environment and initializing the Windows Server 2022 setup.

## 1. Virtualization Environment & Resource Planning
For this lab, I chose **Oracle VM VirtualBox** as the hypervisor. I carefully allocated hardware resources to ensure the server can handle Active Directory and Domain Controller roles efficiently.

### **Final VM Configuration Summary:**
* **Virtual Machine Name:** `Windows_Server_2022`
* **Base Memory (RAM):** 4096 MB (4GB)
* **Processors:** 2 CPUs
* **Boot Method:** Legacy BIOS (EFI Disabled)
* **Storage:** 50 GB Dynamic VDI
* **Unattended Install:** Skipped (to allow for manual custom configuration).

---

### **System Configuration Overview:**

#### **Step 1: Final Resource & OS Summary**
Below is a comprehensive summary of the Virtual Machine settings before the OS installation process. This ensures all parameters meet the corporate lab requirements.

<img width="1135" height="549" alt="1" src="https://github.com/user-attachments/assets/ef61869a-58f3-4efe-b0d0-ad9cddc35f48" />


#### **Step 2: Operating System Installation**
After configuring the virtual hardware, I proceeded with the manual installation of **Windows Server 2022**. 

* **Version Selected:** Windows Server 2022 Standard Evaluation (Desktop Experience).
  
  <img width="861" height="653" alt="3" src="https://github.com/user-attachments/assets/ab4d036e-b230-4969-bc15-70851bcb20bd" />

* **Installation Type:** Custom (Advanced) to ensure a clean installation on the unallocated 50GB space.
  
<img width="890" height="736" alt="4" src="https://github.com/user-attachments/assets/8fdf1621-e053-430e-8bb4-74453aa2195f" />

*Caption: Choosing the Desktop Experience to ensure a GUI is available for administration.*

<img width="832" height="671" alt="5" src="https://github.com/user-attachments/assets/2b0f2c2e-6529-4dca-8ffc-9cd73a8d2bb7" />

*Caption: Allocating the full 50GB drive for the primary system partition.*

#### **Step 3: Post-Installation & Initial Setup**
Once the installation was complete, I performed the following essential administrative tasks:

1.  **Administrator Account Setup:** Created a secure password for the built-in Administrator account.
2.  **Server Renaming:** Changed the default computer name to `DC-MASTER` for better identification within the domain.
3.  **Static IP Configuration:** Assigned a manual IPv4 address to ensure consistent network connectivity for future Domain Services.

