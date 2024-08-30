# Stamp

System to simplify issuing certificates on the Project Origin platform.

In the Project-Origin Electricity implementation a Granular Certificate consists of a fungible and non-fungible digital assets.
The non-fungible part are the information on the GC, all the attributes on it.
The fungible assets are called GC slices and contain the owner information and the amount in the slice.

The GCs are issued by an issuer and are stored in a registry. And an owner keeps track of their ownership of GC slices in a wallet.
The process of issuing a GC is a complex process that involves multiple systems, to simplify this process, the OriginStamp is created.

It will enable an issuer to issue GCs using a simple REST API, and OriginStamp will take care of the complexity of the process.

## Problem

Each entity that issues GCs has to implement a system that can handle the issuing process,
which is a multi-step process that involves multiple systems.

1. The issuer first issues the certificate to the registry
2. Once the registry is finalized the issuer sends the information to the receivers wallet
3. The receivers wallet can then verify the information against the registry and store it.

More info about the process can be found [here](./receive-slice.md).

There is also a multitude of security aspects which should be handled by the issuer to ensure the integrity and privacy of the data.
Therefore a common system to handle the issuing process was needed.

## Solution

The solution is to have a system that can handle the issuing process and offload the all the cryptographic complexity and multi-step process from the issuer.

OriginStamp will enable an issuer to issue GCs using a simple REST API,
and OriginStamp will take care of the complexity of the process.

![Stamp](../stamp/stamp-system.drawio.svg)


