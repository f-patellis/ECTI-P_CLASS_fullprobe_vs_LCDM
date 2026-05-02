### ECTI-P (CLASS Full-Likelihood) vs ΛCDM

Full likelihood cosmological analysis of a late-time, background-only extension of ΛCDM.

---

## Overview

This repository presents a full cosmological comparison between:

- ΛCDM (reference model)
- ECTI-P (late-time phenomenological extension)

using:

- Planck 2018 TT/TE/EE (full likelihood)
- Pantheon+ SN Ia
- DESI 2024 BAO
- RSD data
- KiDS-1000

---

## Model

The ECTI-P model modifies the late-time expansion history:

E²(z) = Ωm(1+z)³ + (1−Ωm) exp[β exp(−z/zt)]

with:

- β = −0.10
- zt = 0.10

ΛCDM is recovered for β = 0.

---

## Implementation

- Background: modified via ECTI-P
- Perturbations: ΛCDM (standard CLASS treatment)
- No modification to early-time physics or recombination

---

## Status

- Full likelihood pipeline implemented (CLASS + Cobaya)
- Production runs completed
- Consolidation runs in progress

---

More results and figures will be added.
