# rustbugs



| Project | CVE-ID (or Src) | Link | Culprit | Consequense | Details | Propagated | Finder |
|---------|---------|---------|---------|---------|---------|---------|---------|
| rust-std | 2018-1000810 | pull/54399 | IMP:ARO | OOR:BO | arithmatic overflow + unsafe write | No | scottmcm-Rust |
| 2018-1000657 | issues/44800 | IMP:LOE | BO | logical error + unsafe write (VecDeque) | No (jesse99-deps) |
  | 2019-12083 | issues/60784 | API:TRAIT | BO | soundness hole when impl Error::type_id() | No (seanmonstar-deps) |
  | Advisory-DB | issues/79808 | IMP:LOE | DP | logical error (VecDeque) | ayourtch |
  | \multirow{10}{*}{GitHub} | issues/17207 | FFI (Imp) | UB | jemalloc: unchecked argument | gmorenz |
  | | issues/25841 | IMP:ARO | UB$\to$DP | arithmatic overflow$\to$shared mut aliases (RefCell) | Veedrac |
  | | issues/27970 | IMP:FFI+CC+SYS | CC$\to$UAF | setenv is unsafe |  bluss-Rust   |
  | | issues/33770 | IMP:FFI+CC | UB | glibc recursive lock$\to$shared mut aliases | Amanieu |
  | | issues/35836 | IMP:FFI+CC | UB | recursive RWlock on Windows is UB | retep998-Rust |
  | | issues/39465 | API:MUT | UB$\to$DP | $\to$shared mut aliases | christophebiocca |
  | | issues/39575 | API:SAFE+FFI | CC$\to$UB | UB according to POSIX | fweimer |
  | | issues/42135 | IMP:LOE | UB | error related to unsafe trait | scottmcm-Rust |
  | | issues/42789 | IMP:LOE+ZST | UB | inconsistant addresses for interators over ZST | RalfJung-Rust |
  | | issues/43733 | IMP:SAFE+CC | UB | possible to bypass unsafe marker | eddyb-Rust |
  | | issues/44637 | API:TRAIT | BO | soundness hole in when impl Placer | andy-hanson |
  | | issues/45197 | IMP:LOE+CC | DR$\to$DP | allow concurrent acc. without sync/send | cuviper-Rust |
  | | issues/46775 | IMP:FFI+CC | UAF | | Diggsey |
  | | issues/48006 | IMP:SYS | BO | arithmatic overflow on 16-bit platforms  | oberien |
  | | issues/48493 | IMP:LOE | UNINIT | free uninitialized mem | jleedev |
  | | issues/51780 | IMP:LOE+CC | DR$\to$DP | insufficient synchronization  | jhjourdan |
  | | issues/54857 | IMP:LOE+ZST | UB | inconsistant addresses for ZST of Vec | jturner314  |
  | | issues/54908 | IMP:LOE | OOR | misaligned reference | RalfJung  |
  | | issues/54957 | IMP:LOE | OOR | unsafe type conversion | RalfJung |
  | | issues/57534 | IMP:SYS+CC+FFI | UAF | thread local variables | YES:mtak- |
  | | issues/60977 | IMP:RAII:LOE | DF | inconsistency while exception handling | ExpHP |
  | | issues/66544 | API:GENERIC+TRAIT | UB | soundness holes of Pin when impl DerefMut | comex |
  | | issues/67194 | API:GENERIC+TRAIT | | soundness holes when impl PartialEq | comex |
  | | issues/76367 | IMP:RAII+CC | UB | logical error (SyncOnceCell/dropck+PhantomData) |  m-ou-se-Rust |
  | | issues/78498 | IMP:LOE | UB | logical error for catch_unwind (String) | SkiFire13 |
