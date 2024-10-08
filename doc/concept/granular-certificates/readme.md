---
uid: granular_certificate
---

# Granular Certificate

**Granular Certificate** is a term defined by the [EnergyTag Organization](https://energytag.org).

It is a goal for the **Project-Origin** to be **Compliant with the EnergyTag Standard**

## Description

In Project-Origin, a Granular Certificate (GC) can describe either a **production or consumption** of energy at a meter [^et].

[^et]: In the EnergyTag scheme a GC only relates to the production of energy,
    consumption verification is done with the help of a *consumption verification body*.

A GC consists of two parts:

- A immutable "header" which is the [collection of attributes](attributes.md) on the GC.
  These data **cannot be changed** after the GC has been issued.
  These attributes describe all the properties on the GC,
  like the [grid area](attributes.md#grid-area),
  [time period](attributes.md#period)
  or which [asset](attributes.md#assetid) the GC originates from.

- A collection of [slices](#slices), when a GC is [issued](transactions/issue.md),
  it is created with 1 initial slice.
  An active slice contains two values, the **quantity** of the slice, and the **owner's public-key**.
  All transactions on an existing GC and the life-cycle happens through the slices.

![Sketch of the GCs two parts.](gc.drawio.svg)

---

## Slices

As described above, a GC is immutable, and contains the entire quantity measured at the meter for the period,
***so how could trading and claiming parts of a certificate work?***

To solve this, Project-Origin borrowed a term from the financial sector, **stock-slicing**,
where a single stock can be traded as slices. This happens on top of the existing stock market.

This was implemented as a core part of the architecture of the GC system in Project-Origin.
A GC consists of **1 to n slices**, when the GC is issued, **one initial slice** is created.
Similar to baking a cake, "1 slice (whole cake)" exists.

When a GC is issued, it is created with a single initial slice.

A slice is always owned by a single public-key.[^public-key]

[^public-key]: Public-private keys was chosen since the registries do not have the concept of accounts and users. Ownership of a GC is purely done with the help of a public-private key pair.
It is up to the integrating system to implement an accounting system and manage ownership through public-private keys.

A slice can be uniquely identified by its commitment,
[this was chosen as they were already unique and to save on adding another field with no added value.](https://github.com/orgs/project-origin/discussions/19#discussioncomment-5719035)

### Slice life-cycle

A slice has a specific life-cycle. When the slice is created, it becomes **active**.

When the owner wants to perform any action on the slice, they need to create a [transaction](../transactions.md#transactions).
Note that most transactions are final, in there is no way to reverse them once performed.

Below is a diagram of the life-cycle of a slice given transactions that can be performed on it.

```mermaid
stateDiagram-v2
    [*] --> Active
    Active --> Removed: Slice
    Active --> Active: Transfer
    Active --> Allocated: Allocate
    Allocated --> Claimed: Claim

    note right of Removed
        Removed slices are <b>not</b>
        counted when calculating the total,
        since new slices representing the
        amount was created.
    end note

    note left of [*]
        A slice can be created by an IssueCommand to create a new GC.
        Or a SliceCommand on an existing GC slice to create new slices.
    end note
```

- [Issue transaction](transactions/issue.md): Used by an **Issuing Body** to issue a new GC.
- [Transfer transaction](transactions/transfer.md): Transfers the ownership of an existing slice to a new owner.
- [Slice transaction](transactions/slice.md): Enables the owner to create any number of new slices from an exsting slice.
- [Allocate and claim transaction](transactions/claim.md): Claim a production slice to a consumption slice of same quantity.
