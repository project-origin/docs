# Zero knowledge proof

Zero-knowledge proofs are a way to prove that you know something, without revealing what you know.
This is done by creating a proof that can be verified by others, without revealing the secret information.

This is an advanced cryptographic concept, which we won't go into detail about here, only a simple explanation of how it can be used in
ProjectOrigin.

> [!Video https://www.youtube.com/embed/V5uVKZn3F_4?si=l2xeRz5zET3yDKh0]

For abstract examples of zero-knowledge proofs, see [Wikipedia](https://en.wikipedia.org/wiki/Zero-knowledge_proof).

## Sigma proof

In ProjectOrigin, zero-knowledge proofs are used to ensure that proofs to zero are correct.
This is used to ensure that the sum of the quantities in a certificate is correct, without revealing the actual values of the energies,
and without revealing the randomness used in the commitments.

More in depth information about how this is done can be found in the [ZKProof Specification](./zk-proof.md#sigma-proof).

## Range proof

Zero-knowledge proofs can also be used to ensure that a value is within a specific range.
This is used to ensure that the quantities in a certificate are non-negative, and that the sum of the energies add up correctly.
If one could create negative quantities, a split of a certificate could be used to create energy out of nothing,
therefore it is important to ensure that the quantities are non-negative.

More in depth information about how this is done can be found in the [ZKProof Specification](./zk-proof.md#range-proof).

## External resources

More info can also be found [here](https://medium.com/coinmonks/zero-knowledge-proofs-um-what-a092f0ee9f28).

And [here](./advanced/zk-proof.md).
