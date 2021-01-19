# rustbugs
  
| Project | CVE-ID (or Src) | Link | Culprit | Difficulty to Triger  | Consequense | Details | Finder-Role | Propagated | Revise (Unsafe->Safe) |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | **CVE-2018-1000810** | [pull/54399](https://github.com/rust-lang/rust/pull/54399) | ARO | ERR | OOR | arithmatic overflow (str:repeat) | scottmcm-Rust | No | 
| rust-std | **CVE-2018-1000657** | [issues/44800](https://github.com/rust-lang/rust/issues/44800) | BOUNDARY | ERR | OOR | incorrect boundary check (VecDeque) | jesse99-deps | No |
| rust-std | **CVE-2019-12083** | [issues/60784](https://github.com/rust-lang/rust/issues/60784) | TTYPECONV+ALIGN | UNSOUND | OOR | soundness hole impl Error::type_id() + downcasting | seanmonstar-deps | No | 
| rust-std | GitHub | [issues/17207](https://github.com/rust-lang/rust/issues/17207) | FFI | UNSOUND | UB | args are UB in jemalloc ( Vec::from_elem) | gmorenz | No | 
| rust-std | GitHub | [issues/25841](https://github.com/rust-lang/rust/issues/25841) | ARO+MODEL | ERR | UAF | arithmatic overflow->shared mut aliases (RefCell) | Veedrac | No | 
| rust-std | GitHub | [issues/27970](https://github.com/rust-lang/rust/issues/27970) | FFI+CC+SYS+MODEL | MID | UAF | setenv is unsafe | bluss-Rust | No | 
| rust-std | GitHub | [issues/33770](https://github.com/rust-lang/rust/issues/33770) | FFI+CC+MODEL | UNSOUND | UAF | glibc recursive lock is UB->shared mut aliases | Amanieu | No | 
| rust-std | GitHub | [issues/35836](https://github.com/rust-lang/rust/issues/35836) | FFI+CC+MODEL | UNSOUND | UAF | recursive RWlock on Windows is UB | retep998-Rust | No | 
| rust-std | GitHub | [issues/39465](https://github.com/rust-lang/rust/issues/39465) | FNSIG(MUT) | UNSOUND | DP | Fn signature issue->shared mut aliases | christophebiocca | No | 
| rust-std | GitHub | [issues/39575](https://github.com/rust-lang/rust/issues/39575) | FNSIG(UNSAFE)+FFI+CC | UNSOUND | UB | should be unsafe, UB according to POSIX (CommandExt::before_exec) | fweimer | No | 
| rust-std | GitHub | [issues/42135](https://github.com/rust-lang/rust/issues/42135) | CASE+TRAIT | ERR | UB | incorrect size_hint for degenerate inclusive ranges  (TrustedLen) | scottmcm-Rust | No | 
| rust-std | GitHub | [issues/42789](https://github.com/rust-lang/rust/issues/42789) | TYPE(ZST)+GENERIC+TRAIT | ERR | OOR | interators over ZST slices are undefined->random addr （Iter+ZST） | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/43733](https://github.com/rust-lang/rust/issues/43733) | LOE+CC+DESIGN | UNSOUND | UAF | access static value without unsafe marker->CC(thread::local) | eddyb-Rust | No | 
| rust-std | GitHub | [issues/44637](https://github.com/rust-lang/rust/issues/44637) | TRAIT+DESIGN | UNSOUND | OOR | soundness hole (Placer) | andy-hanson | No | 
| rust-std | GitHub | [issues/45197](https://github.com/rust-lang/rust/issues/45197) | TRAIT+CC | UNSOUND | UAF | bypassing sync/send check（Cell as fmt::Arguments） | cuviper-Rust | No | 
| rust-std | GitHub | [issues/46775](https://github.com/rust-lang/rust/issues/46775) | FFI+CC+SYS | MID | UAF | multi-thread unsafe (unix::process::CommandExt::exec) | Diggsey | No | 
| rust-std | GitHub | [issues/48006](https://github.com/rust-lang/rust/issues/48006) | ARO+SYS | ERR | OOR | arithmatic overflow on 16-bit platforms | oberien | No | 
| rust-std | GitHub | [issues/48493](https://github.com/rust-lang/rust/issues/48493) | GENERIC+RAII | ERR | UNINIT | Weak<T> frees uninitialized mem with <Void> | jleedev | No | 
| rust-std | GitHub | [issues/51780](https://github.com/rust-lang/rust/issues/51780) | EAPI(MEM)+CC | ERR | DR->UAF | insufficient synchronization (Arc::is_unique) Relaxed->Acquire | jhjourdan | No | 
| rust-std | GitHub | [issues/54857](https://github.com/rust-lang/rust/issues/54857) | TYPE(ZST)+GENERIC+LOE+LLVM | ERR | OOR | UB in computing the offset addr for ZST or 0-len Vec（Vec） | jturner314 | No | 
| rust-std | GitHub | [issues/54908](https://github.com/rust-lang/rust/issues/54908) | GENERICS+ALIGN | ERR | OOR | misaligned reference （RC，ARC） | RalfJung | No | 
| rust-std | GitHub | [issues/54957](https://github.com/rust-lang/rust/issues/54957) | LOE | ERR | OOR | inconsistent type of Root node (BTreeSet) | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/57534](https://github.com/rust-lang/rust/issues/57534) | IMP:FFI+CC+SYS | UAF | thread local variables is freed before \_tlv_atexit (thread_local) | mtak- | May | 
| rust-std | GitHub | [issues/60977](https://github.com/rust-lang/rust/issues/60977) | UNWIND+RAII | DF | double free while panic (Vec::drain_filter) | rustonaut | No | 
| rust-std | GitHub | [issues/66544](https://github.com/rust-lang/rust/issues/66544) | API:TRAIT+GENERIC | UB->UAF | soundness holes of when impl DerefMut/Clone (Pin) | comex |
| rust-std | GitHub | [issues/67194](https://github.com/rust-lang/rust/issues/67194) | API:TRAIT+SPEC | UB->OOR | violate the always applicable test (PartialEq for RangeInclusive) | comex | No | 
| rust-std | GitHub | [issues/72624](https://github.com/rust-lang/rust/issues/72624) | ARO | OOR | possible arithmatic overflow (DroplessArena::alloc_raw) | bluss-Rust | No |
| rust-std | GitHub | [issues/72760](https://github.com/rust-lang/rust/issues/72760) | IMP:LOE+TYPE | UB | invalid UTF-8 | RalfJung-Rust | No |
| rust-std | GitHub | [issues/76367](https://github.com/rust-lang/rust/issues/76367) | RAII+CC | UAF | logical error (SyncOnceCell/dropck)+PhantomData | m-ou-se-Rust |
| rust-std | GitHub | [issues/78477](https://github.com/rust-lang/rust/issues/78477) | IMP:LOE | UNKNOWN | violate pointer provenance rules | RalfJung-Rust | No |
| rust-std | GitHub | [issues/78498](https://github.com/rust-lang/rust/issues/78498) | UNWIND+TYPE | UB | invalid UTF-8 while catch_unwind (String) | SkiFire13 | No |
| rust-std | Advisory-DB | [issues/79808](https://github.com/rust-lang/rust/issues/79808) | IMP:BOUNDARY | UB->\*UAF | incorrect boundary check (VecDeque) | ayourtch | No |
| rust-std | GitHub | [issues/80338](https://github.com/rust-lang/rust/issues/80338) | IMP:BOUNDARY | UB->\*UAF | incorrect boundary check (VecDeque)-79808 | Aratz | No |
| rustc (fake-static) | Advisory-DB | [issues/25860](https://github.com/rust-lang/rust/issues/25860) | API:LIFE | UB->UAF | type system issue->lifetime inconsistency | No (aturon-Rust)| No | 
| arrayfire-rust  | **CVE-2018-20998** | [issues/176](https://github.com/arrayfire/arrayfire-rust/issues/176) | ALIGN+FFI | OOR | FFI-compatability/repr() | No (Aidan24) | No | 
| ncurses | **CVE-2019-15547** | [issues/172](https://github.com/jeaye/ncurses-rs/issues/172) | FNSIG(SAFE)+FFI | OOR | FFI-unchecked argument/printw() | thomcc | No | 
| ncurses | **CVE-2019-15548** | [issues/186](https://github.com/jeaye/ncurses-rs/issues/186) | FNSIG(SAFE)+FFI | OOR | FFI-unchecked argument/instr(), mvwinstr() | thomcc |
| rusqlite | **CVE-2020-35873** | [sessions.rs](https://github.com/rusqlite/rusqlite/commit/ac30e169ae51b262bc8cf7026469851ce39b23c6) | API:LIFETIME+FFI | UAF | similar to CVE-2018-20997 as_ptr() | thomcc-deps| No | 
| rusqlite | **CVE-2020-35872** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/71b2f5187b0cbace3f8b6ff53432ff2ca0defcf0) | API:ALIGN+FFI | UB->OOR | + repr(C) | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35871** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | API:TBOUND+CC | DR->UAF | lack sync/send bound | thomcc-deps| No | 
| rusqlite | **CVE-2020-35870** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | API:TBOUND+CC | DR->UAF | lack sync/send bound | thomcc-deps | No | 
| rusqlite | **CVE-2020-35869** | [log](https://github.com/rusqlite/rusqlite/commit/2327d3b774927fdf48903c0bdc1ca7ec93c7c8d0) | API:EAPI+FFI | OOR | wrong parameters in api call | thomcc-deps| No | 
| rusqlite | **CVE-2020-35868** | [UnlockNotification](https://github.com/rusqlite/rusqlite/commit/45fd77ee43c38eea4d6f4e2e56c1667a55ec654f) | API:LOE+CC | UB->UAF | UnlockNotification  | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35867** | [create_module](https://github.com/rusqlite/rusqlite/commit/3c6b57fe1b2cc87e7ebecde43dd836ffb1c4ea5c) | FNSIG(LIFETIME) | UB->UAF | static ref should point to static ret value | thomcc-deps| No | 
| rusqlite | **CVE-2020-35866** | [VTab](https://github.com/rusqlite/rusqlite/commit/c9ef5bd63cad5c0c123344c072b490a1a9bcbe1f) | FNSIG(SAFE) | UB | should declare trait as unsafe | No (gwenn-deps) | No | 
| rust-base64 | **CVE-2017-1000430** | [issues/28](https://github.com/marshallpierce/rust-base64/issues/28) | IMP:ARO | OOR | arithmatic overflow + unsafe write | No (alicemaz) | No | 
| failure | **CVE-2020-25575** | [issues/336](https://github.com/rust-lang-nursery/failure/issues/336) | TTYPECONV+ALIGN | OOR | downcast->misalign: same as CVE-2019-12083 | No (Qwaz-sec) | No | 
| bumpalo | **CVE-2020-35861** | [issues/69](https://github.com/fitzgen/bumpalo/issues/69) | IMP:LOE(Simple) | OOR(Read) | copy wrong size | No (Riey-deps)| No | 
| compact_arena | **CVE-2019-16139** | [issues/22](https://github.com/llogiq/compact_arena/issues/22) | IMP:LOE | UB->OOR | NLL issue->Index trait/get_unchecked() | No (CAD97) | No | 
| lz4_flex | Trophy | - | IMP:LOE | OOR | logical error in space allocation | Pascal Seitz-sec | No | 
| ozone | **CVE-2020-35877** | [index](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/buffer.rs#L38-L48) | API:BOUNDARY | OOR(Read) | lack boundary check | No (n.a.) | No | 
| ozone | **CVE-2020-35878** | [remove_entry](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/map.rs#L94-L101) | IMP:RAII | UNINIT | implement drop with uninit mem | No (n.a.)| No | 
 safe-transmute | **CVE-2018-21000** | [pull/36](https://github.com/nabijaczleweli/safe-transmute-rs/pull/36) | IMP:EAPI | OOR | wrong param order of from_raw_parts() | No (Enet4-deps)| No | 
| slice-deque | **CVE-2018-20995** | [issues/57](https://github.com/gnzlbg/slice_deque/issues/57) | IMP:BOUNDARY | OOR | error in boundary check + unsafe write | No (aldanor-deps) | No | 
| slice-deque | **CVE-2019-15543** | [pull/66](https://github.com/gnzlbg/slice_deque/pull/66) | IMP:CASE+LOE | OOR | lack special case handling ->memory misalignment | No (zimond) | No | 
| rust-smallvec | **CVE-2019-15554** | [issues/149](https://github.com/servo/rust-smallvec/issues/149) | IMP:LOE | OOR | logical error + unsafe write | No (ehuss) | No | 
| rust-smallvec | Advisory-DB | [issues/126](https://github.com/servo/rust-smallvec/issues/126) | RAII+UNWIND | UNINIT | init vector with mem:uninitialized() | No (mbrubeck) | No | 
| rust-smallvec | **CVE-2019-15551** | [issues/148](https://github.com/servo/rust-smallvec/issues/148) | IMP:LOE | UAF | logical error in manuall deallocation | No (ehuss) | No | 
| rust-smallvec | **CVE-2018-20991** | [issues/96](https://github.com/servo/rust-smallvec/issues/96) | UNWIND+RAII | DF | buffer shrinking too late | No (Vurich) | No | 
| simd-json | **CVE-2019-15550** | [pull/27](https://github.com/simd-lite/simd-json/pull/27) | IMP:CASE | OOR | lack special case handling->mem misalign/get_unchecked() | No (Licenser-deps) | No | 
| v_espace | Trophy Case | issues/47 | IMP:LOE | OOR | logical error->mem misalign | \_mm_load_si128() | No (tmiasko) | No | 
| sized-chunks | **CVE-2020-25791** | [issues/11:unit](https://github.com/bodil/sized-chunks/issues/11) | API:CASE+GENERIC | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25792** | [issues/11:pair](https://github.com/bodil/sized-chunks/issues/11) | API:CASE+GENERIC | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25793** | [issues/11:From](https://github.com/bodil/sized-chunks/issues/11) | API:CASE+GENERIC | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25796** | [issues/11:InlineArray](https://github.com/bodil/sized-chunks/issues/11) | API:CASE+GENERIC | OOR:BO | no input check->memory misalignment | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25794** | [issues/11:clone](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | UNINIT | panic->drop uninitialized memory | No (Qwaz-sec)  | No | 
| sized-chunks | **CVE-2020-25795** | [issues/11:insert_from](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | UNINIT | panic $\to$ rop uninitialized memory | No (Qwaz-sec)  | No | 
| actix-net | **CVE-2020-35902** | [issues/91](https://github.com/actix/actix-net/issues/91) | API:LOE(SYS:MMAP) | UAF | frame should be pined | sebzim4500 | No | 
| actix-net | **CVE-2020-35899** | [pull/158](https://github.com/actix/actix-net/pull/158) | EAPI+DR | UB->UAF | replace Cell<T> with Rc<RefCell<T>> | Shnatsel | No | 
| actix-net | **CVE-2020-35898** | [issues/160](https://github.com/actix/actix-net/issues/160) | EAPI+RC | UB->UAF | replace Cell<T> with Rc<RefCell<T>>  | Shnatsel | No | 
| actix-web | Advisory-DB | issues/289 | API:MUTE | UB->UAF | transmute immutable ref to mutable | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | API:LIFE | UAF | transmutate lifetime to static | seanmonstar | No | 
| actix-web | Advisory-DB | issues/289 | IMP:TRAIT+GENERIC | UAF | Clone+Rc | seanmonstar | No | 
| actix-web | Advisory-DB | issues/301 | API:CC+TRAIT+GENERIC | UAF | unsafe impl of Send for generics races Rc | seanmonstar-Mozilla | No | 
| actix-web | **CVE-2020-35901** | [issues/1321](https://github.com/actix/actix-web/issues/1321) | API:LOE(SYS:MMAP) | UAF | BodyStream should be pined | sebzim4500 | No | 
| alg_ds | Advisory-DB | issues/1 | IMP:RAII | UNINIT | init with alloc::alloc | Qwaz-Sec | No | 
| rust-arch | **CVE-2020-35885** | [issues/2](https://github.com/pigeonhands/rust-arch/issues/2) | IMP:RAII+STRUCT | UB:UAF | self defined struct: direct construction->drop memory not owned | Qwaz-Sec | No | 
| arc-swap | **CVE-2020-35711** | [issues/45](https://github.com/vorner/arc-swap/issues/45) | API:PHANTOM+TRAIT | UAF | logical errors +PhantomData | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Array | TBOUND+CC | DR->UAF | lack send/sync bound  | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:Index | IMP:TRAIT | OOR | lack boundary check | Qwaz-Sec | No | 
| arr | Advisory-DB | issues/1:from... | IMP: | UNINIT | drop uninitialized mem | Qwaz-Sec | No | 
| array-queue | **CVE-2020-35900** | [issues/2](https://github.com/raviqqe/array-queue/issues/2) | IMP:NO | UAF | FALSE CVEs? | ammaraskar-Sec | No | 
| array-queue | Advisory-DB | issues/2 | RAII | UNINIT | use mem::uninitialized() | ammaraskar-Sec | No | 
| atom | **CVE-2020-35897** | [issues/13](https://github.com/slide-rs/atom/issues/13) | API:TBOUND+CC | DR->UAF | lack send/sync bound | ammaraskar-Sec | No | 
| chunky | Advisory-DB | issues/2 | IMP:LOE | OOR | API ignores memory alignment requirement | Qwaz-Sec  | No | 
| dync | **CVE-2020-35903** | [issues/4](https://github.com/elrnv/dync/issues/4) | IMP:ALIGN | OOR | memory misalignment | ammaraskar-Sec | No | 
| concread | **CVE-2020-35928** | [issues/48](https://github.com/kanidm/concread/issues/48) | API:TBOUND+CC | DR->UAF | lack send/sync bound | JOE1994-Sec | No | 
| futures-intrusive | Advisory-DB | issues/53 | API:TRAIT+CC | CC->UAF | lack send/sync bound | ammaraskar-Sec| No | 
| futures-rs | **CVE-2020-35906** | [pull/2206](https://github.com/rust-lang/futures-rs/pull/2206) | API:TBOUND+LIFE | UAF | lack lifetime bound | Darksonn | No | 
| futures-rs| **CVE-2020-35907** | [issues/2091](https://github.com/rust-lang/futures-rs/issues/2091) | IMP:LOE+LIFE | UAF | ref lives longer than thread (UnsafeCell->Lazy) | goffrie | No | 
| futures-rs| **CVE-2020-35905** | [issues/2239](https://github.com/rust-lang/futures-rs/issues/2239) | API:TBOUND+CC | CC->UAF | lack send/sync bound | Qwaz-Sec | No | 
| futures-rs| **CVE-2020-35908** | [issues/2050](https://github.com/rust-lang/futures-rs/issues/2050) | API:LOE+CC | UAF | lack enough sync: impl sync for a structure with Cell<T> | okready | No | 
| pulse-binding-rust | Advisory-DB | | PHANTOM | UAF | lack lifetime bound: +PhantomData | jnqnfe | No | 
| pulse-binding-rust | Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready | No |
| parking_lot | **CVE-2020-35910** | [MappedMutexGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | DR->UAF | lack send bound | ammaraskar-Sec | No |  
| parking_lot | **CVE-2020-35911** | [MappedRwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | DR->UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | **CVE-2020-35912** | [MappedRwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | DR->UAF |  lack send bound | ammaraskar-Sec | No |  
| parking_lot | **CVE-2020-35913** | [RwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND+CC | DR->UAF |  lack sync bound | ammaraskar-Sec | No | 
| parking_lot | **CVE-2020-35914** | [RwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND+CC | DR->UAF |  lack sync bound | ammaraskar-Sec | No | 
| magnetic | **CVE-2020-35925** | [issues/9](https://github.com/johnshaw/magnetic/issues/9) | TBOUND+CC | DR->UAF | lack send/sync bound | JOE1994-Sec | No | 
| miow | **CVE-2020-35921** | [issues/38](https://github.com/yoshuawuyts/miow/issues/38) | IMP:FFI | UB | assumes the same layout of FFI | faern | No | 
| net2-rs | **CVE-2020-35920** | [issues/105](https://github.com/deprecrated/net2-rs/issues/105) | IMP:FFI | UB | assumes the same layout of FFI | Thomasdezeeuw | No |  
| rust-ordered-float | **CVE-2020-35923** | [pull/71](https://github.com/reem/rust-ordered-float/pull/71) | IMP:LOE | UB | panic may cause UB | branpk | No |  
| pyo3 | **CVE-2020-35917** | [pull/1297](https://github.com/PyO3/pyo3/pull/1297) | IMP:RAII+LOE | IMP：UAF | unthought of dropping | davidhewitt | No |  
| thex | **CVE-2020-35927** | - | API:TBOUND+CC | DR->UAF | lack send/sync bound | Qwaz-Sec | No |  
| time | **CVE-2020-26235** | [issues/293](https://github.com/time-rs/time/issues/293) | FFI+CC+SYS | UB->UAF | call non-atomic libc functions (setenv) | quininer | <-> |  
| try-mutex | **CVE-2020-35924** | [issues/2](https://github.com/mpdn/try-mutex/issues/2) | TBOUND+CC | DR->UAF | lack send/sync bound | ammaraskar-Sec | No |  
| isahc | **CVE-2019-16140** | [issues/2](https://github.com/sagebind/isahc/issues/2) | RAII | UAF | unsafe constructor+no ManuallyDrop | No (nox) | No | 
| sxd-document  | Trophy Case | issues/47 | IMP:RAII | UAF | unsafe constructor+no ManuallyDrop | No (CryZe-sec) | No | 
| image | **CVE-2019-16138** | [issues/980](https://github.com/image-rs/image/issues/980) | UNWIND+RAII | UNINIT | unsafe allocation->drop uninit mem/set_len() | No (64) | No | 
| image | **CVE-2020-35916** | [issues/1357](https://github.com/image-rs/image/issues/1357) | IMP:EAPI+MUT | UB | convert mutable ptr from const ptr | dodomorandi | No | 
| libflate | **CVE-2019-15552** | [issues/35](https://github.com/sile/libflate/issues/35) | RAII+UNWIND  | UNINIT | enf. ManuallyDrop late->drop uninit | No (Shnatsel-sec) | No | 
| memoffset | **CVE-2019-15553** | [issues/9](https://github.com/Gilnaa/memoffset/issues/9) | RAII+UNWIND | UNINIT | enf. ManuallyDrop late->drop uninit mem  | No (Centril) | No | 
| linked-hash-map | **CVE-2020-25573** | [pull/100](https://github.com/contain-rs/linked-hash-map/pull/100/) | RAII | UNINIT | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)| No | 
| rio | **CVE-2020-35876** | [issues/11](https://github.com/spacejam/rio/issues/30) | FNSIG(SAFE) | UAF | logical error: soundness hole | No (dtolnay-Rust) | No | 
| bitvec | **CVE-2020-35862** | [issues/55](https://github.com/myrrlyn/bitvec/issues/55) | IMP:LOE | UAF | logical error: false assumption | No (kulp-sec) | No | 
| cbox-rs | **CVE-2020-35860** | [issues/2](https://github.com/TomBebbington/cbox-rs/issues/2) | FNSIG(SAFE) | UAF | declare unsafe API as safe | No (eduardosm) | No | 
| rust-openssl | **CVE-2018-20997** | [issues/941](https://github.com/sfackler/rust-openssl/issues/941) | RAII | UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)| No | 
| string-interner | **CVE-2019-16882** | [issues/9](https://github.com/Robbepop/string-interner/issues/9) | TRAIT | UAF | bad derived clone | No (lo48576-deps) | No |  
| crossbeam | **CVE-2018-20996** | [issues/82](https://github.com/crossbeam-rs/crossbeam/issues/82) | RAII | DF | shared mut aliases+auto drop/+ManuallyDrop | No (c0gent-deps) | No | 
| crossbeam | **CVE-2020-35904** | [pull/533](https://github.com/crossbeam-rs/crossbeam/pull/533) | IMP:LOE | UB->UAF | drop memory not owned | caelunshun | No | 
| generator-rs | **CVE-2019-16144** | [issues/11](https://github.com/Xudong-Huang/generator-rs/issues/11) | RAII | DF | shared mut aliases+auto drop | No (vOROn200) | No | 
| generator-rs | Advisory-DB | [issues/9](https://github.com/Xudong-Huang/generator-rs/issues/9) | FNSIG(SAFE) | UB | func. sign.->deref invalid/null pointer | No (jonas-schievink)| No | 
| generator-rs | Advisory-DB | [issues/13](https://github.com/Xudong-Huang/generator-rs/issues/13) | API | UB | bad func. exposure  | No (jonas-schievink) | No | 
| generator-rs | Advisory-DB  | [issues/14](https://github.com/Xudong-Huang/generator-rs/issues/14) | API | UB | bad func. exposure | No (jonas-schievink)  | No | 
| linea.rs | **CVE-2019-16880** | [issues/1](https://github.com/strake/linea.rs/pull/2) | UNWIND+RAII | DF | enf. ManuallyDrop late | No (Phosphorus15)| No | 
| portaudio-rs | **CVE-2019-16881** | [issues/20](https://github.com/mvdnes/portaudio-rs/issues/20) | UNWIND+RAII | DF | enf. ManuallyDrop late | No (Phosphorus15) | No | 
| http | **CVE-2020-25574** | [issues/354](https://github.com/hyperium/http/issues/354) | UNWIND+RAII | DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) | No | 
| http | Advisory-DB | [issues/355](https://github.com/hyperium/http/issues/355) | TBOUND+LIFE | DR->UAF | lack lifetime bound->multile mut refs  | No (Qwaz-sec)  | No | 
| internment | **CVE-2020-35874** | issues/11 | IMP:CC+GEN | UB | impl error: Ordering, atomic::fence() | No (ryzhyk-deps)| No | 
| spin-rs  | **CVE-2019-16137** | [issues/65](https://github.com/mvdnes/spin-rs/issues/65) | IMP:EAPI+CC | UB->UAF | impl error: Ordering::Relaxed->Release | 64 | No | 
| bigint | **CVE-2020-35880** | [deprecated](https://github.com/paritytech/bigint/commit/7e71521a61b009afc94c91135353102658550d42) | IMP:DEP | UB | use uint instead | | No | 
| array | **CVE-2020-35886** | [issues/1](https://github.com/sjep/array/issues/1) | TBOUND+CC | DR->UAF | lack Sync/Send bound | Qwaz-Sec | No |
| array | **CVE-2020-35887** | [issues/1](https://github.com/sjep/array/issues/1) | IMP:LOE | OOR | Index and IndexMut impl does not check the array bound | Qwaz-Sec | No | Yes |
| array | **CVE-2020-35888** | [issues/1](https://github.com/sjep/array/issues/1) | RAII | UNINIT | drop uninit mem | Qwaz-Sec | No |
| crayon | **CVE-2020-35889** | [issues/87](https://github.com/shawnscode/crayon/issues/87) | IMP:CUST+CC+TRAIT | UAF | time-of-check to time-of-use (TOCTOU) bug | Qwaz | No | 
| ordnung | **CVE-2020-35890** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | IMP:LOE | OOR | | Qwaz | No |
| ordnung | **CVE-2020-35891** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | UNWIND+RAII | DF | | Qwaz | No |
| simple-slab | **CVE-2020-35892** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | IMP:BOUNDARY | OOR | Slab::index() does not perform the boundary checking | Qwaz | No |
| simple-slab | **CVE-2020-35893** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | IMP:BOUNDARY | OOR | copies an element from an invalid address due to off-by-one error | Qwaz | No | 
| obstack | **CVE-2020-35894** | [issues/4] (https://github.com/petertodd/rust-obstack/issues/4) | IMP:CASE+CUST+LOE | UB | generates unaligned references for types with a large alignment | Qwaz | No | 
| stack-rs | **CVE-2020-35895** | [issues/4](https://github.com/arcnmx/stack-rs/issues/4) | IMP:BOUNDARY | OOR | lack boundary check | ammaraskar | No | No |
| vm-memory | **CVE-2020-13759** | [issues/93](https://github.com/rust-vmm/vm-memory/issues/93) | EAPI+RW+CC | UB | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)| No | 
| Rocket | **CVE-2020-35882** | [issues/1312](https://github.com/SergioBenitez/Rocket/issues/1312) | IMP:LOE+TRAIT+CC | UB->UAF| Clone may incur mutable aliases | Qwaz | No |
| teaclave-sgx-sdk  | **CVE-2020-5499** | www.mitre.org | API:CC+LOE | UB | may init twice by another thread/+Once::new() | No (Chen-sec) | No | 
| claxon  | **CVE-2018-20992**/Trophy | [issues/10](https://github.com/ruuda/claxon/issues/10) | IMP:LOE | UNINIT->DL | Vec::set_len()->read unit mem | No (Shnatsel-sec)| No | 
| traitobject | **CVE-2020-35881** | [issues/7](https://github.com/reem/rust-traitobject/issues/7) | IMP:LOE+TYPECONV | UB->OOR | assumes that the first element is a fat pointer is the data pointer | eduardosm | No |
| rust-rgb | **CVE-2020-25016** | [issues/35](https://github.com/kornelski/rust-rgb/issues/35) | FNSIG(SAFE) | UB | declare unsafe API as safe | No (HeroicKatora) | No | 
| renderdoc-rs | **CVE-2019-16142** | [issues/27](https://github.com/ebkalderon/renderdoc-rs/issues/27) | FNSIG(MUT) | UB | mutable (internal mutation) | No (ebkalderon-owner) | No | 
| rulinalg | **CVE-2020-35879** | [issues/201](https://github.com/AtheMathmo/rulinalg/issues/201) | FNSIG(LIFE) | UB->UAF | func. sign.:lifetime | No (Qwaz-sec)  | No | 
| flatbuffers | **CVE-2020-35864** | [issues/5825](https://github.com/google/flatbuffers/issues/5825) | FNSIG(SAFE) | UB | func. sign.: safety declaration | No (eduardosm)| No | 
| flatbuffers | Advisory-DB | issues/5530 | IMP:LOE | UB | logical error->invalid bit pattern for bool | No (nagisa)| No | 
| once_cell | **CVE-2019-16141** | [issues/46](https://github.com/matklad/once_cell/issues/46) | EAPI | UB | unreachable_unchecked()->panic!() | No (xfix-deps) | No | 
| capnproto-rust | Trophy Case | cargo-fuzz/issues/40 | IMP:LOE | Unsound | logical error | No (dwrensha-sec)| No | 
| lucet | **CVE-2020-35859** | pull/401 | IMP:LOE  | UB | logical error->memory man. issue | No (acfoltzer-deps) | No | 
| rand | **CVE-2020-25576** | [issues/779](https://github.com/rust-random/rand/issues/779) | EAPI+R/W+LLVM | UB | reading unaligned mem/ptr::read_unaligned() | (RalfJung-sec)| No | 
| os_str_bytes | **CVE-2020-35865** | [pull/1](https://github.com/dylni/os_str_bytes/pull/1) | IMP:LOE+TYPE | UB |  eduardosm  | No | 
| servo (exe) | GitHub | issues/1186 | IMP:RAII | DF | impl Drop with unsafe | kmcallister | No | 
| servo (exe) | GitHub | issues/2412 | IMP:RAII | DF  | unsafe cast?  |  | No | 
| servo (exe) | GitHub | issues/14014 | IMP:CC+RAII | UAF |   | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/14416 | IMP:RAII | UAF  | FnBox  | pcwalton-deps | No | 
| servo (exe) | GitHub | issues/20158 | APU:SAFE | UB | declare unsafe constructor as safe  | nox-org | No | 
| servo (exe) | GitHub | issues/21186 | IMP:CC+LOE | UB | Relaxed$\to$Acquire |  | No | 
| servo (exe) | GitHub | pull/26641 | IMP:LOE | UB | mem::transmute->Box::into_raw() | dylni | No |
| wasmer (exe) | GitHub | pull/1092 | IMP:SAFE | OOR | lack input consistency check + unsafe constructor | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1206 | IMP:SAFE | Unsound | possible to create shared mutable aliases | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1209 | IMP:SAFE | CC:DR | multiple Cells for the same memory | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | pull/1837 | IMP:SAFE | Unsound | declare unsafe API as safe | MarkMcCaskey-dev | No | 
| wasmer (exe) | GitHub | issues/1568 | RAII: | UAF | shared mutable alises (slice+to_vec()) | Hywan-dev | No | 
| alacritty (exe) | GitHub | pull/4397 | IMP:MODEL | UAF | shared mut aliases (ptr::copy->clone) | kchibisov-dev | No | 
| alacritty (exe) | GitHub | pull/2176  | IMP:LOE | UAF | logical error (+as_ref()) | aspurdy | No | 
| diem-libra (exe) | GitHub | pull/1949 | API:LIFE | UAF | ineffective lifetime restriction | dtolnay-Rust  |
| wint | GitHub | issues/599 | IMP:CC | UB | non-atomic cell for multi-thread apps | andrewhickman | No | 
| wint | GitHub | pull/611 | IMP:CC | UB | non-atomic cell for multi-thread apps | francesca64-dev | No | 
| wint | GitHub | issues/1745 | IMP:LOE | UAF | logical error | qthree | No | 
| Tokio | **CVE-2020-35922** | [issues/1386](https://github.com/tokio-rs/tokio/issues/1386) | FFI | UB | assumes the same layout of FFI | Nemo157-Rust | No | 
| Tokio | GitHub | *pull/254 |  | UAF | | seanmonstar-dev | No | 
| Tokio | GitHub | issues/354 | IMP: | UNINIT | uninit memory for Vec<u8> with set_len() | udoprog | No | 
| Tokio | GitHub | issues/593 | :CC |  | | NPN |
| Tokio | GitHub | pull/2030/ | API: | OOR | trait safety | Marwes | 
| Tokio | GitHub | pull/2612/ | API:TRAIT | OOR | error in specify Trait impl Type  | taiki-e-dev | 
| Tokio | GitHub | issues/3014 | IMP:LOE | UAF | off-by-one logical error | NikosEfthias |
| curl-rust | GitHub | pull/2 | IMP:SAFE | UAF | **using mem::transmute() | No(alexcrichton-rust) | No | 
| curl-rust | GitHub | issues/333 | API:CC | UB | does not enforce FFI restrictions | DemiMarie/sagebind-deps | Yes | 
| curl-rust | GitHub | issues/340 | API:SAFE | UAF | exposing unsafe cleanup APIs as safe | sagebind-deps | No | 

### Notes: 
OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; CC: concurrency issue; DF: double free; DL: data leakage; DP: dangling pointer; DR: data race; 
RC: race condition; UAF: use-after-free.

### Other CVEs (Non-Memory-Safety Issue): 
* Crypto/Functionality Issue: CVE-2016-10932, CVE-2017-18587, CVE-2018-20999, CVE-2019-15545, CVE-2019-16760, CVE-2017-1000168, CVE-2020-15093, CVE-2020-26281, CVE-2020-35926, CVE-2020-35883;

* MITM/Code Injection: CVE-2016-10931, CVE-2016-10933, CVE-2020-26222, CVE-2020-26297, CVE-2020-28247, CVE-2020-35863, CVE-2020-35884; 

* StackOverflow/Crash: CVE-2017-18589, CVE-2018-20989, CVE-2018-20993, CVE-2018-20994, CVE-2019-15542, CVE-2019-15544, CVE-2019-15549, CVE-2020-35857, CVE-2020-35858, CVE-2020-35875, CVE-2020-35896, CVE-2020-35909.

* Cargo/Rustdoc: CVE-2018-1000622, CVE-2019-16760  
