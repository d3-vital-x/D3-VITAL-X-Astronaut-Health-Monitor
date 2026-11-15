
# Experimental Design
## Extended IAAFT Surrogate Spectral-Matching Evaluation

**Project:** D³ VITAL-X Astronaut Health Monitor  
**Research Track:** Global Event — Research Engine Framework  
**Experiment:** Extended IAAFT Test 02B  
**Random Seed:** `20261114`

---

## 1. Research Objective

This experiment evaluates the iterative spectral-matching behavior of an Iterative Amplitude Adjusted Fourier Transform (IAAFT) surrogate-generation procedure across multiple ECG signal channels and replicate trajectories.

The primary objective is to quantify how the selected spectral-error measure changes as the number of IAAFT iterations increases.

The experiment is designed as a computational-method evaluation. It does not attempt to establish clinical diagnostic performance, medical prediction accuracy, or astronaut-specific health status.

## 2. Dataset Scope

The experiment uses an ECG benchmark dataset containing:

| Parameter | Configuration |
|---|---:|
| Total rows | 80,000 |
| Number of channels | 6 |
| Replicates per channel | 10 |
| Total trajectories | 60 |
| Random seed | `20261114` |

The 80,000-row value describes the reported input dataset size. The exact record composition, sampling frequency, channel units, patient/record distribution, and preprocessing history must be documented in the dataset provenance record.

The six channels are evaluated separately. The channel label `MA_MLII` is retained as reported in the experiment outputs. Other channel labels should be taken directly from the source dataset and the actual experiment files.

No unverified assumption should be made about channel equivalence, clinical meaning, or physiological interpretation.

## 3. Experimental Structure

The design contains six channel-level groups.

Each channel is evaluated through ten replicate trajectories:

\[
6\ \text{channels} \times 10\ \text{replicates}
= 60\ \text{trajectories}
\]

Each trajectory is evaluated at four iteration checkpoints:

\[
K = \{200,\ 300,\ 400,\ 500\}
\]

The checkpoints provide a common basis for comparing spectral-matching error as the iterative procedure progresses.

The experiment should preserve the relationship between:

- Dataset identifier
- Channel identifier
- Replicate identifier
- Iteration checkpoint
- Algorithm configuration
- Computed spectral-error value

## 4. Experimental Factors

### 4.1 Channel

Channel is treated as a grouping variable. Results should be reported separately for each channel before any aggregate comparison is made.

### 4.2 Replicate

Ten replicate trajectories are used per channel to examine variability across surrogate-generation runs.

Replicate-level outputs should not be replaced by aggregate means. The original observations should remain available for inspection.

### 4.3 Iteration Checkpoint

The experiment evaluates the procedure at 200, 300, 400, and 500 iterations.

These checkpoints allow the comparison of intermediate and later spectral-matching behavior.

### 4.4 Randomization

The recorded random seed is:

`20261114`

The seed should be applied consistently to the random-number generation components of the experiment. Any separate random generator or library-specific seed should also be recorded.

## 5. Primary Evaluation Objective

The primary outcome is the spectral-matching error between the original signal and its generated surrogate at each specified checkpoint.

The exact error definition, normalization, frequency range, and numerical implementation must be documented in `iaaft_methodology.md` and the experiment configuration.

The principal comparison is:

\[
E_{200},\ E_{300},\ E_{400},\ E_{500}
\]

where \(E_k\) denotes the spectral-error value at iteration checkpoint \(k\).

A lower value indicates closer agreement under the selected spectral-error definition. It does not automatically indicate improved clinical or predictive performance.

## 6. Secondary Evaluation Metrics

Where available, the experiment records:

- Mean spectral error
- Median spectral error
- Standard deviation
- 95th-percentile spectral error
- Maximum residual spectral error
- Relative error reduction
- Replicate-level variability

The aggregation procedure should identify whether statistics are calculated across replicates, channels, or both.

Channel-specific and experiment-wide summaries must remain distinguishable.

## 7. Reported Observation

The extended experiment reports decreasing mean spectral error with increasing iteration checkpoints across the six tested channels.

The maximum reported reduction between the 200- and 500-iteration checkpoints is:

**56.44% for the MA_MLII channel.**

This is a result of the tested computational spectral-matching procedure and its selected error metric.

It is not a 56.44% improvement in clinical accuracy, anomaly-detection performance, patient outcomes, astronaut health prediction, or diagnostic reliability.

The result should be independently recalculated from the archived raw and comparison CSV files before publication as a verified numerical claim.

## 8. Data and Output Requirements

The experiment should retain, at minimum:

1. Dataset and channel identifiers.
2. Replicate identifiers.
3. Iteration checkpoint values.
4. Spectral-error measurements.
5. Algorithm and configuration metadata.
6. Random seed.
7. Execution environment information.
8. Summary and comparison outputs.

Expected result artifacts include:

- `iaaft_extended_raw.csv`
- Summary CSV output
- Comparison CSV output

The exact filenames and column schemas should match the files actually committed to the repository.

## 9. Reproducibility and Quality Controls

A reproducible run should:

- Verify the input dataset before execution.
- Confirm the expected six channels.
- Confirm the configured number of replicates.
- Verify the 60-trajectory design.
- Record the iteration checkpoints.
- Preserve the random seed and algorithm parameters.
- Validate output row counts and required fields.
- Preserve raw measurements before aggregation.
- Record execution errors and incomplete runs.

Any deviation from the planned design must be documented.

## 10. Interpretation and Scientific Boundaries

This experiment evaluates IAAFT surrogate spectral-matching behavior under a specified computational configuration.

It does not establish:

- Clinical validity.
- Diagnostic sensitivity or specificity.
- Medical prediction accuracy.
- Astronaut-specific physiological validity.
- Detection of a confirmed health event.
- Flight-safety or mission-readiness certification.

Independent validation with appropriately characterized datasets and domain-expert review would be required before any clinical or operational interpretation.

---

**Research principle:** Quantify the computational behavior that was measured; do not infer outcomes that the experiment was not designed to test.
