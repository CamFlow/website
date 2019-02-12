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
sudo dnf install ncurses-devel cmake clang gcc-c++ wget git openssl-devel zlib patch mosquitto bison flex ruby
```

For Fedora 28 and above, also run:

``` BASH
sudo dnf install elfutils-libelf-devel
```

#### Ubuntu

``` BASH
sudo apt-get -y install build-essential
sudo apt-get -y install libncurses-dev cmake clang g++ wget git libssl-dev bc nano patch mosquitto bison flex ruby
```

On more recent Ubuntu releases you should also run:

``` BASH
sudo apt-get -y install libelf-dev
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
Configuration options need to be carefully considered in resource constrained environment.
{{% /block %}}

For the installation process to take effect you need to reboot the machine.

``` BASH
sudo reboot now
```

You can install older release of CamFlow as follow:

``` BASH

git clone https://github.com/CamFlow/camflow-install
cd camflow-install
make v0.4.2
sudo reboot now
```

Replace `v0.4.2` by your desired target version.

{{% block note %}}
Only the most recent release is actively supported.
{{% /block %}}
