# broken-mir

Repro: run `cargo clippy` in this directory.

Expected output: typechecks fine, boss!

Actual output:

```
cargo clippy
    Checking broken-mir v0.1.0 (/home/amos/bearcove/broken-mir)
warning: Error finalizing incremental compilation session directory `/home/amos/bearcove/broken-mir/target/debug/incremental/broken_mir-3jg493t7jkrit/s-gdwtcmorgw-1apjoc8-working`: No such file or directory (os error 2)

error: internal compiler error: no errors encountered even though `delay_span_bug` issued

error: internal compiler error: broken MIR in Item(WithOptConstParam { did: DefId(0:7 ~ broken_mir[e8cc]::run::{closure#0}), const_param_did: None }) (after pass PhaseChange-Runtime(Optimized)) at bb29[0]:
                                use of local _21, which has no storage here
  --> src/lib.rs:10:6
   |
10 |     };
   |      ^
   |
   = note: delayed at compiler/rustc_const_eval/src/transform/validate.rs:128:36

thread 'rustc' panicked at 'Box<dyn Any>', compiler/rustc_errors/src/lib.rs:1530:13
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

note: the compiler unexpectedly panicked. this is a bug.

note: we would appreciate a bug report: https://github.com/rust-lang/rust-clippy/issues/new

note: Clippy version: clippy 0.1.65 (f5193a9 2022-09-25)

query stack during panic:
end of query stack
warning: `broken-mir` (lib) generated 1 warning
error: could not compile `broken-mir`; 1 warning emitted
```