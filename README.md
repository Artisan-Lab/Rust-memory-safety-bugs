# rustbugs



| Project | CVE-ID (or Src) | Link | Culprit | Consequense | Details | Propagated | Finder |
|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | 2018-1000810 | pull/54399 | IMP:ARO | OOR:BO | arithmatic overflow + unsafe write | No | scottmcm-Rust |

OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; CC: concurrency issue; DF: double free; DL: data leakage; DP: dangling pointer; DR: data race; RC: race condition; UAF: use-after-free.
