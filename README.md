# FedoraNUC
Using the NUC as a Fedora workstaton.

## Preparing the NUC
 * Download [Fedora 22](https://download.fedoraproject.org/pub/fedora/linux/releases/22/Workstation/x86_64/iso/Fedora-Live-Workstation-x86_64-22-3.iso)
 * Download the [Live USB Creator](https://fedorahosted.org/liveusb-creator/)
 * Find a USB drive
 * Use the Live USB Creator to install a bootable image to the USB drive
 * Copy the [updated bios](wy0035.bio) onto the USB drive
 * F7 to enter BIOS update, select BIOS file from USB
 * Boot and it finds the USB drive, boot to fedora live
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
