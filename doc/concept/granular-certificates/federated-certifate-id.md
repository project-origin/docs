---
uid: federated_certificate_id
---

# Federated Certificate ID

The **Federated Certificate ID** (FID) it is the unique identifier for a certificate.
It consist of two parts

- RegistryName:  identifier for which [registry](../registry.md) holds the certificate[^1].
- StreamId: Is the unique id of the certificate on the registry, it is a Uuid4.

[^1]: [Granular Certificate](readme.md)

This **Federated Certificate ID** is the unique identifier for a GC on the network,
since a Uuid4 is not guaranteed unique, therefore the FID should always be used.

## Registry Name

The RegistryName is an identifier for the specific [registry](../registry.md)
holding the GC.

A GC's whole lifecycle always exists on a single registry,
removing the need for the federated network to reach consensus,
since the holding registry has the full mandate to invoke changes on the GC.

The RegistryName is used to route commands to the correct registry,
as to remove the need for a lookup table to identify which registry a
GC lives on.

## Stream ID

The StreamID is the unique id of the certificate.

The term StreamID comes from the underlying [streams](../transactions.md#streams),
where all transactions on a GC is stored in a stream for the GC.

The StreamID is a Uuid4, and is the unique identifier for a GC on a registry.
