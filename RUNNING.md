# Running / Reproducibility Notes

This repository documents the full-likelihood ECTI-P vs ΛCDM analysis using CLASS + Cobaya.

The complete production chains, covariance matrices, logs, configuration files, and modified CLASS background implementation are archived on Zenodo:

https://doi.org/10.5281/zenodo.19983709

---

## Scope

This repository is intended to document and verify the reported results.

It is **not a one-click reproducibility package**.

Full reproduction requires a working local installation of:

- CLASS
- Cobaya
- Planck 2018 likelihoods
- CosmoSIS / cosmosis2cobaya components (for KiDS-1000 COSEBIs)

---

## ECTI-P implementation

ECTI-P is implemented as a modified CLASS background.

The modified CLASS directory used for the production run is included in the Zenodo archive:

    class_mod/classy_ecti_bgonly/

The implementation modifies the background expansion history only.

The perturbation sector is kept in the standard ΛCDM treatment.

---

## Configuration files

The main Cobaya configuration files are provided in the Zenodo archive.

Reference configuration:

    config/ECTI_FULLPROBE_200000_run1.updated.yaml

The `.updated.yaml` files are exact outputs from the production environment.

⚠️ Some paths are machine-specific and must be adapted before rerunning, e.g.:

    /root/ecti_planck/

---

## Data and likelihoods

The analysis uses:

- Planck 2018 TTTEEE + low-ℓ TT/EE likelihoods
- Pantheon+ SN Ia (SH0ES disabled)
- DESI 2024 BAO
- RSD fσ8 compilation
- KiDS-1000 COSEBIs via CosmoSIS/cosmosis2cobaya

External likelihood data must be installed separately where required.

---

## Verification from chains

Primary reproducibility route: **verification from MCMC chains**.

Zenodo archive contains:

    chains/
    config/
    figures/
    logs/
    class_mod/
    README_ZENODO.txt

These allow independent verification of:

- posterior distributions
- MAP values
- χ² breakdown
- Δχ² comparison
- H₀ and S₈ shifts

---

## Important limitation

Due to the combined CLASS + Cobaya + Planck + CosmoSIS pipeline,
full one-click reproducibility is not guaranteed.

The archive provides all necessary outputs and configurations
to reproduce the analysis within a properly configured environment.
