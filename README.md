# FedoraNUC
Using the NUC as a Fedora workstaton. Tested on the D54250WYK.

## Preparing the NUC
 * Download [Fedora 25 Media Writer for OSX](https://getfedora.org/fmw/FedoraMediaWriter-osx-4.0.7.dmg)
 * Find a USB drive
 * Use the Fedora 25 Media Writer for OSX to install a bootable image to the USB drive
 * Copy the [updated bios](https://downloadcenter.intel.com/download/26450/BIOS-Update-WYLPT10H-86A-?product=76977) onto the USB drive
 * F7 to enter BIOS update, select BIOS file from USB
 * F10 to enter the boot menu select the USB drive, boot to fedora live
 * Install to hard drive and use the wizard to set it up
 * Remove the usb device and power on.
 * Start ssh server (as root): `systemctl start sshd.service`
 * Enable ssh server on boot (as root): `systemctl enable sshd.service`
 * add yourself as a sudoer: `echo "XXXXXX ALL=(root) ALL" > /etc/sudoers.d/XXXXXX`
 * run `ifconfig` to get the ip address, The rest you can do remotely over ssh!
 * `copy ssh keys into ~/.ssh/`
 * `chmod 600 ~/.ssh/*`
 * Git config `git config --global user.name "XXXXXXXX" && git config --global user.email "XXXX@XXXXXXXXX" && git config --global push.default simple`
 * `git clone git@github.com:Tom-Davidson/FedoraNUC.git ~/Documents/Provisioning`
 * `sudo yum install ansible`
 * `clear && ansible-playbook -i "localhost," -c local ~/Documents/Provisioning/dev.yml --ask-sudo-pass`
