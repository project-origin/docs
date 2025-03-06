---
uid: federated_certificate_id
---

# Federated Certificate ID

The **Federated Certificate ID** (FID) it is the unique identifier for a certificate.
It consist of two parts

- RegistryName: An identifier for which [registry](../registry.md) holds the certificate[^1].
- StreamId: The identifier for the certificate within that registry, as a UUID4.

[^1]: [Granular Certificate](readme.md)

While UUID4s are designed to be practically unique, they are not mathematically guaranteed to be unique.

Because of this, the **Federated Certificate ID** (FID) (which combines the RegistryName with the StreamID) should always be used as the definitive unique identifier for a certificate across all registries.

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

The StreamID is the identifier for a certificate, within a registry.

The term StreamID comes from the underlying [streams](../transactions.md#streams),
where all transactions on a GC is stored in a stream for the GC.

The StreamID is a Uuid4, which provides a very high probability of uniqueness within a registry.

However, because a UUID4 is generated randomly and cannot be guaranteed to be unique in absolute terms, it is used in conjunction with the RegistryName to form the globally unique FID.
