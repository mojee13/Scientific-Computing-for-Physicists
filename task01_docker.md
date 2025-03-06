# How to Install Docker and Run AlmaLinux 9 on Windows 11
Author: Mojtaba Roshana
__________________________________________________________________

## Step 1: Install Docker Desktop on Windows 11

1. **Download Docker Desktop**
   - Go to the [Docker Desktop Download Page](https://www.docker.com/products/docker-desktop/).
   - Choose "Docker Desktop for Windows" and download the installer.
  
2. **Run the Installer**
   - Double-click the downloaded file to start the installation.
   - Follow the setup wizard instructions to complete the installation.
   - Your system will be restarted after installation

3. **Start Docker Desktop**
   - After installation, Docker Desktop will start automatically.
   - Ensure Docker Desktop is running by checking the whale icon in the system tray.
   - Open PowerShell or Windows Terminal and run:
     ```powershell
     docker --version

### 2. Enable WSL 2
- Open PowerShell as Administrator and run:
  ```powershell
  wsl --install
  ```
- Set WSL 2 as default:
  ```powershell
  wsl --set-default-version 2
  ```
  
## Step 3: Pull the AlmaLinux 9 Image

Open powrshell and run the following command to download the AlmaLinux 9 image:
```
docker pull almalinux:9
```
## Step 4: Run an AlmaLinux 9 Container
Execute the following command to start a container in interactive mode:
```
docker run -it --name almalinux9-container almalinux:9
```
**Container Options Explained:**
   - ```-it```: Runs the container in interactive mode with a terminal.
   - ```--name almalinux9-container```: Assigns a name to the container.
   - ```almalinux:9```: Specifies the AlmaLinux 9 image.

Now you are in AlmaLinux 9!
