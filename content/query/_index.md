---
title: "CamQuery"
date: 2018-01-28T21:48:57+01:00
anchor: "query"
weight: 90
---

The concept behind CamQuery is described in our [CCS'18 paper](http://camflow.org/publications/ccs-2018.pdf).

{{% block note %}}
This section is under construction as we work further on this aspect of the project.
If you encounter any difficulty, please contact [Thomas Pasquier](http://tfjmp.org)!
{{% /block %}}

We assume a machine with CamFlow newly installed and running.
To build and load the demo query, do as follow:
```
git clone https://github.com/camflow/libcamquery
cd libcamquery
make build
make load
```

You may need to install dependencies such as `elfutils-libelf-devel`.

To test that the query has been properly loaded:
```
dmesg
```

You should see the following entries:
```
Provenance: loading new query... (My Example Query)
Hello World!
Provenance: registering policy hook...
```

By default CamFlow does not generate provenance. We are going to change its configuration (more info [here](https://github.com/CamFlow/documentation/blob/master/docs/configuration.md)).
```
sudo camflow -a true
sudo camflow -a false
```

Those commands turned on and off whole-system provenance capture. You now run:
```
dmesg
```
You should see a list of edges and vertices.
