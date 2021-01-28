# Install WSL2 on Windows 10 Legacy systems. 
Please follow the instruction in step-1 or Step-2 on enabling virtualization based on the BIOS type. 
 
1. Enabling Virtualization in non UEFI systems - [Enabling vt-x in Windows 10 when you can't find UEFI virtualization settings with standard methods](https://www.youtube.com/watch?v=wlfS0UEMUqc
)

2. Enabling in UEFI Systems - [How to enable Virtualization (VT-x) in Bios Windows 10](https://www.youtube.com/watch?v=MOuTxfzCvMY )

3. Follow the steps in [Install Windows Subsystem for Linux (WSL) on Windows 10 | Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/install-win10) or [How to Install WSL 2 on Windows 10 (Updated) - OMG! Ubuntu!](https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10)
 
4. To summarize
- Open PowerShell as an admin and run the following script:
```
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
```
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```	 
- Let's update the WSL 2 Linux kernel. Go to https://aka.ms/wsl2kernel and follow the download link, an MSI installation will complete the update:
```
    #Run this to will make all distros run on WSL2 by default:
    wsl --set-default-version 2
```
- Now it is time to install your favorite Linux distro. I installed Ubuntu. Now open PowerShell and ensure that WSL is correctly using version 2 for your distro:
```
      wsl --list -v
 ```