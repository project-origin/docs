# Registry and federated network

## What is a Registry?

In ProjectOrigin a registry is a single node in the federated network.

A Registry main responsibility is to hold and ensure the rules of the network are applied to the data it holds,
and provide a tamper-evident[^tamper] log of all changes to the data.

[^tamper]: Tamper-evident ensures it is possible to detect if the data has been changed, but cannot prevent it.
Any system can be tampered with, but the goal is to make it detectable and hold the hosting part accountable.

Each registry can hold any number of [GCs](../granular-certificates/readme.md).
It is up to the issuing body[^ib] to specify which registry to put a GC on
at the time of issuance with the help of the [Federated Certificate ID](../granular-certificates/federated-certifate-id.md)

[^ib]: The issuing body is the entity that has the legal right to issue GCs within a given area.

The life-cycle of a single GC always stays within the same registry as to ensure atomic operations on the GC
and reduce the need for distributed transactions.

In practice this makes each registry the authority of what is the truth for the current state of a GCs held within it.

Some transactions like [claim](../granular-certificates/transactions/claim.md)
does span multiple registries, but are performed as a distributed transaction using a saga pattern.

### Registry != Area

GCs for the same [area](../granular-certificates/attributes.md#grid-area)
can exist on different registries, as well as GCs for multiple areas can
exists on the same registry.

The registry is, simply put, a node in a network holding and ensuring the
rules of the network are applied, but there is no hard rule on how these should be split.

## Federated network

Project-Origin chose to go with a federated network to ensure that the network as to ensure
that a network can be governed by a group of entities, which can ensure in follows current law and legislation.

A network of registries is a federated network, where each registry is a node in the network.

A federated network is governed by an authority or group,
where the current group is [Energy Track and Trace](https://github.com/Energy-Track-and-Trace),
which are defining a set of rules that apply for the electricy GCs and which rules apply to be part of the network.

All these rules are defined **must** be defined as software and will be enforced by the nodes in the network.
