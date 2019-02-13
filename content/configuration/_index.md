---
title: "Configuration"
date: 2018-01-27T15:42:17+01:00
anchor: "configuration"
weight: 70
---

One of the strengths of CamFlow is the ability to fine-tune the provenance information it captures.
Edit `/etc/camflow.ini` to modify the capture configuration.
To apply a new configuration, reboot the machine.

{{% block tip %}}
Alternatively when developing policy you can experiment using `camflow` CLI (see `camflow -h`).
Policies defined through the CLI are not persisted in current release.
{{% /block %}}
