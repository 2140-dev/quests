# Compressed Blocks

For a subset of users, likely many, their initial block download will be limited by bandwidth.
The current encoding of a bitcoin block is particularly wasteful in bytes. Take the `version` field for instance, which uses 4 bytes, even though there are 3 standard versions.
Using a generic compression algorithm, `zstd` in this example, we find that as much as 24% bandwidth savings is possible (note each block was compressed individually):
```
=== zstd level 22 on 10000 random blocks in [480000, 930000] ===
Total original:   12839650447 bytes
Total compressed: 9719379328 bytes
Aggregate ratio:  0.7570  (savings 24.30%)
```

- Can we develop a compression scheme or more efficient encoding to speed up IBD without placing too much of a burden on serving peers?
- Can a grouping of blocks aid in compression further?
