# Giolit Trading Risk Verifier — Software License Agreement

**Version 1.0 — Trial Version**

**Giolit Labs**, Ramavarmapuram P.O., Thrissur, Kerala, India ("**Giolit Labs**", "we")
www.giolit.com · business.giolitlabs@gmail.com

By installing, copying or using the Giolit Trading Risk Verifier you
agree to this agreement on your own behalf and on behalf of the organisation you
represent ("**you**", the "**Licensee**"). If you do not agree, do not install or
use the Software.

---

## 1. Definitions

- **Software**: the Giolit Trading Risk Verifier version 1, also
  called the Giolit Trading Verifier, including the program (`trade-verify`), the
  libraries (`libgiolit_*`), the header files, the documentation (README,
  Tutorial, this agreement), the example specifications and logs, and any
  updates Giolit Labs provides.
- **Trial Version**: the Software as distributed for evaluation, with the
  usage limits in section 4.
- **Licensed Version**: the Software used under a License File purchased from
  Giolit Labs (section 7).
- **License File**: the file issued by Giolit Labs, or by a distributor Giolit
  Labs has authorised, that states the terms of a purchased license (license
  number, licensee, runs and period). Each License File is bound to the buyer it
  was issued to.
- **Authorised Distributor**: a party Giolit Labs has authorised to sell
  licenses and issue License Files.
- **Specification**: the GTSL files, with the files they import (FIXatdl,
  FIX Orchestra), and the FIX logs that you give the Software to verify or
  replay.
- **Run**: one invocation of the Software that verifies one Specification or
  replays one log.
- **Output**: what the Software produces: console results, violating and
  witness runs (text, JSON, FIX messages, market paths), certificates and
  reports, and JSON result files.

## 2. Ownership and intellectual property

2.1 **Giolit Labs is the sole and exclusive owner** of the Software and of all
proprietary code, algorithms, methods and know-how behind it, including without
limitation: the trading specification language (GTSL) and its translation into
verification models (event step models, the order-slot and aggregate order
models, protocol and market models, constraint monitors); the methods for
computing invariants and inductive lemmas; the goal-directed search, the
counterexample shortening and the conformance replay; the risk headroom and
optimization methods; the scheduling of the verification engines; and all
related source code, object code, specifications and documentation,
together with all intellectual property rights in them.

2.2 The Software is **licensed, not sold**. This agreement grants a limited
right of use only. No ownership, title or other right in the Software passes to
you, and all rights not expressly granted are reserved by Giolit Labs.

2.3 "Giolit", the Giolit logo, "Giolit Trading Risk Verifier" and
"Giolit Trading Verifier" are trade marks of Giolit Labs. You may not use them
except to identify the Software and its Output unchanged.

2.4 Scientific publications describing general verification techniques (model
checking, abstract interpretation, counterexample-guided refinement,
k-liveness and the like) remain free to all. This agreement protects Giolit
Labs' specific implementation and methods, not the underlying public science.

2.5 **Your Specifications remain yours.** Giolit Labs acquires no right in the Specifications
you verify or in the Output about them.

## 3. Grant of license (Trial Version)

Subject to this agreement, Giolit Labs grants you a **non-exclusive,
non-transferable, non-sublicensable, revocable** license to install and use the
Trial Version for the **internal evaluation** of the Software, within the limits
of section 4.

You may share Output of the Trial Version with others to show what the Software
does. You must not present trial Output as produced under a purchased license.

## 4. Trial limits and expiry

4.1 **The Trial Version stops working at the earliest of these:**

| Limit | Value |
|---|---|
| Runs | **1000** Runs per installation |
| Trial period | **50 days** from the first Run on the installation |
| Build validity | **100 days** from the date the distributed build was made. After that, a newer build must be downloaded, or a purchased license must be active. |

4.2 **When does your license expire?** Run:

```sh
trade-verify --license
```

It shows the runs used and left, the end of the trial or license period, and
the date until which this build can be used without a purchased license. It
does not use up a Run.

4.3 **At expiry** the Software refuses new Runs with exit code 4 and a message.
Output produced before expiry remains yours to keep and use under section 3
(trial) or section 7 (licensed).

4.4 The license state is stored on your computer (by default in
`~/.giolit/trade-verify`) and is protected against modification. Attempting to
reset, alter or transfer it, or otherwise to extend the trial by technical
means, breaches this agreement (section 5).

## 5. Restrictions

You must not, and must not allow others to:

a) copy the Software except for installation and reasonable back-up;
b) reverse engineer, decompile, disassemble or otherwise attempt to derive the
   source code, algorithms or methods of the Software, except to the extent that
   applicable law expressly permits this despite this restriction;
c) circumvent, disable or interfere with the license checks, access tokens or
   usage limits, or tamper with the license state;
d) modify, translate or create derivative works of the Software;
e) rent, lease, lend, sell, sublicense, distribute or publish the Software, or
   make it available to third parties, including as a hosted service;
f) use the Software or knowledge of its internal workings to develop a
   competing product or service;
g) remove or alter any proprietary notice or trade mark in the Software or its
   Output;
h) publish benchmark or comparison results of the Trial Version without Giolit
   Labs' written consent.

## 6. Nature of the results

6.1 The Software performs **formal verification relative to a model** built
from the Specification and its stated assumptions: the assumptions and declared
ranges, the order protocol and its options, the market model, the strategy
parameters and rules (or, in controls-only mode, any strategy), the risk
controls, and the time unit (see the Tutorial, section "What a result means").
A result is valid only under those assumptions. Whether your implementation,
your venues and your market behave as the Specification states is outside the
verification; conformance replay of your logs checks it for the runs logged.

