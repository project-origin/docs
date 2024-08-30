# Concordium

Concordium is a public, proof-of-stake blockchain that prioritizes privacy and regulatory compliance.
It features built-in identity verification at the protocol level, ensuring that transactions are both private and traceable.
Concordium aims to provide a secure and transparent platform for businesses and developers to build decentralized applications.

## Immutable log

Concordium has a publishData function that allows for the publishing of data to the blockchain, where it is immutable and can be verified by anyone.
We use this to publish the block header from the registry to the Concordium blockchain, to ensure that the data is tamper-evident and can be verified by anyone.

## Concordium node

To interact with the Concordium blockchain, you need to run a Concordium node.
The node is responsible for validating transactions, maintaining the blockchain, and participating in the consensus protocol.
The node also provides an API for interacting with the blockchain, allowing you to query the blockchain, submit transactions, and more.

## Concordium wallet

To perform transactions on the Concordium blockchain, one needs a Concordium wallet, which holds ones CCD, the native token of the Concordium blockchain.
Every transaction on the blockchain requires a fee, which is paid in CCD.

## Operational notes

In the Registry Chart, there is the posibility to enable the Concordium system,
which will run a node connected to the network.

On startup the node will take some time to sync and catch up with the network,
while it is syncing it will not be able to process transactions.
