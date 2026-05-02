# ECTI-P vs ΛCDM — Full Likelihood (CLASS + Cobaya)  
### Late-time, background-only deformation of ΛCDM (hybrid implementation)

## TL;DR

Full-likelihood (CLASS + Cobaya) FAIR comparison between ΛCDM and ECTI-P:

- Δχ² = −15.69 (MAP)  
- H₀: 70.91 vs 67.94  
- S₈: 0.812 vs 0.829  

Late-time, background-only deformation improving SN Ia fit without degrading CMB constraints.

---

## Context

This repository presents the full-likelihood (CLASS + Cobaya) implementation of the ECTI-P model.

It extends the initial background-only analysis available here:  
[ECTI-P background analysis (GitHub)](https://github.com/f-patellis/ECTI-P_vs_LCDM)

The present work tests the same late-time deformation within a full CMB likelihood framework,
using Planck 2018 TT/TE/EE data and a Boltzmann solver.

The ECTI-P model is implemented as a nested extension of ΛCDM at the background level,
allowing a direct and controlled comparison while maintaining full compatibility with standard perturbation treatments.

This choice enables robust testing within existing Boltzmann pipelines,
pending the development of a fully self-consistent perturbation framework.

---

## Key result

<p align="center">
  <img src="figures/01_corner_overlay_LCDM_vs_ECTI_FULLPROBE_200k.png" width="800">
</p>

- Improvement evaluated at maximum a posteriori (MAP)

**Δχ² = −15.69**  
**ECTI − ΛCDM, FULL PROBE, FAIR comparison**

- Same datasets, likelihoods, priors, and nuisance treatment  
- Same ΛCDM baseline parameter space  
- No early-time, recombination, or perturbation-sector modification  
- Main gain driven by SN Ia, with secondary contribution from cosmic shear  
- No significant degradation of the CMB likelihood  

---

## Interpretation of the gain

This improvement is not uniform across datasets and is dominated by late-time probes.

In particular, the gain originates primarily from the SN Ia likelihood, while BAO and RSD remain statistically consistent with ΛCDM, and the CMB likelihood is preserved.

This behavior is expected for a model that modifies only the late-time expansion history.
---

## χ² breakdown (ECTI − ΛCDM at MAP)

<p align="center">
  <img src="figures/02_delta_chi2_breakdown_MAP.png" width="600">
</p>

**Contribution to Δχ² = χ²(ECTI) − χ²(ΛCDM) evaluated at the MAP.** 

Negative values indicate an improvement of ECTI-P relative to ΛCDM.

CMB: +0.24 | SN Ia: −15.40 | BAO: +2.64 | RSD: +0.34 | Shear: −3.50

The total improvement is dominated by SN Ia, with a secondary contribution from cosmic shear,
while BAO and RSD remain consistent and the CMB likelihood is preserved.

---

## SN Ia residuals at MAP

<p align="center">
  <img src="figures/09_SN_binned_residuals_MAP.png" width="650">
</p>

**Figure — Binned Pantheon+ SN Ia residuals at the MAP for ΛCDM (blue) and ECTI-P (orange).**  
Residuals are defined as μ_obs − μ_model and binned in redshift.

This plot illustrates the origin of the SN-driven χ² improvement: ECTI-P changes the redshift-dependent residual pattern relative to ΛCDM, reducing the mismatch that dominates the total Δχ² gain.

---

## MAP summary

<p align="center">
  <img src="figures/03_MAP_summary_table.png" width="600">
</p>

**Figure — Maximum a posteriori (MAP) parameter values for ΛCDM and ECTI-P.**

Key shifts:
- Higher H₀ in ECTI-P  
- Lower Ωₘ  
- Shift toward lower S₈  

---

## H₀ – S₈ comparison

<p align="center">
  <img src="figures/04_H0_S8_MAP_comparison.png" width="500">
</p>

**Figure — Shift in the H₀–S₈ plane between ΛCDM and ECTI-P.**  
ECTI-P moves toward higher H₀ and lower S₈.

---

## Foreground / prior diagnostics

<p align="center">
  <img src="figures/05_prior_SZ_diagnostic_MAP.png" width="600">
</p>

**Figure — Contribution of priors and nuisance parameters at MAP.**  
No evidence of artificial χ² improvement driven by nuisance parameters.

---

## Model behavior

<p align="center">
  <img src="figures/06_E_ratio_vs_z.png" width="600">
</p>

**Figure — Relative modification of the expansion rate: E_ECTI / E_LCDM − 1.**  
Deviation is confined to low redshift (z ≲ 0.5).

---

<p align="center">
  <img src="figures/07_rhoDE_ratio_vs_z.png" width="600">
</p>

**Figure — Effective dark energy density deformation induced by ECTI-P.**

Effective dark energy density is reduced at low redshift, with the deviation peaking near z ≈ 0 and vanishing at higher redshift.

---

<p align="center">
  <img src="figures/08_SN_mu_difference_model_only.png" width="600">
</p>

**Figure — Induced shift in SN Ia distance modulus (model-only prediction).**  
The deformation aligns with observed SN residual structure.

---

## Model definition

The ECTI-P background expansion is defined as:

E²(z) = H(z)² / H₀²  
= Ωm (1 + z)³ + (1 − Ωm) exp[β exp(−z / zt)]

with fixed:

- β = −0.10  
- zt = 0.10  

ΛCDM is recovered exactly for β = 0.

---

## Calibration of deformation parameters

The deformation parameters (β, zt) are fixed to values calibrated from an independent background-only analysis.

This calibration is documented here:  
🔗 [ECTI-P background analysis (GitHub)](https://github.com/f-patellis/ECTI-P_vs_LCDM)

In that analysis, the parameter pair (β = −0.10, zt = 0.10) was identified as a stable minimum of the likelihood using a full late-time dataset combination.

The present work adopts these calibrated values to ensure a controlled and FAIR comparison with ΛCDM within a full-likelihood (CMB + LSS) framework.

Allowing (β, zt) to vary would introduce additional degrees of freedom and require a dedicated model selection analysis, which is beyond the scope of this study.
This separation ensures that parameter calibration and full-likelihood validation are performed independently.

---

## Implementation

- Boltzmann solver: CLASS  
- Sampler: Cobaya  
- Background: modified via ECTI-P  
- Perturbations: ΛCDM standard treatment  
- Likelihoods: Cobaya + Cosmosis bridge for COSEBIs  
- No modification to early-time physics or recombination  

---

## Data

### Planck 2018 CMB

- `planck_2018_highl_plik.TTTEEE`
- `planck_2018_lowl.TT`
- `planck_2018_lowl.EE`

Reference: Planck Collaboration VI (2020), A&A 641, A6

---

### Pantheon+ SN Ia

- Pantheon+ (2022)  
- SH0ES calibration disabled  
- Full statistical + systematic covariance  

Reference: Brout et al. (2022), ApJ 938, 110

---

### BAO (DESI 2024)

- DESI 2024 BAO distance measurements  
- Observables include D_M / r_s and H(z) · r_s  

Reference: DESI Collaboration (2024), arXiv:2404.03002

---

### RSD

- 7-point fσ₈ compilation  
- Redshift range: 0.02 ≤ z ≤ 1.52  
- Compilation of literature fσ₈ measurements (6dF, SDSS MGS, BOSS DR12, eBOSS-era)  
- Implemented as independent Gaussian constraints  

---

### Weak lensing (KiDS-1000 COSEBIs)

- KiDS-1000 COSEBIs likelihood  
- Data file: `DES-Y3_xipm_and_KiDS-1000_COSEBIs_2.0_300.0.fits`  
- Only KiDS-1000 source bins used in theoretical modeling  
- Angular range: 2′ < θ < 300′  
- COSEBIs modes: n ≤ 5  
- DES Y3 data present in file but not used in this run  

Reference: Asgari et al. (2021), A&A 645, A104

---

## FAIR comparison

Both ΛCDM and ECTI-P use:

- identical likelihoods  
- identical datasets  
- identical priors  
- identical nuisance treatment  
- identical baseline parameter space  

The only difference is the late-time background deformation in ECTI-P.

---

## Parameter space

Baseline sampled parameters:

(H₀, ω_b, ω_cdm, n_s, A_s, τ)

Additional fitted parameter:

- M (SN absolute magnitude)

Derived parameters include:

- σ₈  
- S₈  
- Ωm  

---

## Robustness

- ECTI-P production run: 200k accepted samples  
- Independent validation run (100k samples)  
- Stable MAP region and Δχ² across runs  
- Convergence: R̂ ≈ 1.00–1.01  

---

## Limitations

- Background-only phenomenological model  
- ΛCDM perturbation sector assumed  
- Deformation parameters (β, zt) fixed from independent calibration (not marginalized in this analysis)
- No underlying fundamental theory yet  
- RSD covariance treated diagonally  
- IA and photo-z nuisance parameters fixed  
- KiDS-only modeling within a combined DES+KiDS data file  

---

## Future work

- Full DES Y3 + KiDS joint shear modeling  
- DESI clustering / RSD likelihood integration   
- Extension to a fully self-consistent perturbation framework  
- Independent external reproduction  

---

## Reproducibility

Main configuration:

`/root/ecti_planck/cosmosis2cobaya/inputs/chains/ECTI_FULLPROBE_200000_run1.updated.yaml`

All scripts, figures, and configuration files required to reproduce the analysis are included in this repository.
