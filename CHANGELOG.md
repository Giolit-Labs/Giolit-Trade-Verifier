# Changelog

All notable changes to the Giolit Trading Risk Verifier trial distribution will be documented in this file.

## [1.0.0] - 2026-10-13

### Added
- **Initial Trial Release** of the Giolit Trading Risk Verifier (`trade-verify`).
- **GTSL (Giolit Trading Specification Language)**: High-level risk policy language with first-class dimensional unit typing (prices, ticks, lots, currencies, time intervals).
- **Dual Order Models & Parallel Verification**:
  - Slot Model: Tracks up to $K$ live orders with full FIX protocol state machines, synthesizing concrete 3–15 event counterexamples as standard FIX 4.4 logs.
  - Aggregate Model: Invariant prover sound for any number of orders (proven for 100,000+ orders in <0.5 s).
- **Direct Source Code Verification**: Zero-execution code binding for C++, Python, and Java trading strategies.
- **Floating-Point Verification**: Exact IEEE 754 binary64 `double` semantics with transcendental functions (`exp`, `log`, `sqrt`) for Avellaneda-Stoikov market making.
- **Risk Headroom & Resilience Score**: Computes the worst-case reachable bound on limits and grades resilience from 1 to 5 stars.
- **Evidence Bundles & Signed Proof Certificates**: Generates tamper-evident PDF certificates, JSON reports, FIX 4.4 traces, and market paths.
- **Conformance Replay Engine (`--conform`)**: Ingests drop-copy or execution logs to detect market drift and protocol divergences.
- **Strategy Pattern Library (`--templates`)**: Shipped templates for Market Maker, TWAP, VWAP, POV, Pairs Trading, Lead-Lag, Delta Hedge, Smart Order Router (SOR), and Pre-Trade Risk Gateway.
- **Pre-trade Risk Gate (`--controls-only`)**: Black-box verification of gateway controls across all possible adversarial client strategies.
- **C++ SDK & CI Integration**: Comprehensive public C++ API headers (`include/giolit/`) and 8 production SDK examples.
