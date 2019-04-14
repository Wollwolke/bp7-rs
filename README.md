# bp7-rs
Rust implementation of dtn bundle protocol 7 draft https://tools.ietf.org/html/draft-ietf-dtn-bpbis-12

This library only handles encoding and decoding of bundles, not transmission or other processing of the data.

This is more or less a port of the dtn7 golang implementation: https://github.com/geistesk/dtn7

**This code is not production ready!**

## Benchmarking

A simple benchmark is shipped with the library. It (de)serializes Bundles with a primary block, bundle age block and a payload block with the contents (`b"ABC"`). This benchmark can be used to compare the rust implementation to the golang, python or java implementations. 

```
cargo run --release --example benchmark
    Finished release [optimized] target(s) in 0.29s
     Running `target/release/examples/benchmark`
Creating 100000 bundles with CRC_NO: 	148974 bundles/second
Creating 100000 bundles with CRC_16: 	105303 bundles/second
Creating 100000 bundles with CRC_32: 	105042 bundles/second
Loading 100000 bundles with CRC_NO: 	90988 bundles/second
Loading 100000 bundles with CRC_16: 	135833 bundles/second
Loading 100000 bundles with CRC_32: 	137769 bundles/second
```

These numbers were generated on a MBP 13" 2018 with i5 CPU and 16GB of ram.