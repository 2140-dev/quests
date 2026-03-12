The current state for bitcoin light clients is to use compact block filters ([BIP-158](https://en.bitcoin.it/wiki/BIP_0158)). A good blog to understand them intuitively exists [here](https://ellemouton.com/posts/bip158/). At the time of writing, the disk space required for the index is 12GB, which results in reasonable bandwidth tradeoffs for high privacy; however, one downside is each filter has unique keys for hashing. This creates a CPU bottleneck for clients, limiting the effectiveness of this protocol on mobile devices.
## Research Questions

- Does there exist a compact sketch that does not require (as much) hashing with a sketch size? Note the unique keys are required so attackers cannot maliciously construct scripts.
- Is there a deterministic data structure that would also be compact, but does not require hashes at all?
- Can we do better by querying a range of blocks?

This is an open-ended project, but regardless of the approach, you will likely find the [`bitcoinkernel`](https://docs.rs/bitcoinkernel/latest/bitcoinkernel/) bindings useful.