*rustc (compiler) | Advisory-DB | issues/25860 | RU:LIFE (API) | Unsound | type system issue$\to$lifetime inconsistency | No (aturon-Rust)|
arrayfire-rust  | 2018-20998  | issues/176 | GEN:FFI (Imp) | OOR:BO | FFI-compatability/repr() | No (Aidan24) |
\multirow{2}{*}{ncurses } | 2019-15547 | issues/172 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/printw() | No (thomcc) |
  | 2019-15548 | issues/186 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/instr(), mvwinstr() | No (thomcc) |
\multirow{2}{*}{rusqlite } | Advisory-DB | pull/708 | RU:SAFE:FFI (API) | OOR:BO | FFI-unchecked argument/sqlite3_log() | No (thomcc-deps)|
  | Advisory-DB | issues/703 | RU:LIFE (API) | DP | func. sign.: lifetime declaration | No (gwenn-deps) |
rust-base64  | 2017-1000430 | issues/28 | GEN (Imp) | OOR:BO | arithmatic overflow + unsafe write | No (alicemaz) |
failure  | 2020-25575 | issues/336 | RU:SAFE (API) | OOR:BO | downcast$\to$mem misalign/private_get_type_id() | No (Qwaz-sec) |
bumpalo  | Advisory-DB | issues/69 | GEN (Imp) | OOR:BOR | wrong buffer size + unsafe write | No (Riey-deps)|
*compact_arena  | 2019-16139 | issues/22 | RU:DROP (Imp) | OOR:BOR | NLL issue$\to$Index trait/get_unchecked() | No (CAD97) |
lz4_flex | Trophy | - | IMP:LOE | BO | logical error in space allocation | Pascal Seitz-sec |
\multirow{2}{*}{ozone } | Advisory-DB | RUSTSEC-2020-0022:1 | API:SAFE | OOR:BOR | context issue$\to$Index trait | No (n.a.) |
 | Advisory-DB | RUSTSEC-2020-0022:2 | RAII (Imp) | DP:DUN | implement drop with uninit mem | No (n.a.)|
prost | Advisory/Trophy | issues/267 | GEN (Imp) | OOR:BO | logical error in recursion + unsafe write | No (dbrgn-sec) |
safe-transmute   | 2018-21000 | pull/36 | GEN (Imp) | OOR:BO | logical error + unsafe write | No (Enet4-deps)|
\multirow{2}{*}{slice-deque } | 2018-20995 | pull/58 | GEN (Imp) | OOR:BO | error in boundary check + unsafe write | No (aldanor-deps) |
| 2019-15543 | pull/66 | GEN (Imp) | OOR:BO | logical error$\to$memory misalignment | No (zimond) |
\multirow{4}{*}{rust-smallvec } | 2019-15554 | issues/149 | IMP:GEN (Imp) | OOR:BO | logical error + unsafe write | No (ehuss) |
 | Advisory-DB | issues/126 | RAII:UNWIND (Imp) | DP:DUN | init vector with mem:uninitialized() | No (mbrubeck) |
 | 2019-15551 | issues/148 | GEN (Imp) | DP:UAF | logical error + unsafe deallocation | No (ehuss) |
 | 2018-20991 | issues/96 | RAII:UNWIND (Imp) | DP:DF | buffer shrinking too late | No (Vurich) |
