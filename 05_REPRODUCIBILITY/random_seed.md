
# Random Seed and Reproducibility Audit
## Extended IAAFT Test 02B

**Recorded random seed:** `20261114`

---

## 1. Purpose

This document records the random-seed configuration associated with the extended IAAFT surrogate spectral-matching experiment.

The seed is retained to support traceability and controlled attempts to reproduce the randomized components of the experiment.

## 2. Recorded Configuration

| Parameter | Value |
|---|---|
| Experiment | Extended IAAFT Test 02B |
| Random seed | `20261114` |
| Channels | 6 |
| Replicates per channel | 10 |
| Total trajectories | 60 |
| Iteration checkpoints | 200, 300, 400, 500 |

The seed must be interpreted as the recorded experiment configuration, not as proof that every software component used the same random-number generator state.

## 3. Why the Seed Matters

Random initialization can affect the generated surrogate trajectories.

A fixed seed helps control the random sequence when:

- The same random-number generator is used.
- The same seed is applied at the same point in execution.
- The same sequence of random operations is performed.
- The same implementation and relevant numerical environment are used.

If any of these conditions changes, the resulting trajectories may differ.

## 4. Random-Number Generator Disclosure

For reproducibility, record:

- Random-number library.
- Generator algorithm or class.
- Seed value.
- Seed initialization location.
- Whether one generator is shared or separate generators are used.
- Whether per-channel or per-replicate seeds are derived.
- Any parallel execution or worker-specific seed strategy.

If the implementation uses NumPy, document the actual generator API and version. Do not assume that a seed alone identifies the generator algorithm.

## 5. Seed Handling Recommendations

A controlled implementation should:

1. Define the master seed in one documented configuration location.
2. Initialize the random-number generator explicitly.
3. Avoid undocumented global random-state changes.
4. Record the seed associated with every trajectory.
5. Use a documented strategy for parallel workers.
6. Preserve the configuration with the generated outputs.

If separate seeds are derived for channels or replicates, document the derivation rule and retain the resulting values.

## 6. Reproducibility Audit Checklist

- [ ] Master seed equals `20261114`.
- [ ] Random-number generator is identified.
- [ ] Library and version are recorded.
- [ ] Initialization point is documented.
- [ ] Channel-to-replicate mapping is preserved.
- [ ] Parallel execution strategy is documented.
- [ ] All 60 trajectories have traceable identifiers.
- [ ] Iteration checkpoints are recorded.
- [ ] Raw outputs are preserved.
- [ ] Reproduction differences are documented.

## 7. Reproducibility Limitations

A fixed random seed does not guarantee bitwise-identical results across:

- Different numerical libraries.
- Different library versions.
- Different hardware architectures.
- Different FFT implementations.
- Different floating-point precision.
- Different parallel scheduling.
- Different preprocessing or data ordering.

Therefore, reproducibility claims should distinguish:

**Configuration reproducibility:** The same documented parameters and seed are used.

**Numerical reproducibility:** Outputs agree within a specified numerical tolerance.

**Bitwise reproducibility:** Output files or numerical arrays are exactly identical.

The achieved level should be reported honestly.

## 8. Relation to the Reported Result

The reported maximum spectral-error reduction of 56.44% for MA_MLII between the 200- and 500-iteration checkpoints belongs to the recorded experiment configuration.

The seed helps trace the randomized execution but does not independently validate the result.

The numerical claim should be checked against the archived raw and comparison CSV outputs.

---

**Audit principle:** A seed improves traceability; it does not replace source-code, data, environment, or output verification.
