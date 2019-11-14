# minishift
All tips, commands and troubleshooting about minishift

# Table of Contents
1. [Getting Started - Installation](#install)

<a name="install"/>

# Getting Started - Installation
This tutorial is focused to whom use virtualbox. Steps to whom use ubuntu 18-10 or later. To others OS, go to https://docs.okd.io/latest/minishift/getting-started/setting-up-virtualization-environment.html.
* Get the binary to your OS on https://github.com/minishift/minishift/releases.
* Install the virtualization dependency.
```
sudo apt install qemu-kvm libvirt-daemon libvirt-daemon-system
```
* Add myselft to libvirt(d):
```
sudo usermod -a -G libvirt $(whoami)
```
* Update current session to apply the group change
```
newgrp libvirt
```
