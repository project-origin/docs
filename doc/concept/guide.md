# The hitchhikers guide to ProjectOrigin

This is the hitchhikers guide page, which will try to guide you through the documentation
and help you get started with ProjectOrigin, what it is, and how it works.

## Why

- [Overview of why](./overview.md) - An overview of why ProjectOrigin was created.

## Cryptography and Zero-Knowledge Proofs

Before we start, let's go through some basic cryptographic concepts that are used in ProjectOrigin.

- [Signature](./signature.md) - A way to prove that a message is authentic and has not been tampered with.
- [Pedersen Commitment](./pedersen-commitment.md) - A way to commit, share and calculate on values, without revealing the it.
- [Zero-Knowledge Proof](./zero-knowledge.md) - A way to prove that you know something, without revealing what you know.

## Granular certificate and Transactions

Now that we know the basic cryptographic concepts, let's go through the basic building blocks of ProjectOrigin.

- [Granular Certificates](./granular-certificates/readme.md) - A certificate that holds a quantity of energy in a slice.
- [Transactions](./transactions.md) - A transaction is a request to change the state of a stream grouped into blocks.
- [Verifier](./verifier.md) - A **system** that verifies the validity of a transaction.

## Merkle tree and Blockchain

Now that we know how transactions work, let's go through how to ensure tamper-evidence.

- [Merkle Tree](./merkle-tree.md) - A tree of hashes, which enables proof of inclusion and tamper-evidence.
- [Blockchain](./blockchain.md) - Blocks chained together to form a blockchain to ensure tamper-evidence.
- [Registry](./registry.md) - A **system** that holds the state of a streams and processes transactions.

## Federated network

Now that we know how a single registry works, let's go through how multiple registries can work together.

- [Federated Network](./federated-network.md) - A network of registries that can communicate and share transactions.
- [Orchestration](./orchestration.md) - A way to manage and coordinate the execution of multiple transactions across multiple streams.
- [Wallet (Concept)]() - A **concept** that holds the private keys, users data and signs transactions.
- [WalletSystem](./wallet.md) - A **system** that holds the private keys, users data and signs transactions.

## Advanced concepts

Now that we know the basics, let's go through some more advanced concepts.

- [Chronicler]() - A **component** that records claims to ensure statistical data.

