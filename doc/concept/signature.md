# Signature

A signature is a way to prove that a message is authentic and has not been tampered with.
It is a cryptographic technique that uses a `private key` to sign a message and a `public key` to verify the signature.
The signature is **unique to the message and the private key**, which means that it cannot be forged or tampered with.

## How does it work?

A signature is created by taking a message and using a private key to generate a unique signature.
The signature is then attached to the message and sent to the recipient.
The recipient can use the public key to verify the signature and ensure that the message has not been tampered with.

Below is an example of it from wikipedia, where Alice signs a message with her private key and sends it to Bob.

![Signature](https://upload.wikimedia.org/wikipedia/commons/a/a7/Private_key_signing.png)
</br> FlippyFlink, CC BY-SA 4.0 <https://creativecommons.org/licenses/by-sa/4.0>, via Wikimedia Commons

## Algorithms used in ProjectOrigin

### ED25519

ProjectOrigin uses the ED25519 signature scheme for issuers, which is based on the elliptic curve cryptography.
It is a fast and secure signature scheme that provides strong security guarantees.
The ED25519 signature scheme is widely used in the industry and is considered to be one of the most secure signature schemes available.

It is used for issuers to sign transactions that issue certificates.
The public key is known to all participants, and the private key is kept secret by the issuer.
The signature is used to prove that the certificate was issued by the issuer and has not been tampered with.

### SECp256k1

ProjectOrigin also allows the use of SECp256k1 signature scheme for ownership of certificates,
which is also based on the elliptic curve cryptography.
It is also the signature scheme used in Bitcoin.
It enables hierarchical deterministic keys (like described in [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki)), so that a single key can be used to derive a tree of keys.
