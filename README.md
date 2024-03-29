# minishift
All tips, commands and troubleshooting about minishift. This tutorial is focused to whom use virtualbox.

# Table of Contents
1. [Getting Started - Installation](#install)
   1. [Installing Virtualization Lib](#libvirt)
   1. [Start libvirtd Service](#start_virtualization_service)

<a name="install"/>

# Getting Started - Installation

<a name="libvirt"/>

## Installing Virtualization Environment
Steps to whom use ubuntu 18-10 or later. To others OS, go to https://docs.okd.io/latest/minishift/getting-started/setting-up-virtualization-environment.html.
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
* As root, install KVM driver
```
curl -L https://github.com/dhiltgen/docker-machine-kvm/releases/download/v0.10.0/docker-machine-driver-kvm-ubuntu16.04 -o /usr/local/bin/docker-machine-driver-kvm
chmod +x /usr/local/bin/docker-machine-driver-kvm
```

<a name="start_virtualization_service"/>

## Start libvirtd Service
* Check the status of libvirtd
```
systemctl is-active libvirtd
```
* If status is inactive, start it as follow:
```
sudo systemctl start libvirtd
```
* Check if network status is OK
```
sudo virsh net-list --all

Name                 State      Autostart     Persistent
---------------------------------------------------------
default              active     yes           yes
```
* If state is not active or autostart is no, execute as the follow:
```
sudo virsh net-start default
sudo virsh net-autostart default
```
