plymouth-theme-ubuntu
======================

A plymouth theme (boot progress) for Ubuntu

#Installation instructions
==========================

##Ubuntu8

####Install
```bash
sudo cp -r ubuntu8 /lib/plymouth/themes/ubuntu8
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu8/ubuntu8.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all
```
####Logo choosing
You can choose between 2 different logo's to use.

![logo1](ubuntu8/logo.png) default

![logo2](ubuntu8/logo_other.png) more Windows 8 like

To change to the second logo, rename `logo_other.png` to `logo.png` and that's it!

####Screenshot
![screenshot](screenshot/ubuntu8.png)


##Ubuntu faded

####Install

```bash
sudo cp -r ubuntu-faded /lib/plymouth/themes/ubuntu-faded
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-faded/ubuntu-faded.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all
```
####Screenshot
![screenshot](screenshot/ubuntu-faded.gif)


#Fix plymouth for AMD/Nvidia VGA card
=====================================
In Grub press C and enter ``vbeinfo``. It will show supported resolutions    
Boot Ubuntu and run terminal:    
```bash
sudo apt-get install -y vd86
sudo gedit /etc/default/grub
```
After line ``#GRUB_GFXMODE=640x480`` write ``GRUB_GFXPAYLOAD_LINUX=1920x1080-32`` (here your supported resolution)    
Next in terminal:
```bash
echo "FRAMEBUFFER=y" | sudo tee -a /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all
sudo update-grub
```
Reboot and look at that beautiful screen again.
