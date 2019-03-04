---
title: "Package manager"
date: 2018-01-28T21:55:52+01:00
anchor: "package"
weight: 10
---

The quickest way to install CamFlow is through the packages hosted on [packagecloud](https://packagecloud.io/camflow/provenance). For now, only Fedora and Ubuntu are supported (please, click on this [link](https://packagecloud.io/camflow/provenance) and check which release(s) is/are currently supported). The rest of this section describes how to install CamFlow and its dependencies on Fedora and Ubuntu.

### Fedora

``` BASH
curl -s https://packagecloud.io/install/repositories/camflow/provenance/script.rpm.sh | sudo bash
sudo dnf -y install camflow
```

### Ubuntu
``` bash
curl -s https://packagecloud.io/install/repositories/camflow/provenance/script.deb.sh | sudo bash
sudo apt-get install -y libprovenance=0.4.6-2
sudo apt-get install -y camflowd=0.2.3-2
sudo apt-get install -y camflow-cli=0.1.13-2
sudo apt-get install -y camconfd=0.4.4-2
sudo apt-get install -y linux-libc-dev=4.20.13camflow0.5.3+-1
sudo apt-get install -y linux-image-4.20.13camflow0.5.3+=4.20.13camflow0.5.3+-1
sudo apt-get install -y linux-headers-4.20.13camflow0.5.3+=4.20.13camflow0.5.3+-1
```

{{% block note %}}
Check [online](https://packagecloud.io/camflow/provenance) to find the latest version number and update the above script accordingly.
{{% /block %}}

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

{{% block note %}}
We are a small research team. Packages are tested in virtual environment running over a limited set of hardware configurations. In most cases things work fine. However, if you encounter any issue, please do look at how to build the project from source.
{{% /block %}}
