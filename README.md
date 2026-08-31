# Thermodynamic Model Assessment for Hydrogen-Rich Cryogenic Expansion

## Overview

This project investigates the reliability of thermodynamic models for **hydrogen-rich gas expansion at cryogenic conditions**, using an industrial two-stage turbo-expander as the engineering validation case.

The work originated from a practical modelling discrepancy. During analysis of a hydrogen-rich cryogenic expansion train, the process simulation and the actual machine did not always predict the same thermodynamic behaviour. What initially began as an attempt to understand an equipment-model mismatch developed into a broader investigation of how conventional equations of state represent hydrogen at low temperature.

The central finding motivating this work is that an equation of state can reproduce volumetric properties such as density and compressibility reasonably well while still showing significantly larger errors in the **caloric properties that directly govern expansion**, including:

- heat capacity at constant pressure, $C_p$
- heat capacity at constant volume, $C_v$
- heat-capacity ratio, $\gamma = C_p/C_v$
- enthalpy
- entropy
- isentropic enthalpy change

These differences can propagate into predicted outlet temperature, expander work, recovered shaft power, and phase behaviour.

---

## Research Problem

Cryogenic turbo-expander calculations depend fundamentally on the thermodynamic path followed by the gas.

For an idealised isentropic expansion:

$$
s_{2s} = s_1
$$

and the corresponding isentropic enthalpy change is:

$$
\Delta h_{\mathrm{is}} = h_1 - h_{2s}
$$

The actual expansion is related to the isentropic state through the expander efficiency:

$$
\eta_{\mathrm{is}}
= \frac{h_1-h_2}{h_1-h_{2s}}
= \frac{\Delta h_{\mathrm{actual}}}{\Delta h_{\mathrm{is}}}
$$

and shaft power follows from:

$$
\dot{W}_{\mathrm{shaft}} = \dot{m}\left(h_1-h_2\right)
$$

The shaft-power expression assumes steady, adiabatic operation with negligible changes in kinetic and potential energy between the selected inlet and outlet states.

Accurate prediction therefore requires more than satisfactory pressure-volume-temperature behaviour.

An EOS that predicts density accurately can still provide an inaccurate entropy or enthalpy surface and consequently produce an incorrect expansion trajectory.

This leads to the primary research question:

> **How reliably do conventional process-simulation equations of state represent the thermodynamic behaviour of hydrogen-rich gases during cryogenic expansion when caloric properties, rather than only volumetric properties, determine the process response?**

---

## How the Research Question Emerged

The project did not begin as a general EOS comparison.

It began with an industrial observation:

```text
Industrial turbo-expander
        │
        ▼
Simulation and machine behaviour
did not completely agree
        │
        ▼
Was the difference caused by:
equipment performance,
mixture modelling,
or thermodynamic properties?
        │
        ▼
Remove mixture complexity
        │
        ▼
Benchmark pure hydrogen
        │
        ▼
Volumetric properties:
often good agreement

Caloric properties:
increasing disagreement
as temperature decreases
        │
        ▼
Return to hydrogen-rich mixture
        │
        ▼
Assess consequences for
temperature, enthalpy,
power and phase behaviour

```

A key step was therefore to remove the multicomponent mixture entirely and examine **pure hydrogen**.

This eliminates:

- binary interaction coefficients
- mixing-rule effects
- uncertainty associated with mixture composition
- cross-component departure functions

If a discrepancy remains for pure hydrogen, mixture modelling cannot be its only cause.

---

## Research Questions

### RQ1 — Pure Hydrogen

**Can conventional equations of state accurately represent the low-temperature caloric properties of pure hydrogen?**

This provides the fundamental thermodynamic benchmark.

---

### RQ2 — Volumetric vs Caloric Accuracy

**Does accurate prediction of density or compressibility imply accurate prediction of $C_p$, $C_v$, enthalpy, entropy, or $C_p/C_v$?**

The results indicate that these two forms of accuracy should not be treated as equivalent.

---

### RQ3 — Hydrogen-Rich Mixtures

**How do the limitations identified for pure hydrogen combine with mixture-model assumptions when hydrogen becomes the dominant component of a multicomponent gas?**

This introduces additional effects including:

- binary interaction parameters
- mixing rules
- departure functions
- composition-dependent phase behaviour

---

### RQ4 — Cryogenic Expansion

