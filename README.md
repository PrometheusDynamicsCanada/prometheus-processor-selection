# Cross-Processor Quality Spread Across Sibling 156Q IBM Chips

*Portfolio Hub: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview) · [Detailed Technical Report](DETAILED_TECHNICAL_REPORT.md) · [Evidence Index](EVIDENCE_INDEX.md)*

## Introduction

- **The question:** How much does choosing *which* quantum processor runs a job change the result across sibling chips of the exact same `156`-qubit hardware generation?
- **The test:** Using `33` archived raw IBM Quantum Job ZIP bundles (counted once in [`prometheus-quantum-and-gpu-benchmarks`](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-and-gpu-benchmarks)) plus a `9`-qubit pre-committed selection test, we compared identical `20Q-22Q` dense workloads across `ibm_fez`, `ibm_marrakesh`, and `ibm_kingston`.
- **The finding:** On the identical `20`-qubit dense circuit (`16,384` shots/arm), output-distribution agreement reached **`0.0981` on `ibm_kingston`** vs. **`0.0577` on `ibm_marrakesh`** and **`0.0357` on `ibm_fez`** (**`2.75x` observed cross-chip spread**). In the `9`-qubit prospective selection check, choosing the chip before execution beat fixed assignment on **`6/6`** (`marrakesh`/`fez`) and **`5/6`** (`kingston`) workloads.
- **The significance:** Treating same-generation cloud QPUs as interchangeable leaves large quality differences on the table; compiler choice and chip choice interact.
- **The boundary:** Broadcast runs (`20Q-22Q`) measure empirical spread rather than blind pre-selection, and at `21Q` (`kingston`) and `22Q` (`marrakesh`) SABRE O3 beat Prometheus on `1` of the `3` chips while Prometheus led the other `2`.
- **The evidence:** Opening `20Q` cross-processor chart and `20Q-22Q` table below, with raw IBM Job ZIP verification underneath.

![Same 20-Qubit Dense Workload Across Three Sibling IBM Processors](assets/fig0_opening_processor_spread.png)
*Opening summary: Output-distribution agreement (`F_B`) on the identical 20-qubit dense circuit across `ibm_fez`, `ibm_marrakesh`, and `ibm_kingston` (`2.75x` spread).*

---

## Executive Summary (`20Q-22Q` Multi-QPU Broadcast: `9` Jobs, `27` Circuits, `442,368` Shots)

| Workload | Processor | SABRE O3 $F_B$ `(↑)` | TKET $F_B$ `(↑)` | Prometheus $F_B$ `(↑)` | Best Strategy on Chip | Best Chip for Width |
| :---: | :--- | :---: | :---: | :---: | :--- | :--- |
| **`20Q` `K_20`** | `ibm_fez` | `0.0227` | `0.0022` | **`0.0357`** | Prom (`+57.4%` vs. S) | `ibm_kingston` (**`0.0981`**, `2.75x` vs. Fez) |
| **`20Q` `K_20`** | `ibm_kingston` | `0.0249` | `0.0021` | **`0.0981`** | **Prom (`+293.8%` vs. S)** | **`ibm_kingston` (`0.0981` Prom)** |
| **`20Q` `K_20`** | `ibm_marrakesh` | `0.0293` | `0.0067` | **`0.0577`** | Prom (`+97.3%` vs. S) | `ibm_kingston` (`1.70x` vs. Marrakesh) |
| **`21Q` `K_21`** | `ibm_fez` / `kingston` / `marrakesh` | `0.0133` / **`0.1059`** / `0.0641` | `0.0012` / `0.0020` / `0.0136` | **`0.0345`** / `0.0813` / **`0.0904`** | Prom `2/3` chips; S on Kingston | `ibm_kingston` (**`0.1059` S**) / `marrakesh` (`0.0904` P) |
| **`22Q` `K_22`** | `ibm_fez` / `kingston` / `marrakesh` | `0.0002` / `0.0636` / **`0.1036`** | `0.0005` / `0.0003` / `0.0021` | **`0.0275`** / **`0.0944`** / `0.0815` | Prom `2/3` chips; S on Marrakesh | `ibm_marrakesh` (**`0.1036` S**) / `kingston` (`0.0944` P) |

*Metric Key:* Output-distribution agreement is Classical Bhattacharyya Overlap $F_B = \sum_x \sqrt{P_{\text{ideal}}(x)P_{\text{meas}}(x)}$ (Studio `"State Fidelity"`); full observables are in [`ALL_RESULTS.csv`](ALL_RESULTS.csv).

---

## Inspect the Evidence & Reproduce Supported Checks Offline

- **Command:** `python Fez_Marrakesh_Kingston/3_verify_and_view.py --dir Fez_Marrakesh_Kingston`
- **Dependencies & measured runtime:** Python 3 standard library (`0` cloud credentials, **`~0.04 s`** measured runtime).
- **Start a pilot:** [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca) | [prometheusdynamics.ca](https://prometheusdynamics.ca)

---

## Archived Studio Telemetry Capture

<details>
<summary><strong>Expand Archived Studio UI Telemetry Capture (Job dah7jq7i3e6s738nf8h0 on ibm_kingston) - Click to expand</strong></summary>

![20Q IBM Kingston Studio UI Capture](github_images/Screenshot%20%281447%29.png)
*Studio UI capture for `20Q` Dense `K_20` on `ibm_kingston` (`16,384` shots/compiler; Studio labels $F_B$ as `"State Fidelity"`).*

</details>
