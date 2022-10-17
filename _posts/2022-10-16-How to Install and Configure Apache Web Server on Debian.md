---
layout: single
title: How to Install and Configure Apache Web Server on Debian
excerpt: "The Apache webserver is one of the most popular open-source web servers developed and maintained by the [Apache Software Foundation](https://www.apache.org). Apache is by far the most widely used web server application in Linux operating systems, but it can be used on almost all operating system platforms such as Windows, MAC OS, OS/2, and so on. It allows developers to publish their content over the Internet."
date: 2022-10-16
classes: wide
header:
  teaser: /assets/images/debian-apache/apache.png
  teaser_home_page: true
  icon: /assets/images/hackthebox.webp
categories:
  - Web Server
  - Installation
tags:  
  - apache2
  - httpd
  - debian
---

![](/assets/images/debian-apache/apache.png)

The Apache webserver is one of the most popular open-source web servers developed and maintained by the [Apache Software Foundation](https://www.apache.org). Apache is by far the most widely used web server application in Linux operating systems, but it can be used on almost all operating system platforms such as Windows, MAC OS, OS/2, and so on. It allows developers to publish their content over the Internet.

This article explains how to install and configure Apache web server on Debian 11 (Bullseye). The same steps also work under the older Debian versions and have been tested there as well.

## Install Apache 2 on Debian Linux
Follow the steps below to install Apache2 on your system.

Step 1: Update system repositories
First, we need to update the package sources in our operating system. To do this, run the following command in the terminal as sudo or root:
```bash
$ sudo apt update
```
When prompted for the password, enter the sudo password.
![](/assets/images/debian-apache/update.png)

Step 2: Install Apache 2 with the apt command.

If you are a Linux pro you can install Apache from [source](https://httpd.apache.org/docs/2.4/install.html).
Next in this step, install the Apache2 web server using the following command:
```bash
$ sudo apt install apache2 -y
```
![](/assets/images/debian-apache/install.png)

You will be provided with a Y/n option to continue the installation. Hit y to continue.
