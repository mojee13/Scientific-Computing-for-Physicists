 HOW TO INSTALL ALMALINUX 9 USING DOCKER on Windows 11
Author: Mojtaba Roshana
__________________________________________________________________
# Step 1: Install Docker on Windows

Docker provides a way to run AlmaLinux 9 as a container or within a virtual machine using WSL 2.

## 1. Enable Virtualization
Ensure that **virtualization** is enabled in your BIOS settings.
- Check virtualization support in **Task Manager** → **Performance** → **CPU** (it should say **"Virtualization: Enabled"**).

## 2. Install WSL 2 (Windows Subsystem for Linux)
Open **PowerShell as Administrator** and run:
```powershell
wsl --install
