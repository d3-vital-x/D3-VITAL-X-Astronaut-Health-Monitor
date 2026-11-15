
# IAAFT Methodology
## Iterative Amplitude Adjusted Fourier Transform for Surrogate Spectral Matching

**Project:** D³ VITAL-X Astronaut Health Monitor  
**Method:** Iterative Amplitude Adjusted Fourier Transform (IAAFT)

---

## 1. Introduction

The Iterative Amplitude Adjusted Fourier Transform (IAAFT) is a surrogate-data generation method designed to construct a sequence that approximately preserves two characteristics of an original time series:

1. Its empirical amplitude distribution.
2. Its Fourier-amplitude spectrum.

IAAFT is commonly used in nonlinear time-series analysis and surrogate-data testing.

Within D³ VITAL-X, the method is used as a computational procedure for evaluating surrogate spectral-matching behavior across ECG signal channels.

The procedure is not itself a clinical diagnostic method.

## 2. Methodological Objective

Given an original signal:

\[
x = (x_1,x_2,\ldots,x_N)
\]

the objective is to construct a surrogate sequence:

\[
s = (s_1,s_2,\ldots,s_N)
\]

that approximates the original signal's amplitude distribution and Fourier-amplitude spectrum.

The method alternates between two constraints:

- Amplitude-distribution adjustment.
- Fourier-amplitude adjustment.

These operations are repeated until a stopping condition or predefined iteration limit is reached.

## 3. Fourier Representation

For a discrete signal \(x_n\), its discrete Fourier transform is:

\[
X_k =
\sum_{n=0}^{N-1}
x_n e^{-i2\pi kn/N}
\]

The Fourier amplitude is:

\[
A_k = |X_k|
\]

The Fourier phase is:

\[
\phi_k = \arg(X_k)
\]

The original signal's Fourier-amplitude spectrum provides the spectral target for the surrogate procedure.

The precise implementation must specify transform normalization, treatment of real-valued signals, and any frequency-bin handling.

## 4. IAAFT Procedure

A conventional IAAFT procedure can be summarized as follows.

### Step 1 — Original Signal Preparation

Obtain a valid one-dimensional signal channel:

\[
x = (x_1,\ldots,x_N)
\]

Verify that the input contains an appropriate number of finite observations.

Document missing-value handling, detrending, filtering, normalization, and any other preprocessing.

### Step 2 — Amplitude Distribution Target

Sort the original signal:

\[
x_{\mathrm{sorted}} =
\operatorname{sort}(x)
\]

This sorted sequence defines the empirical amplitude distribution that the surrogate should preserve.

### Step 3 — Spectral Target

Calculate the original Fourier transform and retain its amplitude spectrum:

\[
A_k^{(x)} = |\mathcal{F}(x)_k|
\]

### Step 4 — Initial Surrogate

Initialize a surrogate by randomly permuting the original observations or by using another explicitly documented initialization procedure.

The initialization method must be recorded because it can affect the iterative trajectory.

### Step 5 — Fourier-Amplitude Adjustment

Calculate the Fourier transform of the current surrogate:

\[
S_k^{(t)} =
\mathcal{F}(s^{(t)})_k
\]

Retain the current phase:

\[
\phi_k^{(t)} =
\arg(S_k^{(t)})
\]

Replace its Fourier amplitude with the target amplitude:

\[
\widetilde{S}_k^{(t)}
=
A_k^{(x)}
e^{i\phi_k^{(t)}}
\]

Apply the inverse Fourier transform:

\[
\widetilde{s}^{(t)}
=
\mathcal{F}^{-1}
\left(\widetilde{S}^{(t)}\right)
\]

For real-valued signals, the implementation must preserve the required conjugate-symmetry conditions and handle numerical precision appropriately.

### Step 6 — Amplitude-Distribution Adjustment

Rank the values of the inverse-transformed sequence.

Replace the ranked values with the corresponding order statistics of the original signal.

This produces a new sequence whose empirical amplitude distribution matches the original distribution, subject to the implementation's ranking and tie-handling rules.

### Step 7 — Iteration

Repeat the Fourier-amplitude adjustment and amplitude-distribution adjustment.

The procedure continues until:

- A predefined iteration limit is reached.
- A documented convergence condition is met.
- A numerical or execution failure occurs.

