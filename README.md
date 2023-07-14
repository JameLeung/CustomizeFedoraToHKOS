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


