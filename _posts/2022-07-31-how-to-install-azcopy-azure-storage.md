---
layout: single
title: How to Install AzCopy for Azure Storage
excerpt: "AzCopy is a command-line utility that you can use to copy blobs or files to or from a storage account. In this post, I will cover how to install AzCopy on Windows and Linux. AzCopy V10 is the currently supported version of AzCopy, it also adds additional functionality like sync of blob storage accounts and much more. First, download the AzCopy V10 executable file to any directory on your computer. AzCopy V10 is just an executable file, so there's nothing to install."
date: 2022-07-31
classes: wide
header:
  teaser: /assets/images/cloud-images/azcopy-command.png
  teaser_home_page: true
  icon: /assets/images/hackthebox.webp
categories:
  - scripting
  - proccess
tags:  
  - azcopy
  - microsoft
  - azure
  - storage
  - account
---

![](/assets/images/cloud-images/azcopy.png)

AzCopy is a command-line utility that you can use to copy blobs or files to or from a storage account. In this post, I will cover how to install AzCopy on Windows and Linux. AzCopy V10 is the currently supported version of AzCopy, it also adds additional functionality like sync of blob storage accounts and much more. First, download the AzCopy V10 executable file to any directory on your computer. AzCopy V10 is just an executable file, so there's nothing to install.

## Download AzCopy

First, download the AzCopy V10 executable file to any directory on your computer. AzCopy V10 is just an executable file, so there's nothing to install.

[Windows 64-bit (zip)](https://aka.ms/downloadazcopy-v10-windows)  
[Windows 32-bit (zip)](https://aka.ms/downloadazcopy-v10-windows-32bit)  
[Linux x86-64 (tar)](https://aka.ms/downloadazcopy-v10-linux)  
[Linux ARM64 Preview (tar)](https://aka.ms/downloadazcopy-v10-linux-arm64)  
[macOS (zip)](https://aka.ms/downloadazcopy-v10-mac)  

These files are compressed as a zip file (Windows and Mac) or a tar file (Linux). To download and decompress the tar file on Linux, see the documentation for your Linux distribution.  

For detailed information on AzCopy releases see the [AzCopy release page.](https://github.com/Azure/azure-storage-azcopy/releases)  

## Install AzCopy on Linux

To install AzCopy on Linux, you can run the following shell script, or you can download the [bash](https://drive.google.com/file/d/1wlHxdCltcI7xVLiz-tn9HV5X5vsOjYFp/view?usp=sharing) file and run it from where ever you want. This script will put the AzCopy executable into the /usr/bin folder so that you can run it from anywhere.

```bash
#!/bin/bash

#Download AzCopy
wget https://aka.ms/downloadazcopy-v10-linux

#Expand Archive
tar -xvf downloadazcopy-v10-linux

#(Optional) Remove existing AzCopy version
sudo rm /usr/bin/azcopy > /dev/null 2>&1

#Remove unnecessary files
sudo rm downloadazcopy-v10-linux

#Move AzCopy to the destination you want to store it
sudo cp ./azcopy_linux_amd64_*/azcopy /usr/bin/

#Remove unnecessary files
sudo rm -r azcopy_linux_amd64_*/

#Check if the file exists
sudo ls -lah /usr/bin/ | grep azcopy
```

##Install AzCopy on Windows


To install AzCopy on Windows, you can run the following PowerShell script, or you can download the zip file and run it from where ever you want. This script will add the AzCopy folder location to your system path so that you can run the AzCopy command from anywhere.

```powershell
#Download AzCopy
Invoke-WebRequest -Uri "https://aka.ms/downloadazcopy-v10-windows" -OutFile AzCopy.zip -UseBasicParsing
 
#Curl.exe option (Windows 10 Spring 2018 Update (or later))
curl.exe -L -o AzCopy.zip https://aka.ms/downloadazcopy-v10-windows
 
#Expand Archive
Expand-Archive ./AzCopy.zip ./AzCopy -Force
 
#Move AzCopy to the destination you want to store it
Get-ChildItem ./AzCopy/*/azcopy.exe | Move-Item -Destination "C:\Users\local\AzCopy\AzCopy.exe"
 
#Add your AzCopy path to the Windows environment PATH (C:\Users\thmaure\AzCopy in this example), e.g., using PowerShell:
$userenv = [System.Environment]::GetEnvironmentVariable("Path", "User")
[System.Environment]::SetEnvironmentVariable("PATH", $userenv + ";C:\Users\local\AzCopy", "User")
```

I hope this helps you to install AzCopy and configure it. If you have any questions, feel free to leave a comment.

