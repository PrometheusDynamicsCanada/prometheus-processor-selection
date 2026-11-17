# Detailed Technical Report & Supporting Ledgers: `prometheus-processor-selection`

*Companion technical report to [`README.md`](README.md) · Part of the [Prometheus quantum execution portfolio](https://github.com/PrometheusDynamicsCanada/prometheus-quantum-overview)*

---

## 2. Visual Walkthrough: 20-Qubit Dense All-to-All (K_20) Broadcast Across 3 Heron QPUs

All three executions below compile the same 20-qubit dense all-to-all logical workload (39 logical depth, 230 logical gates, 16,384 shots/compiler, 49,152 shots/job; source package: [`Fez_Marrakesh_Kingston/`](Fez_Marrakesh_Kingston/)).

### 2A. Target Processor: `ibm_fez` (Job `dah7efb9k43c73aedfp0`, 20Q Dense All-to-All, 16,384 Shots/Compiler)

| Target QPU | Metric & Direction | SABRE O3 | TKET | Prometheus | Prometheus vs. Best Baseline |
| :--- | :--- | ---: | ---: | ---: | ---: |
| `ibm_fez` | Distribution Fidelity F_B (↑) | 0.0227 | 0.0022 | **0.0357** | **+57.37%** |
| `ibm_fez` | Total Variation Distance TVD (↓) | 0.9193 | 0.9779 | **0.8960** | **-2.54%** |
| `ibm_fez` | Heavy-Output Probability HOP (↑) | 0.5389 | 0.5264 | **0.5430** | **+0.77%** |
| `ibm_fez` | Cross-Entropy XEB (↑) | 20.0724 | 2.6434 | **27.1090** | **+35.06%** |
| `ibm_fez` | Shannon Entropy H (bits) | 13.9381 | 13.9716 | **13.9213** | **-0.12%** |
| `ibm_fez` | Compiled Circuit Depth (↓) | 390 | 596 | **315** | **-19.23%** |
| `ibm_fez` | Two-Qubit CZ Gates (↓) | 474 | 799 | **405** | **-14.56%** |

<details>
<summary><strong>View <code>ibm_fez</code> Studio Screenshots (Figures 2a-2d)</strong></summary>

![20Q IBM Fez measured results](github_images/Screenshot%20%281440%29.png)

*Figure 2a: `ibm_fez` 20Q Dense All-to-All (Job ID: `dah7efb9k43c73aedfp0`, 16,384 shots/compiler) - Measured Execution Results (F_B: 0.0227 SABRE / 0.0022 TKET / 0.0357 Prometheus; TVD: 0.9193 / 0.9779 / 0.8960; XEB: 20.0724 / 2.6434 / 27.1090).*

![20Q IBM Fez hardware allocation](github_images/Screenshot%20%281441%29.png)

*Figure 2b: `ibm_fez` 20Q Dense All-to-All - Physical 156-Qubit Hardware Allocation View.*

![20Q IBM Fez structural comparison](github_images/Screenshot%20%281442%29.png)

*Figure 2c: `ibm_fez` 20Q Dense All-to-All - Compiled Circuit Structural Comparison (Depth: 390 SABRE / 596 TKET / 315 Prometheus; 2Q Gates: 474 / 799 / 405).*

![20Q IBM Fez metric chart](github_images/Screenshot%20%281443%29.png)

*Figure 2d: `ibm_fez` 20Q Dense All-to-All - Comparative Observable Chart (16,384 shots/compiler).*

</details>

### 2B. Target Processor: `ibm_kingston` (Job `dah7efgmhr3c73e665g0`, 20Q Dense All-to-All, 16,384 Shots/Compiler)

| Target QPU | Metric & Direction | SABRE O3 | TKET | Prometheus | Prometheus vs. Best Baseline |
| :--- | :--- | ---: | ---: | ---: | ---: |
| `ibm_kingston` | Distribution Fidelity F_B (↑) | 0.0249 | 0.0021 | **0.0981** | **+293.81%** |
| `ibm_kingston` | Total Variation Distance TVD (↓) | 0.9147 | 0.9789 | **0.8089** | **-11.57%** |
| `ibm_kingston` | Heavy-Output Probability HOP (↑) | 0.5236 | 0.4880 | **0.6176** | **+17.95%** |
| `ibm_kingston` | Cross-Entropy XEB (↑) | 19.7459 | 2.1115 | **58.1474** | **+194.48%** |
| `ibm_kingston` | Shannon Entropy H (bits) | 13.9276 | 13.9434 | **13.8115** | **-0.83%** |
| `ibm_kingston` | Compiled Circuit Depth (↓) | 512 | 596 | **315** | **-38.48%** |
| `ibm_kingston` | Two-Qubit CZ Gates (↓) | 600 | 799 | **409** | **-31.83%** |

<details>
<summary><strong>View <code>ibm_kingston</code> Studio Screenshots (Figures 3a-3d)</strong></summary>

![20Q IBM Kingston measured results](github_images/Screenshot%20%281444%29.png)

*Figure 3a: `ibm_kingston` 20Q Dense All-to-All (Job ID: `dah7efgmhr3c73e665g0`, 16,384 shots/compiler) - Measured Execution Results (F_B: 0.0249 SABRE / 0.0021 TKET / 0.0981 Prometheus; TVD: 0.9147 / 0.9789 / 0.8089; XEB: 19.7459 / 2.1115 / 58.1474).*

![20Q IBM Kingston hardware allocation](github_images/Screenshot%20%281445%29.png)

*Figure 3b: `ibm_kingston` 20Q Dense All-to-All - Physical 156-Qubit Hardware Allocation View.*

![20Q IBM Kingston structural comparison](github_images/Screenshot%20%281446%29.png)

*Figure 3c: `ibm_kingston` 20Q Dense All-to-All - Compiled Circuit Structural Comparison (Depth: 512 SABRE / 596 TKET / 315 Prometheus; 2Q Gates: 600 / 799 / 409).*

![20Q IBM Kingston metric chart](github_images/Screenshot%20%281447%29.png)

*Figure 3d: `ibm_kingston` 20Q Dense All-to-All - Comparative Observable Chart (16,384 shots/compiler).*

</details>

### 2C. Target Processor: `ibm_marrakesh` (Job `dah7ekgmhr3c73e665kg`, 20Q Dense All-to-All, 16,384 Shots/Compiler)

| Target QPU | Metric & Direction | SABRE O3 | TKET | Prometheus | Prometheus vs. Best Baseline |
| :--- | :--- | ---: | ---: | ---: | ---: |
| `ibm_marrakesh` | Distribution Fidelity F_B (↑) | 0.0293 | 0.0067 | **0.0577** | **+97.34%** |
| `ibm_marrakesh` | Total Variation Distance TVD (↓) | 0.9032 | 0.9578 | **0.8609** | **-4.69%** |
| `ibm_marrakesh` | Heavy-Output Probability HOP (↑) | 0.5388 | 0.5381 | **0.5758** | **+6.86%** |
| `ibm_marrakesh` | Cross-Entropy XEB (↑) | 19.4430 | 7.6657 | **38.1583** | **+96.26%** |
| `ibm_marrakesh` | Shannon Entropy H (bits) | 13.9112 | 13.9549 | **13.8697** | **-0.30%** |
| `ibm_marrakesh` | Compiled Circuit Depth (↓) | 337 | 596 | **300** | **-10.98%** |
| `ibm_marrakesh` | Two-Qubit CZ Gates (↓) | 439 | 799 | **396** | **-9.79%** |

<details>
<summary><strong>View <code>ibm_marrakesh</code> Studio Screenshots (Figures 4a-4d)</strong></summary>

![20Q IBM Marrakesh measured results](github_images/Screenshot%20%281448%29.png)

*Figure 4a: `ibm_marrakesh` 20Q Dense All-to-All (Job ID: `dah7ekgmhr3c73e665kg`, 16,384 shots/compiler) - Measured Execution Results (F_B: 0.0293 SABRE / 0.0067 TKET / 0.0577 Prometheus; TVD: 0.9032 / 0.9578 / 0.8609; XEB: 19.4430 / 7.6657 / 38.1583).*

![20Q IBM Marrakesh hardware allocation](github_images/Screenshot%20%281449%29.png)

*Figure 4b: `ibm_marrakesh` 20Q Dense All-to-All - Physical 156-Qubit Hardware Allocation View.*

![20Q IBM Marrakesh structural comparison](github_images/Screenshot%20%281450%29.png)

*Figure 4c: `ibm_marrakesh` 20Q Dense All-to-All - Compiled Circuit Structural Comparison (Depth: 337 SABRE / 596 TKET / 300 Prometheus; 2Q Gates: 439 / 799 / 396).*

![20Q IBM Marrakesh metric chart](github_images/Screenshot%20%281451%29.png)

*Figure 4d: `ibm_marrakesh` 20Q Dense All-to-All - Comparative Observable Chart (16,384 shots/compiler).*

</details>

---

## 3. Cryptographic Evidence Integrity & Reproducibility

Every hardware execution in this repository is packaged with its raw IBM Quantum job metadata, measurement payloads, and SHA-256 cryptographic digests:

```bash
python Fez_Marrakesh_Kingston/3_verify_and_view.py
```

- [`RESULTS.md`](RESULTS.md) - Consolidated multi-QPU broadcast tables and analysis.
- [`EVIDENCE_INDEX.md`](EVIDENCE_INDEX.md) & [`REPOSITORY_SHA256SUMS.txt`](REPOSITORY_SHA256SUMS.txt) - Complete IBM Quantum Job ID, ZIP package, and SHA-256 inventory.
- [`REPRODUCIBILITY.md`](REPRODUCIBILITY.md) & [`docs/HASHING_AND_INTEGRITY.md`](docs/HASHING_AND_INTEGRITY.md) - Step-by-step SHA-256 verification workflow.
- [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md) - Field definitions and metric conventions.
