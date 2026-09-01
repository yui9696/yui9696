### Hi, I'm Moe Tabei

Independent researcher, based in Japan, working fully remote.
I make claims that other people can check — every result ships with something you can re-run.

**Mathematics — group rings and the Kaplansky unit conjecture**

Fourteen sole-author papers on integral units of the Promislow group: the integral case of
Higman's question, open since 1940. Four on arXiv (math.GR) —
[2607.18346](https://arxiv.org/abs/2607.18346) ·
[2607.19687](https://arxiv.org/abs/2607.19687) ·
[2608.00103](https://arxiv.org/abs/2608.00103) ·
[2608.02982](https://arxiv.org/abs/2608.02982).

The 79-page monograph consolidating the programme is on Zenodo with a DOI:
[**10.5281/zenodo.22046587**](https://doi.org/10.5281/zenodo.22046587). Its ancillary bundle
is self-verifying — 126 scripts, 415 result files, 9 certificates. Extract it into an empty
directory, run one command, and the paper's headline numbers are recomputed from the shipped
files alone.

Joint work in progress with Prof. André Nies (University of Auckland).

**Post-quantum cryptography — SQIsign implementation security**

Ten manuscripts across the full arithmetic stack, around one falsifiable thesis: address- and
control-flow constant-time is achievable and verifiable at every layer, yet the operand channel
stays open at every layer.

- [**sqisign-verify-trace**](https://github.com/yui9696/sqisign-verify-trace) — golden
  intermediate-value vectors for SQIsign verification: the auxiliary, challenge, and recovered
  commitment curve j-invariants the verifier computes, for 300 KAT signatures. Signing is
  non-deterministic (floating-point lattice reduction), so its KATs can't be reproduced by another
  implementation — but *verification* is deterministic, so these intermediates are
  implementation-independent and can serve as interop vectors where the KATs cannot. Ships the
  73-line instrumentation as a patch (not a copy of the Apache-2.0 reference), a `diff` tool that
  localises which stage a divergent verifier goes wrong at, and an annotated worked example.
- [**sqisign-verify-fuzz**](https://github.com/yui9696/sqisign-verify-fuzz) — an AddressSanitizer
  verification-robustness fuzz harness, the fuzz tooling the reference asked for but never got
  (upstream issue #15). It independently reproduces the open issue #23: because the verifier
  ignores the signature length and fixed-size-decodes, **every** undersized length (all 148/224/292
  at the three levels) triggers a heap out-of-bounds read — mapped here per-length to the exact
  decode line — while 12,000 correct-length malformed inputs are robustly rejected. A reproduction
  of a known-open issue in a non-production reference, framed as such throughout; not a discovery.
- [**sqisign-verify-cost**](https://github.com/yui9696/sqisign-verify-cost) — a verification-cost /
  DoS-surface profiler. A single attacker-controlled signature byte (`two_resp_length`) sets an
  isogeny-chain loop bound in the reference verifier, so an attacker can make verification cost
  **1.50× / 1.82× / 2.17×** the honest median at levels 1/3/5 — the amplification rising with the
  security level, measured over 20 signatures per level and cross-checked to be governed by the
  public byte, not the key (so it is a resource-cost property, not a side-channel). Quantifies the
  CPU-exhaustion concern raised on the NIST pqc-forum. Not a break; a measurement of the
  non-production reference, with the mitigation stated.
- [**sqisign-conformance**](https://github.com/yui9696/sqisign-conformance) — a verification
  conformance suite: labelled positive **and negative** vectors for all three levels, where
  upstream ships 100 valid vectors per level and no negative ones. Verification is the only
  interoperability contract SQIsign has — the spec itself concedes an independent implementation
  may not reproduce its KATs, because signing uses floating-point lattice reduction. Includes a
  measured single-bit malleability map (106,240 verifications: every accepted mutation, at every
  level, lies in the four challenge-matrix entries and nowhere else) and a two-line adapter
  protocol so any verifier, in any language, can be tested. Ships no cryptography.
- [**CA-BPN**](https://github.com/yui9696/sqisign-cabpn-artifact) — a cache-aware batch-size
  policy for constant-time normalization in theta-coordinate isogeny pipelines (SQIsign /
  SQIsign2D / Qlapoti-based IdealToIsogeny), with proved correctness conditions for delayed
  normalisation and a constant-time Rust template. Reproducible sweep harness for Mac, Linux
  and AWS.
- [**timing-guard**](https://github.com/yui9696/timing-guard) — zero-dependency, `unsafe`-free
  Rust implementation of the dudect fixed-vs-random leakage test (Welch's t, percentile
  cropping) for checking your own code's timing behaviour. Statistical tests pinned against
  hand-computed values; the README documents a real false positive the harness itself had to
  engineer away.
- [**cornacchia-kit**](https://github.com/yui9696/cornacchia-kit) — pure-Python, stdlib-only
  solver for x² + d·y² = m and the 4m variant (the quadratic-form core behind isogeny-based
  schemes), with Miller–Rabin, Tonelli–Shanks and Brent–Pollard rho. Completeness cross-checked
  exhaustively against brute force where it is claimed, and the one honest gap is pinned by a
  test case.
- [**supersingular-isogeny-lab**](https://github.com/yui9696/supersingular-isogeny-lab) —
  pure-Python, stdlib-only study toolkit for supersingular curves and isogenies over F<sub>p²</sub>,
  the geometric object SQIsign lives on: F<sub>p²</sub> arithmetic, the Montgomery x-only ladder,
  Vélu's formulas, and the (ℓ+1)-regular isogeny graph checked against the mass formula. Ships a
  `PITFALLS.md` of the classic isogeny-implementation traps, each caught by a test.
- [**ct-toolbox**](https://github.com/yui9696/ct-toolbox) — `no_std`, zero-dependency Rust
  constant-time primitives (branchless select, table lookup, GF(2¹²⁷−1) arithmetic, Montgomery
  ladder), each shipped next to an empirical `timing-guard` test against the leaky anti-pattern
  it replaces. Honest result: 4 of 6 leaks flag, 2 compile to constant-time code — you measure,
  you don't assume.
- [**leakage-lens**](https://github.com/yui9696/leakage-lens) — offline side-channel leakage
  assessment in NumPy: TVLA first- and higher-order Welch t-tests, dudect-style timing analysis,
  Student-t thresholds without SciPy, and a simulator whose masked second-order leak is invisible
  to a first-order test and caught by a second-order one.

**Machine learning**

- [**attention-from-scratch**](https://github.com/yui9696/attention-from-scratch) — a GPT-style
  transformer where the forward *and* backward passes are hand-derived in pure NumPy: every
  gradient verified against central differences (worst relative error 1e-6), causality checked
  bitwise, and a seeded end-to-end demo that reaches 100% held-out exact match on sequence
  reversal in ~40 s on CPU.
- [**nanograd**](https://github.com/yui9696/nanograd) — a reverse-mode autodiff engine over NumPy
  that generalises the hand-derived gradients above into a reusable library, then rebuilds the
  same GPT on top of it. The headline test copies weights across both projects and checks the
  automatic and hand-derived gradients agree to ~1e-15 (machine precision).

**Developer tooling**

- [**retrace**](https://github.com/yui9696/retrace) — a zero-dependency time-travel tracer for
  Python: record a run, then query its history — *when did `x` become `None`?*, *what was the
  stack when this raised?* Uses `sys.monitoring` on 3.12+ and `settrace` on 3.11; building it
  (and its CI) turned up six real bugs, listed honestly in the README.

**Formal verification**

- [**mathlib4 #42931**](https://github.com/leanprover-community/mathlib4/pull/42931) —
  simultaneous diagonalisation of two real quadratic forms, submitted to Mathlib itself.
  No `sorry`; `#print axioms` reports the three standard axioms only.
- [**lean-portfolio**](https://github.com/yui9696/lean-portfolio) — Lean 4 formalisation work.

**Also**

Seven years of solo production backend (Python, TypeScript, Rust, PHP/Laravel, Postgres, AWS),
LLM application development, and smart-contract security research on Cantina.

---

**Available for remote, outcome-based contracts worldwide** — one PoC, one audit, one proof,
one feature. I would rather be paid for a deliverable than for hours.

📬 [tabei@ryun.jp](mailto:tabei@ryun.jp) · [yui9696.github.io](https://yui9696.github.io) · [ORCID 0009-0003-0859-5328](https://orcid.org/0009-0003-0859-5328) · [Google Scholar](https://scholar.google.com/citations?user=dx-sHOQAAAAJ)
