# rustbugs
  
| Project | Src | Link | Culprit | Consequense | Details | Finder-Role | Propagated | Unsafe->Safe | BadDrop? |
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | **CVE-2018-1000810** | [pull/54399](https://github.com/rust-lang/rust/pull/54399) | ARO | OOR | arithmatic overflow (str:repeat) | scottmcm-Rust | No | | - |
| rust-std | **CVE-2018-1000657** | [issues/44800](https://github.com/rust-lang/rust/issues/44800) | BOUNDARY | OOR | incorrect boundary check (VecDeque) | jesse99-deps | No | | - |
| rust-std | **CVE-2019-12083** | [issues/60784](https://github.com/rust-lang/rust/issues/60784) | TYPE+TYPECONV | OOR | TRAIT：TYPECONV:soundness hole impl Error::type_id() + downcasting | seanmonstar-deps | No | - |
| rust-std | GitHub | [issues/17207](https://github.com/rust-lang/rust/issues/17207) | FFIUB | UB | args are UB in jemalloc ( Vec::from_elem) | gmorenz | No | 
| rust-std | GitHub | [issues/25841](https://github.com/rust-lang/rust/issues/25841) | ARO+MODEL | UAF | arithmatic overflow->shared mut aliases (RefCell) | Veedrac | No | 
| rust-std | GitHub | [issues/27970](https://github.com/rust-lang/rust/issues/27970) | FFIUB | DR->UAF | setenv is unsafe | bluss-Rust | No | 
| rust-std | GitHub | [issues/33770](https://github.com/rust-lang/rust/issues/33770) | FFIUB | UAF | glibc recursive lock is UB->shared mut aliases | Amanieu | No | 
| rust-std | GitHub | [issues/35836](https://github.com/rust-lang/rust/issues/35836) | FFIUB | UAF | recursive RWlock on Windows is UB | retep998-Rust | No | 
| rust-std | GitHub | [issues/39465](https://github.com/rust-lang/rust/issues/39465) | FNSIG(MUT) | DP | Fn signature issue->shared mut aliases | christophebiocca | No | 
| rust-std | GitHub | [issues/39575](https://github.com/rust-lang/rust/issues/39575) | FNSIG(UNSAFE)+FFIUB | DR->UB | should be unsafe, UB according to POSIX (CommandExt::before_exec) | fweimer | No | 
| rust-std | GitHub | [issues/42135](https://github.com/rust-lang/rust/issues/42135) | CASE+TGENERIC | UB | miss handling cases (degenerate inclusive ranges  )->incorrect result (TrustedLen) | scottmcm-Rust | No | 
| rust-std | GitHub | [issues/42789](https://github.com/rust-lang/rust/issues/42789) | TGENERIC | OOR | interators over ZST slices are undefined->random addr （Iter+ZST） | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/43733](https://github.com/rust-lang/rust/issues/43733) | LOE | UAF | access static value without unsafe marker->CC(thread::local) | eddyb-Rust | No | 
| rust-std | GitHub | [issues/44637](https://github.com/rust-lang/rust/issues/44637) | CASE | OOR | does not handle -1 properly (Placer) | andy-hanson | No | 
| rust-std | GitHub | [issues/45197](https://github.com/rust-lang/rust/issues/45197) | TYPE | DR->UAF | AUTOTRAIT:bypassing sync/send check（fmt::Arguments）+PhantomData | cuviper-Rust | No | 
| rust-std | GitHub | [issues/46775](https://github.com/rust-lang/rust/issues/46775) | FFIUB | DR->UAF | multi-thread unsafe (unix::process::CommandExt::exec) | Diggsey | No | 
| rust-std | GitHub | [issues/48006](https://github.com/rust-lang/rust/issues/48006) | ARO | OOR | arithmatic overflow on 16-bit platforms | oberien | No | 
| rust-std | GitHub | [issues/48493](https://github.com/rust-lang/rust/issues/48493) | TGENERIC+RAII | UNINIT | Weak<T> frees uninitialized mem with <Void> | jleedev | No | 
| rust-std | GitHub | [issues/51780](https://github.com/rust-lang/rust/issues/51780) | EAPI(MEM) | DR->UAF | insufficient synchronization (Arc::is_unique) Relaxed->Acquire | jhjourdan | No | 
| rust-std | GitHub | [issues/54857](https://github.com/rust-lang/rust/issues/54857) | TGENERIC | OOR | UB in computing the offset addr for ZST or 0-len Vec（Vec） | jturner314 | No | 
| rust-std | GitHub | [issues/54908](https://github.com/rust-lang/rust/issues/54908) | TGENERIC | OOR | misaligned reference（RC, ARC） | RalfJung | No | 
| rust-std | GitHub | [issues/54957](https://github.com/rust-lang/rust/issues/54957) | LOE+TYPE | OOR | inconsistent type of Root node (BTreeSet) | RalfJung-Rust | No | 
| rust-std | GitHub | [issues/57534](https://github.com/rust-lang/rust/issues/57534) | FFIUB | DR->UAF | TLS:_tlv_atexit during tlv_finalize is UB (thread_local) | mtak- | May | 
| rust-std | GitHub | [issues/60977](https://github.com/rust-lang/rust/issues/60977) | UNWIND+RAII | DF | double free while panic (Vec::drain_filter) | rustonaut | No | | May |
| rust-std | GitHub | [issues/66544](https://github.com/rust-lang/rust/issues/66544) | TGENERIC | UAF | soundness holes of when impl DerefMut/Clone (Pin) | comex |
| rust-std | GitHub | [issues/67194](https://github.com/rust-lang/rust/issues/67194) | TGENERIC | OOR | violate the always applicable test (PartialEq for RangeInclusive) | comex | No | 
| rust-std | GitHub | [issues/72624](https://github.com/rust-lang/rust/issues/72624) | ARO | OOR | possible arithmatic overflow (DroplessArena::alloc_raw) | bluss-Rust | No |
| rust-std | GitHub | [issues/72760](https://github.com/rust-lang/rust/issues/72760) | LOE | UB | TYPE:invalid UTF-8 | RalfJung-Rust | No |
| rust-std | GitHub | [issues/76367](https://github.com/rust-lang/rust/issues/76367) | RAII+CC | UAF | logical error (SyncOnceCell/dropck)+PhantomData | m-ou-se-Rust |
| rust-std | GitHub | [issues/78477](https://github.com/rust-lang/rust/issues/78477) | LOE | UNKNOWN | violate pointer provenance rules | RalfJung-Rust | No |
| rust-std | GitHub | [issues/78498](https://github.com/rust-lang/rust/issues/78498) | UNWIND | UB | TYPE:invalid UTF-8 while catch_unwind (String) | SkiFire13 | No |
| rust-std | Advisory-DB | [issues/79808](https://github.com/rust-lang/rust/issues/79808) | BOUNDARY | UB->\*UAF | incorrect boundary check (VecDeque) | ayourtch | No |
| rust-std | GitHub | [issues/80338](https://github.com/rust-lang/rust/issues/80338) | BOUNDARY | UB->\*UAF | incorrect boundary check (VecDeque)-79808 | Aratz | No | | - |
| rustc (fake-static) | Advisory-DB | [issues/25860](https://github.com/rust-lang/rust/issues/25860) | COMPILER | UB->UAF | type system issue->lifetime inconsistency | aturon-Rust | No | - | - | 
| rust-base64 | **CVE-2017-1000430** | [issues/28](https://github.com/marshallpierce/rust-base64/issues/28) | ARO | OOR | arithmatic overflow + unsafe write | No (alicemaz) | No | 
| rust-smallvec | **CVE-2018-20991** | [issues/96](https://github.com/servo/rust-smallvec/issues/96) | UNWIND+RAII | DF | buffer shrinking too late | Vurich | No | | Hard |
| claxon  | **CVE-2018-20992**/Trophy | [issues/10](https://github.com/ruuda/claxon/issues/10) | LOE | UNINIT->DL | Vec::set_len()->read unit mem | Shnatsel-sec | No | No | 
| slice-deque | **CVE-2018-20995** | [issues/57](https://github.com/gnzlbg/slice_deque/issues/57) | BOUNDARY | OOR | error in boundary check + unsafe write | No (aldanor-deps) | No | 
| crossbeam | **CVE-2018-20996** | [issues/82](https://github.com/crossbeam-rs/crossbeam/issues/82) | RAII | DF | shared mut aliases+auto drop/+ManuallyDrop | c0gent-deps | No | | Yes |
| rust-openssl | **CVE-2018-20997** | [issues/941](https://github.com/sfackler/rust-openssl/issues/941) | RAII | UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)| No | Yes |
| arrayfire-rust  | **CVE-2018-20998** | [issues/176](https://github.com/arrayfire/arrayfire-rust/issues/176) | FFIUB | OOR | FFI-compatability/repr() | No (Aidan24) | No | 
| safe-transmute | **CVE-2018-21000** | [pull/36](https://github.com/nabijaczleweli/safe-transmute-rs/pull/36) | EAPI | OOR | wrong param order of from_raw_parts() | Enet4-deps | No | No | - |
| slice-deque | **CVE-2019-15543** | [pull/66](https://github.com/gnzlbg/slice_deque/pull/66) | CASE | OOR | lack special case handling ->memory misalignment | zimond | No | No | - |
| ncurses | **CVE-2019-15547** | [issues/172](https://github.com/jeaye/ncurses-rs/issues/172) | FNSIG(SAFE)+FFIUB | OOR | FFI-unchecked argument/printw() | thomcc | No | 
| ncurses | **CVE-2019-15548** | [issues/186](https://github.com/jeaye/ncurses-rs/issues/186) | FNSIG(SAFE)+FFIUB | OOR | FFI-unchecked argument/instr(), mvwinstr() | thomcc |
| simd-json | **CVE-2019-15550** | [pull/27](https://github.com/simd-lite/simd-json/pull/27) | CASE | OOR | lack special case handling->mem misalign/get_unchecked() | Licenser-deps | No | No | - |
| rust-smallvec | **CVE-2019-15551** | [issues/148](https://github.com/servo/rust-smallvec/issues/148) | LOE | UAF | miss an else branch->manuall deallocation | ehuss | No | No | May | 
| libflate | **CVE-2019-15552** | [issues/35](https://github.com/sile/libflate/issues/35) | RAII+UNWIND  | UNINIT | enf. ManuallyDrop late->drop uninit | No (Shnatsel-sec) | No | | Yes |
| memoffset | **CVE-2019-15553** | [issues/9](https://github.com/Gilnaa/memoffset/issues/9) | RAII+UNWIND | UNINIT | enf. ManuallyDrop late->drop uninit mem  | Centril | No | | Yes |
| rust-smallvec | **CVE-2019-15554** | [issues/149](https://github.com/servo/rust-smallvec/issues/149) | LOE | OOR | logical error + unsafe write | No (ehuss) | No | 
| spin-rs  | **CVE-2019-16137** | [issues/65](https://github.com/mvdnes/spin-rs/issues/65) | EAPI+CC | UB->UAF | impl error: Ordering::Relaxed->Release | 64 | No | No | No |
| image | **CVE-2019-16138** | [issues/980](https://github.com/image-rs/image/issues/980) | UNWIND+RAII | UNINIT | unsafe allocation->drop uninit mem/set_len() | No (64) | No | | Hard |
| compact_arena | **CVE-2019-16139** | [issues/22](https://github.com/llogiq/compact_arena/issues/22) | LOE | OOR | NLL issue->Index trait/get_unchecked() | No (CAD97) | No |
| isahc | **CVE-2019-16140** | [issues/2](https://github.com/sagebind/isahc/issues/2) | RAII | UAF | unsafe constructor+no ManuallyDrop | nox | No | | Yes |
| once_cell | **CVE-2019-16141** | [issues/46](https://github.com/matklad/once_cell/issues/46) | EAPI | UB | unreachable_unchecked()->panic!() | xfix-deps | No | No | - | 
| renderdoc-rs | **CVE-2019-16142** | [issues/27](https://github.com/ebkalderon/renderdoc-rs/issues/27) | FNSIG | UB | MUTABILITY:mutable (internal mutation) | ebkalderon-owner | No | No | - |  
| generator-rs | **CVE-2019-16144** | [issues/11](https://github.com/Xudong-Huang/generator-rs/issues/11) | RAII | DF | shared mut aliases+auto drop | vOROn200 | No | | Yes |
| linea.rs | **CVE-2019-16880** | [issues/1](https://github.com/strake/linea.rs/pull/2) | UNWIND+RAII | DF | enf. ManuallyDrop late | Phosphorus15 | No | | Yes |
| portaudio-rs | **CVE-2019-16881** | [issues/20](https://github.com/mvdnes/portaudio-rs/issues/20) | UNWIND+RAII | DF | enf. ManuallyDrop late | Phosphorus15 | No | | Yes |
| string-interner | **CVE-2019-16882** | [issues/9](https://github.com/Robbepop/string-interner/issues/9) | TYPE+RAII | UAF | CLONE:bad derived clone | No (lo48576-deps) | No |  | No |
| teaclave-sgx-sdk  | **CVE-2020-5499** | www.mitre.org | LOE | DR->UB | may init twice by another thread/+Once::new() | Chen-sec | No | No | - |
| vm-memory | **CVE-2020-13759** | [issues/93](https://github.com/rust-vmm/vm-memory/issues/93) | EAPI | DR->UB | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)| No | 
| rust-rgb | **CVE-2020-25016** | [issues/35](https://github.com/kornelski/rust-rgb/issues/35) | FNSIG | UB | SAFETY:declare unsafe API as safe | HeroicKatora | No | No | - |
| linked-hash-map | **CVE-2020-25573** | [pull/100](https://github.com/contain-rs/linked-hash-map/pull/100/) | EAPI+RAII | UNINIT | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)| No | | May |
| http | **CVE-2020-25574** | [issues/354](https://github.com/hyperium/http/issues/354) | UNWIND+RAII | DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) | No | | May |
| failure | **CVE-2020-25575** | [issues/336](https://github.com/rust-lang-nursery/failure/issues/336) | TYPE+TYPECONV | OOR | TYPECONV:downcast->misalign: same as CVE-2019-12083 | No (Qwaz-sec) | No | 
| rand | **CVE-2020-25576** | [issues/779](https://github.com/rust-random/rand/issues/779) | EAPI | UB | reading unaligned mem/ptr::read_unaligned() | RalfJung-sec | No | No | - |
| time | **CVE-2020-26235** | [issues/293](https://github.com/time-rs/time/issues/293) | FFIUB | DR->UAF | call non-atomic libc functions (setenv) | quininer | <-> |  | No |
| sized-chunks | **CVE-2020-25791** | [issues/11:unit](https://github.com/bodil/sized-chunks/issues/11) | TYPE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25792** | [pair](https://github.com/bodil/sized-chunks/issues/11) | TYPE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25793** | [From](https://github.com/bodil/sized-chunks/issues/11) | TYPE | OOR | lack input consistency check + unsafe write | No (Qwaz-sec) | No | 
| sized-chunks | **CVE-2020-25794** | [clone](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | UNINIT | panic->drop uninitialized memory | Qwaz-sec | No | | Yes |
| sized-chunks | **CVE-2020-25795** | [insert_from](https://github.com/bodil/sized-chunks/issues/11) | UNWIND+RAII | DF | panic->double drop | No (Qwaz-sec)  | No | | Hard |
| sized-chunks | **CVE-2020-25796** | [InlineArray](https://github.com/bodil/sized-chunks/issues/11) | TYPE | OOR | no input check->memory misalignment | No (Qwaz-sec) | No | 
| arc-swap | **CVE-2020-35711** | [issues/45](https://github.com/vorner/arc-swap/issues/45) | RAII+STRUCT | UAF | logical errors +PhantomData | Qwaz-Sec | No | | MAY |
| lucet | **CVE-2020-35859** | [pull/401](https://github.com/bytecodealliance/lucet/pull/401) | LOE  | UB | logical error->memory man. issue | No (acfoltzer-deps) | No | 
| cbox-rs | **CVE-2020-35860** | [issues/2](https://github.com/TomBebbington/cbox-rs/issues/2) | FNSIG | UAF | SAFETY:declare unsafe API as safe | No (eduardosm) | No | | No |
| bumpalo | **CVE-2020-35861** | [issues/69](https://github.com/fitzgen/bumpalo/issues/69) | LOE | OOR(Read) | copy wrong size | No (Riey-deps)| No | 
| bitvec | **CVE-2020-35862** | [issues/55](https://github.com/myrrlyn/bitvec/issues/55) | LOE | UAF | SYSTEM:MacOS reallocate the address after shrinking; Should use the new addr. | kulp-sec | No | No | | No |
| flatbuffers | **CVE-2020-35864** | [issues/5825](https://github.com/google/flatbuffers/issues/5825) | FNSIG | UB | SAFETY:func. sign.: safety declaration | eduardosm | No | No | - |
| os_str_bytes | **CVE-2020-35865** | [pull/1](https://github.com/dylni/os_str_bytes/pull/1) | EAPI+TYPE | UB | unsafe use of char::from_u32_unchecked() | eduardosm  | No | MAY | - |
| rusqlite | **CVE-2020-35866** | [VTab](https://github.com/rusqlite/rusqlite/commit/c9ef5bd63cad5c0c123344c072b490a1a9bcbe1f) | FNSIG(SAFE) | UB | should declare trait as unsafe | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35867** | [create_module](https://github.com/rusqlite/rusqlite/commit/3c6b57fe1b2cc87e7ebecde43dd836ffb1c4ea5c) | FNSIG(LIFETIME) | UAF | static ref should point to static ret value | thomcc-deps| No | 
| rusqlite | **CVE-2020-35868** | [UnlockNotif](https://github.com/rusqlite/rusqlite/commit/45fd77ee43c38eea4d6f4e2e56c1667a55ec654f) | RAII | DR->UB | NLL:mutex lock is released before send condvar | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35869** | [log](https://github.com/rusqlite/rusqlite/commit/2327d3b774927fdf48903c0bdc1ca7ec93c7c8d0) | EAPI+FFIUB | OOR | wrong parameters in api call | thomcc-deps| No | 
| rusqlite | **CVE-2020-35870** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | TBOUND | DR->UAF | lack sync/send bound | thomcc-deps | No | 
| rusqlite | **CVE-2020-35871** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/2ef3628dac35aeba0a97d5fb3a57746b4e1d62b3) | TBOUND | DR->UAF | lack sync/send bound | thomcc-deps| No | 
| rusqlite | **CVE-2020-35872** | [Auxdata API](https://github.com/rusqlite/rusqlite/commit/71b2f5187b0cbace3f8b6ff53432ff2ca0defcf0) | FFIUB | UB->OOR | + repr(C) | No (gwenn-deps) | No | 
| rusqlite | **CVE-2020-35873** | [sessions.rs](https://github.com/rusqlite/rusqlite/commit/ac30e169ae51b262bc8cf7026469851ce39b23c6) | RAII | UAF | similar to CVE-2018-20997 as_ptr() | thomcc-deps| No | 
| internment | **CVE-2020-35874** | [issues/11](https://github.com/droundy/internment/issues/11) | LOE+CC | UB | TOCTOU:impl error: Ordering, atomic::fence() | ryzhyk-deps | No | No | - | 
| rio | **CVE-2020-35876** | [issues/11](https://github.com/spacejam/rio/issues/30) | FNSIG | UAF | SAFETY | No (dtolnay-Rust) | No | | No |
| ozone | **CVE-2020-35877** | [index](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/buffer.rs#L38-L48) | BOUNDARY | OOR(Read) | lack boundary check | No (n.a.) | No | 
| ozone | **CVE-2020-35878** | [remove_entry](https://github.com/bqv/ozone/blob/e21f948b0178ab305f644118f18d87a838c618e0/src/map.rs#L94-L101) | RAII | UNINIT | implement drop with uninit mem | N.A. | No | | Yes | 
| rulinalg | **CVE-2020-35879** | [issues/201](https://github.com/AtheMathmo/rulinalg/issues/201) | FNSIG | UB->UAF | LIFETIME:func. sign.:lifetime | Qwaz-sec | No | | No |
| traitobject | **CVE-2020-35881** | [issues/7](https://github.com/reem/rust-traitobject/issues/7) | EAPI | UB->OOR | assumes that the first element is a fat pointer is the data pointer | eduardosm | No | Yes | No |
| Rocket | **CVE-2020-35882** | [issues/1312](https://github.com/SergioBenitez/Rocket/issues/1312) | TYPE | UAF | Clone may incur mutable aliases | Qwaz | No |
| rust-arch | **CVE-2020-35885** | [issues/2](https://github.com/pigeonhands/rust-arch/issues/2) | TYPE+RAII | UAF | self defined struct: direct construction->drop memory not owned | Qwaz-Sec | No | No | No |
| array | **CVE-2020-35886** | [issues/1:Array](https://github.com/sjep/array/issues/1) | TBOUND | DR->UAF | lack sync/send bound | Qwaz-Sec | No | | No |
| array | **CVE-2020-35887** | [issues/1:Index](https://github.com/sjep/array/issues/1) | BOUNDRY | OOR | Index and IndexMut lack bound check | Qwaz-Sec | No | Yes | - |
| array | **CVE-2020-35888** | [new_from_template](https://github.com/sjep/array/issues/1) | RAII | UNINIT | alloc:alloc(), then *ptr = value | Qwaz-Sec | No | | No |
| crayon | **CVE-2020-35889** | [issues/87](https://github.com/shawnscode/crayon/issues/87) | TGENERIC | OOR | time-of-check to time-of-use (TOCTOU) bug | Qwaz | No | | No |
| ordnung | **CVE-2020-35890** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | LOE | OOR |  | Qwaz | No | | No |
| ordnung | **CVE-2020-35891** | [issues/8](https://github.com/maciejhirsz/ordnung/issues/8) | UNWIND+RAII | DF | panic->double free | Qwaz | No | | May |
| simple-slab | **CVE-2020-35892** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | BOUNDARY | OOR | Slab::index() does not perform the boundary checking | Qwaz | No |
| simple-slab | **CVE-2020-35893** | [issues/2](https://github.com/nathansizemore/simple-slab/issues/2) | BOUNDARY | OOR | copies an element from an invalid address due to off-by-one error | Qwaz | No | 
| obstack | **CVE-2020-35894** | [issues/4](https://github.com/petertodd/rust-obstack/issues/4) | TGENERIC+CASE | UB | generates unaligned references for types with a large alignment | Qwaz | No | No | - |
| stack-rs | **CVE-2020-35895** | [issues/4](https://github.com/arcnmx/stack-rs/issues/4) | BOUNDARY | OOR | lack boundary check | ammaraskar | No | No |
| atom | **CVE-2020-35897** | [issues/13](https://github.com/slide-rs/atom/issues/13) | TBOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec | No | | No | 
| actix-net | **CVE-2020-35898** | [issues/160](https://github.com/actix/actix-net/issues/160) | EAPI | DR->UAF | replace Cell<T> with Rc<RefCell<T>>  | Shnatsel | No | | No |
| actix-net | **CVE-2020-35899** | [pull/158](https://github.com/actix/actix-net/pull/158) | EAPI | DR->UAF | replace Cell<T> with Rc<RefCell<T>> | Shnatsel | No | | No |
| actix-web | **CVE-2020-35901** | [issues/1321](https://github.com/actix/actix-web/issues/1321) | TBOUND | DR->UAF | BodyStream should be pined | sebzim4500 | No | | No |
| actix-net | **CVE-2020-35902** | [issues/91](https://github.com/actix/actix-net/issues/91) | TBOUND | DR->UAF | frame should be pined | sebzim4500 | No | No | No |
| dync | **CVE-2020-35903** | [issues/4](https://github.com/elrnv/dync/issues/4) | TGENERIC | OOR | memory misalignment | ammaraskar-Sec | No | 
| crossbeam | **CVE-2020-35904** | [pull/533](https://github.com/crossbeam-rs/crossbeam/pull/533) | EAPI | UAF | drop memory not owned Vec->Box | caelunshun | No |
| futures-rs| **CVE-2020-35905** | [issues/2239](https://github.com/rust-lang/futures-rs/issues/2239) | TBOUND | DR->UAF | lack send/sync bound | Qwaz-Sec | No | No | No |
| futures-rs | **CVE-2020-35906** | [pull/2206](https://github.com/rust-lang/futures-rs/pull/2206) | TBOUND(LIFE) | UAF | lack lifetime bound | Darksonn | No | | No |
| futures-rs| **CVE-2020-35907** | [issues/2091](https://github.com/rust-lang/futures-rs/issues/2091) | LOE | UAF | TLS:ref lives longer than thread (UnsafeCell->Lazy) | goffrie | No | | No |
| futures-rs| **CVE-2020-35908** | [issues/2050](https://github.com/rust-lang/futures-rs/issues/2050) | FNSIG(DEP) | UAF | sync for a structure with Cell<T> | okready | No | - | No |
| parking_lot | **CVE-2020-35910** | [MappedMutex](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND | DR->UAF | lack send bound | ammaraskar-Sec | No | No | No |
| parking_lot | **CVE-2020-35911** | [RwLockRead](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND | DR->UAF |  lack sync bound | ammaraskar-Sec | No | No | No |
| parking_lot | **CVE-2020-35912** | [RwLockWrite](https://github.com/Amanieu/parking_lot/issues/258) | TBOUND | DR->UAF |  lack send bound | ammaraskar-Sec | No | No | No |  
| parking_lot | **CVE-2020-35913** | [RwLockRead](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND | DR->UAF | lack sync bound | ammaraskar-Sec | No | No | No | 
| parking_lot | **CVE-2020-35914** | [RwLockWrite](https://github.com/Amanieu/parking_lot/issues/259) | TBOUND | DR->UAF | lack sync bound | ammaraskar-Sec | No |  No | No |
| futures-intrusive | **CVE-2020-35915** | [issues/53](https://github.com/Matthias247/futures-intrusive/issues/53) | TBOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec| No | No | No |
| image | **CVE-2020-35916** | [issues/1357](https://github.com/image-rs/image/issues/1357) | EAPI | UB | MUT:convert mutable ptr from const ptr | dodomorandi | No | 
| pyo3 | **CVE-2020-35917** | [pull/1297](https://github.com/PyO3/pyo3/pull/1297) | RAII | UAF | unthought of dropping: Py(ptr, _) = other | davidhewitt | No |  | Hard |
| net2-rs | **CVE-2020-35920** | [issues/105](https://github.com/deprecrated/net2-rs/issues/105) | FFIUB | UB | assumes the same layout of FFI | Thomasdezeeuw | No | No | No |  
| miow | **CVE-2020-35921** | [issues/38](https://github.com/yoshuawuyts/miow/issues/38) | FFIUB | UB | assumes the same layout of FFI | faern | No | No | No | 
| rust-ordered-float | **CVE-2020-35923** | [pull/71](https://github.com/reem/rust-ordered-float/pull/71) | UNWIND | UB | panic may cause UB | branpk | No | No | No |  
| try-mutex | **CVE-2020-35924** | [issues/2](https://github.com/mpdn/try-mutex/issues/2) | TBOUND | DR->UAF | lack send/sync bound | ammaraskar-Sec | No |  | No |
| magnetic | **CVE-2020-35925** | [issues/9](https://github.com/johnshaw/magnetic/issues/9) | TBOUND | DR->UAF | lack send/sync bound | JOE1994-Sec | No | No | No |
| thex | **CVE-2020-35927** | - | TBOUND | DR->UAF | lack send/sync bound | Qwaz-Sec | No |  | No | 
| concread | **CVE-2020-35928** | [issues/48](https://github.com/kanidm/concread/issues/48) | TBOUND+CC | DR->UAF | lack send/sync bound | JOE1994-Sec | No | | No |
| concread | **CVE-2020-35928** | [issues/48](https://github.com/kanidm/concread/issues/48) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| reffers-rs | **CVE-2020-36203** | [issues/7](https://github.com/diwic/reffers-rs/issues/7) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| im-rs | **CVE-2020-36204** | [issues/157](https://github.com/bodil/im-rs/issues/157) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| rust-xcb | **CVE-2020-36205** | [issues/93](https://github.com/rtbo/rust-xcb/issues/93) | TYPE | UAF | struct can be init with any ptr | ammaraskar | No | - | ? |
| rusb | **CVE-2020-36206** | [issues/44](https://github.com/a1ien/rusb/issues/44) | TBOUND | DR->UAF | lack sync/send bound | Qwaz | No | - | No |
| aovec | **CVE-2020-36207** | [RustSec](https://rustsec.org/advisories/RUSTSEC-2020-0099.html) | TBOUND | DR->UAF | lack sync/send bound |  | No | - | No |
| conquer-once | **CVE-2020-36208** | [issues/3](https://github.com/oliver-giersch/conquer-once/issues/3) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| late-static | **CVE-2020-36209** | [issues/1](https://github.com/Richard-W/late-static/issues/1) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| autorand-rs | **CVE-2020-36210** | [issues/5](https://github.com/mersinvald/autorand-rs/issues/5) | UNWIND+RAII | UNINIT | panic->drop uninit memory | JOE1994  | No | - | No |
| gfwx-rs | **CVE-2020-36211** | [issues/7](https://github.com/Devolutions/gfwx-rs/issues/7) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| abi_stable_crates | **CVE-2020-36212** | [issues/44](https://github.com/rodrimati1992/abi_stable_crates/issues/44) | UNWIND+RAII | DF | bug copied from Rust std-lib (60977) | Qwaz | No | - | No |
| abi_stable_crates | **CVE-2020-36213** | [issues/44](https://github.com/rodrimati1992/abi_stable_crates/issues/44) | UNWIND | UB | bug copied from Rust std-lib (78498) | Qwaz | No | - | No |
| multiqueue2 | **CVE-2020-36214** | [issues/10](https://github.com/abbychau/multiqueue2/issues/10) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| hashconsing | **CVE-2020-36215** | [issues/1](https://github.com/AdrienChampion/hashconsing/issues/1) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| eventio | **CVE-2020-36216** | [issues/33](https://github.com/petabi/eventio/issues/33) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| may | **CVE-2020-36217** | [issues/88](https://github.com/Xudong-Huang/may/issues/88) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| buttplug-rs | **CVE-2020-36218** | [issues/225](https://github.com/buttplugio/buttplug-rs/issues/225) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| rust-atomic-option | **CVE-2020-36219** | [issues/4](https://github.com/reem/rust-atomic-option/issues/4) | TBOUND | DR->UAF | lack sync/send bound | ammaraskar | No | - | No |
| va-ts | **CVE-2020-36220** | [issues/4](https://github.com/video-audio/va-ts/issues/4) | TBOUND | DR->UAF | lack sync/send bound | JOE1994 | No | - | No |
| generator-rs | Advisory-DB | [issues/9](https://github.com/Xudong-Huang/generator-rs/issues/9) | FNSIG | UB | SAFETY:func. sign.->deref invalid/null pointer | jonas-schievink | No | No | - |
| generator-rs | Advisory-DB | [issues/13](https://github.com/Xudong-Huang/generator-rs/issues/13) | FNSIG | UB | bad func. exposure  | No (jonas-schievink) | No | 
| generator-rs | Advisory-DB  | [issues/14](https://github.com/Xudong-Huang/generator-rs/issues/14) | FNSIG | UB | bad func. exposure | No (jonas-schievink)  | No | 
| flatbuffers | Advisory-DB | [issues/5530](https://github.com/google/flatbuffers/issues/5530) | TYPE | UB | invalid bit pattern for bool | nagisa | No | No | - |
| array-queue | Advisory-DB | [issues/2](https://github.com/raviqqe/array-queue/issues/2) | TYPE+RAII | UNINIT | use mem::uninitialized() | ammaraskar-Sec | No | 
| chunky | Advisory-DB | [issues/2](https://github.com/aeplay/chunky/issues/2) | TGENERIC | OOR | API ignores memory alignment requirement | Qwaz-Sec  | No | No | - |
| pulse-binding-rust | Advisory-DB | [Iterator](https://github.com/jnqnfe/pulse-binding-rust/commit/9e31c82d71749619387cb9d0c9698134d05b28c9) | RAII | UAF | lack lifetime bound: +PhantomData | jnqnfe | No | | May |
| pulse-binding-rust | Advisory-DB | [catch_unwind](https://github.com/jnqnfe/pulse-binding-rust/commit/7fd282aef7787577c385aed88cb25d004b85f494) | UNWIND+FFIUB | UB | handle FFI caused UB with catch_unwind() | okready | No | No | - |
| actix-web | Advisory-DB | [issues/289](https://github.com/actix/actix-web/issues/289) | LOE | UAF | multiple issues | seanmonstar | No | No | - |
| actix-web | Advisory-DB | [issues/301](https://github.com/actix/actix-web/issues/301) | TBOUND | UAF | InternalError with generics is unsound for Rc | seanmonstar-Mozilla | No | 
| alg_ds | Advisory-DB | [issues/1](https://gitlab.com/dvshapkin/alg-ds/-/issues/1) | TGENERIC | UNINIT | alloc:alloc(), then *ptr = value | Qwaz-Sec | No | | No |
| http | Advisory-DB | [issues/355](https://github.com/hyperium/http/issues/355) | TBOUND | DR->UAF | LIFETIME:lack lifetime bound->multile mut refs  | No (Qwaz-sec)  | No | 
| rust-smallvec | Advisory-DB | [issues/126](https://github.com/servo/rust-smallvec/issues/126) | EAPI | UNINIT | init vector with mem:uninitialized() | No (mbrubeck) | No | Yes |
| v_espace | Trophy Case | [issues/47](https://github.com/botika/v_escape/issues/47) | CASE+FFIUB | OOR | logical error->mem misalign | \_mm_load_si128() | tmiasko | No | No | - |
| capnproto-rust | Trophy Case | [issues/40](https://dwrensha.github.io/capnproto-rust/2017/02/27/cargo-fuzz.html) | LOE | UB | error parameters of set_far() | dwrensha-sec | No | No | - | 
| sxd-document  | Trophy Case | [issues/47](https://github.com/shepmaster/sxd-document/issues/47) | RAII | UAF | unsafe constructor+no ManuallyDrop | CryZe-sec | No | | Yes |
| lz4_flex | Trophy | [commit](https://github.com/PSeitz/lz4_flex/commit/ce92fbf28c94a0f1f6ebc711c86d854e2c9e5622) | LOE | OOR | logical error in space allocation | Pascal Seitz-sec | No | 
| alacritty (exe) | GitHub | [pull/4397](https://github.com/alacritty/alacritty/pull/4397) | TYPE | UAF | shared mut aliases (ptr::copy->clone) | kchibisov-dev | No | Yes | No |
| alacritty (exe) | GitHub | [pull/2176](https://github.com/alacritty/alacritty/pull/2176)  | RAII | UAF | value of as_ptr() is dropped after map_or_else() (+as_ref()), Similar to CVE-2018-20997? | aspurdy | No | No | May |
| curl-rust | GitHub | [pull/2](https://github.com/alexcrichton/curl-rust/pull/2) | RAII | UAF | **using mem::transmute() | No(alexcrichton-rust) | No | Yes | May |
| curl-rust | GitHub | [issues/333](https://github.com/alexcrichton/curl-rust/issues/333) | FFIUB | DR->UB | does not enforce FFI restrictions | DemiMarie/sagebind-deps | Yes | No | - |
| curl-rust | GitHub | [issues/340](https://github.com/alexcrichton/curl-rust/issues/340) | FNSIG | UAF | SAFETY:exposing unsafe cleanup APIs as safe | sagebind-deps | No | 
| diem-libra (exe) | GitHub | [pull/1949](https://github.com/diem/diem/pull/1949) | FNSIG | UAF | LIFETIME:ineffective lifetime restriction (too_owned()) | dtolnay-Rust | No | No | May |
| servo (exe) | GitHub | [issues/1186](https://github.com/servo/servo/issues/1186) | RAII+FFIUB | DF | [impl Drop with unsafe](https://github.com/servo/rust-layers/compare/3caa5900ea6f5185f1ca4571a4f0e1215dab6937...a6cdac57469b61266bb9abf7551d24f93fd2bb98) | kmcallister | No | Yes | - | 
| servo (exe) | GitHub | [issues/2412](https://github.com/servo/servo/issues/2412) | LOE | DF | unsafe cast: *()=>Vec<> | glennw | No | Yes | No |
| servo (exe) | GitHub | [issues/14014](https://github.com/servo/servo/issues/14014) | LOE | DR->UAF | clone FlowRef lead to share aliases => Arc<Flow>  | pcwalton-deps | No | 
| servo (exe) | GitHub | [issues/14416](https://github.com/servo/servo/issues/14416) | LOE | UAF | FnBox<()>  | pcwalton-deps | No | No | No |
| servo (exe) | GitHub | [issues/20158](https://github.com/servo/servo/issues/20158) | FNSIG | UB | SAFETY:declare unsafe constructor as safe  | nox-org | No | 
| servo (exe) | GitHub | [issues/21186](https://github.com/servo/servo/issues/21186) | EAPI | DR->UB | Relaxed->Acquire, same as rust-std-51780 | RalfJung | No | No | No | 
| servo (exe) | GitHub | [pull/26641](https://github.com/servo/servo/issues/26641) | EAPI | UB | mem::transmute->Box::into_raw(), unsafe should be removed? | dylni | No | May | - |
| Tokio | **CVE-2020-35922** | [issues/1386](https://github.com/tokio-rs/tokio/issues/1386) | FFIUB | UB | assumes the same layout of FFI | Nemo157-Rust | No | No | No |
| Tokio | GitHub | [*pull/254](https://github.com/tokio-rs/tokio/issues/254) | RAII | UAF | drop | seanmonstar-dev | No | No | Hard |
| Tokio | GitHub | [pull/2030](https://github.com/tokio-rs/tokio/issues/2030) | TYPE | OOR | similar to CVE-2019-12083, vulnerable to false trait impl | Marwes | No | No | - |
| Tokio | GitHub | [pull/2612](https://github.com/tokio-rs/tokio/issues/2612) | TBOUND | OOR | lack trait bound: +unpin  | taiki-e-dev | No | No | - |
| Tokio | GitHub | [issues/3014](https://github.com/tokio-rs/tokio/issues/3014) | LOE | UAF | off-by-one logical error | NikosEfthias | No | No | No |
| array-queue | **CVE-2020-35900** | [issues/2](https://github.com/raviqqe/array-queue/issues/2) | NO | UAF | FALSE CVEs? | ammaraskar-Sec | No | | - | 
| bigint | **CVE-2020-35880** | [deprecated](https://github.com/paritytech/bigint/commit/7e71521a61b009afc94c91135353102658550d42) | UNMAINTAIN | UB | library unmaintained/deprecated | | No | 
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

### Other CVEs (Non-Memory-Safety Issue): 
* Crypto/Functionality Issue: CVE-2016-10932, CVE-2017-18587, CVE-2018-20999, CVE-2019-15545, CVE-2019-16760, CVE-2017-1000168, CVE-2020-15093, CVE-2020-26281, CVE-2020-35926, CVE-2020-35883,CVE-2020-36202;

* MITM/Code Injection: CVE-2016-10931, CVE-2016-10933, CVE-2020-26222, CVE-2020-26297, CVE-2020-28247, CVE-2020-35863, CVE-2020-35884; 

* StackOverflow/Crash: CVE-2017-18589, CVE-2018-20989, CVE-2018-20993, CVE-2018-20994, CVE-2019-15542, CVE-2019-15544, CVE-2019-15549, CVE-2020-35857, CVE-2020-35858, CVE-2020-35875, CVE-2020-35896, CVE-2020-35909.

* Cargo/Rustdoc: CVE-2018-1000622, CVE-2019-16760  
