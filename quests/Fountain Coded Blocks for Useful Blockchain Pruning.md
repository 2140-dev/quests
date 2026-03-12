Pruned nodes are nodes that do not store the full archival history of blocks. These nodes are useful for use cases like creating block templates, however they are currently not useful in bootsrapping new nodes that come online. The following paper describes a scheme for nodes to prune data , yet still assist in initial block download of new nodes: https://arxiv.org/pdf/1906.12140 

## Components

- [ ] Implement the probably distribution in the paper described in the paper to determine how many blocks to XOR per epoch in Rust
- [ ] Use the new [consensus encoding](https://github.com/rust-bitcoin/rust-bitcoin/tree/master/consensus_encoding) crate to build a "droplet" struct that encodes a set of blocks. Either multiple blocks or the singleton block
- [ ] Parse the signet chain using [the bitcoin kernel bindings](https://docs.rs/bitcoinkernel/latest/bitcoinkernel/) and create droplets using the new type according to your probability distribution. Save each droplet to a file (no database is required)
- [ ] Repeat the step above for your desired reduction in total storage. For instance if you wish to reduce local data requirements by 10x, repeat roughly 11 times. Attempt to reconstruct the chain using these droplets.