# HybridQC examples

Read [Worked examples](../docs/worked-examples.pdf) alongside [Running HybridQC](../docs/running-hybridqc.pdf).

These are small, deterministic teaching cases for the normalized HybridQC JSON interface. The service times are assumed, arrivals are zero, the policy is FIFO, and QEC is disabled. Transfer tasks are omitted to isolate stage ordering and resource contention.

| Example | Configuration | Jobs | Checked final finish |
| --- | --- | --- | --- |
| One DQC pipeline | `baseline-config.json` | `one-job.json` | 9 s |
| Eight jobs, baseline | `baseline-config.json` | `eight-jobs.json` | 54 s |
| Two QPUs | `two-qpus-config.json` | `eight-jobs.json` | 54 s |
| Two controllers | `two-controllers-config.json` | `eight-jobs.json` | 35 s |
| Both doubled | `balanced-config.json` | `eight-jobs.json` | 35 s |
| Coupled QA-to-DQC | `hybrid-config.json` | `hybrid-jobs.json` | 16 s |

Run from a simulator checkout with this directory at `examples/`:

```sh
python -m hybridqc.cli.hcu_sim \
  --config examples/baseline-config.json \
  --jobs examples/one-job.json \
  --execution microstep \
  --output runs/tutorial-one.json
```

Use a new output path for each comparison. Files under `expected/` contain selected observables from executed examples, rather than the full CLI output schema. Compare those fields with your generated summary. The paper-data example in the PDF requires only Python and the public Zenodo archive.
