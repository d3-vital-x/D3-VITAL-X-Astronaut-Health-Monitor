# 04 | Visual Evidence

## Convergence Curves and Spectral-Error Distributions

### 1. Purpose

This directory contains visual representations of the extended IAAFT experiment.

The figures are intended to make convergence behavior, channel-level differences, and replicate variability easier to inspect.

### 2. Expected Visual Artifacts

The directory may include:

- **Convergence curves:** spectral error plotted against iteration checkpoints.
- **Channel-wise comparisons:** differences in spectral-matching behavior across the six channels.
- **Error distributions:** distributions of spectral error across replicates.
- **Replicate-level plots:** variation among the 10 trajectories per channel.
- **Checkpoint comparisons:** visual comparison of results at 200, 300, 400, and 500 iterations.

### 3. Experimental Context

The visual evidence corresponds to an experiment configured with:

- 80,000 ECG rows.
- 6 channels.
- 10 replicates per channel.
- 60 total trajectories.
- Iteration checkpoints: 200, 300, 400, and 500.
- Random seed: `20261114`.

The maximum reported spectral-error reduction was 56.44% for the MA_MLII channel between the 200- and 500-iteration checkpoints.

### 4. Figure Interpretation

Visual trends should be interpreted together with the numerical outputs in `03_VALIDATION_RESULTS/`.

A decreasing error curve indicates improved matching under the selected spectral-error measure. It does not, by itself, establish statistical significance, clinical usefulness, or predictive performance.

Error distributions should be examined for dispersion, outliers, and replicate-level variability rather than relying only on average values.

### 5. Figure Documentation

Each published figure should include:

- Figure title and identifier.
- Channel and replicate scope.
- Iteration checkpoint information.
- Metric definition and units, where applicable.
- Dataset and experiment reference.
- Plot-generation configuration.

### 6. Scientific Boundary

These figures document computational surrogate-matching behavior only.

They are not medical visualizations, clinical evidence, or confirmation of astronaut health conditions.

---

**Related evidence:** Numerical results are maintained in `03_VALIDATION_RESULTS/`.
