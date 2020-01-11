# FedoraNUC

Using the NUC as a Fedora workstaton.

## Preparing the NUC

* Download [Fedora 31](https://download.fedoraproject.org/pub/fedora/linux/releases/31/Workstation/x86_64/iso/Fedora-Workstation-Live-x86_64-31-1.9.iso)
* Download the [Live USB Creator](https://fedorahosted.org/liveusb-creator/)
* Burn the iso to the USB drive (I used Balena Etcher `brew cask install etcher`)
* Put the USB drive into a back usb port
* Boot the NUC and use F10 to enter the boot menu, select the USB drive, boot into Fedora Live Workstation
* Install to hard drive and use the wizard to set it up
* Remove the usb device and power on
* Run through the setup wizard
* Control Panel -> Devices -> Display to select a good resolution
* Control Panel -> Power to turn off power saving like disable network and screen
* Control Panel -> Details -> Users to enable automatic login
* Control Panel -> Sharing -> Remote Login = ON
* Control Panel -> Network -> [Cog] to find the IP address
* Test ssh login from another machine and configure from there
* `sudo -i`
* `dnf update -y dnf* && dnf update -y`
* Disable IPv6 if required with `sysctl -w net.ipv6.conf.all.disable_ipv6=1 && sysctl -w net.ipv6.conf.default.disable_ipv6=1`
* `dnf install -y ansible`
* `git clone https://github.com/Tom-Davidson/FedoraNUC.git /root/Provisioning`
* `ansible-playbook --inventory "<IP_ADDRESS>", --user <SSH_USERNAME> --ask-pass --ask-become-pass /root/Provisioning/<INSTALL_TYPE>.yml`

* Copy the [updated bios](wy0035.bio) onto the USB drive
* F7 to enter BIOS update, select BIOS file from USB
