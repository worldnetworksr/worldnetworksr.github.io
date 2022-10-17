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

Step 3: Verify the Apache installation
Once the installation is completed, you can view the Apache version installed by running the following command in Terminal. This way you can also verify that Apache is successfully installed on your system.
```bash
$ sudo apache2 -version
```
![](/assets/images/debian-apache/apacheversion.png)

## Manage Apache Service Using Systemd
At this point, the Apache webserver is up and running. You can manage the Apache service using the systemctl command line utility.
```bash
$ sudo systemctl stop apache2
```
To restart the Apache service, run the following command:
```bash
$ sudo systemctl restart apache2
```
To enable the Apache service to start at system reboot, run the following command:
```bash
$ sudo systemctl enable apache2
```
To verify the status of the Apache service, run the following command:
```bash
$ sudo systemctl status apache2
```
You will get the following output:
![](/assets/images/debian-apache/apachestatus.png)

## Verify the Apache listen port
You can check the Apache listening port using the following command:
```bash
ss -antpl
```
![](/assets/images/debian-apache/apacheport.png)

## Verify Apache Webserver is working
You can verify if the Apache web server is working fine by requesting a web page from the Apache webserver.
Execute the below command in Terminal to find the IP address of your server.
```bash
$ hostname -I
```
Once you find the IP address, type http:// followed by the IP address of your web server as follows:

http://server_IP

Now, open your web browser and access the Apache test page using the URL http://your-server-ip. You should see the Apache test page in the following screen:
Note: If the firewall is running on your system, you will need to allow certain web ports so that external users can access it.
![](/assets/images/debian-apache/apachesite.png)

## Apache Virtual Hosting
Apache provides virtual hosting feature that allow you to host multiple websites on a single server. In this section, we will host two website using the domain names example.com and example.net.

Step 1: Make a Directory for Each Site.

You’ll create a directory for each site that you’ll be hosting, within the /var/www folder.  This location newly created location is also dubbed the document root location; you’ll need to set this path later in the configuration file.  Sub the example.com and example.net for your domain names.
```bash
$ sudo mkdir -p /var/www/domain.com/public_html
$ sudo mkdir -p /var/www/domain2.com/public_html
```
![](/assets/images/debian-apache/dir.png)

Step 2: Set Folder Permissions
```bash
$ sudo chmod -R 755 /var/www
```
Step 3: Set up an Index Page.
To see a home page you’ll want to make sure the index.html file is created for each domain. Now we will create a sample index page to test our example.com and example.net sites. To do so, we will create an HTML file using the nano editor as follows:
```bash
$ sudo nano /var/www/example.com/public_html/index.html
```
Add the following code:
```bash
<html>
    <head>
        <p>Welcome to Apache Web Server!</p>
    </head>
    <body>
        <h3>Success!  The example.com virtual host is working!</h3>
    <script>class RocketElementorAnimation{constructor(){this.deviceMode=document.createElement("span"),this.deviceMode.id="elementor-device-mode",this.deviceMode.setAttribute("class","elementor-screen-only"),document.body.appendChild(this.deviceMode)}_detectAnimations(){let t=getComputedStyle(this.deviceMode,":after").content.replace(/"/g,"");this.animationSettingKeys=this._listAnimationSettingsKeys(t),document.querySelectorAll(".elementor-invisible[data-settings]").forEach(t=>{const e=t.getBoundingClientRect();if(e.bottom>=0&&e.top<=window.innerHeight)try{this._animateElement(t)}catch(t){}})}_animateElement(t){const e=JSON.parse(t.dataset.settings),i=e._animation_delay||e.animation_delay||0,n=e[this.animationSettingKeys.find(t=>e[t])];if("none"===n)return void t.classList.remove("elementor-invisible");t.classList.remove(n),this.currentAnimation&&t.classList.remove(this.currentAnimation),this.currentAnimation=n;let s=setTimeout(()=>{t.classList.remove("elementor-invisible"),t.classList.add("animated",n),this._removeAnimationSettings(t,e)},i);window.addEventListener("rocket-startLoading",function(){clearTimeout(s)})}_listAnimationSettingsKeys(t="mobile"){const e=[""];switch(t){case"mobile":e.unshift("_mobile");case"tablet":e.unshift("_tablet");case"desktop":e.unshift("_desktop")}const i=[];return["animation","_animation"].forEach(t=>{e.forEach(e=>{i.push(t+e)})}),i}_removeAnimationSettings(t,e){this._listAnimationSettingsKeys().forEach(t=>delete e[t]),t.dataset.settings=JSON.stringify(e)}static run(){const t=new RocketElementorAnimation;requestAnimationFrame(t._detectAnimations.bind(t))}}document.addEventListener("DOMContentLoaded",RocketElementorAnimation.run);</script></body>
</html>
```
Save and close the file when you are finished.

