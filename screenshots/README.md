## Downloading VMware Workstation

To build the lab environment, VMware Workstation Pro was downloaded to run the Ubuntu Server virtual machine.

The installer was obtained from the VMware download portal where different release versions are available.

In this case the Windows version of VMware Workstation Pro was selected.

![VMware download portal](screenshots/01-vmware-download-portal.png)

## Creating the Virtual Machine

A new VM was created in VMware Workstation using the Ubuntu Server ISO.

VMware automatically detected the operating system from the installer disk.

This allows VMware to preconfigure the VM using the Easy Install feature.

![VM Install Wizard](screenshots/02-vm-install-wizard.png)

## Issue Encountered: Virtualization Disabled

When attempting to power on the virtual machine, VMware returned the following error:

"This host supports AMD-V, but AMD-V is disabled."

This indicates that CPU virtualization support was disabled in the system BIOS/UEFI firmware.

Since VMware relies on hardware virtualization extensions to run virtual machines, the VM could not start until this feature was enabled.

Resolution:

Virtualization (SVM / AMD-V) was enabled in the BIOS settings and the host machine was restarted.

After enabling virtualization, VMware was able to start the Ubuntu virtual machine successfully.

![AMD-V Disabled Error](screenshots/03-amd-virtualization-disabled-error.png)

## Issue Encountered: Operating System Not Found

After enabling virtualization and starting the VM, the system displayed the following message:

"Operating System not found"

The VM attempted a PXE network boot because it could not detect a bootable installation disk.

This occurred because the Ubuntu Server ISO was not properly mounted to the VM.

After attaching the ISO file to the virtual CD drive and restarting the VM, the Ubuntu installer launched correctly.

![OS Not Found Error](screenshots/04-os-not-found-pxe-boot.png)

## Fixing Boot Error: Attaching Ubuntu ISO

After the VM failed to boot and displayed "Operating system not found", the issue was traced to the installation media not being attached.

The Ubuntu Server ISO was manually mounted to the VM's virtual CD/DVD drive through VMware's Virtual Machine Settings.

Once the ISO was attached, the VM was restarted and the Ubuntu installer launched successfully.

![Attach Ubuntu ISO](screenshots/05-attach-ubuntu-iso.png)

## Configuring Network Connectivity

During installation Ubuntu automatically detected the VM network adapter and configured it using DHCP.

The interface `ens33` received the IP address:

```
192.168.20.128
```

This confirms the virtual machine successfully connected to the network through the VMware virtual adapter.

Network connectivity is required so the server can download updates and install packages during setup.

![Ubuntu Network Configuration](screenshots/06-ubuntu-network-configuration.png)

## Enabling SSH Access

During installation the OpenSSH server package was selected to allow remote administration of the server.

SSH enables administrators to securely access the machine over the network using encrypted connections.

Password authentication was enabled during the setup process.

Example connection command:

ssh username@server-ip

![OpenSSH installation](screenshots/07-enable-openssh-install.png)

## First Boot of the Server

After installation completed, the Ubuntu server started successfully and initialized system services.

The boot process shows systemd starting core services such as snapd and cloud-init. SSH host keys were also generated, confirming that the OpenSSH service is active and ready for remote connections.

This indicates the server installation finished successfully and the system is ready for configuration.

![Ubuntu First Boot](screenshots/08-first-server-boot.png)

## Editing the Default Web Page

After installing Nginx, the default webpage was modified to verify that the web server was functioning correctly.

The file edited was:

/var/www/html/index.html

The page content was updated with a simple HTML message to confirm the deployment.

![Editing nginx page](screenshots/09-edit-nginx-index-page.png)
