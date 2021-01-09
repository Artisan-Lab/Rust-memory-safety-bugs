# rustbugs
  
| Project | CVE-ID (or Src) | Link | Culprit | Consequense | Details | Finder-Role | Propagated |
|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | CVE-2018-1000810 | [pull/54399](https://github.com/rust-lang/rust/pull/54399) | IMP:ARO | OOR | arithmatic overflow (str:repeat) | scottmcm-Rust | No | 
| rust-std | CVE-2018-1000657 | [issues/44800](https://github.com/rust-lang/rust/issues/44800) | IMP:COND | OOR | incorrect boundary check (VecDeque) | jesse99-deps | No |
| rust-std | CVE-2019-12083 | [issues/60784](https://github.com/rust-lang/rust/issues/60784) | API:TRAIT+DESIGN | OOR | soundness hole impl Error::type_id() + downcasting | seanmonstar-deps | No | 
| rust-std | GitHub | [issues/17207](https://github.com/rust-lang/rust/issues/17207) | IMP:FFI | UB | args are UB in jemalloc ( Vec::from_elem) | gmorenz | No | 
| rust-std | GitHub | [issues/25841](https://github.com/rust-lang/rust/issues/25841) | IMP:ARO+MODEL | UB->UAF | arithmatic overflow->shared mut aliases (RefCell) | Veedrac | No | 
| rust-std | GitHub | [issues/27970](https://github.com/rust-lang/rust/issues/27970) | IMP:FFI+CC+SYS+MODEL | UB->UAF | setenv is unsafe | bluss-Rust | No | 
| rust-std | GitHub | [issues/33770](https://github.com/rust-lang/rust/issues/33770) | IMP:FFI+CC+MODEL | UB->UAF | glibc recursive lock is UB->shared mut aliases | Amanieu | No | 
| rust-std | GitHub | [issues/35836](https://github.com/rust-lang/rust/issues/35836) | IMP:FFI+CC+MODEL | UB->UAF | recursive RWlock on Windows is UB | retep998-Rust | No | 
| rust-std | GitHub | [issues/39465](https://github.com/rust-lang/rust/issues/39465) | API:SIG | UB->DP | Fn signature issue->shared mut aliases | christophebiocca | No | 
| rust-std | GitHub | [issues/39575](https://github.com/rust-lang/rust/issues/39575) | API:SIG+FFI+CC | UB | should be unsafe, UB according to POSIX (CommandExt::before_exec) | fweimer | No | 
| rust-std | GitHub | [issues/42135](https://github.com/rust-lang/rust/issues/42135) | IMP:COND | UB->OOR | error related to unsafe trait (TrustedLen) | scottmcm-Rust | No | 
| rust-std | GitHub | [issues/42789](https://github.com/rust-lang/rust/issues/42789) | IMP:TRAIT+ZST | UB->OOR | interators over ZST slices are undefined->random addr （Iter+ZST） | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/43733](https://github.com/rust-lang/rust/issues/43733) | IMP:CC+DESIGN | UB->UAF | access static value without unsafe marker->CC(thread::local) | eddyb-Rust | No | 
| rust-std | GitHub | [issues/44637](https://github.com/rust-lang/rust/issues/44637) | API:TRAIT+DESIGN | BO->OOR | soundness hole (Placer) | andy-hanson | No | 
| rust-std | GitHub | [issues/45197](https://github.com/rust-lang/rust/issues/45197) | API:CC | CC->UAF | bypassing sync/send check（Cell as fmt::Arguments） | cuviper-Rust | No | 
| rust-std | GitHub | [issues/46775](https://github.com/rust-lang/rust/issues/46775) | IMP:FFI+EH+CC+SYS | UAF | multi-thread unsafe (unix::process::CommandExt::exec) | Diggsey | No | 
| rust-std | GitHub | [issues/48006](https://github.com/rust-lang/rust/issues/48006) | IMP:ARO+SYS | OOR | arithmatic overflow on 16-bit platforms | oberien | No | 
| rust-std | GitHub | [issues/48493](https://github.com/rust-lang/rust/issues/48493) | IMP:RAII | UNINIT | free uninitialized mem (Weak) | jleedev | No | 
| rust-std | GitHub | [issues/51780](https://github.com/rust-lang/rust/issues/51780) | IMP:CC | DR->UAF | insufficient synchronization (Arc::is_unique) Relaxed->Acquire | jhjourdan | No | 
| rust-std | GitHub | [issues/54857](https://github.com/rust-lang/rust/issues/54857) | IMP:LOE+LLVM+ZST | UB | UB in computing the offset addr for ZST or 0-len Vec（Vec） | jturner314 | No | 
| rust-std | GitHub | [issues/54908](https://github.com/rust-lang/rust/issues/54908) | IMP:LOE | OOR | misaligned reference （RC，ARC） | RalfJung | No | 
| rust-std | GitHub | [issues/54957](https://github.com/rust-lang/rust/issues/54957) | IMP:LOE | UB->OOR | inconsistent type of Root node (BTreeSet) | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/57534](https://github.com/rust-lang/rust/issues/57534) | IMP:CC+SYS+FFI | UAF | thread local variables is freed before \_tlv_atexit (thread_local) | mtak- | May | 
| rust-std | GitHub | [issues/60977](https://github.com/rust-lang/rust/issues/60977) | IMP:UNWIND+RAII | DF | double free while panic (Vec::drain_filter) | rustonaut | No | 
| rust-std | GitHub | [issues/66544](https://github.com/rust-lang/rust/issues/66544) | API:TRAIT+GENERIC | UB->UAF | soundness holes of when impl DerefMut/Clone (Pin) | comex |
| rust-std | GitHub | [issues/67194](https://github.com/rust-lang/rust/issues/67194) | API:TRAIT | UB->OOR | soundness holes when impl PartialEq (RangeInclusive) | comex | No | 
| rust-std | GitHub | [issues/72624](https://github.com/rust-lang/rust/issues/72624) | IMP:ARO | OOR | possible arithmatic overflow (DroplessArena::alloc_raw) | bluss-Rust | No |
| rust-std | GitHub | [issues/72760](https://github.com/rust-lang/rust/issues/72760) | IMP:LOE | UB | invalid UTF-8 | RalfJung-Rust | No |
| rust-std | GitHub | [issues/76367](https://github.com/rust-lang/rust/issues/76367) | IMP:RAII+CC | UAF | logical error (SyncOnceCell/dropck)+PhantomData | m-ou-se-Rust |
| rust-std | GitHub | [issues/78477](https://github.com/rust-lang/rust/issues/78477) | IMP:LOE | UNKNOWN | violate pointer provenance rules | RalfJung-Rust | No |
| rust-std | GitHub | [issues/78498](https://github.com/rust-lang/rust/issues/78498) | IMP:UNWIND | UB | invalid UTF-8 while catch_unwind (String) | SkiFire13 | No |
| rust-std | Advisory-DB | [issues/79808](https://github.com/rust-lang/rust/issues/79808) | IMP:COND | UB->\*UAF | incorrect boundary check (VecDeque) | ayourtch | No |
| rust-std | GitHub | [issues/80338](https://github.com/rust-lang/rust/issues/80338) | IMP:COND | UB->\*UAF | incorrect boundary check (VecDeque)-79808 | Aratz | No |
| rustc (fake-static) | Advisory-DB | [issues/25860](https://github.com/rust-lang/rust/issues/25860) | API:LIFE | UB->UAF | type system issue->lifetime inconsistency | No (aturon-Rust)| No | 
| arrayfire-rust  | CVE-2018-20998 | [issues/176](https://github.com/arrayfire/arrayfire-rust/issues/176) | IMP:FFI | OOR | FFI-compatability/repr() | No (Aidan24) | No | 
| ncurses | CVE-2019-15547 | [issues/172](https://github.com/jeaye/ncurses-rs/issues/172) | API:SIG+FFI | OOR | FFI-unchecked argument/printw() | thomcc | No | 
| ncurses | CVE-2019-15548 | [issues/186](https://github.com/jeaye/ncurses-rs/issues/186) | API:SIG+FFI | OOR | FFI-unchecked argument/instr(), mvwinstr() | thomcc |
| rusqlite | Advisory-DB | pull/708 | API:SIG+FFI | OOR | FFI-unchecked argument/sqlite3_log() | thomcc-deps| No | 
| rusqlite | Advisory-DB | issues/703 | API:SIG | UB->UAF | func. sign.: lifetime declaration | No (gwenn-deps) | No | 
| rust-base64 | CVE-2017-1000430 | [issues/28](https://github.com/marshallpierce/rust-base64/issues/28) | IMP:ARO | OOR | arithmatic overflow + unsafe write | No (alicemaz) | No | 
| failure | CVE-2020-25575 | [issues/336](https://github.com/rust-lang-nursery/failure/issues/336) | API:SIG | OOR | SAFE downcast$\to$mem misalign/private_get_type_id() | No (Qwaz-sec) | No | 
| bumpalo | Advisory-DB | [issues/69](https://github.com/fitzgen/bumpalo/issues/69) | IMP:LOE | OOR(Read) | wrong buffer size + unsafe write | No (Riey-deps)| No | 
| compact_arena | CVE-2019-16139 | [issues/22](https://github.com/llogiq/compact_arena/issues/22) | \*IMP:DROP+LIFE | OOR(Read) | NLL issue->Index trait/get_unchecked() | No (CAD97) | No | 
| lz4_flex | Trophy | - | IMP:LOE | OOR | logical error in space allocation | Pascal Seitz-sec | No | 
| ozone | Advisory-DB | RUSTSEC-2020-0022:1 | API:SAFE | OOR:BOR | context issue->Index trait | No (n.a.) | No | 
| ozone | Advisory-DB | RUSTSEC-2020-0022:2 | IMP:RAII | DP:DUN | implement drop with uninit mem | No (n.a.)| No | 
| prost | Advisory/Trophy | issues/267 | IMP:LOE | OOR | logical error in recursion + unsafe write | No (dbrgn-sec) | No | 
| safe-transmute | CVE-2018-21000 | [pull/36](https://github.com/nabijaczleweli/safe-transmute-rs/pull/36) | IMP:LOE | OOR | logical error + unsafe write | No (Enet4-deps)| No | 
| slice-deque | CVE-2018-20995 | [issues/57](https://github.com/gnzlbg/slice_deque/issues/57) | IMP:LOE | OOR | error in boundary check + unsafe write | No (aldanor-deps) | No | 
| slice-deque | CVE-2019-15543 | [pull/66](https://github.com/gnzlbg/slice_deque/pull/66) | IMP:LOE | OOR | logical error->memory misalignment | No (zimond) | No | 
| rust-smallvec | CVE-2019-15554 | [issues/149](https://github.com/servo/rust-smallvec/issues/149) | IMP:LOE | OOR | logical error + unsafe write | No (ehuss) | No | 
| rust-smallvec | Advisory-DB | [issues/126](https://github.com/servo/rust-smallvec/issues/126) | IMP:RAII+UNWIND | UNINIT | init vector with mem:uninitialized() | No (mbrubeck) | No | 
| rust-smallvec | CVE-2019-15551 | [issues/148](https://github.com/servo/rust-smallvec/issues/148) | IMP:LOE | DP:UAF | logical error + unsafe deallocation | No (ehuss) | No | 
| rust-smallvec | CVE-2018-20991 | [issues/96](https://github.com/servo/rust-smallvec/issues/96) | IMP:RAII+UNWIND | DF | buffer shrinking too late | No (Vurich) | No | 
| simd-json | CVE-2019-15550 | [pull/27](https://github.com/simd-lite/simd-json/pull/27) | IMP:LOE | OOR | logical error->mem misalign/get_unchecked() | No (Licenser-deps) | No | 
| v_espace | Trophy Case | issues/47 | IMP:LOE | OOR | logical error->mem misalign | \_mm_load_si128() | No (tmiasko) | No | 
| sized-chunks | CVE-2020-25791 | [issues/11:unit](https://github.com/bodil/sized-chunks/issues/11) | API:LOE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | CVE-2020-25792 | [issues/11:pair](https://github.com/bodil/sized-chunks/issues/11) | API:LOE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | CVE-2020-25793 | [issues/11:From](https://github.com/bodil/sized-chunks/issues/11) | API:LOE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | CVE-2020-25796 | [issues/11:InlineArray](https://github.com/bodil/sized-chunks/issues/11) | API:LOE | OOR:BO | no input check->memory misalignment | No (Qwaz-sec) | No | 
| sized-chunks | CVE-2020-25794 | [issues/11:clone](https://github.com/bodil/sized-chunks/issues/11) | IMP:RAII+UNWIND | UNINIT | panic->drop uninitialized memory | No (Qwaz-sec)  | No | 
| sized-chunks | CVE-2020-25795 | [issues/11:insert_from](https://github.com/bodil/sized-chunks/issues/11) | IMP:RAII+UNWIND | UNINIT | panic $\to$ rop uninitialized memory | No (Qwaz-sec)  | No | 
| actix-net | Advisory-DB | issues/91 |  | UAF | | sebzim4500 | No | 
| actix-net | Advisory-DB | pull/158 | API:RC | UB->UAF | replace Cell with RefCell | Shnatsel  | No | 
| actix-net | Advisory-DB | issues/160 | API:RC | UB->UAF | replace Cell with RefCell | Shnatsel | No | 
| actix-web | Advisory-DB | issues/289 | API:MUTE | UB->UAF | transmute immutable ref to mutable | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | API:LIFE | UAF | transmutate lifetime to static | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | IMP:TRAIT+GENERIC | UAF | Clone+Rc | seanmonstar | No | 
| actix-web | Advisory-DB | issues/301 | API:CC+TRAIT+GENERIC | UAF | unsafe impl of Send for generics races Rc | seanmonstar-Mozilla | No | 
| actix-web | Advisory-DB | issues/1321 | API:PAR | UAF |  | sebzim4500 | No | 
| alg_ds | Advisory-DB | issues/1 | IMP:RAII | UNINIT | init with alloc::alloc | Qwaz-Sec | No | 
| rust-arch | Advisory-DB | issues/2 | IMP:RAII | UAF | drop a memory not owned | Qwaz-Sec | No | 
| arc-swap | CVE-2020-35711 | [issues/45](https://github.com/vorner/arc-swap/issues/45) | API:TRAIT | UAF | +PhantomData | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Array | API:TRAIT+CC | CC->UAF | lack send/sync bound  | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Index | IMP:TRAIT | OOR | lack boundary check | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:from... | IMP: | UNINIT | drop uninitialized mem | Qwaz-Sec | No | 
| array-queue | Advisory-DB | issues/2 | IMP:LOE | UAF | index may point to freed mem | ammaraskar-Sec | No | 
| array-queue | Advisory-DB | issues/2 | IMP:RAII | UNINIT | use mem::uninitialized() | ammaraskar-Sec | No | 
| atom | Advisory-DB | issues/13 | API:TRAIT | UB->UAF | lack send/sync bound | ammaraskar-Sec | No | 
| chunky | Advisory-DB |issues/2 | IMP:LOE | OOR | API ignores memory alignment requirement | Qwaz-Sec  | No | 
| dync | Advisory-DB | issues/4 | IMP:LOE | OOR | memory misalignment | ammaraskar-Sec | No | 
| concread | Advisory-DB | issues/48 | API:CC+TRAIT | CC->UAF | lack send/sync bound | JOE1994-Sec | No | 
| futures-intrusive | Advisory-DB | issues/53 | API:TRAIT+CC | CC->UAF | lack send/sync bound | ammaraskar-Sec| No | 
| futures-rs | Advisory-DB | pull/2206 | API:GENERICS+LIFE | UAF | lack lifetime bound | Darksonn | No | 
| futures-rs| Advisory-DB | issues/2091 | IMP:LIFE+CC | UAF | return static ref to Send | goffrie | No | 
| futures-rs| Advisory-DB | issues/2239 | API:TRAIT+GENERICS+CC | CC->UAF | lack send/sync bound | Qwaz-Sec | No | 
| futures-rs| Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready | No | 
| pulse-binding-rust | Advisory-DB | API:LIFE+GENERICS+RAII | UAF | lack lifetime bound: +PhantomData | jnqnfe | No | 
| pulse-binding-rust | Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready | No | 
| parking_lot | CVE-2020-35910 | [MappedMutexGuard](https://github.com/Amanieu/parking_lot/issues/258) | API:TRAIT+CC+GENERICS | CC->UAF |  lack send bound | ammaraskar-Sec | No |  
| parking_lot | CVE-2020-35911 | [MappedRwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/258) | API:TRAIT+CC+GENERICS | CC->UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | CVE-2020-35912 | [MappedRwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/258) | API:TRAIT+CC+GENERICS | CC->UAF |  lack send bound | ammaraskar-Sec | No |  
| parking_lot | CVE-2020-35913 | [RwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/259) | API:TRAIT+CC+GENERICS | CC->UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | CVE-2020-35914 | [RwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/259) | API:TRAIT+CC+GENERICS | CC->UAF |  lack sync bound | ammaraskar-Sec | No | 
| magnetic | CVE-2020-35925 | [issues/9](https://github.com/johnshaw/magnetic/issues/9) | API:TRAIT+CC+GENERICS | CC->UAF | lack send/sync bound | JOE1994-Sec | No | 
| miow | CVE-2020-35921 | [issues/38](https://github.com/yoshuawuyts/miow/issues/38) | FFI | UB | assumes the same layout of FFI | faern | No | 
| net2-rs | CVE-2020-35920 | [issues/105](https://github.com/deprecrated/net2-rs/issues/105) | FFI | UB | assumes the same layout of FFI | Thomasdezeeuw | No |  
| rust-ordered-float | CVE-2020-35923 | [pull/71](https://github.com/reem/rust-ordered-float/pull/71) | IMP:LOE | UB | panic may cause UB | branpk | No |  
| pyo3 | CVE-2020-35917 | [pull/1297](https://github.com/PyO3/pyo3/pull/1297) | IMP:LOE+RAII | IMP：UAF | unthought of dropping | davidhewitt | No |  
| thex | CVE-2020-35927 | - | API:TRAIT+GENERICS+CC | CC->UAF | lack send/sync bound | Qwaz-Sec | No |  
| time | CVE-2020-26235 | [issues/293](https://github.com/time-rs/time/issues/293) | CC+SYS | CC->UAF | call non-atomic system functions | quininer | No |  
| try-mutex | CVE-2020-35924 | [issues/2](https://github.com/mpdn/try-mutex/issues/2) | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec | No |  
| isahc | CVE-2019-16140 | [issues/2](https://github.com/sagebind/isahc/issues/2) | IMP:RAII | UAF | unsafe constructor+no ManuallyDrop | No (nox) | No | 
| sxd-document  | Trophy Case | issues/47 | IMP:RAII | UAF | unsafe constructor+no ManuallyDrop | No (CryZe-sec) | No | 
| image | CVE-2019-16138 | [issues/980](https://github.com/image-rs/image/issues/980) | IMP:RAII+UNWIND | UNINIT | unsafe allocation->drop uninit mem/set_len() | No (64) | No | 
| image | CVE-2020-35916 | [issues/1357](https://github.com/image-rs/image/issues/1357) | IMP:MUT | UB | convert mutable ptr from const ptr | dodomorandi | No | 
| libflate | CVE-2019-15552 | [issues/35](https://github.com/sile/libflate/issues/35) | IMP:RAII+UNWIND  | UNINIT | enf. ManuallyDrop late->drop uninit | No (Shnatsel-sec) | No | 
| memoffset | CVE-2019-15553 | [issues/9](https://github.com/Gilnaa/memoffset/issues/9) | IMP:RAII+UNWIND | UNINIT | enf. ManuallyDrop late->drop uninit mem  | No (Centril) | No | 
| linked-hash-map | CVE-2020-25573 | [pull/100](https://github.com/contain-rs/linked-hash-map/pull/100/) | IMP:RAII | UNINIT | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)| No | 
| rio | Advisory-DB |  issues/30 | RU:SAFE (API) | UAF | logical error: soundness hole | No (dtolnay-Rust) | No | 
| bitvec | Advisory-DB | issues/55 | IMP:LOE | UAF | logical error: false assumption | No (kulp-sec) | No | 
| cbox-rs | Advisory-DB | issues/2 | RU:SAFE (API) | UAF | declare unsafe API as safe | No (eduardosm) | No | 
| rust-openssl | CVE-2018-20997 | [issues/941](https://github.com/sfackler/rust-openssl/issues/941) | IMP:RAII | UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)| No | 
| string-interner | CVE-2019-16882 | [issues/9](https://github.com/Robbepop/string-interner/issues/9) | IMP:TRAIT | UAF | bad derived clone | No (lo48576-deps) | No |  
| crossbeam | CVE-2018-20996 | [issues/82](https://github.com/crossbeam-rs/crossbeam/issues/82) | IMP:RAII | DF | shared mut aliases+auto drop/+ManuallyDrop | No (c0gent-deps) | No | 
| crossbeam | Advisory-DB | [pull/533](https://github.com/crossbeam-rs/crossbeam/pull/533) | IMP:LOE | UB->UAF | drop memory not owned | caelunshun | No | 
| generator-rs | CVE-2019-16144 | [issues/11](https://github.com/Xudong-Huang/generator-rs/issues/11) | IMP:RAII | DF | shared mut aliases+auto drop | No (vOROn200) | No | 
| generator-rs | Advisory-DB | [issues/9](https://github.com/Xudong-Huang/generator-rs/issues/9) | API:SAFE | UB | func. sign.$\to$deref invalid/null pointer | No (jonas-schievink)| No | 
| generator-rs | Advisory-DB | [issues/13](https://github.com/Xudong-Huang/generator-rs/issues/13) | GEN (API) | UB | bad func. exposure  | No (jonas-schievink) | No | 
| generator-rs | Advisory-DB  | [issues/14](https://github.com/Xudong-Huang/generator-rs/issues/14) | GEN (API) | UB | bad func. exposure | No (jonas-schievink)  | No | 
| linea.rs | CVE-2019-16880 | [issues/1](https://github.com/strake/linea.rs/pull/2) | IMP:RAII+UNWIND | DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15)| No | 
| portaudio-rs | CVE-2019-16881 | [issues/20](https://github.com/mvdnes/portaudio-rs/issues/20) | IMP:RAII | DP:DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15) | No | 
| http | CVE-2020-25574 | [issues/354](https://github.com/hyperium/http/issues/354) | IMP:RAII | DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) | No | 
| http | Advisory-DB | [issues/355*](https://github.com/hyperium/http/issues/355) | API:MUT | UB | func. sign.$\to$multiple mutable refs/Send$\to$Sync  | No (Qwaz-sec)  | No | 
| internment  | Advisory-DB | issues/11 | IMP:CC+GEN | UB | impl error: Ordering, atomic::fence() | No (ryzhyk-deps)| No | 
| spin-rs  | CVE-2019-16137 | [issues/65](https://github.com/mvdnes/spin-rs/issues/65) | IMP:CC+GEN | UB | impl error: Ordering::Relaxed$\to$Release | No (64) | No | 
| vm-memory | CVE-2020-13759 | [issues/93](https://github.com/rust-vmm/vm-memory/issues/93) | IMP:CC+GEN | UB | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)| No | 
| teaclave-sgx-sdk  | CVE-2020-5499 | www.mitre.org | API:CC+LOE | UB | may init twice by another thread/+Once::new() | No (Chen-sec) | No | 
| claxon  | CVE-2018-20992/Trophy | [issues/10](https://github.com/ruuda/claxon/issues/10) | IMP:LOE | UNINIT->DL | unsafe buf alloc$\to$read unit mem/Vec::set_len() | No (Shnatsel-sec)| No | 
| rust-rgb | CVE-2020-25016 | [issues/35](https://github.com/kornelski/rust-rgb/issues/35) | RU:Safe (API) | UB | declare unsafe API as safe | No (HeroicKatora) | No | 
| renderdoc-rs | CVE-2019-16142 | [issues/27](https://github.com/ebkalderon/renderdoc-rs/issues/27) | RU:MUT (API) | UB | func. sign.$\to$unsync. internal mutation | No (ebkalderon-owner) | No | 
| rulinalg | Advisory-DB | issues/201 | API:LIFE | UB->UAF | func. sign.:lifetime | No (Qwaz-sec)  | No | 
| flatbuffers | Advisory-DB | issues/5825 | API:SAFE | UB | func. sign.: safety declaration | No (eduardosm)| No | 
| flatbuffers | Advisory-DB | issues/5530 | IMP:LOE | UB | logical error->invalid bit pattern for bool | No (nagisa)| No | 
| once_cell | CVE-2019-16141 | [issues/46](https://github.com/matklad/once_cell/issues/46) | IMP:LOE | UB | unreachable_unchecked()->panic!() | No (xfix-deps) | No | 
| capnproto-rust | Trophy Case | cargo-fuzz/issues/40 | IMP:LOE | Unsound | logical error | No (dwrensha-sec)| No | 
| lucet | Advisory-DB | pull/401 | IMP:LOE  | UB | logical error->memory man. issue | No (acfoltzer-deps) | No | 
| rand | CVE-2020-25576 | [issues/779](https://github.com/rust-random/rand/issues/779) | IMP:LOE | UB | reading unaligned mem/ptr::read_unaligned() | No (RalfJung-sec)| No | 
| servo (exe) | GitHub | issues/1186 | IMP:RAII | DF | impl Drop with unsafe | kmcallister | No | 
| servo (exe) | GitHub | issues/2412 | IMP:RAII | DF  | *unsafe cast?  |  | No | 
| servo (exe) | GitHub | issues/14014 | IMP:CC+RAII | UAF |   | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/14416 | IMP:RAII | UAF  | FnBox  | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/20158 | APU:SAFE | UB | declare unsafe constructor as safe  | nox-org | No | 
| servo (exe) | GitHub | issues/21186 | IMP:CC+LOE | UB | Relaxed$\to$Acquire |  | No | 
| servo (exe) | GitHub | pull/26641 | IMP:LOE | UB | mem::transmute->Box::into_raw() | dylni | No |
| wasmer (exe) | GitHub | pull/1092 | IMP:SAFE | OOR | lack input consistency check + unsafe constructor | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1206 | IMP:SAFE | Unsound | possible to create shared mutable aliases | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1209 | IMP:SAFE | CC:DR | multiple Cells for the same memory | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1837 | IMP:SAFE | Unsound | declare unsafe API as safe | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | issues/1568 | RAII: | DP:UAF | shared mutable alises (slice+to_vec()) | Hywan-dev | No | 
| alacritty (exe) | GitHub | pull/4397 | IMP:MODEL | UAF | shared mut aliases (ptr::copy->clone) | kchibisov-dev | No | 
| alacritty (exe) | GitHub | pull/2176  | IMP:LOE | UAF | logical error (+as_ref()) | aspurdy | No | 
| diem-libra (exe) | GitHub | pull/1949 | API:LIFE | UAF | ineffective lifetime restriction | dtolnay-Rust  |
| wint | GitHub | issues/599 | IMP:CC | UB | non-atomic cell for multi-thread apps | andrewhickman | No | 
| wint | GitHub | pull/611 | IMP:CC | UB | non-atomic cell for multi-thread apps | francesca64-dev | No | 
| wint | GitHub | issues/1745 | IMP:LOE | UAF | logical error | qthree | No | 
| Tokio | CVE-2020-35922 | issues/1386 | FFI | UB | assumes the same layout of FFI | Nemo157-Rust | No | 
| Tokio | GitHub | *pull/254 |  | DP:UAF | | seanmonstar-dev | No | 
| Tokio | GitHub | issues/354 | IMP: | UNINIT | uninit memory for Vec<u8> with set_len() | udoprog | No | 
| Tokio | GitHub | issues/593 | :CC |  | | NPN |
| Tokio | GitHub | pull/2030/ | API: | OOR | trait safety | Marwes | 
| Tokio | GitHub | pull/2612/ | API:TRAIT | OOR | error in specify Trait impl Type  | taiki-e-dev | 
| Tokio | GitHub | issues/3014 | IMP:LOE | UAF | off-by-one logical error | NikosEfthias |
| curl-rust | GitHub | pull/2 | IMP:SAFE | UAF | **using mem::transmute() | No(alexcrichton-rust) | No | 
| curl-rust | GitHub | issues/333 | API:CC | UB | does not enforce FFI restrictions | DemiMarie/sagebind-deps | Yes | 
| curl-rust | GitHub | issues/340 | API:SAFE | UAF | exposing unsafe cleanup APIs as safe | sagebind-deps | No | 

## Notes: OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; CC: concurrency issue; DF: double free; DL: data leakage; DP: dangling pointer; DR: data race; 
RC: race condition; UAF: use-after-free.

## Other CVEs of Non-Memory-Safety Bugs
Crypto/Functionality Issue: CVE-2016-10932, CVE-2017-18587, CVE-2018-20999, CVE-2019-15545, CVE-2019-16760, CVE-2017-1000168, CVE-2020-15093, CVE-2020-35926, CVE-2020-35883; 
MITM/Code Injection: CVE-2016-10931, CVE-2016-10933, CVE-2020-28247, CVE-2020-26222, CVE-2020-28247; 
StackOverflow/Crash: CVE-2017-18589, CVE-2018-20989, CVE-2018-20993, CVE-2018-20994, CVE-2019-15542, CVE-2019-15544, CVE-2019-15549, CVE-2020-35909.
Cargo/Rustdoc: CVE-2018-1000622, CVE-2019-16760 