Repeat the steps for your second domain.

## Configure Apache to Host Website
Step 1: Next, you will need to create an Apache virtual host configuration file to serve the index.html located inside example.com directory.
You can create it with the following command:
```bash
$ sudo nano /etc/apache2/sites-available/example.com.conf
```
Repeat the steps for your second domain, using the command below.
```bash
$ sudo nano /etc/apache2/sites-available/example.net.conf
```
*Note:* Also you can copy the default configuration file for to create new sites.
```bash
$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf
$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.net.conf
```
Step 2: Edit the Config File for Each Site.
At the bare minimum, you’ll adjust and add the highlighted lines within the <VirtualHost *:80> and </VirtualHost> tags.

*Note:* ServerAlias is the alternative name for your domain, in this case and in most, you’ll put www in front of the domain name so people can view the site by either www or non www (ServerName).
```bash
$ sudo nano /etc/apache2/sites-available/example.com.conf
```
Add the following code:
```bash
<VirtualHost *:80>
ServerAdmin admin@example.com
ServerName example.com
ServerAlias www.example.com
DocumentRoot /var/www/example.com/public_html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
Save the file. Repeat this process for your example.net.conf file, be sure to update your ServerName, ServerAlias and DocumentRoot for your second domain.

Step 3: Enable Your Config File.
Out of the box, your server is set to read the default 000-default.conf file.  But, in our previous step we made a new config file for each domain.  So, we will need to disable the default file.
```bash
$ sudo a2dissite 000-default.conf
```
To have your server mapped to your domains you’ll need to enable each of your newly made .conf files.
```bash
$ sudo a2ensite example.com.conf
$ sudo a2ensite example.net.conf
```
We restart the Apache service to register our changes.
```bash
$ sudo systemctl restart apache2
```
Now test the configuration for any syntax errors:
```bash
$ sudo apache2ctl configtest
```
In case there is no error, you will receive the following output.








![](/assets/images/debian-apache/8.0.png)

In some cases, you might receive the following error (in this case it happened during our tests on a Debian 10/11 systems):
![](/assets/images/debian-apache/9.0.png)
Solve apache configuration errors.
To resolve this error, create the servername.conf file by executing the following command:
```bash
$ sudo nano /etc/apache2/conf-available/servername.conf
```
Add the following line in it:

ServerName example.com
![](/assets/images/debian-apache/10.0.png)

Set a server name.

Once done, press Ctrl+O to save and then Ctrl+X to exit the file.

After that run the following command:
```bash
$ sudo a2enconf servername
```
Restart apache to apply the changed config

Now reload the Apache2:
```bash
$ sudo systemctl reload apache2
```
Once done, again run the following command to test the configuration file:
```bash
$ sudo apache2ctl configtest
```
Now you will see the error has been removed.





![](/assets/images/debian-apache/11.0.png)

Step 4: Verify Apache Configurations
After starting Apache you now can view that the configurations are working by either editing your /etc/host file on your computer or by editing your domain's DNS.
![](/assets/images/debian-apache/12.0.png)

Step 5: Test if Apache is serving your domain name.


Now open the browser and navigate to:

http://example.com

Replace example.com with your own domain name.

The following index page shows now you are able to access all your websites.
![](/assets/images/debian-apache/13.0.png)

In this article, we have learned how to install and configure the Apache web server on a Debian 11 or Debian 10 OS. We have done some basic configurations that include changes to the firewall, setting up the virtual host, and how to manage the Apache services using some commands. I hope it has given you a basic overview of how to use Apache to host the websites properly.
