
# 08 | Limitations and Safety

## Scientific Scope, Responsible Interpretation, and Non-Clinical Use

### 1. Purpose

This directory defines the scientific, computational, and operational boundaries of the D³ VITAL-X research framework.

The project is an independent research prototype developed for computational signal analysis and research-oriented platform exploration.

### 2. Experimental Scope

The reported extended IAAFT experiment used:

- 80,000 ECG rows.
- 6 signal channels.
- 10 replicates per channel.
- 60 total trajectories.
- Iteration checkpoints of 200, 300, 400, and 500.
- Random seed `20261114`.

A maximum reported spectral-error reduction of 56.44% was observed for the MA_MLII channel between the 200- and 500-iteration checkpoints.

This finding is limited to the tested surrogate spectral-matching procedure and experimental configuration.

### 3. What the Result Does Not Demonstrate

The reported 56.44% reduction does **not** establish:

- 56.44% clinical accuracy.
- Medical diagnostic performance.
- Improved patient outcomes.
- Astronaut-specific health prediction.
- Anomaly-detection sensitivity or specificity.
- Detection of a confirmed physiological event.
- Flight-safety or mission-readiness certification.

IAAFT spectral matching evaluates agreement under a selected spectral-error measure. It does not independently validate a medical or operational decision.

### 4. Biomedical Data Boundary

The use of ECG benchmark signals does not make the system an astronaut-specific medical monitoring solution.

Dataset origin, population, recording conditions, channel definitions, preprocessing, and usage permissions must be considered when interpreting results.

No claim of clinical generalization should be made without appropriate independent studies and expert review.

### 5. Non-Clinical Scope

D³ VITAL-X is:

- A research and computational experimentation prototype.
- A framework for signal characterization and quantitative analysis.
- A platform-development initiative.

D³ VITAL-X is **not**:

- A medical device.
- A diagnostic or treatment system.
- A substitute for qualified medical professionals.
- A certified astronaut health-monitoring system.
- A flight-safety decision or mission-certification tool.

### 6. Human Review and Responsible Use

Biomedical outputs must be treated as research indicators requiring human review.

No health-related decision should be made solely from a computational score, visualization, anomaly indicator, or surrogate-analysis result.

### 7. Further Validation Required

Before any clinical or operational interpretation, additional work would be required, including:

- Independent datasets and external validation.
- Clearly defined ground truth and evaluation protocols.
- Appropriate statistical testing.
- Population and domain generalization studies.
- Robustness and failure-mode assessment.
- Qualified biomedical and domain-expert review.
- Relevant regulatory and operational evaluation.

### 8. Reporting Principle

All claims must remain proportional to the evidence.

A computational improvement is not automatically a clinical improvement. A detected numerical pattern is not automatically a physiological event.

---

**Safety statement:** Research indicators only. No diagnosis, treatment recommendation, or flight-safety certification.