**How do thermodynamic-model differences propagate into the predicted performance of a real cryogenic expansion process?**

The investigated outputs include:

- outlet temperature, $T_{\mathrm{out}}$
- isentropic enthalpy drop, $\Delta h_{\mathrm{is}}$
- isentropic efficiency, $\eta_{\mathrm{is}}$
- recovered shaft power, $\dot{W}_{\mathrm{shaft}}$

and predicted phase state.

---

## Thermodynamic Models Investigated

The study compares several thermodynamic approaches commonly available for process simulation:

- Peng–Robinson (PR)
- Soave–Redlich–Kwong (SRK)
- Lee–Kesler–Plöcker (LKP)
- Benedict–Webb–Rubin–Starling (BWRS)
- hydrogen-specific process-simulation models
- NIST REFPROP-based property calculations

The objective is not simply to rank the models.

The more important objective is to determine **which thermodynamic properties cause their predictions to diverge and under what conditions those differences become relevant to engineering calculations**.

---

## Pure-Hydrogen Benchmark

The pure-H₂ comparison is used as an isolation experiment.

Representative cryogenic states from the expansion study are evaluated without any mixture effects.

One of the clearest observations concerns:

$$
\gamma = \frac{C_p}{C_v}
$$

The reference-quality hydrogen calculation predicts a pronounced increase in $\gamma$ as temperature decreases.

Representative values are approximately:

| Temperature | REFPROP $\gamma$ | PR | SRK |
|---:|---:|---:|---:|
| −104.2 °C | 1.489 | 1.447 | 1.434 |
| −127.9 °C | 1.516 | 1.443 | 1.434 |
| −151.0 °C | 1.553 | 1.439 | 1.434 |

At the coldest investigated condition, several conventional EOS underpredict $C_p/C_v$ by approximately **7–8%** relative to the reference calculation.

The error therefore increases as the system enters deeper cryogenic conditions.

---

## A Key Finding: Volumetric Accuracy Does Not Guarantee Caloric Accuracy

One of the most important observations from the study is that some models reproduce pure-hydrogen density extremely well while showing much larger caloric-property errors.

For example, BWRS and LKP can reproduce pure-H₂ density to approximately the **sub-1% level**, with some investigated states showing deviations of only a few hundredths of a percent.

At the same states, however, the error in:

$$
\gamma = \frac{C_p}{C_v}
$$

can approach:

$$
7\text{–}8\%
$$

at the lowest temperature.

This leads to an important modelling principle:

$$
\boxed{
\text{Accurate } \rho \text{ or } Z
\;\not\Rightarrow\;
\text{accurate } C_p,\,C_v,\,h,\,s,\,\gamma
}
$$

This distinction is particularly important for expansion processes because their calculated performance depends primarily on enthalpy and entropy rather than density alone.

---

## Why This Matters for a Turbo-Expander

A turbo-expander converts a thermodynamic enthalpy decrease into shaft work while producing refrigeration.

The predicted outlet state therefore depends on the calculated entropy and enthalpy surfaces.

A simplified propagation path is:

```text
Equation of state
      ↓
Cp, Cv, h, s
      ↓
Isentropic outlet state
      ↓
Δh_isentropic
      ↓
Actual outlet temperature
      ↓
Recovered shaft power

```

Consequently, relatively modest thermodynamic-property differences can become measurable differences in predicted equipment performance.

---

## Industrial Validation

The second part of the study evaluates a **hydrogen-rich multicomponent gas undergoing two-stage cryogenic expansion**.

The industrial system is used as a validation platform rather than being the sole subject of the research.

Multiple operating conditions are considered to distinguish:

- temperature-dependent thermodynamic effects
- load-dependent machine effects
- EOS-dependent property predictions
- potential phase-boundary effects

The comparison includes conventional process EOS, reference-quality property calculations, vendor information where available, and operating data.

Detailed industrial operating data are intentionally not included in this repository.

---

## Selected Industrial Observations

The full dataset is reserved for the associated manuscript, but several general trends can be reported.

Conventional EOS show a systematic tendency to predict warmer outlet temperatures than those observed at the colder stages of the expansion.

The disagreement becomes more pronounced in the deeper cryogenic region.

At normal and high-load operation, similar model errors are observed despite differences in throughput, suggesting that **thermodynamic state is an important driver of the discrepancy rather than flow rate alone**.

