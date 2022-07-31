---
layout: single
title: How to Install AzCopy for Azure Storage
excerpt: "AzCopy is a command-line utility that you can use to copy blobs or files to or from a storage account. In this post, I will cover how to install AzCopy on Windows and Linux. AzCopy V10 is the currently supported version of AzCopy, it also adds additional functionality like sync of blob storage accounts and much more. First, download the AzCopy V10 executable file to any directory on your computer. AzCopy V10 is just an executable file, so there's nothing to install."
date: 2022-07-31
classes: wide
header:
  teaser: /assets/images/htb-writeup-delivery/delivery_logo.png
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

![](/assets/images/htb-writeup-delivery/delivery_logo.png)

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
