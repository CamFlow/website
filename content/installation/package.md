---
title: "Package manager"
date: 2018-01-28T21:55:52+01:00
anchor: "package"
weight: 10
---

The quickest way to install CamFlow is through the packages hosted on [packagecloud](https://packagecloud.io/camflow/provenance). For now, only Fedora is supported (please, click on this [link](https://packagecloud.io/camflow/provenance) and check which release(s) is/are currently supported).

{{% block note %}}
We also [distribute packages for Ubuntu](https://packagecloud.io/app/camflow/provenance/search?dist=ubuntu%2Fbionic),
but they are more sparsely tested, **we strongly encourage the use of Fedora**.
{{% /block %}}

### Fedora

``` BASH
curl -s https://packagecloud.io/install/repositories/camflow/provenance/script.rpm.sh | sudo bash
sudo dnf -y install camflow
```

### After installing packages


Next we need to activate the two CamFlow services:

``` BASH
sudo systemctl enable camconfd.service
sudo systemctl enable camflowd.service
```

After reboot we should be ready to use CamFlow.

``` BASH
sudo reboot now
```

{{% block warn %}}
Packages are tested in virtual environment with a limited set of configurations.
In most cases things work fine.
However, if you encounter any issue, please do look at how to build the project from source.
{{% /block %}}
