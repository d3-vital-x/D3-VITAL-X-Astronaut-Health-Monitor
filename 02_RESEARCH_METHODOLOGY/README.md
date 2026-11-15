# 02 | Research Methodology

## Experimental Design and IAAFT Methodology

### 1. Purpose

This directory describes the experimental design and computational procedures used to evaluate surrogate-signal spectral matching within the D³ VITAL-X research framework.

The methodology emphasizes controlled experiments, measurable convergence behavior, and reproducible computation.

### 2. Experimental Design

The extended IAAFT experiment was configured as follows:

| Parameter | Configuration |
|---|---:|
| Dataset size | 80,000 rows |
| Number of channels | 6 |
| Replicates per channel | 10 |
| Total trajectories | 60 |
| Iteration checkpoints | 200, 300, 400, 500 |
| Random seed | `20261114` |

The experiment evaluates spectral-matching behavior across multiple channels and replicate trajectories.

The experimental configuration is documented in:

- `experimental_design.md` — dataset scope, channel configuration, replicate structure, checkpoints, and evaluation plan.
- `iaaft_methodology.md` — IAAFT procedure, iterative spectral matching, convergence assessment, and error metrics.

### 3. Methodological Workflow

1. Verify dataset structure and channel availability.
2. Prepare individual signal channels for analysis.
3. Establish the original signal's relevant statistical and spectral characteristics.
4. Generate surrogate trajectories using the selected IAAFT procedure.
5. Evaluate spectral matching at predefined iteration checkpoints.
6. Calculate residual spectral error and summary statistics.
7. Compare results across channels and replicates.
8. Preserve outputs for reproducibility and independent inspection.

### 4. Evaluation Metrics

The experiment may report:

- Mean spectral error
- Median spectral error
- Standard deviation
- 95th-percentile spectral error
- Maximum residual error
- Relative improvement between checkpoints
- Replicate-level variability

Metrics are interpreted within the scope of surrogate spectral matching.

### 5. Reported Observation

Across the tested channels, mean spectral error decreased with increasing iteration checkpoints.

The maximum reported reduction between 200 and 500 iterations was 56.44% for the MA_MLII channel.

This is a computational convergence observation for the tested configuration. It is not evidence of clinical prediction accuracy, anomaly-detection sensitivity, or medical significance.

### 6. Methodological Boundaries

The results depend on the dataset, channel preparation, algorithm implementation, iteration settings, and evaluation procedure.

They should not be generalized beyond the tested conditions without further experiments and independent validation.

---

**Related files**

- `experimental_design.md`
- `iaaft_methodology.md`
