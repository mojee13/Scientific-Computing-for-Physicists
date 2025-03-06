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
The Windows Subsystem for Linux (WSL) is a feature of the Windows operating system that enables you to run a Linux file system, along with Linux command-line tools and GUI apps, directly on Windows, alongside your traditional Windows desktop and apps. With Docker Desktop running on WSL 2, users can leverage Linux workspaces and avoid maintaining both Linux and Windows build scripts. In addition, WSL 2 provides improvements to file system sharing and boot time. Docker Desktop uses the dynamic memory allocation feature in WSL 2 to improve the resource consumption.

- Open PowerShell as Administrator and run:
  ```powershell
  wsl --install
  ```
- Set WSL 2 as default:
  ```powershell
  wsl --set-default-version 2
  ```
  
## Step 3: Pull the AlmaLinux 9 Image

Open WSL and run the following command to download the AlmaLinux 9 image:
```
docker pull almalinux:9
```
## Step 4: Run an AlmaLinux 9 Container
Execute the following command to start a container in interactive mode:
```
docker run -it --name almalinux9-1 almalinux:9
```
**Container Options Explained:**
   - ```-it```: Runs the container in interactive mode with a terminal.
   - ```--name almalinux9A```: Assigns a name to the container.
   - ```almalinux:9```: Specifies the AlmaLinux 9 image.

Now you are in AlmaLinux 9!

You can exit with the following command:
```exit```
and execute it again with the command:


To stop the container you can use the command

```
docker stop almalinux9A
```

and to start it :

``` 
docker start almalinux9A
```
If you want to enter it:
```
docker exec -it  almalinux9A bash
```

You can check the docker images by this command:
```
docker images
```
You can see all docker process status with this command:
```
docker ps -a
```
