The [SwiftSync](https://github.com/2140-dev/swiftsync-bips/blob/master/swiftsync.md) draft BIP describes an _aggregate_ that is the sum of hashes, which represent elements in a set. Two of these aggregates are compared at the end of the protocol. If they are equivalent, verification succeeds, otherwise, verification fails. More formally, the client generates a $salt$ and computes $SHA256_{salt}$ of the coin data. The digest is interpreted as an unsigned 256 bit integer.

For a set of coins $A = \{Coin_{0}, .., Coin_{n}}$, we define $Agg_{A} = H_{salt}(Coin_{0}) + .. + H_{salt}(Coin_{n})$.

Is it possible to show that this aggregate is provably secure against a probabilistic polynomial time algorithm? i.e. can an attacker create a set $B$, such that $Agg_{A} = Agg_{B}$ and $A \neq B$

For more detail, see the [adHashT](./files/adHashT.pdf).