simd-json  | 2019-15550 | pull/27 | GEN (Imp) | OOR:BO | logical error$\to$mem misalign/get_unchecked() | No (Licenser-deps) |
v_espace  | Trophy Case | issues/47 | IMP:GEN (Imp) | OOR:BO | logical error$\to$mem misalign/_mm_load_si128() | No (tmiasko) |
\multirow{6}{*}{sized-chunks } | 2020-25791 | issues/11:unit | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) |
| 2020-25792 | issues/11:pair | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) |
| 2020-25793 | issues/11:From | GEN (API) | OOR:BO | lack input consistency check + unsafe write | No (Qwaz-sec) |
| 2020-25796 | issues/11:InlineArray | GEN (API) | OOR:BO | no input check$\to$memory misalignment | No (Qwaz-sec) |
| 2020-25794 | issues/11:clone | RAII:UNWIND (Imp) | DP:DUN | panic $\to$ drop uninitialized memory | No (Qwaz-sec)  |
| 2020-25795 | issues/11:insert_from | RAII:UNWIND (Imp) | DP:DUN | panic $\to$ rop uninitialized memory | No (Qwaz-sec)  | 
\multirow{3}{*}{actix-net} | Advisory-DB | issues/91 |  | UAF | | sebzim4500 |
| Advisory-DB | pull/158 | API:RC | UB$\to$UAF | replace Cell with RefCell | Shnatsel  |
| Advisory-DB | issues/160 | API:RC | UB$\to$UAF | replace Cell with RefCell | Shnatsel |
\multirow{3}{*}{actix-web} | Advisory-DB | issues/289 | API:MUTE | UB:DP | transmute immutable ref to mutable | seanmonstar |
| | issues/289 | API:LIFE | DP | transmutate lifetime to static | seanmonstar |
| | issues/289 | IMP:TRAIT+GENERIC | DP | Clone+Rc | seanmonstar |
| Advisory-DB | issues/301 | API:CC+TRAIT+GENERIC | UAF | unsafe impl of Send for generics races Rc | seanmonstar-Mozilla |
| Advisory-DB | issues/1321 | API:PAR | UAF |  | sebzim4500 |
alg_ds | Advisory-DB | issues/1 | IMP:RAII | UNINIT | init with alloc::alloc | Qwaz-Sec |
rust-arch | Advisory-DB | issues/2 | IMP:RAII | UAF | drop a memory not owned | Qwaz-Sec |
arc-swap | CVE-2020-35711 | issues/45 | API:TRAIT | UAF | +PhantomData | Qwaz-Sec |
arr | Advisory-DB | issues/1:Array | API:TRAIT+CC | RC$\to$UAF | lack send/sync bound  | Qwaz-Sec |
arr | Advisory-DB | issues/1:Index | IMP:TRAIT | OOR | lack boundary check | Qwaz-Sec |
arr | Advisory-DB | issues/1:from... | IMP: | UNINIT | *drop uninitialized mem | Qwaz-Sec |
array-queue | Advisory-DB | issues/2 | IMP:LOE | UAF | index may point to freed mem | ammaraskar-Sec |
array-queue | Advisory-DB | issues/2 | IMP:RAII | UNINIT | use mem::uninitialized() | ammaraskar-Sec |
atom | Advisory-DB | issues/13 | API:TRAIT | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec |
chunky | Advisory-DB |issues/2 | IMP:LOE | OOR | API ignores memory alignment requirement | Qwaz-Sec  |
dync | Advisory-DB | issues/4 | IMP:LOE | OOR | memory misalignment | ammaraskar-Sec |
concread | Advisory-DB | issues/48 | API:CC+TRAIT | RC$\to$UAF | lack send/sync bound | JOE1994-Sec |
futures-intrusive | Advisory-DB | issues/53 | API:TRAIT+CC | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec|
\multirow{4}{*}{futures-rs} | Advisory-DB | pull/2206 | API:GENERICS+LIFE | UAF | lack lifetime bound | Darksonn |
| Advisory-DB | issues/2091 | IMP:LIFETIME+CC | UAF | return static ref to Send | goffrie | 
| Advisory-DB | issues/2239 | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | Qwaz-Sec | 
| Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready |
\multirow{2}{*}{pulse-binding-rust} | Advisory-DB | API:LIFETIME+RAII | UAF | lack lifetime bound: +PhantomData | jnqnfe | 
| Advisory-DB | issues/2050 | API:TRAIT+CC | UAF | impl sync for a structure with Cell<T> | okready |
\multirow{5}{*}{parking_lot} | CVE-2020-35910 | issues/258:MappedMutexGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack send bound | ammaraskar-Sec | 
| CVE-2020-35911 | issues/258:MappedRwLockReadGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec | 
| CVE-2020-35912 | issues/258:MappedRwLockWriteGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack send bound | ammaraskar-Sec | 
| CVE-2020-35913 | issues/259:RwLockReadGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec | 
| CVE-2020-35914 | issues/259:RwLockWriteGuard | API:TRAIT+CC+GENERICS | RC$\to$UAF |  lack sync bound | ammaraskar-Sec |
magnetic | CVE-2020-35925 | issues/9 | API:TRAIT+CC+GENERICS | lack send/sync bound | JOE1994-Sec  |
miow | CVE-2020-35921 | issues/38 | FFI | UB | assumes the same layout of FFI | faern | 
net2-rs | CVE-2020-35920 | issues/105 | FFI | UB | assumes the same layout of FFI | Thomasdezeeuw | 
rust-ordered-float | CVE-2020-35923 | pull/71 | IMP:LOE | UB | panic may cause UB | branpk | 
pyo3 | CVE-2020-35917 | pull/1297 | IMP:LOE+RAII | UAF | unthought of dropping | davidhewitt | 
thex | CVE-2020-35927 | - | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | Qwaz-Sec | 
time | CVE-2020-26235 | issues/293 | CC+SYS | RC$\to$UAF | call non-atomic system functions |  quininer | 
try-mutex | CVE-2020-35924 | issues/2 | API:TRAIT+GENERICS+CC | RC$\to$UAF | lack send/sync bound | ammaraskar-Sec | 

