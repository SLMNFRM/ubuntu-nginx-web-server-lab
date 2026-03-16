# Ubuntu Nginx Web Server Lab

## Overview

This lab was built to practice deploying a basic Linux web server inside a virtual machine.

The server runs Ubuntu Server and hosts a simple webpage using Nginx. The goal was to get comfortable with Linux administration, installing services, editing configuration files, and accessing the server from the host machine over the network.

The environment was created using VMware Workstation.

---

## Environment

Host machine: Personal laptop  
Hypervisor: VMware Workstation  

Virtual machine configuration:

CPU: 2 vCPU  
RAM: 4GB  
Disk: 40GB  

Operating system:

Ubuntu Server 24.04 LTS

---

## What was done

1. Created Ubuntu Server VM in VMware
2. Installed base system and enabled OpenSSH
3. Updated packages
4. Installed Nginx
5. Edited the default web page
6. Verified access from host browser

---

## Nginx Installation

Installed nginx using apt:

sudo apt update  
sudo apt install nginx -y

Verified service status:

sudo systemctl status nginx

The service started automatically after installation.

---

## Custom Web Page

Default page was modified here:

/var/www/html/index.html

Content used:

<h1>Suleiman Lab Server</h1>  
<p>First VM deployed</p>

After saving the file, refreshing the browser confirmed the page update.

---

## Network Test

VM IP was retrieved using:

ip a

The server was then accessed from the host machine using a browser:

http://VM-IP

The custom page loaded successfully.

---

## Key Takeaways

- Learned the basic workflow of deploying a Linux server
- Installed and verified a system service
- Modified web server content
- Tested network connectivity between host and VM

---

## Next Steps

Things I want to add to this lab later:

- SSH key authentication
- Basic firewall rules with UFW
- Fail2ban for login protection
- Multiple VMs to simulate a small network
