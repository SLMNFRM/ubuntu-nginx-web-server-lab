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
