# Additional Instructions for a TV box

- RPM Fusion repo: `sudo dnf install -y  https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm && sudo dnf install -y https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm`
- Kodi `sudo dnf -y install kodi`
- Make it autostart `mkdir -p ~/.config/autostart && cp /usr/share/applications/kodi.desktop ~/.config/autostart/ && chmod +x ~/.config/autostart/kodi.desktop`

- `dnf install -y nfs-utils`
- `firewall-cmd --permanent --add-service mountd && firewall-cmd --permanent --add-service rpc-bind && firewall-cmd --add-service=nfs --permanent && firewall-cmd --reload`
- `echo "/home 192.168.0.0/16(rw,no_root_squash,insecure)" >> /etc/exports`
- `sudo systemctl enable nfs && sudo systemctl restart nfs`
- `exportfs -r`
