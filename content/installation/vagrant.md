---
title: "Vagrant"
date: 2018-01-28T21:54:02+01:00
anchor: "vagrant"
weight: 30
---

Using a vagrant virtual machine is much simpler. First you need to install [vagrant](https://developer.hashicorp.com/vagrant/install) and [virtualbox](https://www.virtualbox.org/manual/ch02.html).

On Ubuntu, for example, that can be done as follows:
```bash
sudo apt-get install virtualbox
sudo apt-get install vagrant
```

{{% block warn %}}
Some Linux distributions ship very outdated versions of VirtualBox or Vagrant.
Outdated versions, and host/guest version mismatch are known to cause all sorts of troubles during provisioning.

Please check [Vagrant](https://developer.hashicorp.com/vagrant/install) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads) for details on how to install the latest version.
{{% /block %}}

Once vagrant and virtualbox are installed, you need to obtain CamFlow vagrant provision script:
``` bash
git clone https://github.com/CamFlow/vagrant.git
cd ./vagrant
```

There are different provisioning scripts available within the `CamFlow/vagrant.git` repository: please see in the [camflow/vagrant](https://github.com/CamFlow/vagrant) for details on what they do. We will use the `rpm` provisioning script as an example:
``` bash
cd ./rpm
vagrant plugin install vagrant-vbguest
vagrant up
# we reboot after the provisioning
vagrant reload
```
You can customize the `Vagrantfile` to personalize your experience.


{{% block warn %}}
Running virtual machines is resource-consuming. Please, make sure the host has sufficient resources to do so (disk space, RAM, CPU etc.).
{{% /block %}}
