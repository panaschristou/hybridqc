<h1 align="center">HybridQC</h1>

<p align="center">
  <strong>Hardware-Grounded Simulation of<br>Tightly Integrated Hybrid Quantum-Classical Systems</strong>
</p>

<p align="center">
  <a href="https://doi.org/10.1145/3828523.3857132">Paper</a> &nbsp;·&nbsp;
  <a href="#documentation">Documentation</a> &nbsp;·&nbsp;
  <a href="#components">Components</a> &nbsp;·&nbsp;
  <a href="#running-the-simulator">Get started</a> &nbsp;·&nbsp;
  <a href="https://doi.org/10.5281/zenodo.23170503">Dataset</a> &nbsp;·&nbsp;
  <a href="#authors-and-citation">Citation</a>
</p>

---

HybridQC studies how hybrid applications execute on machines that combine **classical processors, quantum devices, controllers, memory, and interconnects**. It represents an application as dependent stages and a machine as a graph of finite resources. The simulator tracks service, waiting, overlap, and completion as jobs contend for that machine.

### What can you study?

- **Resource upgrades:** Which resource should be replicated, and when does controller capacity limit quantum-device scaling?
- **Scheduling:** How does the policy affect completion and waiting across mixed workloads?
- **Workload growth:** Which growth axes exhaust the machine first?
- **Deployment:** How do integrated execution and cloud overhead affect the same workload?

## Documentation

| Start with | What you will find |
| --- | --- |
| **[Supplementary results](docs/supplementary-results.pdf)** · PDF | Supporting results, extended methods, equations, and figures. |
| **[Running HybridQC](docs/running-hybridqc.pdf)** · PDF | Environment setup, input files, commands, and output fields. |
| **[Worked examples](docs/worked-examples.pdf)** · PDF | Guided comparisons with **[input files and checked results](examples/README.md)**. |
| **[Published dataset](https://doi.org/10.5281/zenodo.23170503)** · Zenodo | 31 CSV datasets, a data catalog, and a dictionary of fields and units. |

## Components

| Component | Role |
| --- | --- |
| **Workload construction** | Creates quantum-annealing, digital-quantum, classical, and coupled application stages with their dependencies and service inputs. |
| **Machine model** | Describes CPUs, GPUs, quantum devices, controllers, memories, and directed links, including their capacities and timing parameters. |
| **Backend profiles** | Uses IBM and D-Wave measurements to estimate physical quantum-device occupancy. Provider turnaround is represented separately when studying cloud execution. |
| **Scheduling policies** | Selects eligible work and forms batches using queue order, age, predicted service, or resource pressure. |
| **Execution engine** | Advances simulated time, enforces resource admission and release, and records stage and job completion. Python prepares inputs and orchestrates experiments. A compiled Rust engine executes the normalized model. |
| **Results and analysis** | Reports completion counts, elapsed time, job latency, service and waiting, resource utilization, and topology/policy comparisons. |

Quantum annealing (QA) uses repeated samples from an encoded optimization problem. Digital quantum computing (DQC) executes gate-based circuits. The ATC studies include QA-only, DQC-only, and coupled workloads, with quantum error correction disabled.

## Running the simulator

> **Source availability:** Source-code release is pending institutional authorization from Fordham University. Running simulations requires the source checkout and compiled extension. The documentation and published data can be read independently.

1. **Prepare your checkout** using the [installation guide](docs/running-hybridqc.pdf).
2. **Run the supplied inputs** from the [examples directory](examples/README.md) and compare your output with the checked results.
3. **Design a comparison:** define the workload stages, backend service profiles, and resource graph. Keep the seed and inputs fixed while varying the architectural decision of interest.

The guide documents the HybridQC JSON command interface. The small teaching examples use explicit assumed durations. The data-reading example uses the archived paper results. Check completion before interpreting speedup, and preserve the input and model identities with each result.

## Supporting results and data

The [supplementary results](docs/supplementary-results.pdf) cover:

- Policy time composition and workload-specific topology choices.
- Cloud versus integrated execution.
- Workload growth and incomplete configurations.
- Controller and link sensitivity.
- QA sampling and load shedding.

The PDF retains the two supporting figures outside the revised main paper. The [Zenodo archive](https://doi.org/10.5281/zenodo.23170503) contains the full numerical tables across six topics: system configuration, hardware measurements, topology and scheduling, workload scaling, cloud execution, and sensitivity studies. Use `DATA_CATALOG.csv` to find a study and `DATA_DICTIONARY.md` to interpret its fields and units.

<details>
<summary><strong>Browse the documentation package</strong></summary>

```text
README.md
CITATION.cff
docs/
  supplementary-results.pdf
  running-hybridqc.pdf
  worked-examples.pdf
examples/
  README.md
  *-config.json
  one-job.json
  eight-jobs.json
  hybrid-jobs.json
  expected/
```

</details>

## Authors and citation

**Panayiotis Christou · Shuwen Kan · Ying Mao**

*[HybridQC: Hardware-Grounded Simulation of Tightly Integrated Hybrid Quantum-Classical Systems](https://doi.org/10.1145/3828523.3857132).*

**SIGOPS ATC 2026**, November 15–18, Hong Kong, China. ACM.
**Paper DOI:** [10.1145/3828523.3857132](https://doi.org/10.1145/3828523.3857132).

Use the paper citation for HybridQC and the dataset citation for the numerical data. GitHub's **Cite this repository** menu provides the paper citation through [CITATION.cff](CITATION.cff).

<details>
<summary><strong>Copy the paper citation</strong></summary>

```bibtex
@inproceedings{christou_hybridqc_2026,
  author    = {Christou, Panayiotis and Kan, Shuwen and Mao, Ying},
  title     = {{HybridQC}: Hardware-Grounded Simulation of Tightly Integrated Hybrid Quantum-Classical Systems},
  booktitle = {The 2026 ACM SIGOPS Annual Technical Conference},
  series    = {SIGOPS ATC 2026},
  year      = {2026},
  publisher = {Association for Computing Machinery},
  doi       = {10.1145/3828523.3857132},
  url       = {https://doi.org/10.1145/3828523.3857132}
}
```

</details>

For the numerical data, cite **[HybridQC: Supplementary Data](https://doi.org/10.5281/zenodo.23170503)**. The dataset is distributed under **CC BY 4.0**.

<details>
<summary><strong>Copy the dataset citation</strong></summary>

```bibtex
@dataset{christou_hybridqc_data_2026,
  author  = {Christou, Panayiotis and Kan, Shuwen and Mao, Ying},
  title   = {HybridQC: Supplementary Data},
  year    = {2026},
  version = {1.0.0},
  doi     = {10.5281/zenodo.23170503},
  url     = {https://doi.org/10.5281/zenodo.23170503}
}
```

</details>

## Licenses

- **Paper:** [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/), as recorded in the ACM publication release.
- **Zenodo dataset:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- **Repository:** unless otherwise noted, the materials in this repository are licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/). See [LICENSE](LICENSE) for the full terms.
