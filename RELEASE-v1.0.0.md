# Giolit Trading Risk Verifier 1.0.0 — Trial Edition

**Stop backtesting bugs. Start proving safety.** The industry's first formal verification engine and CI/CD release gate for algorithmic trading strategies, execution algorithms, and pre-trade risk gateways. 

Unlike backtesting (which checks only the historical paths someone recorded) or simulators (which sample anticipated paths), **Giolit Trading Risk Verifier explores every possible interleaving of market events, fills, cancels, and message sequences allowed by the exchange protocol and market assumptions.**

For every trading rule and risk limit you specify, it returns either:
- **PROVEN:** A mathematical proof (inductive invariant) that the rule holds for **every possible run**, any market move, any fill timing, and **any number of orders ($N \to \infty$)**, accompanied by a signed PDF proof certificate.
- **VIOLATED:** A concrete, reproducible counterexample that breaks the rule — event by event, delivered as a **standard FIX 4.4 message log** your quant team can immediately replay and debug.

> **Zero Runtime Latency:** Runs entirely offline as a static verifier and CI release gate. Zero nanoseconds added to your live execution hot path.  
> **100% On-Premises & Air-Gapped:** Zero cloud dependencies, zero external solver calls. Your proprietary alpha models, strategies, and parameters never leave your local infrastructure.

---

## Download

| File | Size | SHA-256 |
|---|---|---|
| `giolit-trade-verifier-1.0.0-trial.tar.gz` | 5.0 MB | `6090ba8169f74f2699745c8e5e7b64d7cee7aea27408debfe675ea7f30296f3a` |

Verify after downloading:

```sh
shasum -a 256 -c CHECKSUMS.txt   # macOS
sha256sum -c CHECKSUMS.txt       # Linux
```

---

## 60 Seconds to Your First Proof (Ubuntu 24.04 x86_64)

```sh
# 1. Install system dependencies
sudo apt update
sudo apt install libllvm18 libclang-cpp18 libclang-common-18-dev libc6-dev libssl3

# 2. Extract and install (user prefix ~/.local/giolit-trade-verifier)
tar xzf giolit-trade-verifier-1.0.0-trial.tar.gz
cd giolit-trade-verifier-1.0.0-trial/code && ./install.sh

# 3. Verify
cd ~/.local/giolit-trade-verifier/share/giolit/examples

# Run flawed position limit (omits open working orders) -> VIOLATION FOUND + FIX trace
trade-verify 01_position_limit.gts

# Run fixed position limit -> ALL CONSTRAINTS PROVEN in 0.03 s
trade-verify 02_position_limit_fixed.gts

# Evaluate risk headroom and Giolit Resilience Score (1 to 5 stars)
trade-verify --headroom 02_position_limit_fixed.gts

# Generate tamper-evident PDF certificate & evidence bundle
trade-verify --report=cert --issued-to="Alpha Trading Desk" 02_position_limit_fixed.gts
```

New here? Start with [`docs/Brochure.pdf`](https://github.com/Giolit-Labs/Giolit-Trade-Verifier/blob/main/docs/Brochure.pdf) (the product in 6 pages), then read [`docs/Tutorial-1-Verifying-Trading-Strategies.pdf`](https://github.com/Giolit-Labs/Giolit-Trade-Verifier/blob/main/docs/Tutorial-1-Verifying-Trading-Strategies.pdf).

---

## Measured, Not Marketed — 0 Wrong Answers

The release benchmark suite evaluates **44 specifications comprising 180 individual trading rules**:

| Metric | Result |
|---|---|
| **Total Rules Evaluated** | **180** |
| **PROVEN Constraints** | **145** |
| **VIOLATED Constraints (with concrete counterexample trace)** | **34** |
| **FEASIBLE / INFEASIBLE Targets** | **1** |
| **Wrong Answers** | **0** |
| **Scale: Unbounded Orders ($N \to \infty$)** | **100,000+ simultaneous orders proved in < 0.5 s** |
| **Multi-Venue Concurrency** | **16 concurrent venues verified in 21 s** |
| **Exact IEEE 754 Floating-Point** | **Avellaneda-Stoikov market maker proved with exact binary64 `double`** |

Every single verification is reproducible: console output, `results.json`, and `reproduce.sh` scripts are included in `results/` inside the bundle.

---

## Real-World Bug Hunt: 4 Bugs Found in Unmodified Open-Source Code

Giolit evaluated unmodified production code from popular open-source trading platforms, discovering critical race conditions and state desynchronizations:

| Strategy | Platform | Language | Violated Constraint | Root Cause |
|---|---|---|---|---|
| **Simple PMM** | **Hummingbot** | Python | `one_quote_per_side` | Cancels and re-quotes in a single tick without awaiting cancel ACK; quotes double up (`open_qty = 2`). |
| **HFT Demo** | **WonderTrader** | C++ | `one_working` & `position_cap` | Split trade and order callbacks (`on_trade` / `on_order`) interleave out-of-order, causing position to hit 2. |
| **TWAP Unit** | **WonderTrader** | C++ | `never_past_target` | Slicing calculations and order timing allow buying/selling past the parent order's target position. |
| **VWAP Unit** | **WonderTrader** | C++ | `never_past_target` | Execution fills during cancel-replace cycles result in target volume overshoot. |

---

## What's Inside the Bundle

- **`code/`** — `bin/trade-verify` binary, shared libraries (`lib/`), public C++ headers (`include/giolit/`), strategy templates (`share/giolit/templates/`), tutorial examples (`share/giolit/examples/`), C++ SDK examples (`share/giolit/sdk-examples/`), installer and uninstaller.
- **`documents/`** — `Brochure.pdf`, `README.pdf`, `Reference-Manual.pdf`, `Tutorial-1` (Verifying Trading Strategies), `Tutorial-2` (SDK Guide), `Tutorial-3` (Algorithmic Trading Primer), `License-Terms.pdf`, and Markdown originals.
- **`benchmarks/`** — 44 formal specifications with known answers, C++/Python/Java bindings, and `MANIFEST.tsv`.
- **`results/`** — Complete evidence for all 180 benchmark constraints (`results.json`, console output, `reproduce.sh`, `SUMMARY.csv`).

---

## Trial License

The trial edition permits **1000 runs within 50 days** on one computer. `trade-verify --license` shows your status without consuming a run.

For commercial licenses (floating CI/CD cluster licenses, unwatermarked PDF certificates), custom exchange FIX protocol modeling, C++/Python code bindings, or FPGA/HFT pre-trade gateway verification:

📧 **business.giolitlabs@gmail.com** · 🌐 **www.giolit.com**

---
*Giolit Labs, Thrissur, Kerala, India — Sole owner of the Giolit Trading Risk Verifier. Use is subject to the License Terms.*
