---
title: "Recording configuration"
date: 2018-01-28T21:55:52+01:00
anchor: "recording"
weight: 2
---

After CamFlow captures provenance, you can configure *where* and *in what format* the provenance information is published.

The configuration file is `/etc/camflowd.ini`.

To apply a new configuration, run `systemctl restart camflowd.service`.

## Sample configuration

Here is a sample `/etc/camflowd.ini` configuration.

``` INI
[general]
;output=null
;output=mqtt
;output=unix_socket
;output=fifo
output=log

format=w3c
;format=spade_json

[log]
path=/tmp/audit.log

[mqtt]
address=m12.cloudmqtt.com:17065
username=camflow
password=test
; message delivered: 0 at most once, 1 at least once, 2 exactly once
qos=2
; topic, provided prefix + machine_id (e.g. camflow/provenance/1234)
topic=camflow/provenance/

[unix]
address=/tmp/camflowd.sock

[fifo]
path=/tmp/camflowd-pipe
```

## Configuration parameters

Following is a list of the parameters and their effects, broken down by section.

### general

| parameter | description |
|-----------|-------------|
| `output`  | where to publish provenance records? |
| `format`  | in what format to publish provenance records? |

#### output

| value   | effect |
|---------|--------|
| `null`  | discard provenance records |
| `mqtt`  | publish to an MQTT service |
| `unix_socket` | publish to a UNIX socket |
| `fifo`  | publish to a named pipe ("FIFO") |
| `log`   | publish to a log file |

#### format

| value | effect |
|-------|--------|
| `w3c`        | use [w3c PROV-JSON](./w3c.md) format |
| `spade_json` | use [SPADE JSON](https://github.com/ashish-gehani/SPADE/wiki/Reporting-provenance-using-JSON) format |

### log

If `output=log`, these parameters take effect.

| parameter | description |
|-----------|-------------|
| `path`      | publish to this file |

### mqtt

If `output=mqtt`, these parameters take effect.

| parameter   | description |
|-------------|-------------|
| `address`   | MQTT broker |
| `username`  | credentials |
| `password`  | credentials |
| `qos`       | delivery guarantees |

#### qos

For each record, publish to broker...

| value | effect |
|-------|--------|
| 0     | at most once  |
| 1     | at least once |
| 2     | exactly once  |

### unix\_socket

If `output=unix_socket`, these parameters take effect.

| parameter | description |
|-----------|-------------|
| `address`   | publish to the socket at this path |

### fifo

If `output=fifo`, these parameters take effect.

| parameter | description |
|-----------|-------------|
| `path`    | publish to the fifo at this path |
