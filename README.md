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
systemctl enable sddm

flatpak install flathub org.gnome.Extensions
flatpak run org.gnome.Extensions
sudo dnf install grub-custom*
grub-customizer

dnf copr enable nunodias/whatsapp-for-linux
dnf install whatsapp-for-linux

install set-gdm-wallpaper 
remind the script need to change to support 
gnome-shell-light.css
gnome-shell-dark.css

#plymouth
sudo plymouth-set-default-theme -R "hexa_retro"


j@nbjal03:~$ cat /etc/gdm/Xsetup
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode eDP-1 "1920x1080_60.00"
xrandr --output eDP-1 --mode "1920x1080_60.00"
xrandr --newmode "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync
xrandr --addmode DVI-I-1 "1920x1080_50.00"
xrandr --output DVI-I-1 "1920x1080_50.00"

sudo chmod +x /etc/gdm/Xsetup

#install latest driver
sudo dnf install xorg-x11-drv-intel

#copy video into 
/usr/share/videos/hongkong

#to add video into screensaver
install 
plasma-smart-video-wallpaper-reborn

for the SDDM video modification, found the QtMultimedia need to do quite a lot of works
Need to change the Main.Qml to make it comptible
the source is uploaded for reference

To change the logo for KDE
in file

sudo vi /etc/xdg/kcm-about-distrorc

[General]
LogoPath=/usr/share/pixmaps/hklogo5.png
Name=HKOS
Website=https://www.linkedin.com/in/jame-l-a2320323/
Version=40.1

To change logot in GNOME
sudo mkdir -p /usr/share/icons/hicolor/128x128/apps
sudo cp /path/to/your-logo.svg /usr/share/icons/hicolor/128x128/apps/hkoso.svg
sudo gtk-update-icon-cache /usr/share/icons/hicolor

sudo nano /etc/os-release

NAME="HKOS"
VERSION="40.1"
ID=hkos
PRETTY_NAME="HKOS 40.1"
LOGO=hkos
HOME_URL="https://www.linkedin.com/in/jame-l-a2320323/"

sudo chmod 644 /usr/share/icons/hicolor/128x128/apps/hkos.svg

##kdeconnect not working
very difficult

it is only binded in the IPV6 and need to recompile
sudo dnf groupinstall "Development Tools"
sudo dnf install cmake qt5-qtbase-devel kf5-kdbusaddons-devel kf5-ki18n-devel kf5-knotifications-devel git extra-cmake-modules gcc-c++
git clone https://invent.kde.org/network/kdeconnect-kde.git
cd kdeconnect-kde
nano core/backends/lan/lanlinkprovider.cpp

 const QHostAddress bindAddress = m_testMode ? QHostAddress::LocalHost : QHostAddress::AnyIP;
 to
const QHostAddress bindAddress = m_testMode ? QHostAddress::LocalHost : QHostAddress::AnyIPv4;
sudo dnf install kf6-kirigami-addons-devel
sudo dnf copr enable @kde-frameworks/kde-frameworks-6
sudo dnf install qt6-qtbase-devel cmake extra-cmake-modules pulseaudio-libs-devel kf6-kcoreaddons-devel

git clone https://invent.kde.org/libraries/pulseaudio-qt.git
cd pulseaudio-qt
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
sudo make install

sudo dnf install qt6-qtwayland-devel
 sudo ln -s /usr/lib64/qt6/libexec/qtwaylandscanner /usr/bin/qtwaylandscanner
 sudo chmod 755 /usr/bin/qtwaylandscanner 

sudo dnf install wayland-devel

sudo dnf install wayland-protocols-devel
sudo dnf install dbus-devel
sudo dnf install qt6-qtbase-devel kf6-kwindowsystem-devel kf6-kdbusaddons-devel cmake extra-cmake-modules
git clone https://invent.kde.org/frameworks/kstatusnotifieritem.git
cd kstatusnotifieritem

sudo dnf install kf6-kstatusnotifieritem-devel
sudo dnf install qt6-qtmultimedia-devel
sudo dnf install kf6-kcrash-devel kf6-ki18n-devel kf6-kconfigwidgets-devel kf6-kdbusaddons-devel kf6-kiconthemes-devel kf6-knotifications-devel kf6-kio-devel kf6-kcmutils-devel kf6-solid-devel kf6-kirigami-devel kf6-kpeople-devel kf6-kguiaddons-devel kf6-kdoctools-devel
sudo dnf install qt6-qtconnectivity-devel
sudo dnf install libfakekey-devel
sudo dnf install qt6-qtbase-devel qt6-qtwayland-devel wayland-devel wayland-protocols-devel