6.2 Only PROVEN, PROVEN* (for at most the stated number of live orders),
VIOLATED, FEASIBLE and INFEASIBLE are verification results. UNDECIDED is not a
statement about the Specification's correctness. The Output is not investment,
trading, legal or regulatory advice.

6.3 The Software is a tool to support your own engineering judgement. It does
not replace your simulation, review, safety assessment or sign-off processes.
You are responsible for how you use its Output, in particular for trading
systems you operate and for any regulatory submission that relies on it.

## 7. Purchasing a license

7.1 **How to purchase.** Write to **business.giolitlabs@gmail.com**, use the
contact options on **www.giolit.com**, or contact an Authorised Distributor,
stating:

- your name and organisation;
- the intended use (for example a trading desk, a broker's risk team, an
  algorithm vendor, a verification service, research);
- the number of users or installations;
- the license term you need (for example 12 months) and the expected volume of
  Runs;
- the output of `trade-verify --version` and `trade-verify --license` from the
  installation(s).

Giolit Labs will send a quotation. Licenses are available by term and by
volume, and verification services (properties written and proved by Giolit
Labs' engineers, and review of results) can be offered alongside.

7.2 **Activation.** After purchase you receive a License File, a license number
and a password, from Giolit Labs or an Authorised Distributor. Apply the License
File to each licensed installation:

```sh
trade-verify --activate customer.lic   # asks for the buyer's name, address and password
trade-verify --license                 # confirms the new terms
```

A License File activates only with the name, address and password of the buyer
it was issued to. Keep the password confidential; you are responsible for its
use. A purchased license replaces the trial limits with the Runs and period
stated in the License File, and lifts the build-validity limit while it is
active. It applies to the installation it was activated on.

7.3 **Licensed Output.** You may share Output produced under a purchased license
with your clients, auditors and certification bodies. You must not present
Output as produced under a license other than your own.

7.4 **Renewal.** A purchased license ends at the end of its period or when its
Runs are used, whichever comes first. `trade-verify --license` shows both. Contact
Giolit Labs before that date for a renewal License File. Activating it continues
your use without reinstalling.

7.5 The terms of a purchased license (price, term, number of installations,
support) are set out in the order or quotation accepted by both parties. Where
they differ from this agreement, the order prevails.

## 8. Third-party components

8.1 The Software uses the following components, which you install separately
through your operating system and which are governed by their own licenses:

| Component | License |
|---|---|
| LLVM and Clang 18 (`libllvm18`, `libclang-cpp18`), when the C front end is installed | Apache License 2.0 with LLVM Exceptions |
| OpenSSL 3 (`libssl3`) | Apache License 2.0 |

8.2 The Software includes the following components, whose notices and license
texts are reproduced in `THIRD-PARTY-NOTICES.md`:

| Component | License |
|---|---|
| pugixml (© Arseny Kapoulkine) | MIT License |

8.3 The benchmark specifications in the `benchmarks/` folder of the trial
package are Giolit Labs' own and are provided so that you can reproduce the
results in the package.

Nothing in this agreement limits your rights under those licenses.

## 9. Data and privacy

The Software runs entirely on your computer. It does not transmit your
Specifications, logs, results or any other data to Giolit Labs or to third
parties, and it needs no network connection. Result files record the names of
the analysed files, the constraints and their runs. You decide whether and with
whom to share them.

## 10. Warranty disclaimer

The Software, and in particular the Trial Version, is provided **"AS IS"**,
without warranty of any kind, express or implied, including without limitation
warranties of merchantability, fitness for a particular purpose, accuracy of
results, and non-infringement, to the maximum extent permitted by applicable
law.

## 11. No liability

Giolit Labs is not liable to you, or to anyone claiming through you, for any
damages of any kind arising from or related to the Software, its Output or this
agreement, however caused and on any theory of liability (contract, tort
including negligence, or otherwise): direct, indirect, incidental, special,
consequential or punitive damages, and loss of profits, revenue, data, silicon
re-spins or business opportunities. This applies to the Trial Version and to
every Licensed Version, even if Giolit Labs was advised that such damages were
possible. Only where applicable law does not allow liability to be excluded does
liability remain, and then only to the minimum extent that law requires.

## 12. Term and termination

This agreement is effective from your first installation or use. It ends
automatically when the trial expires (section 4), unless you have activated a
purchased license. Giolit Labs may terminate it immediately if you breach
sections 2, 4.4 or 5. On termination you must stop using the Software and
delete all copies. Sections 2, 5, 6 and 9 to 14 survive termination.

## 13. Export control

You shall comply with all export control and sanctions laws that apply to your
use of the Software.

## 14. General

14.1 This agreement is governed by the laws of India. The High Court of Kerala
has exclusive jurisdiction over any dispute arising from it.

14.2 This agreement, together with any accepted order for a Licensed Version,
is the entire agreement between you and Giolit Labs about the Software. It
supersedes all prior understandings.

14.3 If any provision is held unenforceable, the rest remains in force.

14.4 A failure to enforce a right is not a waiver of it.

14.5 Giolit Labs may update this agreement for new versions of the Software. The
version delivered with a build governs that build.

---

*Giolit Labs — Ramavarmapuram P.O., Thrissur, Kerala, India — www.giolit.com —
business.giolitlabs@gmail.com*
