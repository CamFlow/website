---
title: "Provenance graph"
date: 2018-01-28T21:54:02+01:00
anchor: "graph"
weight: 1
---

CamFlow represents the execution of a system as a directed acyclic graph.
Vertices in the graph represent states of kernel objects (e.g. threads, files, sockets etc...) and relations represent flow of information between those states.

[![CamFlow graph overview](./images/graph.png "CamFlow graph overview")](./images/graph.pdf)

In the above example `process 1` clones `process 2`.
`process 2` writes to a `pipe`.
`process 1` reads from the same `pipe`.
Versions are created to guarantee acyclicity and to represent proper ordering of information (see our [CCS'18 paper](http://camflow.org/publications/ccs-2018.pdf) for details).

{{% block note %}}
Further description of the provenance are discussed in the [output section](#output_format).
{{% /block %}}