ln -s /usr/lib64/qt6/libexec/moc /usr/bin/moc

in CMakeLists.txt
# Include the private directory
include_directories(/usr/include/qt6/QtGui/6.8.2/QtGui/private)

change coding for 
 vi ~/Downloads/kdeconnect-kde/declarativeplugin/pointerlockerwayland.cpp
#include <QtWaylandClient/QWaylandClientExtension>  // Ensure this is included

class PointerConstraints : public QWaylandClientExtensionTemplate<PointerConstraints, 1>  // Version 1 for zwp_pointer_constraints_v1
{
    Q_OBJECT
public:
    PointerConstraints() : QWaylandClientExtensionTemplate<PointerConstraints, 1>(1) {}
};
Q_DECLARE_WAYLAND_EXTENSION(PointerConstraints, QtWayland::zwp_pointer_constraints_v1)

class RelativePointerManagerV1 : public QWaylandClientExtensionTemplate<RelativePointerManagerV1, 1>  // Version 1 for zwp_relative_pointer_manager_v1
{
    Q_OBJECT
public:
    RelativePointerManagerV1() : QWaylandClientExtensionTemplate<RelativePointerManagerV1, 1>(1) {}
};
Q_DECLARE_WAYLAND_EXTENSION(RelativePointerManagerV1, QtWayland::zwp_relative_pointer_manager_v1)




#Facial Recognition
Enable repository
dnf copr enable principis/howdy

Install howdy
dnf --refresh install howdy

Configure your camera
Find all video devices:

$ ls /dev/video*

Configure howdy:

sudo howdy config
# or use your favorite text editor
sudo vim /lib64/security/howdy/config.ini

Change device_path to your camera.

device_path = /dev/video2

You can test if you've chosen the correct camera by running howdy test and see if the IR emitters turn on.

Configure PAM
Configure howdy for sudo
Add the following line to the top of /etc/pam.d/sudo

auth       sufficient   pam_python.so /lib64/security/howdy/pam.py

Configure howdy for kde lockscreen
Modify /etc/pam.d/kde so it looks like this:

$ cat /etc/pam.d/kde
auth     [success=done ignore=ignore default=bad] pam_selinux_permit.so
auth        sufficient      pam_python.so /lib64/security/howdy/pam.py
auth        substack      password-auth
...

Your lockscreen might not be running Howdy as root, which prevents Howdy from running. Setting the execution bit so every user can run Howdy might be the solution

chmod o+x /lib64/security/howdy/dlib-data

Configure howdy for login (sddm)
Modify /etc/pam.d/sddm so it looks like this:

$ cat sddm
auth     [success=done ignore=ignore default=bad] pam_selinux_permit.so
auth        sufficient   pam_python.so /lib64/security/howdy/pam.py
auth        substack      password-auth
...

See below to apply SELinux and permission fixes.

Configure howdy for login (gdm)
Modify /etc/pam.d/gdm-password so it looks like this:

$ cat gdm-password
auth     [success=done ignore=ignore default=bad] pam_selinux_permit.so
auth        sufficient    pam_python.so /lib64/security/howdy/pam.py
auth        substack      password-auth

See below to apply SELinux and permission fixes.

Permission issues
Your lockscreen might not be running Howdy as root, which prevents Howdy from running. Setting the execution bit so every user can run access dlib-data should solve this:

chmod o+x /lib64/security/howdy/dlib-data

 
cd ~/Downloads/kdeconnect-kde/build
rm -rf *
cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
sudo make install

install the intel video driver

sudo dnf install libva libva-utils intel-media-driver intel-gpu-tools

Need to use 
howdy-beta - principis - Fedora Copr
instead of non-howdy stable, it uses python2.x and cannot work with fedora 40

also, need to install by following the web page below 

https://copr.fedorainfracloud.org/coprs/principis/howdy-beta/

need to steps as below

change the device
sudo howdy config 
change devicepath


sudo howdy add -U j
sudo howdy test 

need to change the /etc/pam.d/sudo config

auth       required   pam_howdy.so
auth       required   pam_unix.so

so it need to d facial + password to trigger sudo 

add this in /etc/pam.d/kde
auth       sufficient   pam_howdy.so

add this in /etc/pam.d/sddm
auth     [success=done ignore=ignore default=bad] pam_selinux_permit.so
auth        sufficient     pam_howdy.so

add this in gdm-password
auth     [success=done ignore=ignore default=bad] pam_selinux_permit.so





