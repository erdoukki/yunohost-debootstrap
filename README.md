# yunohost-debootstrap
This script allow you to create yunohost installation with debootstrap.

# debian and ubuntu

## Setup on debian

```
sudo apt install debootstrap
git clone https://github.com/YunoHost/yunohost-debootstrap
sudo cp yunohost-debootstrap/yunohost /usr/share/debootstrap/scripts/
```

## Additional equirements on ubuntu

```
sudo apt install debian-archive-keyring
```

## Patch debootstrap on debian
You may need to patch debootstrap like this (not needed on ubuntu, nor on openwrt):
```
sed -i "s@#\!/bin/bash@#\!/bin/sh@" /usr/sbin/debootstrap
```

## Test it
```
mkdir ynh_chroot
sudo debootstrap --include="acpi-support-base,kbd,udev,linux-image-amd64,openssh-server,ca-certificates,debhelper" yunohost ./ynh_chroot/ https://deb.debian.org/debian/
```

# openwrt

## Setup on openwrt
```
opkg update
opkg install bash debootstrap git git-http
git clone https://github.com/YunoHost/yunohost-debootstrap
cp yunohost-debootstrap/yunohost /usr/share/debootstrap/scripts/
```

## Test it on openwrt
```
mkdir ynh_chroot
bash debootstrap --arch=arm64 --include="openssh-server,ca-certificates,debhelper" --no-check-gpg --no-check-certifica
te --verbose yunohost ./ynh_chroot/ https://deb.debian.org/debian/
```