isahc | 2019-16140 | issues/2 | RAII (Imp) | DP:UAF | unsafe constructor+no ManuallyDrop | No (nox) |
sxd-document  | Trophy Case | issues/47 | RAII (Imp) | DP:UAF | unsafe constructor+no ManuallyDrop | No (CryZe-sec) |
\multirow{2}{*}{image} | 2019-16138 | issues/980 | RAII:UNWIND* (Imp) | DP:DUN | unsafe allocation$\to$drop uninit mem/set_len() | No (64) |
| CVE-2020-35916 | issues/1357 | IMP:MUT | UB | convert mutable ptr from const ptr | dodomorandi |
libflate  | 2019-15552 | issues/35 | RAII:UNWIND (Imp) | DP:DUN  | enf. ManuallyDrop late$\to$drop uninit | No (Shnatsel-sec) |
*memoffset  | 2019-15553 | issues/9 | RAII:UNWIND (Imp) | DP:DUN | enf. ManuallyDrop late$\to$drop uninit mem  | No (Centril) |
linked-hash-map  | 2020-25573 | pull/100 | RAII (Imp) | DP:DUN | object with uninit mem of type T (HashMap) | No (SpaceManiac-deps)|
rio | Advisory-DB |  issues/30 | RU:SAFE (API) | DP:UAF | logical error: soundness hole | No (dtolnay-Rust) |
*bitvec  | Advisory-DB | issues/55 | GEN* (Imp) | DP:UAF | logical error: false assumption | No (kulp-sec) |
cbox-rs  | Advisory-DB | issues/2 | RU:SAFE (API) | DP:UAF+DF | declare unsafe API as safe | No (eduardosm) |
rust-openssl  | 2018-20997 | issues/941 | RAII (Imp) | DP:UAF | pointer obj lifetime inconsistency/as_ptr() | No (fred-gremlin)|
*string-interner  | 2019-16882 | issues/9 | IMP:RU:DERIVE (Imp) | DP:UAF | bad derived clone | No (lo48576-deps) | 
*crossbeam  | 2018-20996 | issues/82 | IMP:RAII* (Imp) | DP:DF | shared mut aliases+auto drop/+ManuallyDrop | No (c0gent-deps) |
crossbeam | Advisory-DB | pull/533 | IMP:LOE | UB$\to$UAF | drop memory not owned | caelunshun  |
\multirow{4}{*}{generator-rs } | 2019-16144 | issues/11 | IMP:RAII* (Imp) | DP:DF | shared mut aliases+auto drop | No (vOROn200) |
  | Advisory-DB | issues/9 | RU:SAFE (API) | Unsound | func. sign.$\to$deref invalid/null pointer | No (jonas-schievink)|
  | Advisory-DB | issues/13 | GEN (API) | Unsound | bad func. exposure  | No (jonas-schievink) |
  | Advisory-DB  | issues/14 | GEN (API) | Unsound | bad func. exposure | No (jonas-schievink)  |
