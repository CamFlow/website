---
title: "Examples"
date: 2018-01-28T21:55:52+01:00
anchor: "examples"
weight: 10
---

_Example of an inode vertex in W3C PROV format:_
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
_Example of an inode vertex in SPADE JSON format:_
```
{
  "type":"Entity",
  "id":"ACAAAAAAACDZtAAAAAAAAAEAAACVwxEABgAAAAAAAAA=",
  "annotations":
  {
    "object_id":"46297",
    "object_type":"socket",
    "boot_id":1,
    "cf:machine_id":"cf:1164181",
    "version":6,"cf:date":"2020:07:11T10:41:28",
    "epoch":2,
    "uid":0,
    "gid":0,
    "mode":"0xc1ff",
    "secctx":"system_u:object_r:unlabeled_t:s0",
    "ino":18274,
    "uuid":"00000000-0000-0000-0000-000000000000"
  }
}
```


_Example of a write edge in W3C PROV format:_
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

_Example of a write edge in SPADE JSON format:_
```
{
  "type":"WasGeneratedBy",
  "from":"ABAAAAAAACCi2wAAAAAAAAEAAACVwxEAAQAAAAAAAAA=",
  "to":"AQAAAAAAAECk2wAAAAAAAAEAAACVwxEACQAAAAAAAAA=",
  "annotations":
  {
    "id":"IAAAAAAAQID0CwAAAAAAAAEAAACVwxEAAAAAAAAAAAA=",
    "relation_id":"3060",
    "relation_type":"write",
    "boot_id":1,
    "cf:machine_id":"cf:1164181",
    "cf:date":"2020:07:11T10:41:28",
    "epoch":2,
    "jiffies":"4294759940",
    "allowed":"true",
    "flags":"2",
    "task_id":"56228",
    "from_type":"pipe",
    "to_type":"task"
  }
}
```

{{% block note %}}
Vertex and edge attributes within the `prov:` namespace are described in the [W3C PROV-JSON documentation](https://www.w3.org/Submission/2013/SUBM-prov-json-20130424/).
The permissible values for the `prov:type` are described [for relations](https://github.com/CamFlow/camflow-dev/blob/master/docs/RELATIONS.md) and [for vertices](https://github.com/CamFlow/camflow-dev/blob/master/docs/VERTICES.md).
We describe in the next section the attributes within the `cf:` (**C**am**F**low) namespace.
{{% /block %}}