The thermodynamic-model differences also propagate into:

- predicted enthalpy drop
- isentropic work
- recovered shaft power
- predicted proximity to the phase boundary

---

## Hydrogen-Rich Mixture Modelling

The mixture problem introduces an additional level of complexity.

Conventional process EOS commonly represent mixture interactions using relatively simple mixing rules and fixed binary interaction parameters.

Reference-quality formulations can employ more detailed binary departure functions for well-characterised component pairs, including temperature- and density-dependent behaviour.

The industrial research therefore examines two different sources of error:

```text
Pure-component hydrogen representation
                +
Mixture interaction representation
                ↓
Hydrogen-rich cryogenic prediction

```

The pure-H₂ benchmark is important because it demonstrates that not all disagreement can automatically be attributed to binary interaction parameters.

---

## Ortho/Para Hydrogen Considerations

Hydrogen presents an additional modelling issue because its thermodynamic properties depend on its nuclear-spin composition.

Hydrogen may be represented as:

- normal hydrogen
- para-hydrogen
- equilibrium hydrogen

The distinction becomes increasingly important at cryogenic temperatures.

For rapid turbo-expansion without a conversion catalyst, the hydrogen spin composition may not have sufficient time to reach instantaneous equilibrium.

The appropriate treatment therefore depends on conversion kinetics as well as thermodynamic equilibrium.

This remains an important consideration in interpreting hydrogen-specific property packages and low-temperature hydrogen calculations.

---

## Research Strategy

The overall validation strategy is:

```text
1. Industrial observation
          ↓
2. Identify possible thermodynamic origin
          ↓
3. Remove mixture effects
          ↓
4. Benchmark pure hydrogen
          ↓
5. Separate volumetric and caloric accuracy
          ↓
6. Evaluate hydrogen-rich mixture behaviour
          ↓
7. Propagate property differences through
   cryogenic expansion calculations
          ↓
8. Compare against industrial behaviour
          ↓
9. Assess temperature, enthalpy,
   power and phase prediction

```

---

## Repository Scope

This repository is intended to document:

- the research problem
- thermodynamic reasoning
- validation methodology
- selected pure-hydrogen benchmarks
- selected anonymised results
- analysis code suitable for non-proprietary examples

It is **not** intended to provide the complete unpublished research dataset.

---

## Data Availability

The study uses industrial operating data, equipment information, process composition data, vendor information, and detailed simulation results.

These datasets are subject to confidentiality and publication restrictions and are therefore not publicly released.

The repository will contain only:

- selected pure-component benchmark data
- anonymised or normalised results
- demonstration datasets
- calculation methodology
- reusable analysis code

Raw industrial data and manuscript-critical datasets are excluded from version control.

---

## Repository Structure

```text
hydrogen-rich-cryogenic-expansion/
│
├── README.md
│
├── docs/
│   ├── research_problem.md
│   ├── validation_strategy.md
│   ├── thermodynamic_models.md
│   └── data_availability.md
│
├── data/
│   ├── public/
│   └── templates/
│
├── notebooks/
│   ├── 01_pure_h2_benchmark.ipynb
│   ├── 02_volumetric_vs_caloric_accuracy.ipynb
│   ├── 03_ortho_para_sensitivity.ipynb
│   ├── 04_isentropic_expansion_physics.ipynb
│   └── 05_anonymised_industrial_validation.ipynb
│
├── src/
│   ├── thermodynamic_metrics.py
│   ├── expander_analysis.py
│   └── error_metrics.py
│
├── figures/
│
└── results/

```

---

## Current Status

Research ongoing.

The complete industrial analysis is being prepared for publication.

Results included in this repository should therefore be regarded as selected supporting material rather than the complete manuscript dataset.

---

## Main Research Message

The central conclusion motivating this work is:

> **The suitability of an equation of state for hydrogen-rich cryogenic expansion cannot be judged from density or compressibility accuracy alone. Models capable of reproducing hydrogen volumetric behaviour can still exhibit substantially larger errors in low-temperature caloric properties, and these differences can propagate directly into predicted expansion temperature, enthalpy change, shaft work, power recovery, and phase behaviour.**

The turbo-expander is therefore used as the industrial validation platform.

The broader research problem is the **thermodynamic reliability of hydrogen-rich mixtures undergoing deep cryogenic expansion**.
