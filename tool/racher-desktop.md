# Rancher Desktop Installation on Alma Linux 10

```bash

cd ~/Downloads

[ -r /dev/kvm ] && [ -w /dev/kvm ] || echo 'insufficient privileges'

gpg --generate-key

pass init <generated-key>

sudo usermod -a -G kvm "$USER"

sudo sysctl -w net.ipv4.ip_unprivileged_port_start=80
echo "net.ipv4.ip_unprivileged_port_start=80" | sudo tee -a /etc/sysctl.conf


wget https://download.opensuse.org/repositories/isv:/Rancher:/stable/AppImage/rancher-desktop-latest-x86_64.AppImage

sudo chmod +x ~/Downloads/rancher-desktop-latest-x86_64.AppImage

~/Downloads/rancher-desktop-latest-x86_64.AppImage --appimage-extract

sudo mv ~/Downloads/squashfs-root /opt/rancher-desktop

sudo chown -R $USER:$USER /opt/rancher-desktop

mkdir -p ~/.config/autostart
vim ~/.config/autostart/rancher-desktop.desktop


[Desktop Entry]
Type=Application
Name=Rancher Desktop
Exec=/opt/rancher-desktop/AppRun
Icon=/opt/rancher-desktop/usr/share/icons/hicolor/256x256/apps/rancher-desktop.png
Comment=Run Rancher Desktop on startup
X-GNOME-Autostart-enabled=true


sudo chmod +x ~/.config/autostart/rancher-desktop.desktop

```
