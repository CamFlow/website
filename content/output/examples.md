---
title: "Examples"
date: 2018-01-28T21:55:52+01:00
anchor: "examples"
weight: 10
---

_Example of an inode vertex:_
```
"ABAAAAAAACAe9wIAAAAAAE7aeaI+200UAAAAAAAAAAA=": {
    "cf:id": "194334",
    "prov:type": "fifo",
    "cf:boot_id": 2725894734,
    "cf:machine_id": 340646718,
    "cf:version": 0,
    "cf:date": "2017:01:03T16:43:30",
    "cf:jiffies": "4297436711",
    "cf:uid": 1000,
    "cf:gid": 1000,
    "cf:mode": "0x1180",
    "cf:secctx": "unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023",
    "cf:ino": 51964,
    "cf:uuid": "32b7218a-01a0-c7c9-17b1-666f200b8912",
    "prov:label": "[fifo] 0"
}
```

_Example of a write edge:_
```
"QAAAAAAAQIANAAAAAAAAAE7aeaI+200UAAAAAAAAAAA=": {
    "cf:id": "13",
    "prov:type": "write",
    "cf:boot_id": 2725894734,
    "cf:machine_id": 340646718,
    "cf:date": "2017:01:03T16:43:30",
    "cf:jiffies": "4297436711",
    "prov:label": "write",
    "cf:allowed": "true",
    "prov:activity": "AQAAAAAAAEAf9wIAAAAAAE7aeaI+200UAQAAAAAAAAA=",
    "prov:entity": "ABAAAAAAACAe9wIAAAAAAE7aeaI+200UAQAAAAAAAAA=",
    "cf:offset": "0"
 }
```

{{% block note %}}
Vertex and edge attributes within the `prov:` namespace are described in the [W3C PROV-JSON documentation](https://www.w3.org/Submission/2013/SUBM-prov-json-20130424/).
The permissible values for the `prov:type` are described [for relations](https://github.com/CamFlow/camflow-dev/blob/master/docs/RELATIONS.md) and [for vertices](https://github.com/CamFlow/camflow-dev/blob/master/docs/VERTICES.md).
We describe in the next section the attributes within the `cf:` (**C**am**F**low) namespace.
{{% /block %}}
