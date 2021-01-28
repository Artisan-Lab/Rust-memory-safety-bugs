# rustbugs
  
| Project | CVE-ID (or Src) | Link | Culprit | Difficulty to Triger  | Consequense | Details | Finder-Role | Propagated | Revise (Unsafe->Safe) | BadDrop? |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | **CVE-2018-1000810** | [pull/54399](https://github.com/rust-lang/rust/pull/54399) | ARO | ERR | OOR | arithmatic overflow (str:repeat) | scottmcm-Rust | No | | - |
| rust-std | **CVE-2018-1000657** | [issues/44800](https://github.com/rust-lang/rust/issues/44800) | BOUNDARY | ERR | OOR | incorrect boundary check (VecDeque) | jesse99-deps | No | | - |
| rust-std | **CVE-2019-12083** | [issues/60784](https://github.com/rust-lang/rust/issues/60784) | TYPE+TYPECONV | UNSOUND | OOR | TRAIT：TYPECONV:soundness hole impl Error::type_id() + downcasting | seanmonstar-deps | No | - |
| rust-std | GitHub | [issues/17207](https://github.com/rust-lang/rust/issues/17207) | FFIUB | UNSOUND | UB | args are UB in jemalloc ( Vec::from_elem) | gmorenz | No | 
| rust-std | GitHub | [issues/25841](https://github.com/rust-lang/rust/issues/25841) | ARO+MODEL | ERR | UAF | arithmatic overflow->shared mut aliases (RefCell) | Veedrac | No | 
| rust-std | GitHub | [issues/27970](https://github.com/rust-lang/rust/issues/27970) | FFIUB+CC | MID | UAF | setenv is unsafe | bluss-Rust | No | 
| rust-std | GitHub | [issues/33770](https://github.com/rust-lang/rust/issues/33770) | FFIUB+CC | UNSOUND | UAF | glibc recursive lock is UB->shared mut aliases | Amanieu | No | 
| rust-std | GitHub | [issues/35836](https://github.com/rust-lang/rust/issues/35836) | FFIUB+CC | UNSOUND | UAF | recursive RWlock on Windows is UB | retep998-Rust | No | 
| rust-std | GitHub | [issues/39465](https://github.com/rust-lang/rust/issues/39465) | FNSIG(MUT) | UNSOUND | DP | Fn signature issue->shared mut aliases | christophebiocca | No | 
| rust-std | GitHub | [issues/39575](https://github.com/rust-lang/rust/issues/39575) | FNSIG(UNSAFE)+FFI+CC | UNSOUND | UB | should be unsafe, UB according to POSIX (CommandExt::before_exec) | fweimer | No | 
| rust-std | GitHub | [issues/42135](https://github.com/rust-lang/rust/issues/42135) | CASE+TGENERIC | ERR | UB | miss handling cases (degenerate inclusive ranges  )->incorrect result (TrustedLen) | scottmcm-Rust | No | 
| rust-std | GitHub | [issues/42789](https://github.com/rust-lang/rust/issues/42789) | GENERIC+CASE | ERR | OOR | interators over ZST slices are undefined->random addr （Iter+ZST） | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/43733](https://github.com/rust-lang/rust/issues/43733) | LOE+CC | UNSOUND | UAF | access static value without unsafe marker->CC(thread::local) | eddyb-Rust | No | 
| rust-std | GitHub | [issues/44637](https://github.com/rust-lang/rust/issues/44637) | CASE | UNSOUND | OOR | does not handle -1 properly (Placer) | andy-hanson | No | 
| rust-std | GitHub | [issues/45197](https://github.com/rust-lang/rust/issues/45197) | TYPE+CC | UNSOUND | UAF | AUTOTRAIT:bypassing sync/send check（fmt::Arguments）+PhantomData | cuviper-Rust | No | 
| rust-std | GitHub | [issues/46775](https://github.com/rust-lang/rust/issues/46775) | FFIUB+CC | MID | UAF | multi-thread unsafe (unix::process::CommandExt::exec) | Diggsey | No | 
| rust-std | GitHub | [issues/48006](https://github.com/rust-lang/rust/issues/48006) | ARO | ERR | OOR | arithmatic overflow on 16-bit platforms | oberien | No | 
| rust-std | GitHub | [issues/48493](https://github.com/rust-lang/rust/issues/48493) | GENERIC+RAII | ERR | UNINIT | Weak<T> frees uninitialized mem with <Void> | jleedev | No | 
| rust-std | GitHub | [issues/51780](https://github.com/rust-lang/rust/issues/51780) | EAPI(MEM)+CC | ERR | DR->UAF | insufficient synchronization (Arc::is_unique) Relaxed->Acquire | jhjourdan | No | 
| rust-std | GitHub | [issues/54857](https://github.com/rust-lang/rust/issues/54857) | GENERIC+CASE | ERR | OOR | UB in computing the offset addr for ZST or 0-len Vec（Vec） | jturner314 | No | 
| rust-std | GitHub | [issues/54908](https://github.com/rust-lang/rust/issues/54908) | GENERIC+CASE | ERR | OOR | misaligned reference（RC，ARC） | RalfJung | No | 
| rust-std | GitHub | [issues/54957](https://github.com/rust-lang/rust/issues/54957) | LOE+TYPE | ERR | OOR | inconsistent type of Root node (BTreeSet) | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/57534](https://github.com/rust-lang/rust/issues/57534) | UBFFI+CC | ERR | UAF | TLS:_tlv_atexit during tlv_finalize is UB (thread_local) | mtak- | May | 
| rust-std | GitHub | [issues/60977](https://github.com/rust-lang/rust/issues/60977) | UNWIND+RAII | ERR | DF | double free while panic (Vec::drain_filter) | rustonaut | No | | May |
| rust-std | GitHub | [issues/66544](https://github.com/rust-lang/rust/issues/66544) | TGENERIC | ERR | UB->UAF | soundness holes of when impl DerefMut/Clone (Pin) | comex |
| rust-std | GitHub | [issues/67194](https://github.com/rust-lang/rust/issues/67194) | TGENERIC | UNSOUND | UB->OOR | violate the always applicable test (PartialEq for RangeInclusive) | comex | No | 
| rust-std | GitHub | [issues/72624](https://github.com/rust-lang/rust/issues/72624) | ARO | EER | OOR | possible arithmatic overflow (DroplessArena::alloc_raw) | bluss-Rust | No |
| rust-std | GitHub | [issues/72760](https://github.com/rust-lang/rust/issues/72760) | LOE | MID | UB | TYPE:invalid UTF-8 | RalfJung-Rust | No |
| rust-std | GitHub | [issues/76367](https://github.com/rust-lang/rust/issues/76367) | RAII+CC | ERR | UAF | logical error (SyncOnceCell/dropck)+PhantomData | m-ou-se-Rust |
| rust-std | GitHub | [issues/78477](https://github.com/rust-lang/rust/issues/78477) | LOE | NO | UNKNOWN | violate pointer provenance rules | RalfJung-Rust | No |
| rust-std | GitHub | [issues/78498](https://github.com/rust-lang/rust/issues/78498) | UNWIND | ERR | UB | TYPE:invalid UTF-8 while catch_unwind (String) | SkiFire13 | No |
| rust-std | Advisory-DB | [issues/79808](https://github.com/rust-lang/rust/issues/79808) | BOUNDARY | EER | UB->\*UAF | incorrect boundary check (VecDeque) | ayourtch | No |
| rust-std | GitHub | [issues/80338](https://github.com/rust-lang/rust/issues/80338) | BOUNDARY | ERR | UB->\*UAF | incorrect boundary check (VecDeque)-79808 | Aratz | No | | - |
| rustc (fake-static) | Advisory-DB | [issues/25860](https://github.com/rust-lang/rust/issues/25860) | COMPILER | UNSOUND | UB->UAF | type system issue->lifetime inconsistency | aturon-Rust | No | - | - | 
| arrayfire-rust  | **CVE-2018-20998** | [issues/176](https://github.com/arrayfire/arrayfire-rust/issues/176) | FFIUB | ERR | OOR | FFI-compatability/repr() | No (Aidan24) | No | 
| ncurses | **CVE-2019-15547** | [issues/172](https://github.com/jeaye/ncurses-rs/issues/172) | FNSIG(SAFE)+FFI | UNSOUND | OOR | FFI-unchecked argument/printw() | thomcc | No | 
| ncurses | **CVE-2019-15548** | [issues/186](https://github.com/jeaye/ncurses-rs/issues/186) | FNSIG(SAFE)+FFI | UNSOUND | OOR | FFI-unchecked argument/instr(), mvwinstr() | thomcc |
| rusqlite | **CVE-2020-35873** | [sessions.rs](https://github.com/rusqlite/rusqlite/commit/ac30e169ae51b262bc8cf7026469851ce39b23c6) | RAII | ERR | UAF | similar to CVE-2018-20997 as_ptr() | thomcc-deps| No | 
| rusqlite | **CVE-2020-35872** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/71b2f5187b0cbace3f8b6ff53432ff2ca0defcf0) | FFIUB | ERR | UB->OOR | + repr(C) | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35871** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | TBOUND+CC | UNSOUND | DR->UAF | lack sync/send bound | thomcc-deps| No | 
| rusqlite | **CVE-2020-35870** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | TBOUND+CC | UNSOUND | DR->UAF | lack sync/send bound | thomcc-deps | No | 
| rusqlite | **CVE-2020-35869** | [log](https://github.com/rusqlite/rusqlite/commit/2327d3b774927fdf48903c0bdc1ca7ec93c7c8d0) | EAPI+FFI | ERR| OOR | wrong parameters in api call | thomcc-deps| No | 
| rusqlite | **CVE-2020-35868** | [UnlockNotification](https://github.com/rusqlite/rusqlite/commit/45fd77ee43c38eea4d6f4e2e56c1667a55ec654f) | RAII+CC | ERR | UB | NLL:mutex lock is released before send condvar | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35867** | [create_module](https://github.com/rusqlite/rusqlite/commit/3c6b57fe1b2cc87e7ebecde43dd836ffb1c4ea5c) | FNSIG(LIFETIME) | UNSOUND | UB->UAF | static ref should point to static ret value | thomcc-deps| No | 
| rusqlite | **CVE-2020-35866** | [VTab](https://github.com/rusqlite/rusqlite/commit/c9ef5bd63cad5c0c123344c072b490a1a9bcbe1f) | FNSIG(SAFE) | UNSOUND | UB | should declare trait as unsafe | No (gwenn-deps) | No | 
| rust-base64 | **CVE-2017-1000430** | [issues/28](https://github.com/marshallpierce/rust-base64/issues/28) | ARO | ERR | OOR | arithmatic overflow + unsafe write | No (alicemaz) | No | 
| failure | **CVE-2020-25575** | [issues/336](https://github.com/rust-lang-nursery/failure/issues/336) | TYPE+TYPECONV | UNSOUND | OOR | TYPECONV:downcast->misalign: same as CVE-2019-12083 | No (Qwaz-sec) | No | 
| bumpalo | **CVE-2020-35861** | [issues/69](https://github.com/fitzgen/bumpalo/issues/69) | LOE(Simple) | ERR | OOR(Read) | copy wrong size | No (Riey-deps)| No | 
| compact_arena | **CVE-2019-16139** | [issues/22](https://github.com/llogiq/compact_arena/issues/22) | LOE | ERR | OOR | NLL issue->Index trait/get_unchecked() | No (CAD97) | No |
| lz4_flex | Trophy | [commit](https://github.com/PSeitz/lz4_flex/commit/ce92fbf28c94a0f1f6ebc711c86d854e2c9e5622) | LOE | ERR | OOR | logical error in space allocation | Pascal Seitz-sec | No | 
| ozone | **CVE-2020-35877** | [index](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/buffer.rs#L38-L48) | BOUNDARY | MID | OOR(Read) | lack boundary check | No (n.a.) | No | 
| ozone | **CVE-2020-35878** | [remove_entry](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/map.rs#L94-L101) | RAII | ERR | UNINIT | implement drop with uninit mem | N.A. | No | | Yes | 
 safe-transmute | **CVE-2018-21000** | [pull/36](https://github.com/nabijaczleweli/safe-transmute-rs/pull/36) | EAPI | ERR | OOR | wrong param order of from_raw_parts() | Enet4-deps | No | No | - |
| slice-deque | **CVE-2018-20995** | [issues/57](https://github.com/gnzlbg/slice_deque/issues/57) | BOUNDARY | ERR |OOR | error in boundary check + unsafe write | No (aldanor-deps) | No | 
| slice-deque | **CVE-2019-15543** | [pull/66](https://github.com/gnzlbg/slice_deque/pull/66) | CASE | ERR | OOR | lack special case handling ->memory misalignment | zimond | No | No | - |
| rust-smallvec | **CVE-2019-15554** | [issues/149](https://github.com/servo/rust-smallvec/issues/149) | LOE | ERR | OOR | logical error + unsafe write | No (ehuss) | No | 
| rust-smallvec | Advisory-DB | [issues/126](https://github.com/servo/rust-smallvec/issues/126) | EAPI | ERR | UNINIT | init vector with mem:uninitialized() | No (mbrubeck) | No | Yes |
| rust-smallvec | **CVE-2019-15551** | [issues/148](https://github.com/servo/rust-smallvec/issues/148) | LOE | ERR | UAF | miss an else branch->manuall deallocation | ehuss | No | No | May | 
| rust-smallvec | **CVE-2018-20991** | [issues/96](https://github.com/servo/rust-smallvec/issues/96) | UNWIND+RAII | ERR | DF | buffer shrinking too late | Vurich | No | | Hard |
| simd-json | **CVE-2019-15550** | [pull/27](https://github.com/simd-lite/simd-json/pull/27) | CASE | ERR | OOR | lack special case handling->mem misalign/get_unchecked() | Licenser-deps | No | No | - |
| v_espace | Trophy Case | [issues/47](https://github.com/botika/v_escape/issues/47) | CASE+FFIUB | ERR | OOR | logical error->mem misalign | \_mm_load_si128() | tmiasko | No | No | - |
| sized-chunks | **CVE-2020-25791** | [issues/11:unit](https://github.com/bodil/sized-chunks/issues/11) | TYPE+CASE | UNSOUND | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25792** | [issues/11:pair](https://github.com/bodil/sized-chunks/issues/11) | TYPE+CASE | UNSOUND | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25793** | [issues/11:From](https://github.com/bodil/sized-chunks/issues/11) | TYPE+CASE | UNSOUND | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25796** | [issues/11:InlineArray](https://github.com/bodil/sized-chunks/issues/11) | TYPE+CASE | UNSOUND | OOR | no input check->memory misalignment | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25794** | [issues/11:clone](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | ERR | UNINIT | panic->drop uninitialized memory | Qwaz-sec | No | | Yes |
| sized-chunks | **CVE-2020-25795** | [issues/11:insert_from](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | ERR | DF | panic->double drop | No (Qwaz-sec)  | No | | Hard |
| actix-net | **CVE-2020-35902** | [issues/91](https://github.com/actix/actix-net/issues/91) | TBOUND+CC | UNSOUND | DR->UAF | frame should be pined | sebzim4500 | No | No | No |
| actix-net | **CVE-2020-35899** | [pull/158](https://github.com/actix/actix-net/pull/158) | EAPI+CC | ERR | DR->UAF | replace Cell<T> with Rc<RefCell<T>> | Shnatsel | No | | No |
| actix-net | **CVE-2020-35898** | [issues/160](https://github.com/actix/actix-net/issues/160) | EAPI+CC | ERR | DR->UAF | replace Cell<T> with Rc<RefCell<T>>  | Shnatsel | No | | No |
| actix-web | Advisory-DB | [issues/289](https://github.com/actix/actix-web/issues/289) | LOE | UNSOUND | UAF | multiple issues | seanmonstar | No | No | - |
| actix-web | Advisory-DB | [issues/301](https://github.com/actix/actix-web/issues/301) | TGENERIC | UNSOUND | UAF | InternalError with generics is unsound for Rc | seanmonstar-Mozilla | No | 
| actix-web | **CVE-2020-35901** | [issues/1321](https://github.com/actix/actix-web/issues/1321) | TBOUND+CC | UNSOUND | DR->UAF | BodyStream should be pined | sebzim4500 | No | | No |
| alg_ds | Advisory-DB | [issues/1](https://gitlab.com/dvshapkin/alg-ds/-/issues/1) | TGENERIC | UNSOUND | UNINIT | alloc:alloc(), then *ptr = value | Qwaz-Sec | No | | No |
| rust-arch | **CVE-2020-35885** | [issues/2](https://github.com/pigeonhands/rust-arch/issues/2) | TYPE+RAII | UNSOUND | UAF | self defined struct: direct construction->drop memory not owned | Qwaz-Sec | No | No | No |
| arc-swap | **CVE-2020-35711** | [issues/45](https://github.com/vorner/arc-swap/issues/45) | RAII+STRUCT | ERR | UAF | logical errors +PhantomData | Qwaz-Sec | No | | MAY |
| array-queue | **CVE-2020-35900** | [issues/2](https://github.com/raviqqe/array-queue/issues/2) | - | NO | UAF | FALSE CVEs? | ammaraskar-Sec | No | | - | 
| array-queue | Advisory-DB | [issues/2](https://github.com/raviqqe/array-queue/issues/2) | TYPE+RAII | ERR | UNINIT | use mem::uninitialized() | ammaraskar-Sec | No | 
| atom | **CVE-2020-35897** | [issues/13](https://github.com/slide-rs/atom/issues/13) | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec | No | | No | 
| chunky | Advisory-DB | [issues/2](https://github.com/aeplay/chunky/issues/2) | TGENERIC | UNSOUND | OOR | API ignores memory alignment requirement | Qwaz-Sec  | No | No | - |
| dync | **CVE-2020-35903** | [issues/4](https://github.com/elrnv/dync/issues/4) | TGENERIC | ERR | OOR | memory misalignment | ammaraskar-Sec | No | 
| concread | **CVE-2020-35928** | [issues/48](https://github.com/kanidm/concread/issues/48) | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | JOE1994-Sec | No | | No |
| futures-intrusive | CVE-2020-35915 | [issues/53](https://github.com/Matthias247/futures-intrusive/issues/53) | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec| No | No | No |
| futures-rs | **CVE-2020-35906** | [pull/2206](https://github.com/rust-lang/futures-rs/pull/2206) | TBOUND+LIFE | UNSOUND | UAF | lack lifetime bound | Darksonn | No | | No |
| futures-rs| **CVE-2020-35907** | [issues/2091](https://github.com/rust-lang/futures-rs/issues/2091) | LOE | ERR | UAF | TLS:ref lives longer than thread (UnsafeCell->Lazy) | goffrie | No | | No |
| futures-rs| **CVE-2020-35905** | [issues/2239](https://github.com/rust-lang/futures-rs/issues/2239) | TBOUND+CC | UNSOUND | CC->UAF | lack send/sync bound | Qwaz-Sec | No | No | No |
| futures-rs| **CVE-2020-35908** | [issues/2050](https://github.com/rust-lang/futures-rs/issues/2050) | FNSIG(DEP) | MID | UAF | sync for a structure with Cell<T> | okready | No | - | No |
| pulse-binding-rust | Advisory-DB | [Iterator](https://github.com/jnqnfe/pulse-binding-rust/commit/9e31c82d71749619387cb9d0c9698134d05b28c9) | TYPE | UNSOUND | UAF | lack lifetime bound: +PhantomData | jnqnfe | No | | May |
| pulse-binding-rust | Advisory-DB | [catch_unwind](https://github.com/jnqnfe/pulse-binding-rust/commit/7fd282aef7787577c385aed88cb25d004b85f494) | UNWIND+FFIUB | ERR | UB | handle FFI caused UB with catch_unwind() | okready | No | No | - |
| parking_lot | **CVE-2020-35910** | [MappedMutexGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | UNSOUND | DR->UAF | lack send bound | ammaraskar-Sec | No | No | No |
| parking_lot | **CVE-2020-35911** | [MappedRwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | UNSOUND | DR->UAF |  lack sync bound | ammaraskar-Sec | No | No | No |
| parking_lot | **CVE-2020-35912** | [MappedRwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND+CC | UNSOUND | DR->UAF |  lack send bound | ammaraskar-Sec | No | No | No |  
| parking_lot | **CVE-2020-35913** | [RwLockReadGuard](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND+CC | UNSOUND | DR->UAF | lack sync bound | ammaraskar-Sec | No | No | No | 
| parking_lot | **CVE-2020-35914** | [RwLockWriteGuard](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND+CC | UNSOUND | DR->UAF | lack sync bound | ammaraskar-Sec | No |  No | No |
| magnetic | **CVE-2020-35925** | [issues/9](https://github.com/johnshaw/magnetic/issues/9) | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | JOE1994-Sec | No | No | No |
| miow | **CVE-2020-35921** | [issues/38](https://github.com/yoshuawuyts/miow/issues/38) | FFIUB | ERR | UB | assumes the same layout of FFI | faern | No | No | No | 
| net2-rs | **CVE-2020-35920** | [issues/105](https://github.com/deprecrated/net2-rs/issues/105) | FFIUB | ERR | UB | assumes the same layout of FFI | Thomasdezeeuw | No | No | No |  
| rust-ordered-float | **CVE-2020-35923** | [pull/71](https://github.com/reem/rust-ordered-float/pull/71) | UNWIND | ERR | UB | panic may cause UB | branpk | No | No | No |  
| pyo3 | **CVE-2020-35917** | [pull/1297](https://github.com/PyO3/pyo3/pull/1297) | RAII | ERR | UAF | unthought of dropping: Py(ptr, _) = other | davidhewitt | No |  | Hard |
| thex | **CVE-2020-35927** | - | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | Qwaz-Sec | No |  | No |
| time | **CVE-2020-26235** | [issues/293](https://github.com/time-rs/time/issues/293) | FFIUB+CC | ERR | UB->UAF | call non-atomic libc functions (setenv) | quininer | <-> |  | No |
| try-mutex | **CVE-2020-35924** | [issues/2](https://github.com/mpdn/try-mutex/issues/2) | TBOUND+CC | UNSOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec | No |  | No |
| isahc | **CVE-2019-16140** | [issues/2](https://github.com/sagebind/isahc/issues/2) | RAII | ERR | UAF | unsafe constructor+no ManuallyDrop | nox | No | | Yes |
| sxd-document  | Trophy Case | [issues/47](https://github.com/shepmaster/sxd-document/issues/47) | RAII | ERR | UAF | unsafe constructor+no ManuallyDrop | CryZe-sec | No | | Yes |
| image | **CVE-2019-16138** | [issues/980](https://github.com/image-rs/image/issues/980) | UNWIND+RAII | ERR | UNINIT | unsafe allocation->drop uninit mem/set_len() | No (64) | No | | Hard |
| image | **CVE-2020-35916** | [issues/1357](https://github.com/image-rs/image/issues/1357) | EAPI | ERR | UB | MUT:convert mutable ptr from const ptr | dodomorandi | No | 
| libflate | **CVE-2019-15552** | [issues/35](https://github.com/sile/libflate/issues/35) | RAII+UNWIND  | ERR | UNINIT | enf. ManuallyDrop late->drop uninit | No (Shnatsel-sec) | No | | Yes |
| memoffset | **CVE-2019-15553** | [issues/9](https://github.com/Gilnaa/memoffset/issues/9) | RAII+UNWIND | ERR | UNINIT | enf. ManuallyDrop late->drop uninit mem  | Centril | No | | Yes |
| linked-hash-map | **CVE-2020-25573** | [pull/100](https://github.com/contain-rs/linked-hash-map/pull/100/) | EAPI+RAII | ERR | UNINIT | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)| No | | May |
| rio | **CVE-2020-35876** | [issues/11](https://github.com/spacejam/rio/issues/30) | FNSIG(SAFE) | UNSOUND | UAF | logical error: soundness hole | No (dtolnay-Rust) | No | | No |
| bitvec | **CVE-2020-35862** | [issues/55](https://github.com/myrrlyn/bitvec/issues/55) | LOE+SYS | ERR | UAF | MacOS reallocate the address after shrinking; Should use the new addr. | kulp-sec | No | No | | No |
| cbox-rs | **CVE-2020-35860** | [issues/2](https://github.com/TomBebbington/cbox-rs/issues/2) | FNSIG(SAFE) | UNSOUND | UAF | declare unsafe API as safe | No (eduardosm) | No | | No |
| rust-openssl | **CVE-2018-20997** | [issues/941](https://github.com/sfackler/rust-openssl/issues/941) | RAII | ERR | UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)| No | Yes |
| string-interner | **CVE-2019-16882** | [issues/9](https://github.com/Robbepop/string-interner/issues/9) | DERIVE+RAII | ERR | UAF | CLONE:bad derived clone | No (lo48576-deps) | No |  | No |
| crossbeam | **CVE-2018-20996** | [issues/82](https://github.com/crossbeam-rs/crossbeam/issues/82) | RAII | DF | shared mut aliases+auto drop/+ManuallyDrop | c0gent-deps | No | | Yes |
| crossbeam | **CVE-2020-35904** | [pull/533](https://github.com/crossbeam-rs/crossbeam/pull/533) | EAPI | ERR | UB->UAF | drop memory not owned Vec->Box | caelunshun | No | 
| generator-rs | **CVE-2019-16144** | [issues/11](https://github.com/Xudong-Huang/generator-rs/issues/11) | RAII | ERR | DF | shared mut aliases+auto drop | vOROn200 | No | | Yes |
| generator-rs | Advisory-DB | [issues/9](https://github.com/Xudong-Huang/generator-rs/issues/9) | FNSIG(SAFE) | UNSOUND | UB | func. sign.->deref invalid/null pointer | jonas-schievink | No | No | - |
| generator-rs | Advisory-DB | [issues/13](https://github.com/Xudong-Huang/generator-rs/issues/13) | FNSIG | UNSOUND | UB | bad func. exposure  | No (jonas-schievink) | No | 
| generator-rs | Advisory-DB  | [issues/14](https://github.com/Xudong-Huang/generator-rs/issues/14) | FNSIG | UNSOUND | UB | bad func. exposure | No (jonas-schievink)  | No | 
| linea.rs | **CVE-2019-16880** | [issues/1](https://github.com/strake/linea.rs/pull/2) | UNWIND+RAII | ERR | DF | enf. ManuallyDrop late | Phosphorus15 | No | | Yes |
| portaudio-rs | **CVE-2019-16881** | [issues/20](https://github.com/mvdnes/portaudio-rs/issues/20) | UNWIND+RAII | ERR | DF | enf. ManuallyDrop late | Phosphorus15 | No | | Yes |
| http | **CVE-2020-25574** | [issues/354](https://github.com/hyperium/http/issues/354) | UNWIND+RAII | DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) | No | | May |
| http | Advisory-DB | [issues/355](https://github.com/hyperium/http/issues/355) | TBOUND+LIFE | UNSOUND | DR->UAF | lack lifetime bound->multile mut refs  | No (Qwaz-sec)  | No | 
| internment | **CVE-2020-35874** | [issues/11](https://github.com/droundy/internment/issues/11) | LOE+CC | ERR | UB | TOCTOU:impl error: Ordering, atomic::fence() | ryzhyk-deps | No | No | - | 
| spin-rs  | **CVE-2019-16137** | [issues/65](https://github.com/mvdnes/spin-rs/issues/65) | EAPI+CC | ERR | UB->UAF | impl error: Ordering::Relaxed->Release | 64 | No | No | No |
| bigint | **CVE-2020-35880** | [deprecated](https://github.com/paritytech/bigint/commit/7e71521a61b009afc94c91135353102658550d42) | UNMAINTAIN | UNSOUND | UB | library unmaintained/deprecated | | No | 
| array | **CVE-2020-35886** | [issues/1:Array](https://github.com/sjep/array/issues/1) | TBOUND+CC | UNSOUND | DR->UAF | lack sync/send bound | Qwaz-Sec | No | | No |
| array | **CVE-2020-35887** | [issues/1:Index](https://github.com/sjep/array/issues/1) | BOUNDRY | MID | OOR | Index and IndexMut lack bound check | Qwaz-Sec | No | Yes | - |
| array | **CVE-2020-35888** | [new_from_template](https://github.com/sjep/array/issues/1) | RAII | ERR | UNINIT | alloc:alloc(), then *ptr = value | Qwaz-Sec | No | | No |
| crayon | **CVE-2020-35889** | [issues/87](https://github.com/shawnscode/crayon/issues/87) | TGENERIC | ERR | OOR | time-of-check to time-of-use (TOCTOU) bug | Qwaz | No | | No |
| ordnung | **CVE-2020-35890** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | LOE | ERR | OOR |  | Qwaz | No | | No |
| ordnung | **CVE-2020-35891** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | UNWIND+RAII | DF | panic->double free | Qwaz | No | | May |
| simple-slab | **CVE-2020-35892** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | BOUNDARY | MID | OOR | Slab::index() does not perform the boundary checking | Qwaz | No |
| simple-slab | **CVE-2020-35893** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | BOUNDARY | ERR | OOR | copies an element from an invalid address due to off-by-one error | Qwaz | No | 
| obstack | **CVE-2020-35894** | [issues/4](https://github.com/petertodd/rust-obstack/issues/4) | GENERIC+CASE | ERR | UB | generates unaligned references for types with a large alignment | Qwaz | No | No | - |
| stack-rs | **CVE-2020-35895** | [issues/4](https://github.com/arcnmx/stack-rs/issues/4) | BOUNDARY | MID | OOR | lack boundary check | ammaraskar | No | No |
| vm-memory | **CVE-2020-13759** | [issues/93](https://github.com/rust-vmm/vm-memory/issues/93) | EAPI+RW+CC | ERR | UB | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)| No | 
| Rocket | **CVE-2020-35882** | [issues/1312](https://github.com/SergioBenitez/Rocket/issues/1312) | TYPE | ERR | UB->UAF | Clone may incur mutable aliases | Qwaz | No |
| teaclave-sgx-sdk  | **CVE-2020-5499** | www.mitre.org | LOE+CC | MID | UB | may init twice by another thread/+Once::new() | Chen-sec | No | No | - |
| claxon  | **CVE-2018-20992**/Trophy | [issues/10](https://github.com/ruuda/claxon/issues/10) | LOE | ERR | UNINIT->DL | Vec::set_len()->read unit mem | Shnatsel-sec | No | No | 
| traitobject | **CVE-2020-35881** | [issues/7](https://github.com/reem/rust-traitobject/issues/7) | EAPI+ | ERR | UB->OOR | assumes that the first element is a fat pointer is the data pointer | eduardosm | No | Yes | No |
| rust-rgb | **CVE-2020-25016** | [issues/35](https://github.com/kornelski/rust-rgb/issues/35) | FNSIG(SAFE) | UNSOUND | UB | declare unsafe API as safe | HeroicKatora | No | No | - |
| renderdoc-rs | **CVE-2019-16142** | [issues/27](https://github.com/ebkalderon/renderdoc-rs/issues/27) | FNSIG(MUT) | UNSOUND | UB | mutable (internal mutation) | ebkalderon-owner | No | No | - | 
| rulinalg | **CVE-2020-35879** | [issues/201](https://github.com/AtheMathmo/rulinalg/issues/201) | FNSIG(LIFE) | UNSOUND | UB->UAF | func. sign.:lifetime | Qwaz-sec | No | | No |
| flatbuffers | **CVE-2020-35864** | [issues/5825](https://github.com/google/flatbuffers/issues/5825) | FNSIG(SAFE) | UNSOUND | UB | func. sign.: safety declaration | eduardosm | No | No | - |
| flatbuffers | Advisory-DB | [issues/5530](https://github.com/google/flatbuffers/issues/5530) | TYPE | ERR | UB | invalid bit pattern for bool | nagisa | No | No | - | 
| once_cell | **CVE-2019-16141** | [issues/46](https://github.com/matklad/once_cell/issues/46) | EAPI | ERR | UB | unreachable_unchecked()->panic!() | xfix-deps | No | No | - | 
| capnproto-rust | Trophy Case | [issues/40](https://dwrensha.github.io/capnproto-rust/2017/02/27/cargo-fuzz.html) | LOE | ERR | UB | error parameters of set_far() | dwrensha-sec | No | No | - | 
| lucet | **CVE-2020-35859** | [pull/401](https://github.com/bytecodealliance/lucet/pull/401) | LOE  | ERR | UB | logical error->memory man. issue | No (acfoltzer-deps) | No | 
| rand | **CVE-2020-25576** | [issues/779](https://github.com/rust-random/rand/issues/779) | EAPI | ERR | UB | reading unaligned mem/ptr::read_unaligned() | RalfJung-sec | No | No | - |
| os_str_bytes | **CVE-2020-35865** | [pull/1](https://github.com/dylni/os_str_bytes/pull/1) | EAPI+TYPE | ERR | UB | unsafe use of char::from_u32_unchecked() | eduardosm  | No | MAY | - |
| alacritty (exe) | GitHub | [pull/4397](https://github.com/alacritty/alacritty/pull/4397) | TYPE | ERR | UAF | shared mut aliases (ptr::copy->clone) | kchibisov-dev | No | Yes | No |
| alacritty (exe) | GitHub | [pull/2176](https://github.com/alacritty/alacritty/pull/2176)  | RAII | ERR | UAF | value of as_ptr() is dropped after map_or_else() (+as_ref()), Similar to CVE-2018-20997? | aspurdy | No | No | May |
| curl-rust | GitHub | [pull/2](https://github.com/alexcrichton/curl-rust/pull/2) | RAII | ERR | UAF | **using mem::transmute() | No(alexcrichton-rust) | No | Yes | May |
| curl-rust | GitHub | [issues/333](https://github.com/alexcrichton/curl-rust/issues/333) | FFIUB+CC | UNSOUND | UB | does not enforce FFI restrictions | DemiMarie/sagebind-deps | Yes | No | - |
| curl-rust | GitHub | [issues/340](https://github.com/alexcrichton/curl-rust/issues/340) | FNSIG(SAFE) | UNSOUND | UAF | exposing unsafe cleanup APIs as safe | sagebind-deps | No | 
| diem-libra (exe) | GitHub | [pull/1949](https://github.com/diem/diem/pull/1949) | FNSIG(LIFE) | ERR | UAF | ineffective lifetime restriction (too_owned()) | dtolnay-Rust | No | No | May |
| servo (exe) | GitHub | [issues/1186](https://github.com/servo/servo/issues/1186) | RAII+FFIUB | ERR | DF | [impl Drop with unsafe](https://github.com/servo/rust-layers/compare/3caa5900ea6f5185f1ca4571a4f0e1215dab6937...a6cdac57469b61266bb9abf7551d24f93fd2bb98) | kmcallister | No | Yes | - | 
| servo (exe) | GitHub | [issues/2412](https://github.com/servo/servo/issues/2412) | LOE | ERR | DF | unsafe cast: *()=>Vec<> | glennw | No | Yes | No |
| servo (exe) | GitHub | [issues/14014](https://github.com/servo/servo/issues/14014) | LOE+CC | UNSOUND | UAF | clone FlowRef lead to share aliases => Arc<Flow>  | pcwalton-deps | No | 
| servo (exe) | GitHub | [issues/14416](https://github.com/servo/servo/issues/14416) | LOE | ERR | UAF | FnBox<()>  | pcwalton-deps | No | No | No |
| servo (exe) | GitHub | [issues/20158](https://github.com/servo/servo/issues/20158) | FNSIG(SAFE) | UNSOUND | UB | declare unsafe constructor as safe  | nox-org | No | 
| servo (exe) | GitHub | [issues/21186](https://github.com/servo/servo/issues/21186) | EAPI+CC | ERR | UB | Relaxed->Acquire, same as rust-std-51780 | RalfJung | No | No | No | 
| servo (exe) | GitHub | [pull/26641](https://github.com/servo/servo/issues/26641) | EAPI | ERR | UB | mem::transmute->Box::into_raw(), unsafe should be removed? | dylni | No | May | - |
| Tokio | **CVE-2020-35922** | [issues/1386](https://github.com/tokio-rs/tokio/issues/1386) | FFIUB | EER | UB | assumes the same layout of FFI | Nemo157-Rust | No | No | No |
| Tokio | GitHub | [*pull/254](https://github.com/tokio-rs/tokio/issues/254) | RAII | ERR | UAF | drop | seanmonstar-dev | No | No | Hard |
| Tokio | GitHub | [pull/2030](https://github.com/tokio-rs/tokio/issues/2030) | TYPE | UNSOUND | OOR | similar to CVE-2019-12083, vulnerable to false trait impl | Marwes | No | No | - |
| Tokio | GitHub | [pull/2612](https://github.com/tokio-rs/tokio/issues/2612) | TBOUND | UNSOUND | OOR | lack trait bound: +unpin  | taiki-e-dev | No | No | - |
| Tokio | GitHub | [issues/3014](https://github.com/tokio-rs/tokio/issues/3014) | LOE | ERR | UAF | off-by-one logical error | NikosEfthias | No | No | No |

### Curlprits:
- EAPI: error in API usage.
- RAII: resource acquisition is initialization.
- UNWIND: error occurs in stack unwinding or exception handling.
- TYPE: type-safety issue.
- TYPECONV:type conversion issue.
- TBOUND: insufficient bound.
- TGENERIC: soundness hole for accpting some types as the generic.
- ARO: arithmatic overflow.
- BOUNDARY: boundary check issue or lack boundary check.
- CASE: lack special case handling.
- LOE: other logical errors.
- FFIUB: undefined behavior due to FFI.
- FNSIG: function signature issue.


### Memory-Safety Consequences: 
- OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; 
- UAF: use-after-free. DP: dangling pointer; 
- DF: double free.
- UNINIT: access/free uninitialized memory. DL: data leakage.
- UB: undefined behaviors.

### Other abbreviations:
- RC: race condition
- DR: data race.
- CC: concurrency issue.

* ERR：
- Developers should be resposible for the bug
- users cannot aware the bug unless they read the implementation details.
- Some bugs can be detected by analyzing the program without PoC. 

* MID: 
- users may be resposible for using the functions in an incorrect way.
- After fix: The program should be able to detect the errors at runtime

* UNSOUND: 
- Users should be resposible for using the functions in an incorrect way.
- After fix, the program should not compile.
- The bug cannot be detected by analyzing the program without PoC. 

### Other CVEs (Non-Memory-Safety Issue): 
* Crypto/Functionality Issue: CVE-2016-10932, CVE-2017-18587, CVE-2018-20999, CVE-2019-15545, CVE-2019-16760, CVE-2017-1000168, CVE-2020-15093, CVE-2020-26281, CVE-2020-35926, CVE-2020-35883;

* MITM/Code Injection: CVE-2016-10931, CVE-2016-10933, CVE-2020-26222, CVE-2020-26297, CVE-2020-28247, CVE-2020-35863, CVE-2020-35884; 

* StackOverflow/Crash: CVE-2017-18589, CVE-2018-20989, CVE-2018-20993, CVE-2018-20994, CVE-2019-15542, CVE-2019-15544, CVE-2019-15549, CVE-2020-35857, CVE-2020-35858, CVE-2020-35875, CVE-2020-35896, CVE-2020-35909.

* Cargo/Rustdoc: CVE-2018-1000622, CVE-2019-16760  
