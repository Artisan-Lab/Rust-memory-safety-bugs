# rustbugs



| Project | CVE-ID (or Src) | Link | Culprit | Consequense | Details | Finder-Role | Propagated |
|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | 2018-1000810 | pull/54399 | IMP:ARO | OOR:BO | arithmatic overflow + unsafe write | scottmcm-Rust | No | 
| rust-std | 2018-1000657 | issues/44800 | IMP:LOE | BO | logical error + unsafe write (VecDeque) | jesse99-deps | 
| rust-std | 2019-12083 | issues/60784 | API:TRAIT | BO | soundness hole when impl Error::type_id() | seanmonstar-deps | No | 
| rust-std | Advisory-DB | issues/79808 | IMP:LOE | DP | logical error (VecDeque) | ayourtch | No | 
| rust-std | GitHub | issues/17207 | FFI (Imp) | UB | jemalloc: unchecked argument | gmorenz | No | 
| rust-std | GitHub | issues/25841 | IMP:ARO | UB$\to$DP | arithmatic overflow$\to$shared mut aliases (RefCell) | Veedrac | No | 
| rust-std | GitHub | issues/27970 | IMP:FFI+CC+SYS | CC$\to$UAF | setenv is unsafe | bluss-Rust | No | 
| rust-std | GitHub | issues/33770 | IMP:FFI+CC | UB | glibc recursive lock$\to$shared mut aliases | Amanieu | No | 
| rust-std | GitHub | issues/35836 | IMP:FFI+CC | UB | recursive RWlock on Windows is UB | retep998-Rust | No | 
| rust-std | GitHub | issues/39465 | API:MUT | UB$\to$DP | $\to$shared mut aliases | christophebiocca | No | 
| rust-std | GitHub | issues/39575 | API:SAFE+FFI | CC$\to$UB | UB according to POSIX | fweimer | No | 
| rust-std | GitHub | issues/42135 | IMP:LOE | UB | error related to unsafe trait | scottmcm-Rust | No | 
| rust-std | GitHub | issues/42789 | IMP:LOE+ZST | UB | inconsistant addresses for interators over ZST | RalfJung-Rust | No | 
| rust-std | GitHub | issues/43733 | IMP:SAFE+CC | UB | possible to bypass unsafe marker | eddyb-Rust | No | 
| rust-std | GitHub | issues/44637 | API:TRAIT | BO | soundness hole in when impl Placer | andy-hanson | No | 
| rust-std | GitHub | issues/45197 | IMP:LOE+CC | DR$\to$DP | allow concurrent acc. without sync/send | cuviper-Rust | No | 
| rust-std | GitHub | issues/46775 | IMP:FFI+CC | UAF | | Diggsey | No | 
| rust-std | GitHub | issues/48006 | IMP:SYS | BO | arithmatic overflow on 16-bit platforms | oberien | No | 
| rust-std | GitHub | issues/48493 | IMP:LOE | UNINIT | free uninitialized mem | jleedev | No | 
| rust-std | GitHub | issues/51780 | IMP:LOE+CC | DR$\to$DP | insufficient synchronization  | jhjourdan | No | 
| rust-std | GitHub | issues/54857 | IMP:LOE+ZST | UB | inconsistant addresses for ZST of Vec | jturner314 | No | 
| rust-std | GitHub | issues/54908 | IMP:LOE | OOR | misaligned reference | RalfJung | No | 
| rust-std | GitHub | issues/54957 | IMP:LOE | OOR | unsafe type conversion | RalfJung | No | 
| rust-std | GitHub | issues/57534 | IMP:SYS+CC+FFI | UAF | thread local variables | YES:mtak- | No | 
| rust-std | GitHub | issues/60977 | IMP:RAII:LOE | DF | inconsistency while exception handling | ExpHP | No | 
| rust-std | GitHub | issues/66544 | API:GENERIC+TRAIT | UB | soundness holes of Pin when impl DerefMut | comex |
| rust-std | GitHub | issues/67194 | API:GENERIC+TRAIT | | soundness holes when impl PartialEq | comex | No | 
| rust-std | GitHub | issues/76367 | IMP:RAII+CC | UB | logical error (SyncOnceCell/dropck+PhantomData) | m-ou-se-Rust |
| rust-std | GitHub | issues/78498 | IMP:LOE | UB | logical error for catch_unwind (String) | SkiFire13 | No | 
| rustc (compiler) | Advisory-DB | issues/25860 | RU:LIFE (API) | Unsound | type system issue$\to$lifetime inconsistency | No (aturon-Rust)| No | 
| arrayfire-rust  | 2018-20998  | issues/176 | GEN:FFI (Imp) | OOR:BO | FFI-compatability/repr() | No (Aidan24) | No | 
| ncurses | 2019-15547 | issues/172 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/printw() | thomcc | No | 
| ncurses | 2019-15548 | issues/186 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/instr(), mvwinstr() | thomcc |
| rusqlite | Advisory-DB | pull/708 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/sqlite3_log() | thomcc-deps| No | 
| rusqlite | Advisory-DB | issues/703 | RU:LIFE (API) | DP | func. sign.: lifetime declaration | No (gwenn-deps) | No | 
| rust-base64 | 2017-1000430 | issues/28 | GEN (Imp) | OOR:BO | arithmatic overflow + unsafe write | No (alicemaz) | No | 
| failure | 2020-25575 | issues/336 | RU:SAFE (API) | OOR:BO | downcast$\to$mem misalign/private_get_type_id() | No (Qwaz-sec) | No | 
| bumpalo | Advisory-DB | issues/69 | GEN (Imp) | OOR:BOR | wrong buffer size + unsafe write | No (Riey-deps)| No | 
| compact_arena  | 2019-16139 | issues/22 | RU:DROP (Imp) | OOR:BOR | NLL issue$\to$Index trait/get_unchecked() | No (CAD97) | No | 
| lz4_flex | Trophy | - | IMP:LOE | BO | logical error in space allocation | Pascal Seitz-sec | No | 
| ozone | Advisory-DB | RUSTSEC-2020-0022:1 | API:SAFE | OOR:BOR | context issue$\to$Index trait | No (n.a.) | No | 
| ozone | Advisory-DB | RUSTSEC-2020-0022:2 | RAII (Imp) | DP:DUN | implement drop with uninit mem | No (n.a.)| No | 
| prost | Advisory/Trophy | issues/267 | GEN (Imp) | OOR:BO | logical error in recursion + unsafe write | No (dbrgn-sec) | No | 
| safe-transmute | 2018-21000 | pull/36 | GEN (Imp) | OOR:BO | logical error + unsafe write | No (Enet4-deps)| No | 
| slice-deque | 2018-20995 | pull/58 | GEN (Imp) | OOR:BO | error in boundary check + unsafe write | No (aldanor-deps) | No | 
| slice-deque | 2019-15543 | pull/66 | GEN (Imp) | OOR:BO | logical error$\to$memory misalignment | No (zimond) | No | 
| rust-smallvec | 2019-15554 | issues/149 | IMP:GEN (Imp) | OOR:BO | logical error + unsafe write | No (ehuss) | No | 
| rust-smallvec | Advisory-DB | issues/126 | RAII:UNWIND (Imp) | DP:DUN | init vector with mem:uninitialized() | No (mbrubeck) | No | 
| rust-smallvec | 2019-15551 | issues/148 | GEN (Imp) | DP:UAF | logical error + unsafe deallocation | No (ehuss) | No | 
| rust-smallvec | 2018-20991 | issues/96 | RAII:UNWIND (Imp) | DP:DF | buffer shrinking too late | No (Vurich) | No | 
| simd-json | 2019-15550 | pull/27 | GEN (Imp) | OOR:BO | logical error$\to$mem misalign/get_unchecked() | No (Licenser-deps) | No | 
| v_espace | Trophy Case | issues/47 | IMP:GEN (Imp) | OOR:BO | logical error$\to$mem misalign | \_mm_load_si128() | No (tmiasko) | No | 
| sized-chunks | 2020-25791 | issues/11:unit | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | 2020-25792 | issues/11:pair | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | 2020-25793 | issues/11:From | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | 2020-25796 | issues/11:InlineArray | GEN (API) | OOR:BO | no input check$\to$memory misalignment | No (Qwaz-sec) | No | 
| sized-chunks | 2020-25794 | issues/11:clone | RAII:UNWIND (Imp) | DP:DUN | panic $\to$ drop uninitialized memory | No (Qwaz-sec)  | No | 
| sized-chunks | 2020-25795 | issues/11:insert_from | RAII:UNWIND (Imp) | DP:DUN | panic $\to$ rop uninitialized memory | No (Qwaz-sec)  | No | 
| actix-net | Advisory-DB | issues/91 |  | UAF | | sebzim4500 | No | 
| actix-net | Advisory-DB | pull/158 | API:RC | UB$\to$UAF | replace Cell with RefCell | Shnatsel  | No | 
| actix-net | Advisory-DB | issues/160 | API:RC | UB$\to$UAF | replace Cell with RefCell | Shnatsel | No | 
| actix-web | Advisory-DB | issues/289 | API:MUTE | UB:DP | transmute immutable ref to mutable | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | API:LIFE | DP | transmutate lifetime to static | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | IMP:TRAIT+GENERIC | DP | Clone+Rc | seanmonstar | No | 
| actix-web | Advisory-DB | issues/301 | API:CC+TRAIT+GENERIC | UAF | unsafe impl of Send for generics races Rc | seanmonstar-Mozilla | No | 
| actix-web | Advisory-DB | issues/1321 | API:PAR | UAF |  | sebzim4500 | No | 
| alg_ds | Advisory-DB | issues/1 | IMP:RAII | UNINIT | init with alloc::alloc | Qwaz-Sec | No | 
| rust-arch | Advisory-DB | issues/2 | IMP:RAII | UAF | drop a memory not owned | Qwaz-Sec | No | 
| arc-swap | CVE-2020-35711 | issues/45 | API:TRAIT | UAF | +PhantomData | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Array | API:TRAIT+CC | RC$\to$UAF | lack send/sync bound  | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Index | IMP:TRAIT | OOR | lack boundary check | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:from... | IMP: | UNINIT | drop uninitialized mem | Qwaz-Sec | No | 
| array-queue | Advisory-DB | issues/2 | IMP:LOE | UAF | index may point to freed mem | ammaraskar-Sec | No | 
| array-queue | Advisory-DB | issues/2 | IMP:RAII | UNINIT | use mem::uninitialized() | ammaraskar-Sec | No | 
| atom | Advisory-DB | issues/13 | API:TRAIT | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec | No | 
| chunky | Advisory-DB |issues/2 | IMP:LOE | OOR | API ignores memory alignment requirement | Qwaz-Sec  | No | 
| dync | Advisory-DB | issues/4 | IMP:LOE | OOR | memory misalignment | ammaraskar-Sec | No | 
| concread | Advisory-DB | issues/48 | API:CC+TRAIT | RC$\to$UAF | lack send/sync bound | JOE1994-Sec | No | 
| futures-intrusive | Advisory-DB | issues/53 | API:TRAIT+CC | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec| No | 
| futures-rs | Advisory-DB | pull/2206 | API:GENERICS+LIFE | UAF | lack lifetime bound | Darksonn | No | 
| futures-rs| Advisory-DB | issues/2091 | IMP:LIFETIME+CC | UAF | return static ref to Send | goffrie | No | 
| futures-rs| Advisory-DB | issues/2239 | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | Qwaz-Sec | No | 
| futures-rs| Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready | No | 
| pulse-binding-rust | Advisory-DB | API:LIFETIME+RAII | UAF | lack lifetime bound: +PhantomData | jnqnfe | No | 
| pulse-binding-rust | Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready | No | 
| parking_lot | CVE-2020-35910 | issues/258:MappedMutexGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack send bound | ammaraskar-Sec | No |  
| parking_lot | CVE-2020-35911 | issues/258:MappedRwLockReadGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | CVE-2020-35912 | issues/258:MappedRwLockWriteGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack send bound | ammaraskar-Sec | No |  
| parking_lot | CVE-2020-35913 | issues/259:RwLockReadGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | CVE-2020-35914 | issues/259:RwLockWriteGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec | No | 
| magnetic | CVE-2020-35925 | issues/9 | API:TRAIT+CC+GENERICS | lack send/sync bound | JOE1994-Sec | No | 
| miow | CVE-2020-35921 | issues/38 | FFI | UB | assumes the same layout of FFI | faern | No | 
| net2-rs | CVE-2020-35920 | issues/105 | FFI | UB | assumes the same layout of FFI | Thomasdezeeuw | No |  
| rust-ordered-float | CVE-2020-35923 | pull/71 | IMP:LOE | UB | panic may cause UB | branpk | No |  
| pyo3 | CVE-2020-35917 | pull/1297 | IMP:LOE+RAII | UAF | unthought of dropping | davidhewitt | No |  
| thex | CVE-2020-35927 | - | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | Qwaz-Sec | No |  
| time | CVE-2020-26235 | issues/293 | CC+SYS | RC$\to$UAF | call non-atomic system functions | quininer | No |  
| try-mutex | CVE-2020-35924 | issues/2 | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec | No |  
| isahc | 2019-16140 | issues/2 | RAII (Imp) | DP:UAF | unsafe constructor+no ManuallyDrop | No (nox) | No | 
| sxd-document  | Trophy Case | issues/47 | RAII (Imp) | DP:UAF | unsafe constructor+no ManuallyDrop | No (CryZe-sec) | No | 
| image | 2019-16138 | issues/980 | RAII:UNWIND* (Imp) | DP:DUN | unsafe allocation$\to$drop uninit mem/set_len() | No (64) | No | 
| image | CVE-2020-35916 | issues/1357 | IMP:MUT | UB | convert mutable ptr from const ptr | dodomorandi | No | 
| libflate | 2019-15552 | issues/35 | RAII:UNWIND (Imp) | DP:DUN  | enf. ManuallyDrop late$\to$drop uninit | No (Shnatsel-sec) | No | 
| memoffset | 2019-15553 | issues/9 | RAII:UNWIND (Imp) | DP:DUN | enf. ManuallyDrop late$\to$drop uninit mem  | No (Centril) | No | 
| linked-hash-map | 2020-25573 | pull/100 | RAII (Imp) | DP:DUN | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)| No | 
| rio | Advisory-DB |  issues/30 | RU:SAFE (API) | DP:UAF | logical error: soundness hole | No (dtolnay-Rust) | No | 
| bitvec | Advisory-DB | issues/55 | GEN* (Imp) | DP:UAF | logical error: false assumption | No (kulp-sec) | No | 
| cbox-rs | Advisory-DB | issues/2 | RU:SAFE (API) | DP:UAF+DF | declare unsafe API as safe | No (eduardosm) | No | 
| rust-openssl | 2018-20997 | issues/941 | RAII (Imp) | DP:UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)| No | 
| string-interner | 2019-16882 | issues/9 | IMP:RU:DERIVE (Imp) | DP:UAF | bad derived clone | No (lo48576-deps) | No |  
| crossbeam | 2018-20996 | issues/82 | IMP:RAII* (Imp) | DP:DF | shared mut aliases+auto drop/+ManuallyDrop | No (c0gent-deps) | No | 
| crossbeam | Advisory-DB | pull/533 | IMP:LOE | UB$\to$UAF | drop memory not owned | caelunshun | No | 
| generator-rs | 2019-16144 | issues/11 | IMP:RAII* (Imp) | DP:DF | shared mut aliases+auto drop | No (vOROn200) | No | 
| generator-rs | Advisory-DB | issues/9 | RU:SAFE (API) | Unsound | func. sign.$\to$deref invalid/null pointer | No (jonas-schievink)| No | 
| generator-rs | Advisory-DB | issues/13 | GEN (API) | Unsound | bad func. exposure  | No (jonas-schievink) | No | 
| generator-rs | Advisory-DB  | issues/14 | GEN (API) | Unsound | bad func. exposure | No (jonas-schievink)  | No | 
| linea | 2019-16880 | issues/1 | RAII:UNWIND (Imp) | DP:DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15)| No | 
| portaudio-rs | 2019-16881 | issues/20 | RU:DROP (Imp) | DP:DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15) | No | 
| http | 2020-25574 | issues/354 | RAII (Imp) | DP:DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) | No | 
| http | Advisory-DB | issues/355* | RU:MUT (API) | Unsound | func. sign.$\to$multiple mutable refs/Send$\to$Sync  | No (Qwaz-sec)  | No | 
| internment  | Advisory-DB | issues/11 | IMP:GEN (Imp) | CC:DR | impl error: Ordering, atomic::fence() | No (ryzhyk-deps)| No | 
| spin-rs  | 2019-16137 | issues/65 | IMP:GEN (Imp) | CC:DR | impl error: Ordering::Relaxed$\to$Release | No (64) | No | 
| vm-memory  | 2020-13759 | issues/93 | IMP:GEN (Imp) | CC:RC | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)| No | 
| teaclave-sgx-sdk  | 2020-5499 | www.mitre.org | GEN (API) | CC:DR | may init twice by another thread/+Once::new() | No (Chen-sec) | No | 
| claxon  | 2018-20992/Trophy | issues/10 | IMP:GEN (Imp) | DL | unsafe buf alloc$\to$read unit mem/Vec::set_len() | No (Shnatsel-sec)| No | 
| rust-rgb  | 2020-25016 | issues/35 | RU:Safe (API) | Unsound | declare unsafe API as safe | No (HeroicKatora) | No | 
| renderdoc-rs | 2019-16142 | issues/27 | RU:MUT (API) | Unsound | func. sign.$\to$unsync. internal mutation | No (ebkalderon-owner) | No | 
| rulinalg | Advisory-DB | issues/201 | RU:LIFE (API)| Unsound | func. sign.:lifetime | No (Qwaz-sec)  | No | 
| flatbuffers | Advisory-DB | issues/5825 | RU:SAFE (API) | Unsound | func. sign.: safety declaration | No (eduardosm)| No | 
| flatbuffers | Advisory-DB | issues/5530 | IMP* (Imp) | Unsound | logical error$\to$invalid bit pattern for bool | No (nagisa)| No | 
| once_cell | 2019-16141 | issues/46 | GEN* (Imp) | Unsound | unreachable_unchecked()$\to$panic!() | No (xfix-deps) | No | 
| capnproto-rust | Trophy Case | cargo-fuzz/issues/40 | GEN* (Imp) | Unsound | logical error | No (dwrensha-sec)| No | 
| lucet | Advisory-DB | pull/401 | GEN (Imp)  | Unsound | logical error$\to$memory man. issue | No (acfoltzer-deps) | No | 
| rand | 2020-25576 | issues/779 | GEN* (Imp) | Unsound | reading unaligned mem/ptr::read_unaligned() | No (RalfJung-sec)| No | 
| servo (exe) | GitHub | issues/1186 | RAII: (Imp) | DP:DF | impl Drop with unsafe | kmcallister | No | 
| servo (exe) | GitHub | issues/2412 | RAII: (Imp) | DP:DF  | *unsafe cast?  |  | No | 
| servo (exe) | GitHub | issues/14014 | RAII: (Imp) | CC$\to$UAF  |   | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/14416 | RAII: (Imp) | DP:UAF  | FnBox  | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/20158 | SAFETY: (API) | UB  | declare unsafe constructor as safe  | nox-org | No | 
| servo (exe) | GitHub | issues/21186 | Gen: (Imp) | CC:DR | Relaxed$\to$Acquire |  | No | 
| servo (exe) | GitHub | pull/26641 | Gen: (Imp) | UB | mem::transmute$\to$Box::into_raw() | dylni | No |
| wasmer (exe) | GitHub | pull/1092 | RU:Safety (Imp) | OOR | lack input consistency check + unsafe constructor | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1206 | RU:Safety (API) | Unsound | possible to create shared mutable aliases | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1209 | RU:Safety (API) | CC:DR | multiple Cells for the same memory | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1837 | RU:Safety (API) | Unsound | declare unsafe API as safe | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | issues/1568 | RAII: | DP:UAF | shared mutable alises (slice+to_vec()) | Hywan-dev | No | 
| alacritty (exe) | GitHub | pull/4397 | MemModel (Imp) | DP::UAF | shared mut aliases (ptr::copy$\to$clone) | kchibisov-dev | No | 
| alacritty (exe) | GitHub | pull/2176  | GEN (Imp) | UAF | logical error (+as_ref()) | aspurdy | No | 
| diem-libra (exe) | GitHub | pull/1949 | RU:Lifetime (API) | DP:UAF | ineffective lifetime restriction | dtolnay-Rust  || wint}| \multirow{3}{*}{GitHub (72 unsafe)} | diem-libra (exe) | GitHub | issues/599 | (Imp) | CC:RC | non-atomic cell for multi-thread apps | andrewhickman | No | 
| diem-libra (exe) | GitHub | pull/611 | CC (Imp) | CC:RC | non-atomic cell for multi-thread apps | francesca64-dev | No | 
| diem-libra (exe) | GitHub | issues/1745 | GEN (Imp) | DP:UAF | logical error | qthree | No | 
| Tokio | CVE-2020-35922 | issues/1386 | FFI | UB | assumes the same layout of FFI | Nemo157-Rust | No | 
| Tokio | GitHub | *pull/254 |  | DP:UAF | | seanmonstar-dev | No | 
| Tokio | GitHub | issues/354 | Gen (Imp) | UB | uninit memory for Vec<u8> with set_len() | udoprog | No | 
| Tokio | GitHub | issues/593 |  | CC | | NPN |
| Tokio | GitHub | pull/2030/ | (API) | OOR | trait safety | Marwes | 
| Tokio | GitHub | pull/2612/ | Trait (API) | OOR | error in specify Trait impl Type  | taiki-e-dev | 
| Tokio | GitHub | issues/3014 | Gen (Imp) | DP:UAF | off-by-one logical error | NikosEfthias |
| curl-rust | GitHub | pull/2 | RU:SAFE (Imp) | DP:UAF | **using mem::transmute() | No(alexcrichton-rust) | No | 
| curl-rust | GitHub | issues/333 | RU: (API) | CC:DR | does not enforce FFI restrictions | DemiMarie/sagebind-deps | Yes | 
| curl-rust | GitHub | issues/340 | RU:SAFE (API) | DP:UAF | exposing unsafe cleanup APIs as safe | sagebind-deps | No | 
  
## Notes: OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; CC: concurrency issue; DF: double free; DL: data leakage; DP: dangling pointer; DR: data race; 
RC: race condition; UAF: use-after-free.

## Other CVEs of Non-Memory-Safety Bugs
Crypto/Functionality Issue: CVE-2016-10932, CVE-2017-18587, CVE-2018-20999, CVE-2019-15545, CVE-2019-16760, CVE-2017-1000168, CVE-2020-15093, CVE-2020-35926, CVE-2020-35883; 
MITM/Code Injection: CVE-2016-10931, CVE-2016-10933, CVE-2020-28247, CVE-2020-26222, CVE-2020-28247; 
StackOverflow/Crash: CVE-2017-18589, CVE-2018-20989, CVE-2018-20993, CVE-2018-20994, CVE-2019-15542, CVE-2019-15544, CVE-2019-15549, CVE-2020-35909.
