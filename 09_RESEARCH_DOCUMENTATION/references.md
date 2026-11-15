
# Research References
## Academic Literature, Signal Processing, and Dataset Provenance

**Project:** D³ VITAL-X Astronaut Health Monitor  
**Research Track:** Global Event — Research Engine Framework

---

## 1. Purpose

This document consolidates the principal methodological and dataset-reference records relevant to the D³ VITAL-X research framework.

References are included to support methodological context, reproducibility, and responsible interpretation.

A cited publication must not be interpreted as independently validating a D³ VITAL-X result unless that publication directly evaluates the same method, dataset, implementation, and experimental claim.

## 2. IAAFT and Surrogate-Data Methodology

### [1] Improved Surrogate Data for Nonlinearity Tests

Schreiber, T., & Schmitz, A. (1996). Improved surrogate data for nonlinearity tests. *Physical Review Letters, 77*(4), 635–638.

https://doi.org/10.1103/PhysRevLett.77.635

**Relevance:** Foundational publication describing an iterative surrogate-generation approach designed to preserve the amplitude distribution and autocorrelation-related structure of a time series.

### [2] Surrogate Time Series

Schreiber, T., & Schmitz, A. (2000). Surrogate time series. *Physica D: Nonlinear Phenomena, 142*(3–4), 346–382.

https://doi.org/10.1016/S0167-2789(00)00043-9

**Relevance:** Review of surrogate time-series methods, methodological considerations, and interpretational limitations.

### [3] Testing for Nonlinearity in Time Series: The Method of Surrogate Data

Theiler, J., Eubank, S., Longtin, A., Galdrikian, B., & Farmer, J. D. (1992). Testing for nonlinearity in time series: The method of surrogate data. *Physica D: Nonlinear Phenomena, 58*(1–4), 77–94.

https://doi.org/10.1016/0167-2789(92)90102-S

**Relevance:** Foundational framework for surrogate-data testing and the interpretation of surrogate comparisons under explicitly stated null hypotheses.

## 3. Biomedical Signal Data Resources

### [4] PhysioBank, PhysioToolkit, and PhysioNet

Goldberger, A. L., Amaral, L. A. N., Glass, L., Hausdorff, J. M., Ivanov, P. Ch., Mark, R. G., Mietus, J. E., Moody, G. B., Peng, C.-K., & Stanley, H. E. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals. *Circulation, 101*(23), e215–e220.

https://doi.org/10.1161/01.CIR.101.23.e215

**Relevance:** Description of the PhysioNet research resource for physiological signal data and related tools.

**Dataset attribution note:** This citation is relevant only if the actual experiment input was obtained from PhysioNet or a dataset hosted by that resource. It does not, by itself, identify the exact source of the 80,000-row ECG input used in the D³ VITAL-X experiment.

### [5] The Impact of the MIT-BIH Arrhythmia Database

Moody, G. B., & Mark, R. G. (2001). The impact of the MIT-BIH Arrhythmia Database. *IEEE Engineering in Medicine and Biology Magazine, 20*(3), 45–50.

https://doi.org/10.1109/51.932724

**Relevance:** Historical and technical context for the MIT-BIH Arrhythmia Database.

**Dataset attribution note:** Cite this work as a dataset-specific reference only if the experiment's source records are confirmed to originate from the MIT-BIH Arrhythmia Database.

## 4. Dataset Provenance and Citation Requirements

The exact dataset used in the extended IAAFT experiment must be identified from its original download record, source documentation, or archived provenance metadata.

Before assigning a definitive dataset citation, record:

- Dataset title.
- Dataset owner or contributing institution.
- Repository or archive.
- DOI, accession, or stable dataset URL.
- Dataset version or release.
- Download or access date.
- Original record identifiers, where permitted.
- Sampling frequency and units.
- Channel names and definitions.
- Applicable license and usage conditions.
- Any preprocessing or selection performed by the research team.

Do not identify the dataset as MIT-BIH, PhysioNet, or another named benchmark solely because it contains ECG signals or familiar channel labels.

## 5. D³ VITAL-X Experimental Result Citation

The extended IAAFT Test 02B configuration is documented in this repository.

Recorded configuration:

- 80,000 ECG rows.
- 6 channels.
- 10 replicates per channel.
- 60 total trajectories.
- Iteration checkpoints: 200, 300, 400, and 500.
- Random seed: `20261114`.

The reported maximum spectral-error reduction is 56.44% for the MA_MLII channel between the 200- and 500-iteration checkpoints.

This is a D³ VITAL-X experiment-specific computational observation. It is not a result reported by the external references listed above.

The claim should be linked to the actual experiment outputs and recalculated from the archived raw and comparison CSV files before being treated as independently verified.

## 6. Citation and Research Integrity Policy

All research documentation should distinguish:

1. External published methodology.
2. External dataset descriptions.
3. D³ VITAL-X experiment configurations.
4. D³ VITAL-X computational results.
5. Team interpretations and hypotheses.
6. Planned but not yet implemented work.

A methodological reference does not automatically validate an implementation.

A dataset citation does not automatically establish that the dataset was used correctly.

A computational result does not automatically establish clinical or operational validity.

## 7. Scientific and Clinical Disclaimer

IAAFT surrogate spectral matching evaluates computational agreement under a selected spectral-error measure.

The reported 56.44% reduction for MA_MLII is not:

- Clinical accuracy.
- Diagnostic sensitivity or specificity.
- Medical prediction accuracy.
- Evidence of improved patient outcomes.
- Proof of astronaut-specific health-monitoring capability.
- Flight-safety certification.

The D³ VITAL-X Global Event repository documents a research and computational prototype.

It does not claim to be a certified medical device or a validated clinical decision-support system.

## 8. Reference Maintenance

When new publications or datasets are added:

- Verify bibliographic details against the publisher or DOI record.
- Include stable identifiers.
- Preserve dataset-specific citation instructions.
- Record access dates for mutable online resources.
- Avoid citing sources that were not actually used.
- Update related methodology and provenance documents when necessary.

---

**Research integrity statement:** Cite the source of a method, identify the source of a dataset, and report the team's own results separately.
