# Network

Project-Origin chose to go with a federated distributed network to make the system
scalable and to allow for multiple parties to participate in the network.

A **network is a collection of registries**, where each registry is a **node** in the network.

The network is governed by an authority or group,
where the current group is [Energy Track and Trace](https://github.com/Energy-Track-and-Trace),
which are defining a set of rules that apply for the electricy GCs and which rules apply to be part of the network.

All these rules defined **must** be implemented as software and will be enforced by the nodes (verifiers) in the network.

The configuration for a network must be defined in a configuration file that is shared among all nodes in the network,
and publically available for anyone to verify against.

## Network configuration

The configuration of the network must define the ruleset for the network and all the nodes in the network.

This makes the network a permissioned network, where only nodes that are invited can participate in the network.

The configuration file must be publically available so anyone can verify the ruleset and the nodes in the network.