For the extended D³ VITAL-X experiment, the reported evaluation checkpoints are:

\[
K = \{200,\ 300,\ 400,\ 500\}
\]

The exact point at which a checkpoint is recorded must be consistent across all channels and replicates.

## 5. Spectral-Matching Mechanism

IAAFT alternates between constraints in two different representations:

| Operation | Target property |
|---|---|
| Fourier-amplitude adjustment | Original Fourier-amplitude spectrum |
| Rank-based amplitude adjustment | Original empirical amplitude distribution |

Because the two constraints are not generally satisfied simultaneously by every intermediate sequence, the procedure iterates between them.

The resulting surrogate is an approximation under the selected implementation and stopping configuration.

An iteration increase does not guarantee monotonic improvement for every possible error definition or implementation. This behavior must be examined from the recorded measurements rather than assumed.

## 6. Spectral-Error Evaluation

The experiment compares the original and surrogate Fourier-amplitude spectra.

One possible normalized error definition is:

\[
E_{\mathrm{rel}}
=
\frac{
\left\|A^{(x)}-A^{(s)}\right\|_2
}{
\left\|A^{(x)}\right\|_2+\epsilon
}
\]

where:

- \(A^{(x)}\) is the original Fourier-amplitude vector.
- \(A^{(s)}\) is the surrogate Fourier-amplitude vector.
- \(\|\cdot\|_2\) is the Euclidean norm.
- \(\epsilon\) is a small numerical stabilizer.

**Important:** This is an illustrative normalized error definition. It must not be assumed to be the exact metric used in the archived experiment unless the source code or experiment configuration confirms it.

If the implementation uses a different error measure, its exact equation, normalization, frequency range, and units must be recorded.

## 7. Relative Error Reduction

Where the same error metric is used at both checkpoints, relative reduction can be calculated as:

\[
R =
\frac{E_{\mathrm{initial}}-E_{\mathrm{final}}}
{E_{\mathrm{initial}}}
\times 100\%
\]

For the reported MA_MLII result:

- Initial checkpoint: 200 iterations.
- Final checkpoint: 500 iterations.
- Reported maximum reduction: 56.44%.

This value must be verified against the corresponding raw and comparison outputs.

It describes the relative reduction in the selected spectral-error measure. It does not describe clinical accuracy or anomaly-detection improvement.

## 8. Additional Error Statistics

The extended experiment may report:

### Mean

\[
\bar{E} =
\frac{1}{n}\sum_{i=1}^{n}E_i
\]

### Median

The central value of the ordered error observations.

### Standard Deviation

\[
s =
\sqrt{
\frac{1}{n-1}
\sum_{i=1}^{n}(E_i-\bar{E})^2
}
\]

### 95th Percentile

The error value at the specified 95th-percentile quantile convention.

### Maximum Residual Error

\[
E_{\max} = \max_i(E_i)
\]

The aggregation population and quantile calculation convention should be documented for every reported statistic.

## 9. Replicate-Level Evaluation

Ten replicate trajectories are configured for each of the six channels.

Replicate-level measurements are important because an aggregate mean can conceal variation between individual runs.

The evaluation should preserve:

- Channel identifier.
- Replicate identifier.
- Iteration checkpoint.
- Spectral-error value.
- Any convergence or failure status.

Channel-level summaries should be calculated from the corresponding replicate-level observations.

## 10. Implementation and Numerical Considerations

The implementation should document:

- FFT library and version.
- Transform normalization.
- Initialization procedure.
- Random-number generator.
- Rank-ordering and tie handling.
- Treatment of missing or non-finite values.
- Numerical precision.
- Stopping criteria.
- Checkpoint recording behavior.
- Error calculation and aggregation.

Any changes to these settings should be treated as a method or configuration change.

## 11. Interpretation

A lower spectral-error value indicates closer agreement between the original and surrogate spectra under the selected error definition.

It does not establish:

- Preservation of every temporal or nonlinear property.
- Statistical significance of a scientific hypothesis.
- Clinical validity.
- Diagnostic accuracy.
- Anomaly-detection sensitivity or specificity.
- Astronaut-specific health-monitoring capability.

IAAFT surrogate generation and spectral-error evaluation are computational methods, not medical diagnoses.

---

**Methodological principle:** Spectral agreement is a measurable computational property, not a substitute for clinical or scientific validation.
