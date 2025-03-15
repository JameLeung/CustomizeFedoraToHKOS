# CustomizeFedoraToHKOS
To customize the Fedora OS to your whole OS (Using my favourate setting HKOS as example)

cd /usr/share/plymouth/themes/spinner
sudo cp <any photo you like>.png watermark.png 

in /usr/share/pixmaps/, overridden following files

fedora_logo.png
fedora_logo.png

In the boot menu, it is not saved in /boot/grub2/grub.cfg

It is save in the directory 
/boot/loader/entries
the file would be like this 

0ee8eed5efe5498f95ae1200a7baae6a-6.3.12-100.fc37.x86_64.conf

Change all config inside and will make it right 

Install Google Earth
https://www.google.com/earth/about/versions/#earth-pro

Install WPS Office
https://www.wps.com/

Install Github access and download
gh auth login

Install Fonts file
06_NotoSansCJKjp.zip
07_NotoSansCJKkr.zip
09_NotoSansCJKtc.zip
10_NotoSansCJKhk.zip
15_NotoSansMonoCJKhk.zip

Install GIMP plugin
curl -L https://github.com/Diolinux/PhotoGIMP/releases/download/1.0/PhotoGIMP.by.Diolinux.v2020.for.Flatpak.zip

Install DarkSquares
https://www.gnome-look.org/p/1000129

Download Displaylink
sudo dnf install   https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install   https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install fedora-40-displaylink-1.14.8-1.github_evdi.x86_64.rpm

Multimedia
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
sudo dnf install vlc vlc-plugins*

Environment
dnf install @kde-desktop-environment
sudo dnf install kdm
systemctl disable gdm
systemctl enable kdm




