# Hierarchical Deterministic Keys (HD Keys)

Wallets and endpoints employ Hierarchical Deterministic Keys (HD Keys) to ensure the uniqueness and security of keys used for each slice.
HD Keys allow for the generation of a sequence of keys from a parent key.
With HD keys we can generate any child private key from the parent private key, and the corresponding public key from the parent public key.
And any child public key from the parent public key.

This enables us to share the public key, where the other party can generate the child keys for, while the owner can generate the corresponding private keys for the child keys, as long as they know the position of the child key.

## BIP32

BIP32 and BIP44, defines hierarchical deterministic (HD) wallets. It allows the generation of a tree of cryptographic keys from a single master key, simplifying key management and backup. This standard is widely used in cryptocurrency wallets for enhanced security and convenience.

![BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032/derivation.png?raw=true)
</br>From the https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki

For more details, refer to the [BIP32 Document](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki).
