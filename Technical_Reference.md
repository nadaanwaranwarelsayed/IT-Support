# 🛠️ IT Support Technical Reference Manual

## 1. Hardware Fundamentals 💻
- **CPU:** Central Processing Unit (The Brain).
- **RAM:** Speed (MHz) & Generations (DDR3, DDR4, DDR5).
- **Storage:** Difference between HDD (SATA) and SSD (NVMe).
- **Motherboard:** Socket types & Chipsets.

## 2. CLI Toolbox (Windows & Linux) ⌨️
### Windows PowerShell Essentials:
- `ls` / `cd` / `mkdir` / `pwd` (Navigation).
- `cp` / `mv` / `rm` (File Management).
- `cat` / `more` (Viewing Content).

### Linux Terminal Essentials:
- `ls -la` / `cd` / `mkdir` / `rm -r`.
- `sudo` (Admin Privileges).
- `grep` / `less` (Searching & Reading).

## 3. System Diagnostics & Health 🩺
- **RAM Info:** `Get-CimInstance Win32_PhysicalMemory | Select Speed, SMBIOSMemoryType`
- **Disk Health:** `Get-PhysicalDisk | Select FriendlyName, HealthStatus`
- **User Management:** `net user`, `Get-LocalUser`, `Get-LocalGroup`.
