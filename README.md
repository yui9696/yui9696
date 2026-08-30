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

**Machine learning**

- [**attention-from-scratch**](https://github.com/yui9696/attention-from-scratch) — a GPT-style
  transformer where the forward *and* backward passes are hand-derived in pure NumPy: every
  gradient verified against central differences (worst relative error 1e-6), causality checked
  bitwise, and a seeded end-to-end demo that reaches 100% held-out exact match on sequence
  reversal in ~40 s on CPU.

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