linea | 2019-16880 | issues/1 | RAII:UNWIND (Imp) | DP:DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15)|
portaudio-rs  | 2019-16881 | issues/20 | RU:DROP (Imp) | DP:DF | enf. ManuallyDrop late$\to$drop twice | No (Phosphorus15) |
\multirow{2}{*}{http } | 2020-25574 | issues/354 | RAII (Imp) | DP:DF | buf. shrinking too late (rely on drop) | No (Qwaz-sec) |
    | Advisory-DB | issues/355* | RU:MUT (API) | Unsound | func. sign.$\to$multiple mutable refs/Send$\to$Sync  | No (Qwaz-sec)  |
internment  | Advisory-DB | issues/11 | IMP:GEN (Imp) | CC:DR | impl error: Ordering, atomic::fence() | No (ryzhyk-deps)|
spin-rs  | 2019-16137 | issues/65 | IMP:GEN (Imp) | CC:DR | impl error: Ordering::Relaxed$\to$Release | No (64) |
vm-memory  | 2020-13759 | issues/93 | IMP:GEN (Imp) | CC:RC | volatile mem acc/ptr::write()$\to$write_volatile() | No (andreeaflorescu-deps)|
teaclave-sgx-sdk  | 2020-5499 | www.mitre.org | GEN (API) | CC:DR | may init twice by another thread/+Once::new() | No (Chen-sec) |
*claxon  | 2018-20992/Trophy | issues/10 | IMP:GEN (Imp) | DL | unsafe buf alloc$\to$read unit mem/Vec::set_len() | No (Shnatsel-sec)|
rust-rgb  | 2020-25016 | issues/35 | RU:Safe (API) | Unsound | declare unsafe API as safe | No (HeroicKatora) |
renderdoc-rs  | 2019-16142 | issues/27 | RU:MUT (API) | Unsound | func. sign.$\to$unsync. internal mutation | No (ebkalderon-owner) |
*rulinalg  | Advisory-DB | issues/201 | RU:LIFE (API)| Unsound | func. sign.:lifetime | No (Qwaz-sec)  |
\multirow{2}{*}{flatbuffers } | Advisory-DB | issues/5825 | RU:SAFE (API) | Unsound | func. sign.: safety declaration | No (eduardosm)|
 | Advisory-DB | issues/5530 | IMP* (Imp) | Unsound | logical error$\to$invalid bit pattern for bool | No (nagisa)|
