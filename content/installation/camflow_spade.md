---
title: "CamFlow-SPADE"
date: 2019-10-11T20:05:00+01:00
anchor: "spade-camflow"
weight: 40
---

The team behind [SPADE](http://www.csl.sri.com/users/gehani/papers/MW-2012.SPADE.pdf) at [SRI](http://www.csl.sri.com/people/gehani/) have worked on a SPADE reporter for CamFlow.
It brings CamFlow generated data at runtime or from audit traces stored on disk into the SPADE ecosystems.
SPADE supports a number of storage backends (e.g. [Neo4J](https://github.com/ashish-gehani/SPADE/wiki/Storing-provenance-in-a-Neo4j-graph-database), [PostgreSQL](https://github.com/ashish-gehani/SPADE/wiki/Storing-provenance-in-a-relational-database#postgresql) etc.), mechanisms to [visualize provenance](https://github.com/ashish-gehani/SPADE/wiki/Viewing-provenance) and a [query framework](https://github.com/ashish-gehani/SPADE/wiki/Querying-SPADE).
Please, visit SPADE's [website](https://github.com/ashish-gehani/SPADE/wiki/Collecting-system-wide-provenance-on-Linux-with-CamFlow) for further instructions.

{{% block note %}}
We are providing a [vagrantfile](https://github.com/CamFlow/vagrant/tree/master/spade) to easily experiment with CamFlow-SPADE integration.
Please do report any issues to the [SPADE](https://github.com/ashish-gehani/SPADE/issues) and [CamFlow](https://github.com/CamFlow/camflow-dev/issues) teams.
{{% /block %}}
