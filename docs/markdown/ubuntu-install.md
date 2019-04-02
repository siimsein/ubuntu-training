Installing Ubuntu Server w/ VirtualBox VM
=========================================

This is a rough guide mainly for the steps that I usually forget when setting up an Ubuntu VM for use as a local development environment.

Setup the VM
------------

Download the ISO image from the Ubuntu website and boot into a fresh VM. Remember that for 64bit VM's to work, you must enable virtualisation support on the host machine (in the BIOS).

Run the Ubuntu install
----------------------

Boot into the ISO and run through the installation wizard. I usually select `danserver.local` as the hostname but you can select whatever you want when you get to that step.

**Ensure that your keyboard is mapped correctly when prompted or you'll run into a whole host of trouble later!**

When you get to the package selection step, ensure that **LAMP Server** is selected by scrolling down to it and hitting the space bar before continuing. If you didn't do this, see the **Install LAMP** section below.

Update the system
-----------------

When installed run `sudo apt-get update` and then `sudo apt-get upgrade` to upgrade all of your packages.