once_cell  | 2019-16141 | issues/46 | GEN* (Imp) | Unsound | unreachable_unchecked()$\to$panic!() | No (xfix-deps) |
*capnproto-rust  | Trophy Case | cargo-fuzz/issues/40 | GEN* (Imp) | Unsound | logical error | No (dwrensha-sec)|
lucet  | Advisory-DB | pull/401 | GEN (Imp)  | Unsound | logical error$\to$memory man. issue | No (acfoltzer-deps) |
*rand  | 2020-25576 | issues/779 | GEN* (Imp) | Unsound | reading unaligned mem/ptr::read_unaligned() | No (RalfJung-sec)|

 \multirow{3}{*}{servo (exe)} |  \multirow{3}{*}{\makecell{GitHub\\317 unsafe}} | issues/1186 | RAII: (Imp) | DP:DF | impl Drop with unsafe | kmcallister  |
 | | issues/2412 | RAII: (Imp) | DP:DF  | *unsafe cast?  |  |
 | | issues/14014 | RAII: (Imp) | CC$\to$UAF  |   | pcwalton-deps |
 | | issues/14416 | RAII: (Imp) | DP:UAF  | FnBox  | pcwalton-deps |
 | | issues/20158 | SAFETY: (API) | UB  | declare unsafe constructor as safe  | nox-org |
 | | issues/21186 | Gen: (Imp) | CC:DR | Relaxed$\to$Acquire |  |
 | | pull/26641 | Gen: (Imp) | UB | mem::transmute$\to$Box::into_raw() | dylni |
 
 \multirow{3}{*}{wasmer (exe)} |  \multirow{3}{*}{\makecell{GitHub\\50 unsafe}} | pull/1092 | RU:Safety (Imp) | OOR | lack input consistency check + unsafe constructor | MarkMcCaskey-dev  |
 | | pull/1206 | RU:Safety (API) | Unsound | possible to create shared mutable aliases | MarkMcCaskey-dev |
 | | pull/1209 | RU:Safety (API) | CC:DR | multiple Cells for the same memory | MarkMcCaskey-dev  |
 | | pull/1837 | RU:Safety (API) | Unsound | declare unsafe API as safe | MarkMcCaskey-dev |
 | | issues/1568 | RAII: | DP:UAF | shared mutable alises (slice+to_vec()) | Hywan-dev  |

\multirow{2}{*}{alacritty (exe)} | \multirow{2}{*}{\makecell{GitHub (21 unsafe)}} | pull/4397 | MemModel (Imp) | DP::UAF | shared mut aliases (ptr::copy$\to$clone) | kchibisov-dev  |
 | | pull/2176  | GEN (Imp) | UAF | logical error (+as_ref()) | aspurdy | 
diem-libra (exe) | GitHub (207 unsafe) | pull/1949 | RU:Lifetime (API) | DP:UAF | ineffective lifetime restriction | dtolnay-Rust  |

\multirow{3}{*}{wint}| \multirow{3}{*}{GitHub (72 unsafe)} | issues/599 | (Imp) | CC:RC | non-atomic cell for multi-thread apps | andrewhickman \\\cline{3-7} 
 | | pull/611 | CC (Imp) | CC:RC | non-atomic cell for multi-thread apps | francesca64-dev |
 | |  issues/1745 | GEN (Imp) | DP:UAF | logical error | qthree  |

\multirow{3}{*}{Tokio } | CVE-2020-35922 | issues/1386 | FFI | UB | assumes the same layout of FFI | Nemo157-Rust | 
 | \multirow{3}{*}{GitHub (84 unsafe)} | *pull/254 |  | DP:UAF | | seanmonstar-dev   | 
 | | issues/354 | Gen (Imp) | UB | uninit memory for Vec<u8> with set_len() | udoprog | 
 | | issues/593 |  | CC | | NPN |
 | | pull/2030/ | (API) | OOR | trait safety | Marwes | 
  | | pull/2612/ | Trait (API) | OOR | error in specify Trait impl Type  | taiki-e-dev | 
 | | issues/3014 | Gen (Imp) | DP:UAF | off-by-one logical error | NikosEfthias |

\multirow{3}{*}{curl-rust  }| \multirow{3}{*}{GitHub (10 unsafe)} | pull/2 | RU:SAFE (Imp) | DP:UAF | **using mem::transmute() | No(alexcrichton-rust) \\\cline{3-7} 
| | issues/333 | RU: (API) | CC:DR | does not enforce FFI restrictions | Yes(DemiMarie/sagebind-deps) \\\cline{3-7} 
| | issues/340 | RU:SAFE (API) | DP:UAF | exposing unsafe cleanup APIs as safe | No(sagebind-deps) \\
OOR:out-of-range access; BO: buffer overflow; BOR: buffer over-read; CC: concurrency issue; DF: double free; DL: data leakage; DP: dangling pointer; DR: data race; RC: race condition; UAF: use-after-free.
