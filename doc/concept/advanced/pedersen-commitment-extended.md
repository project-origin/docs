# Pedersen commitment extended

Here is some additional information about the Pedersen commitment scheme.

## Group definition:

In order to be able to produce and validate the commitments, we need to define a group. The group is defined as follows:

`G` is a cyclic group of prime order `q` with generator `g`. Let * denote the group operation. We will refter to `*`as multiplication even though in some groups (e.g., elliptic curves) this is often called addition of points on the curve.

### Commitment definition

Given the group G the commitment scheme requires two domain parameters `g`and `h` which are both generators of G. These must be selected independently at random.

A commitment to a message `m`, which is a number between 0 and q-1 is done by selecting `r` at random (also between 0 and q-1) and computing the commitment as `C(m,r) = g^m * h^r`.

A commitment is opened and proven to contain message, `m`, by revealing `r`.

As the commitment is an element of G, two commitments `C1 = C(m1, r1)` and `C2 = C(m2, r2)` can be multiplied in G and the result, `C1 * C2`, will be a commitment to the number `(m1 + m2) modulo q`.

## Future work

Making the Pedersen commitment scheme more efficient by using a more efficient group based on eliptic curve cryptography.
