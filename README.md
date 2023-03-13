# BRF - Bpf Runtime Fuzzer

BRF is a coverage-guided fuzzer that aims to fuzz the runtime compononets of eBPF shielded by the verifier. BRF uses semantic-aware and dependency-aware input generation/mutation logic as well as generating syscalls to trigger the execution of eBPF programs to achieve the goal. The implementation of BRF is based on [Syzkaller](https://github.com/google/syzkaller).

## Required binaries/libraries for the image:

llvm-clang

libbpf

## Running BRF:

To start running BRF, use to the included config file, sample\_configs/bookworm\_brf\_core\_1.cfg. 
```
./bin/syz-manager -config sample\_configs/bookworm\_brf\_core\_1.cfg
```

In addition to a typical syzkaller config, virtfs is passed to qemu to share a host directory with the fuzzer. The directory will be used to store the eBPF programs generated by the fuzzer.

Four pseudo syscalls, "syz\_bpf\_prog\_open", "syz\_bpf\_prog\_load", "syz\_bpf\_prog\_attach" and "syz\_bpf\_prog\_run\_cnt", are enabled to generate and run eBPF programs.

To view BRF-specific statistics, open <http_server_address>/brf in a web browser.
