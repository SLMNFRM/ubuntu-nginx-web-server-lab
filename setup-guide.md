# Setup Guide

These are the steps used to build the VM and deploy the web server.

---

## 1. Create VM

Created a new VM in VMware Workstation.

Settings used:

2 CPU  
4GB RAM  
40GB disk  
NAT networking

Mounted Ubuntu Server ISO during setup.

---

## 2. Install Ubuntu Server

Used mostly default installer options.

Important choices:

Installed OpenSSH server  
Created admin user  
Used DHCP networking

---

## 3. Update packages

After first login:

sudo apt update  
sudo apt upgrade -y

---

## 4. Install nginx

sudo apt install nginx -y

The service started automatically.

Checked status:

sudo systemctl status nginx

---

## 5. Edit default webpage

sudo nano /var/www/html/index.html

Replaced default nginx page with simple HTML content.

---

## 6. Test server

Retrieved VM IP:

ip a

Opened browser on host machine:

http://VM-IP

Page loaded correctly.
