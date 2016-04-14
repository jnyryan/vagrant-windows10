# vagrant-windows10

A windows 10 virtual machine setup to run under VagrantUp and VirtualBox


## Prerequisites

You'll need both these to get going.

- Install [git - the source control tool ](https://git-scm.com/downloads)
- Install [VirtualBox - free virtualization software ](https://www.virtualbox.org/wiki/Downloads)
- Install [Vagrant - a tool easily manage and create virtual machines from online images ](https://www.vagrantup.com/)

## Usage

1. Download the virtual box Windows 10 image and add it to the Vagrant Library
``` bash
wget -O ~/Downloads/win10x64Pro.box http://1drv.ms/1RVqzCv
vagrant box add win10x64Pro ~/Downloads/win10x64Pro.box
```
2. Download this repository containing the Vagrant scripts
```
git clone https://github.com/jnyryan/vagrant-windows10.git
cd vagrant-windows10
```
3. Start the VM
```
vagrant up
```
After a minute of the provisioning process the VM will start up.
4. All done, then shut it down
```
vagrant halt
```
or destroy it
```
vagrant destroy
```

## Creating your own Vagrant Base image

This is a WIP of creating a Windows 10 VM.

Method

- Download ISO from [microsoft](https://www.microsoft.com/en-gb/software-download/windows10)
- Create a VirtualBox virtual Machine with Windows 10 installed
- Configure it to be used with Vagrant
  - create user and pwd as vagrant
  - get latest updates
  - change it's name to VagrantPC
  - Reduce the size of the image
- Create the vagrant "box"
- add the box to your vagrant library
- Create a Vagrantfile so start it up


1.
  http://huestones.co.uk/node/305

  http://kamalim.github.io/blogs/how-to-create-you-own-vagrant-base-boxes/

  http://www.mynetworks.me/2015/08/02/windows-10-built-in-administrator-account-issues/

  Reduce the size of the image

  [Reduce-the-size-of-your-windows-10-installation-using-compact](http://winaero.com/blog/reduce-the-size-of-your-windows-10-installation-using-compact-exe/)

  Export the vmand import it again to shrink it

  https://www.maketecheasier.com/shrink-your-virtualbox-vm/

  C:\Windows\System32\cleanmgr.exe /d c:
  sdelete.exe -z c:
  VboxManage clonehd name-of-original-vm.vdi name-of-clone-vm.vdi

### Package the box

```
cd </usr/location/of/image>
vagrant package --base win10x64Pro-vagrantbase --output win10x64Pro.box
vagrant box add win10x64Pro win10x64Pro.box
```

### Repackage the box after making additions

```
cd </usr/location/of/image>
vagrant package --output win10x64ProUpdate.box
vagrant box add win10x64ProUpdate win10x64ProUpdate.box
```
