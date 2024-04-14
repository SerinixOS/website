---
title: Installing carbonOS
description: System requirements and guide on how to install carbonOS on hardware or in a VM
os_version: "2022.3"
---

These instructions are a quick guide to getting carbonOS installed and ready
for testing.

#### System Requirements

- EFI firmware
- CPU new enough to support x86-64-v3 (generally, CPUs made after 2016 work)
- Intel or AMD graphics
- SSD-based storage

<div class="alert alert-warning" role="alert">
  <strong>NVIDIA support is still unfinished!</strong>
  There are still a couple of known issues and rough edges around NVIDIA GPUs.
  The pieces are all there, but it just doesn't work yet. 
</div>

#### Installing onto hardware

<div class="alert alert-danger" role="alert">
  <h4 class="alert-heading">Installation Issue!</h4>
  I've been made aware of an issue that makes it impossible for carbonOS to be
  installed from the 2022.3 ISO. There is a workaround, which I've described
  here (step 6 and onward). Please make sure to follow these steps carefully!
</div>

1. Download the [ISO Image](/download)
2. Write the ISO to a USB flash drive, using `dd`, your OS's disk utility,
   [balenaEtcher](https://www.balena.io/etcher/), or similar software
3. Boot your machine into the EFI firmware. Disable secure boot, and
   ensure that your USB drive has priority in the boot order
4. Boot your machine from the USB drive
5. Select "Try or Install carbonOS" from the menu. If you have at least 8GB of
   RAM, you can select the ramdisk alternative if necessary (i.e. if you need to
   remove the USB drive during installation)
6. Once the system boots, select your language and follow the on-screen
   instructions until you get to the "Try or Install" prompt
7. Select "Try"
8. In the Demo session, open up a terminal and type out the command
   `systemctl stop liveos-boot` but don't run it yet.
9. Open up the installer (it's pinned to the dash). Follow
   on-screen instructions until it starts installing.
10. Wait for the installer to report that it's "Copying Files..."
11. Run the command you've typed out in the terminal, then accept the permission
    prompt that appears
12. Installation should continue as usual, until the end. You may or may not
    receive an "Installation Failed" error, which is likely something you can
    ignore. Try to reboot
13. If installation failed, try again. If it continues to fail, please reach
    out via [#carbonOS on Matrix](https://matrix.to/#/#carbonOS:matrix.org) 

#### Installing onto GNOME Boxes

1. Use GNOME Boxes from [Flathub](https://flathub.org/apps/details/org.gnome.Boxes)
2. Download the [ISO Image](/download)
3. Create a new virtual machine, and select the ISO image you downloaded
4. Boxes will tell you that it couldn't recognize the OS. In the list of
   OS options, select "GNOME OS"
5. Follow the on-screen instructions to finish creating the VM
6. Start the VM
7. Select "Try or Install carbonOS" from the menu
8. Follow steps 6-13 of the "Installing onto Hardware" section

<!-- TODO: Commented out because of https://gitlab.com/carbonOS/issues/-/issues/15
8. Once the system boots, select your language and follow the on-screen
   instructions
-->

#### Installing onto VirtualBox

For the best experience & compatibility, I'd recommend testing carbonOS through
GNOME Boxes. Running carbonOS on VirtualBox is possible, but there are known
limitations:

- VirtualBox tends to drop you into an EFI shell instead of properly selecting
  carbonOS's bootloader
- VirtualBox's GPU driver may have visual oddities, such as invisible or 
  upside-down cursors
  
If you want to try working around these issues, please join
[#carbonOS on Matrix](https://matrix.to/#/#carbonOS:matrix.org) and I'll help you
get it installed. Then I'll write some proper instructions here.

#### Dual-boot, custom partitions, etc

These setups are not officially supported by carbonOS. However, if you'd like
to use carbonOS in these scenarios anyway, you'll need to follow the
[advanced installation instructions](/support/installation-custom.html).
Be warned that these instructions assume you have the prerequisite knowledge
to manually manipulate Linux partitions, filesystems, and configuration.
