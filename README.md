# How Processor Choice Affects Results Across Sibling 156-Qubit Chips

*Portfolio Hub: [Prometheus Quantum Overview](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview) · [Detailed Technical Report](DETAILED_TECHNICAL_REPORT.md) · [Evidence Index](EVIDENCE_INDEX.md)*

Cloud users often treat quantum processors from the same hardware generation as interchangeable and pick whichever queue is shortest. We tested how much output quality varies when the exact same 20-to-22-qubit dense circuits run across three sibling 156-qubit IBM Heron processors (IBM Fez, Marrakesh, and Kingston).

On the identical 20-qubit dense circuit (16,384 shots per compiler), average output agreement reached 0.0981 on IBM Kingston versus 0.0577 on IBM Marrakesh and 0.0357 on IBM Fez - a 2.75x quality spread across chips of the same generation. In a separate 9-qubit prospective selection check, choosing the chip upfront from calibration data beat fixed chip assignment on 6 of 6 workloads against Fez and Marrakesh and 5 of 6 against Kingston.

The 20-to-22-qubit broadcast runs measure observed cross-chip spread rather than blind pre-selection, and at 21 and 22 qubits Qiskit SABRE O3 led on one of the three chips while Prometheus led on the other two (using 33 raw IBM Job ZIP bundles shared with and counted once in `prometheus-quantum-and-gpu-benchmarks`).

This repository contains the raw IBM Job archives, Studio UI captures, and offline verification tools across all 33 archived job bundles and the 144-execution selection suite.

![Same 20-Qubit Dense Workload Across Three Sibling IBM Processors](assets/fig0_opening_processor_spread.png)
*Summary figure: Output agreement on the identical 20-qubit dense circuit across IBM Fez, Marrakesh, and Kingston (2.75x cross-processor spread).*

**[Read the detailed results](#detailed-results) · [Verify the data](#verify-the-data) · [Request an evaluation](https://prometheusdynamics.ca/connect/) · [Book a demonstration](mailto:william@prometheusdynamics.ca?subject=Prometheus%20Evaluation)**

---

<a id="detailed-results"></a>
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

<a id="verify-the-data"></a>
## Inspect the Evidence & Reproduce Supported Checks Offline

- **Command:** `python Fez_Marrakesh_Kingston/3_verify_and_view.py --dir Fez_Marrakesh_Kingston`
- **Dependencies & measured runtime:** Python 3 standard library (`0` cloud credentials, **`~0.04 s`** measured runtime).
- **Request an evaluation or book a demonstration:** [prometheusdynamics.ca/connect](https://prometheusdynamics.ca/connect/) | [william@prometheusdynamics.ca](mailto:william@prometheusdynamics.ca?subject=Prometheus%20Evaluation)

---

## Archived Studio Telemetry Capture

<details>
<summary><strong>Expand Archived Studio UI Telemetry Capture (Job dah7jq7i3e6s738nf8h0 on ibm_kingston) - Click to expand</strong></summary>

![20Q IBM Kingston Studio UI Capture](github_images/Screenshot%20%281447%29.png)
*Studio UI capture for `20Q` Dense `K_20` on `ibm_kingston` (`16,384` shots/compiler; Studio labels $F_B$ as `"State Fidelity"`).*

</details>
