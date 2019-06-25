---
title: "Vagrant"
date: 2018-01-28T21:54:02+01:00
anchor: "vagrant"
weight: 20
---

Using a vagrant virtual machine is much simpler. First you need to install [vagrant](https://www.vagrantup.com/docs/installation/) and [virtualbox](https://www.virtualbox.org/manual/ch02.html).

On Ubuntu, for example, that can be done as follows:
``` BASH
sudo apt-get install virtualbox
sudo apt-get install vagrant
```

{{% block warn %}}
Some Linux distributions ship very outdated version of VirtualBox or Vagrant.
Outdated versions, and host/guest version mismatch are known to cause all sorts of troubles during provisioning.

Please check [Vagrant](https://www.vagrantup.com/downloads.html) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads) for details on how to install the latest version.
{{% /block %}}

Once vagrant and virtualbox are installed, you need to obtain CamFlow vagrant provision script:
``` BASH
git clone https://github.com/CamFlow/vagrant.git
cd ./vagrant
```

There are different provisioning scripts available within the `CamFlow/vagrant.git` repository: please see in the [camflow/vagrant](https://github.com/CamFlow/vagrant) for details on what they do. We will use the `rpm` provisioning script as an example:
``` BASH
cd ./basic-fedora
vagrant plugin install vagrant-vbguest
vagrant up
# we reboot after the provisioning
vagrant halt
vagrant up
```


{{% block warn %}}
Running virtual machines is resource consuming. Please, make sure the host has sufficient resource to do so (disk space, RAM, CPU etc.).
{{% /block %}}

## After Reboot

When booting a VM after successful provisioning, ensure that the CamFlow kernel is chosen in the [GRUB](https://www.gnu.org/software/grub/) menu.
