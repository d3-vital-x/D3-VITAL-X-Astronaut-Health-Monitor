# 05 | Reproducibility

## Execution Environment, Randomness, and Data Provenance

### 1. Purpose

This directory documents the information required to inspect, reproduce, and audit the computational experiments conducted within the D³ VITAL-X research framework.

Reproducibility is treated as a core research requirement rather than an optional reporting feature.

### 2. Core Documentation

| File | Purpose |
|---|---|
| `execution_environment.md` | Software environment, dependency versions, execution platform, and relevant runtime settings. |
| `data_provenance.md` | Dataset origin, access information, preparation history, and applicable usage constraints. |
| Experiment configuration records | Parameters, channel definitions, replicate settings, and iteration checkpoints. |

### 3. Random Seed

The extended IAAFT experiment records:

`random_seed: 20261114`

The seed is part of the experiment configuration and should be preserved when attempting to reproduce the same randomized workflow.

A fixed seed alone does not guarantee bitwise-identical results across different software versions, hardware environments, numerical libraries, or execution configurations.

### 4. Reproducibility Requirements

For each experiment, preserve:

- Dataset identifier and provenance.
- Input dimensions and channel labels.
- Data preparation and quality-control steps.
- Algorithm and implementation version.
- Random seed and relevant parameters.
- Replicate and iteration-checkpoint identifiers.
- Software dependencies and execution environment.
- Raw, summary, and comparison outputs.
- Figure-generation scripts or configuration.
- File hashes, where available.

### 5. Reproduction Workflow

1. Obtain the documented dataset or authorized reference.
2. Verify dataset identity and integrity.
3. Reconstruct the recorded execution environment as closely as practical.
4. Apply the documented preparation procedure.
5. Run the experiment using the recorded configuration.
6. Compare generated outputs with the archived results.
7. Record discrepancies and environmental differences.

### 6. Reproducibility Boundary

Reproduction should distinguish between exact computational replication and approximate numerical agreement.

Any differences in input data, preprocessing, dependencies, hardware, or implementation should be recorded rather than silently ignored.

---

**Objective:** Make experimental results traceable, inspectable, and independently reproducible.
