# Contributing to Giolit-Trade-Verifier

Thanks for your interest in the Giolit Trading Risk Verifier.

## What this repository is

This repository hosts Giolit Labs' **trial bundle**
(`giolit-trade-verifier-1.0.0-trial.tar.gz`, verified by `CHECKSUMS.txt`).
Inside the bundle: the `trade-verify` verifier binary and shared libraries
(`code/bin`, `code/lib`), the public C++ API headers (`code/include/giolit`),
tutorial examples, strategy templates, SDK examples, documents, benchmarks,
and their result evidence. The verification engines themselves are distributed
as binaries; only the documented entry points in `code/include` are public.

## What we accept

- Bug reports with a minimal GTSL specification or code reproducer, the exact
  `trade-verify` command, `trade-verify --version` / `trade-verify --license`
  output, and the result bundle (`--report=DIR`) if shareable.
- Documentation fixes, tutorial improvements, and strategy template suggestions.
- New benchmark specifications (trading strategies with known PROVEN or VIOLATED verdicts).
- SDK example improvements (C++17, buildable with `build.sh` inside the installed
  `share/giolit/sdk-examples`).

We do **not** accept reverse-engineering of the binaries, license-circumvention,
or removal of trial markings (see `LICENSE.md`, sections 2, 4.4, and 5).

## Reporting issues

1. Check `docs/Tutorial-1-Verifying-Trading-Strategies.pdf` (troubleshooting +
   “When a constraint stays UNDECIDED”, §10) and the reference table in `README.md`.
2. Verify integrity: `sha256sum -c CHECKSUMS.txt`, then after extracting,
   `sha256sum -c SHA256SUMS` inside the bundle folder.
3. Open an issue with the template: OS (`Ubuntu 24.04`), exact command,
   expected vs actual verdict, reproducer `.gts` file, and console output.

## Benchmarks

- Add the `.gts` file(s) and any binding/source code under the appropriate
  `benchmarks/` subdirectory with its expected verdict noted in `MANIFEST.tsv`.
