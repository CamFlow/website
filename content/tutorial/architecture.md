---
title: "Architecture overview"
date: 2018-01-28T21:55:52+01:00
anchor: "overview"
weight: 1
---

[![CamFlow architecture overview](./images/arch.png "CamFlow architecture overview")](./images/arch.pdf)

__CamFlow capture mechanism:__ CamFlow is an implementation of the [whole-system provenance concept](http://patrickmcdaniel.org/pubs/acsac12.pdf).
The idea is to perform provenance capture from the OS perspective, while providing guarantees about its completeness.
This is achieved by relying on the OS [reference monitor](https://en.wikipedia.org/wiki/Reference_monitor) that interpose between user level applications and kernel objects.
CamFlow is implemented in the Linux kernel and relies on the [Linux Security Module framework](https://www.kernel.org/doc/Documentation/security/LSM.txt) and the [NetFilter framework](https://en.wikipedia.org/wiki/Netfilter) to effect the interposition.
[source code](https://github.com/CamFlow/camflow-dev)

__camflowd:__ `camflowd` is a daemon charged of recording the provenance captured  in the kernel by CamFlow.
The provenance records are published by CamFlow to [relayfs](https://lwn.net/Articles/174669/) pseudo files.
The daemons retrieve those records, serialise them to a configuration-specified format and write them to a configuration-specified output.
[source code](https://github.com/CamFlow/camflowd)

__camconfd:__ `camconfd` is a daemon charge with configuring the in-kernel capture mechanism.
The configuration daemon reads from `/etc/camflow.ini` and load the specified configuration into the kernel via a [securityfs](https://lwn.net/Articles/153366/) interface.
[source code](https://github.com/CamFlow/camconfd)

__camflow-cli:__ CamFlow CLI (`camflow`) allows to dynamically modify the capture configuration through the command line.
[source code](https://github.com/CamFlow/camflow-cli)

__libprovenance:__ is a C library implementing userspace utility functions to interact with CamFlow [relayfs](https://lwn.net/Articles/174669/) and [securityfs](https://lwn.net/Articles/153366/) interfaces.
[source code](https://github.com/CamFlow/libprovenance)
