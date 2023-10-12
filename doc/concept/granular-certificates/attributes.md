# Attributes

A Granular Certificate has a series of attributes, currently split into two categories,
[primary](#primary-attributes) and [secondary](#secondary-attributes).

## Primary attributes

**Primary attributes** are always present on the certificate.

### Federated CertificateID

Is a [Federated Certificate ID](federated-certifate-id.md), it is the unique identifier for a certificate.
It consist of two parts
- RegistryName: identifier for which [registry](../registry.md) holds the certificate.
- StreamId: Is the unique id of the certificate on the registry, it is a Uuid4.

Together they form a unique identifier for the certificate across all registries.

### Grid Area

The term *Grid area* was chosen instead of *Bidding zone*. The reason for this was to not tightly couple
the system with the current bidding zones, as these areas could be based on other zonees at a later point in time.

Each Issuing body has a number of areas assigned to them, and only they are able to issue
valid GCs for these areas, and only their private key is allowed to sign issuing transactions.

The grid area is used to enforce rules on the registry about how one can claim a production GC
to a consumption GC.

### Period

The period of a GC describes the period of time in between the energy was produced/consumed.

The period consists of two values, a **Start** and **End** timestamp in **unix format**.

Start is considered inclusive and End exclusive,
so to represent 1 whole hour from 10 to 11 on the 5th of January 2022,
the values would contain the following:

|       | Iso8601           | Unix       |
| ----- | ----------------- | ---------- |
| Start | 2022-01-05T10:00Z | 1641376800 |
| End   | 2022-01-05T11:00Z | 1641380400 |

### Quantity

The quantity attribute describes a whole number in **Wh** of the energy flowing through the meter in the period specified.

To ensure the privacy and hide the quantity, the value is hidden using a [Pedersen Commitment](../pedersen-commitments.md).

---

## Secondary attributes

**Secondary attributes** are optional attributes that can be added to the certificate.

Rules may be defined on the registry to enforce which attributes must be present on a certificate, or which attributes are allowed.

Attributes can be defined as different types:
- **Cleartext**: Is visible to everyone.
- **Hashed**: Where only a checksum of the value is visible, so the value can be verified, but not read.

### Examples of common secondary attributes

#### AIB TechCode and FuelCode (production only)

Contains a tech and fuel code, as described in the [AIB Fact sheet 5](https://www.aib-net.org/sites/default/files/assets/eecs/facts-sheets/AIB-2019-EECSFS-05%20EECS%20Rules%20Fact%20Sheet%2005%20-%20Types%20of%20Energy%20Inputs%20and%20Technologies%20-%20Release%207.7%20v5.pdf)
This standard can describe which type of generation unit and which kind of fuel was used in the production of the energy.

Since there was an existing and well-known standard to describe this, Project-Origin chose to follow this standard.

#### AssetId

The AssetId is a unique identifier for the asset that produced or consumed the energy.

This is a free-form string, and can be anything that uniquely identifies the asset.

### Governance

Most of these rules are up to the governance around the federated network to agree upon.
