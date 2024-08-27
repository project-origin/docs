---
uid: pedersen_commitment
---

# Pedersen Commitments

> ## tl;dr
> A Pedersen Commitment is a [homomorphic encryption](https://en.wikipedia.org/wiki/Homomorphic_encryption)
> which enables one to perform calculations on the encrypted data.
>
> The number (`m`) is encrypted using a random value (`r`) which outputs the commitment (`c`).
>
> Commitments enables calculations like `C = C1 * C2` (simplified) where one can verify that
> `C` contains the **sum** of the two messages in `C1` and `C2`.
>
> This enables Project-Origin to prove that the sum of [GC slices](granular-certificates/readme.md?slices)
> are the same as the slice they were created from.

To obfuscate the quantity of energy in the [GCs](./granular-certificates/readme.md) so that only the owner can verify them, we use Pedersen commitments.
A Pedersen commitment lets someone commit to a value without showing what that value is.
You can check the commitment using two pieces of information: `m` (the value) and `r` (a random number).
This scheme is special because enabled two commitments to be `added` together, and the resulting commitment represents the sum of the two original values.

## Pedersen commitments are defined as follows:

| identifier | property   | usage                                        | accessability |
| ---------- | ---------- | -------------------------------------------- | ------------- |
| `c`        | commitment | the commitment itself                        | public        |
| `m`        | message    | the message that is being committed to       | private       |
| `r`        | randomness | the randomness used to commit to the message | private       |

$$c=C(m,r)$$

Where `C`is the commitment function, `m` is the message being committed to, and `r` is a random value used to commit to the message.

## Secure - one-way function

The commitment is a one-way function, meaning that it is easy to compute the commitment given `m` and `r`, but it is computationally infeasible to find `m` given `c` and `r`.

## Homomorphic property

The Pedersen commitment scheme has a homomorphic property.
This enables one to perform calculations on the encrypted data, like adding (`*`) or subtracting (`/`) the commitments.

Below C(m1,r1) and C(m2,r2) are two commitments, and C(m1+m2,r1+r2) is the commitment to the sum of the two messages.

$$C(m1,r1) * C(m2,r2) = C(m1+m2,r1+r2)$$

## Sigma proofs

This also enables us to prove that two commitments subtracted from each other are equal to a commitment to 0.

This is used when we will be splitting the value of a certificate into several commitments, and we want to prove that the sum of the commitments is equal to the committed value in the original production certificate.

$$C´= C_{\text{original}} ~/~ (C_{\text{sliceA}} * C_{\text{sliceB}})$$

`C´` is the commitment to the value of 0, using this, we can prove that the sum of the slices is equal to the original certificate.

This can also be used to prove that two certificates are equal, by subtracting the commitments.

$$C´= C_{\text{certificateA}} ~/~ C_{\text{certificateB}}$$

### Additional reading

[Here](./advanced/pedersen-commitment-extended.md) is some additional info about the Pedersen commitment scheme.

A thorugh description of the Pedersen commitment scheme can be found in the [Pedersen Commitment Scheme](https://crypto.stackexchange.com/questions/64437/what-is-a-pedersen-commitment) article on the crypto.stackexchange forum.

The Pedersen commitment scheme is extensively described in the following paper and proceedings:[Non-Interactive and Information-Theoretic Secure Verifiable Secret Sharing](https://rdcu.be/cWS5M)
