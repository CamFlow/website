---
title: "Capture configuration"
date: 2018-01-28T21:55:52+01:00
anchor: "capture"
weight: 1
---

## Sample configuration

One of the strengths of CamFlow is the ability to fine-tune the provenance information it captures.
Edit `/etc/camflow.ini` to modify the capture configuration.
To apply a new configuration, reboot the machine.

{{% block tip %}}
Alternatively when developing policy you can experiment using `camflow` CLI (see `camflow -h`).
Policies defined through the CLI are not persisted in current release.
{{% /block %}}

Follows a sample `/etc/camflow.ini` configuration:

``` INI
[provenance]
;unique identifier for the machine, use hostid if set to 0
machine_id=0
;enable provenance capture
enabled=true
;record provenance of all kernel object
all=false
node_filter=directory
node_filter=inode_unknown
node_filter=char
node_filter=envp
; propagate_node_filter=directory
; relation_filter=sh_read
; relation_filter=sh_write
; propagate_relation_filter=write

[compression]
; enable/disable versioning
version=true
; enable node compression
node=true
; enable edge compression
edge=true
duplicate=false

[file]
;set opaque file
opaque=/usr/bin/bash
;set tracked file
;track=/home/thomas/test.o
;propagate=/home/thomas/test.o

[ipv4−egress]
;propagate=0.0.0.0/0:80
;propagate=0.0.0.0/0:404
;record exchanged with local server
;record=127.0.0.1/32:80

[ipv4−ingress]
;propagate=0.0.0.0/0:80
;propagate=0.0.0.0/0:404
;record exchanged with local server
;record=127.0.0.1/32:80


[user]
;track=vagrant
;propagate=vagrant
;opaque=vagrant

[group]
;track=vagrant
;propagate=vagrant
;opaque=vagrant

[secctx]
;track=system_u:object_r:bin_t:s0
;propagate=system_u:object_r:bin_t:s0
;opaque=system_u:object_r:bin_t:s0

[relay]
; those parameters set the size of the kernel relay buffer
; more info about relay here:
; https://www.kernel.org/doc/html/latest/filesystems/relay.html
; size of relay buffer is equal to (1 << buff_exp) * subuf_nb
; you may want to change this value if you observe event drops
; (i.e. graph with missing edges and nodes), you can check drops
; through the command:
; camflow --drop
; be careful when changing those values.
buff_exp=20
subuf_nb=8
```

## Configuration parameters

Following is a list of the parameters and their effects, broken down by section.
A "boolean" parameter accepts values "true" or "false".

### provenance

| parameter | description |
|-----------|-------------|
| `machine_id`  | unique identifier for the machine in provenance records, use hostid if set to 0 |
| `enabled`     | boolean; enable provenance capture? if false, the rest of the parameters do not matter |
| `all`         | boolean; capture provenance of all kernel objects? |
| `node_filter` | do not capture this kind of node (i.e. vertex) |
| `relation_filter`           | do not capture this kind of relation (i.e. edge) |
| `propagate_node_filter`     | do not propagate tracking through this kind of node (i.e. vertex) |
| `propagate_relation_filter` | do not propagate tracking through this kind of relation (i.e. edge) |

#### all

| value    | effect |
|----------|--------|
| `true`   | capture provenance for all objects |
| `false`  | capture no provenance except for indicated objects (specified via `file`, `ipv4-ingress`, etc.) |

In either case the provenance record is affected by:
- graph filters (`node_filter`, `propagate_node_filter`, etc.)
- any object marked `opaque`

#### node_filter

You can specify the node_filter parameter multiple times, with a different node type each time.
See [here](https://github.com/CamFlow/camflow-dev/blob/master/docs/VERTICES.md) for the list of supported node types.

#### relation_filter

You can specify the relation_filter parameter multiple times, with a different relation type each time.
See [here](https://github.com/CamFlow/camflow-dev/blob/master/docs/RELATIONS.md) for the list of supported relation types.

#### propagate_node_filter

As with node_filter, you can specify this parameter multiple times for various node types.

#### propagate_relation_filter

As with relation_filter, you can specify this parameter multiple times for various relation types.

{{% block note %}}
No provenance records are emitted for nodes (relations) indicated by `X_filter=Y`.
For nodes (relations) indicated by `propagate_X_filter=Y`, records will be emitted but tracking will not be propagated through them.
{{% /block %}}

### compression

"Compressing" provenance means emitting as few provenance records as possible to capture an interaction.
For example, if a process reads a file three times, then a compressed provenance record would contain only one read relation while a complete provenance record would contain three relations.

This is desirable if the goal of provenance collection is to build a provenance graph.
However, if you are trying to perform a security audit, then the fact and timing of multiple accesses may be of interest.
In this example compression may be undesirable.

| parameter | description |
|-----------|-------------|
| `node`      | boolean; if true only create a new version of an object to avoid a cycle, if false create a new version on any object state change (i.e. when receiving information from other objects) |
| `edge`      | boolean; if true do not repeat multiple consecutive edges of the same type |
| `duplicate` | boolean; if true publish the vertex pair associated with a relation when publishing that relation, if false omit any previously-published vertices |

### file

This describes provenance capture behavior for files.

| parameter | description |
|-----------|-------------|
| `opaque`    | provenance is not captured for any interactions with this file |
| `track`     | directly track any information flow to/from this file and any process resulting from its execution |
| `propagate` | transitively track any information flow to/from this file |

#### track

Use `track` if you want the provenance information to include every time this file is read or written.

#### propagate

Use `propagate` if you want the provenance information to track the flow of data out of this file, through other processes, into other files, etc.

### ipv4-egress

Track information leaving the system being monitored (`connect`).

| parameter | description |
|-----------|-------------|
| `propagate` | similar to file, but for data sent to this IPv4 address |
| `record`    | like `propagate`, but also capture packet content |

Specify an IPv4 address using the format `<ip>/<mask>:<port>`.

### ipv4-ingress

Track information entering the system being monitored (`bind`).

| parameter | description |
|-----------|-------------|
| `propagate` | see ipv4-egress |
| `record`    | see ipv4-egress |

### user

Like `file`, but for users.

| parameter | description |
|-----------|-------------|
| `opaque`  | similar to file, but for this username |
| `track`   | " |
| `propagate` | " |

### group

Like `file`, but for groups.

### secctx

Same as `file`, but for security contexts.

Specify a security context using the format of the main Linux Security Module of the system (see [here](https://selinuxproject.org/page/NB_SC) for SELinux).

{{% block note %}}
Further information about these parameters may be gleaned by perusing the [header files](https://github.com/CamFlow/camflow-dev/tree/master/security/provenance/include) in the kernel module.
{{% /block %}}

### relay

This set the size of the kernel relay buffer.

{{% block warning %}}
If you notice event losses, do adjust this parameters (this may happen with systems under heavy workload).
You can check the number of dropped events using `camflow --drop`.
{{% /block %}}
