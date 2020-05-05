---
title: "From source"
date: 2018-01-28T21:54:02+01:00
anchor: "source"
weight: 20
---

### Dependencies

First we need to install the dependencies required to build our kernel.

Depending on how recent your OS version is, you should install `libelf-dev`, `libelf-devel`, or `elfutils-libelf-devel`.
See this [issue](https://github.com/CamFlow/documentation/issues/3) for details.

#### Fedora

``` BASH
sudo dnf groupinstall 'Development Tools'
sudo dnf install ncurses-devel cmake clang gcc-c++ wget git openssl-devel zlib patch mosquitto bison flex ruby dwarves elfutils-libelf-devel
```

#### Ubuntu

``` BASH
sudo apt-get -y install build-essential
sudo apt-get -y install libncurses-dev cmake clang g++ wget git libssl-dev bc nano patch mosquitto bison flex ruby dwarves libelf-dev
```

### Building and Installing the kernel

We first need to clone the `camflow-install` repository:

``` BASH
git clone https://github.com/CamFlow/camflow-install
```

We then get the installation started:
``` BASH
cd camflow-install
make all
```

This will build and install the CamFlow Linux Security Module as well as the userspace tools. The whole installation procedure may take a significant amount of time. The installation process may ask for the root password, so may not complete in an unattended manner.

The kernel configuration derives from the configuration currently present on the system where you run the build. Early in the build process you will be presented with a GUI to customise the kernel configuration. If you are not sure what to do, do not modify the configuration.

{{% block warn %}}
Configuration options need to be carefully considered in resource-constrained environment.
{{% /block %}}

{{% block warn %}}
Kernel version 5.1.x saw the modification of Linux Security Module stacking.
It is important to ensure that CamFlow is properly loaded and is processed last.

During the configuration stage, select the `Security options`:

![Select "Security options".](./images/security_options.png)

Then select the list at the bottom of the menu:

![Select the list at the bottom of the menu.](./images/list.png)

`provenance` should be listed and appear last:

![provenance should be listed and appear last.](./images/last.png)

If `provenance` is not listed, CamFlow module will simply not be loaded.

{{% /block %}}

For the installation process to take effect you need to reboot the machine.

``` BASH
sudo reboot now
```
