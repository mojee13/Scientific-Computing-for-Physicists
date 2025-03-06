# How to Install Docker and Run AlmaLinux 9 on Windows 11
Author: Mojtaba Roshana
__________________________________________________________________
## Introduction
Docker is a powerful containerization tool that allows you to run applications in isolated environments, making development and deployment more efficient. This guide will walk you through installing Docker on Windows 11, enabling Windows Subsystem for Linux (WSL 2), and running AlmaLinux 9 as a container. By following these steps, you can leverage the flexibility of Linux within Windows while keeping your workflows streamlined.

## Step 1: Install Docker Desktop on Windows 11

1. **Download Docker Desktop**
   - Go to the [Docker Desktop Download Page](https://www.docker.com/products/docker-desktop/).
   - Choose "Docker Desktop for Windows" and download the installer.
  
2. **Run the Installer**
   - Double-click the downloaded file to start the installation.
   - Follow the setup wizard instructions to complete the installation.
   - Your system will be restarted after installation.

3. **Start Docker Desktop**
   - After installation, Docker Desktop will start automatically.
   - Ensure Docker Desktop is running by checking the whale icon in the system tray.
   - Open PowerShell or Windows Terminal and run:
     ```powershell
     docker --version
     ```

## Step 2: Enable WSL 2

The Windows Subsystem for Linux (WSL) is a feature of the Windows operating system that enables you to run a Linux file system, along with Linux command-line tools and GUI apps, directly on Windows. With Docker Desktop running on WSL 2, users can leverage Linux workspaces and avoid maintaining both Linux and Windows build scripts. In addition, WSL 2 provides improvements to file system sharing and boot time. Docker Desktop uses the dynamic memory allocation feature in WSL 2 to improve the resource consumption.

1. **Install WSL 2**
   - Open PowerShell as Administrator and run:
     ```powershell
     wsl --install
     ```
2. **Set WSL 2 as Default**
   - Run the following command to ensure Docker uses WSL 2 as its backend:
     ```powershell
     wsl --set-default-version 2
     ```
3. **Enable WSL 2 Integration in Docker**
   - Open Docker Desktop.
   - Go to **Settings > Resources > WSL Integration**.
   - Ensure your default WSL distribution is enabled.
   
## Step 3: Pull the AlmaLinux 9 Image

Open WSL or PowerShell and run the following command to download the AlmaLinux 9 image:
```
docker pull almalinux:9
```

## Step 4: Run an AlmaLinux 9 Container

Execute the following command to start a container in interactive mode:
```
docker run -it --name Example almalinux:9
```

### **Container Options Explained:**
   - ```-it``` : Runs the container in interactive mode with a terminal.
   - ```--name Example``` : Assigns a name to the container.
   - ```almalinux:9``` : Specifies the AlmaLinux 9 image.

Now you are in AlmaLinux 9!

You can exit with the following command:
```
exit
```

## Step 5: Manage Your AlmaLinux 9 Container

To **stop** the container:
```
docker stop Example
```

To **start** the container again:
``` 
docker start Example
```

To **enter** the running container:
```
docker exec -it Example bash
```

To **list all downloaded Docker images**:
```
docker images
```

To **see all Docker processes and container statuses**:
```
docker ps -a
```

---
This guide provides a complete installation and setup for running AlmaLinux 9 inside a Docker container on Windows 11. Enjoy using Docker and AlmaLinux!
