
# Execution Environment
## Computational Setup and Reproducibility Requirements

**Project:** D³ VITAL-X Astronaut Health Monitor  
**Experiment:** Extended IAAFT Test 02B  
**Configuration Seed:** `20261114`

---

## 1. Purpose

This document specifies the execution-environment information required to inspect and reproduce the D³ VITAL-X computational experiments.

The objective is to make software dependencies, runtime configuration, data preparation, and execution conditions traceable.

The environment description must reflect the actual environment used for each archived experiment. A recommended environment must not be presented as a historical execution record unless it has been verified.

## 2. Execution Environment Record

The following information should be recorded for every reproducibility run.

| Category | Required information |
|---|---|
| Operating system | Name, version, architecture |
| Runtime | Python version |
| Numerical libraries | NumPy, SciPy, and other libraries actually used |
| Data libraries | pandas and file-format libraries actually used |
| FFT implementation | Library and version |
| Visualization | Matplotlib or other plotting library and version |
| Execution platform | Local, cloud notebook, or hosted environment |
| Hardware | CPU architecture and available memory, if known |
| Storage | Input/output storage location and available capacity |
| Source code | Repository commit or version identifier |
| Dependencies | Exact package versions or lock file |
| Execution date | UTC timestamp |
| Randomness | Seed and random-number generator details |

Unknown fields should be marked `Not recorded` rather than inferred.

## 3. Recommended Software Components

The experiment may require the following categories of software, depending on the implementation:

- Python 3.x runtime.
- NumPy for array and numerical operations.
- SciPy for signal-processing and Fourier-related operations.
- pandas for tabular data handling.
- Matplotlib for static scientific figures.
- A compatible CSV reader and writer.

The actual package list must be derived from the experiment's source code and recorded dependency file.

Do not assume that the latest package versions reproduce an earlier execution environment.

## 4. Input Data Requirements

Before execution:

1. Confirm the dataset source and authorization.
2. Verify the expected 80,000-row input scope.
3. Confirm the six expected channel fields.
4. Verify channel labels against the source data.
5. Check for missing, infinite, or non-numeric observations.
6. Record sampling frequency and units when available.
7. Document preprocessing and channel selection.
8. Preserve an immutable reference to the original input.

The dataset's provenance and any transformations must be recorded in `data_provenance.md`.

## 5. Execution Requirements

A reproducibility run should:

- Load the documented dataset.
- Validate the input schema.
- Verify channel availability and ordering.
- Apply the recorded preprocessing.
- Execute the configured IAAFT procedure.
- Generate ten replicate trajectories per channel.
- Evaluate checkpoints at 200, 300, 400, and 500 iterations.
- Preserve raw replicate-level outputs.
- Generate summary and comparison tables.
- Record warnings, failures, and incomplete runs.

The expected experiment structure is:

\[
6 \times 10 = 60\ \text{trajectories}
\]

## 6. Resource and Runtime Considerations

Execution requirements depend on signal length, FFT implementation, number of replicates, iteration count, and intermediate-array allocation.

The experiment should record:

- Peak memory usage, where available.
- Execution duration.
- Failed or interrupted trajectories.
- Storage requirements.
- Any batching or resource-management strategy.

A resource-limited execution environment may use sequential or batched processing. Such changes must be documented because they may affect runtime and execution behavior.

## 7. Output Integrity

Expected artifacts include:

- `iaaft_extended_raw.csv`
- Summary CSV output
- Comparison CSV output
- Convergence figures
- Error-distribution figures
- Execution metadata

The exact output filenames, field names, and row counts must be checked against the committed files.

Where possible, calculate SHA-256 hashes for the input dataset and final output artifacts.

## 8. Reproducibility Audit

A reproducibility audit should verify:

1. Dataset identity and provenance.
2. Input dimensions and channel labels.
3. Software and dependency versions.
4. Algorithm implementation version.
5. Random seed and random-number generator.
6. Replicate and checkpoint counts.
7. Output schema and completeness.
8. Numerical consistency with archived results.
9. Figure-to-CSV consistency.
10. Documented deviations from the original execution.

A successful rerun should be described as an exact reproduction only when the relevant data, code, environment, and numerical outputs support that claim.

Otherwise, report it as an approximate or partial reproduction.

## 9. Environment Disclosure

The repository should distinguish between:

- **Recorded environment:** verified information from the original experiment.
- **Reproduction environment:** information from a later rerun.
- **Recommended environment:** a proposed setup for future execution.

These categories must not be conflated.

---

**Reproducibility principle:** Preserve the environment that generated the result, not merely the environment intended to run it again.
