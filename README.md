# Thermodynamic Model Assessment for Hydrogen-Rich Cryogenic Expansion

## Project overview

This research examines the predictive reliability of equations of state for high-pressure, hydrogen-rich gases undergoing expansion to cryogenic temperatures. It began with a discrepancy between process-simulation predictions and the observed response of a two-stage industrial turbo-expander, then developed into a systematic assessment of whether conventional process models represent the thermodynamic properties that govern cryogenic expansion.

The work separates the problem into two levels: a pure-hydrogen property benchmark, used to isolate model-form limitations before mixture effects are introduced, and a hydrogen-rich mixture assessment validated against industrial operating behaviour.

## Research problem

Conventional process equations of state can reproduce pressure-volume-temperature properties reasonably well while providing substantially weaker predictions of low-temperature caloric properties. For cryogenic expansion, errors in heat capacity, enthalpy and entropy propagate directly into the predicted isentropic temperature change, enthalpy drop, efficiency, shaft work and phase condition.

Good density agreement alone is therefore not sufficient evidence that an equation of state is reliable for hydrogen-rich turbo-expander calculations.

## Primary research question

> How reliably do conventional process-simulation equations of state represent hydrogen-rich gases during cryogenic expansion when caloric properties, rather than only volumetric properties, determine the process response?

## Supporting questions

1. Can conventional equations of state reproduce the low-temperature caloric properties of pure hydrogen?
2. If discrepancies already exist for pure hydrogen, what additional uncertainty is introduced by mixture treatment?
3. How do property-level differences propagate into outlet temperature, enthalpy drop, isentropic work, train power and phase prediction?
4. Which model features explain agreement in volumetric properties but disagreement in caloric properties?

## Research logic

```text
Industrial turbo-expander discrepancy
                |
                v
Separate equipment and mixture effects
                |
                v
Pure-H2 property benchmark
                |
                v
Compare volumetric and caloric accuracy
                |
                v
Hydrogen-rich mixture assessment
                |
                v
Validate process-level consequences
```

## Models and reference framework

The assessment considers commonly used process-simulation models, including Peng-Robinson, Soave-Redlich-Kwong, Lee-Kesler-Plöcker and BWRS, against a high-accuracy reference formulation. Comparisons cover both property-level behaviour and the propagation of thermodynamic differences through cryogenic expansion calculations.

The evaluated quantities include:

- density and compressibility factor;
- isobaric and isochoric heat capacities;
- heat-capacity ratio;
- enthalpy and entropy;
- isentropic and actual outlet temperature;
- enthalpy drop, efficiency and shaft work;
- phase-boundary and condensation predictions.

## Selected public finding

Some conventional models reproduce pure-hydrogen density to within approximately 1% of the reference formulation while still underpredicting the heat-capacity ratio by approximately 7–8% at the coldest investigated condition. This distinction demonstrates why volumetric validation alone can conceal material errors in cryogenic expansion predictions.

## Data availability and confidentiality

This project is based partly on industrial operating data, vendor information and manuscript-critical calculations. These materials are not publicly released.

Only selected, derived and anonymised results suitable for scientific verification will be included in this repository. Raw plant data, identifying equipment information, confidential vendor documentation and unpublished full datasets will remain excluded.

## Planned repository structure

```text
docs/        Research questions, methods and technical notes
data/        Selected derived or anonymised public data only
notebooks/   Reproducible analysis workflows
figures/     Publication-safe figures
src/         Reusable calculation and plotting code
```

## Project status

Ongoing independent research. Manuscript in preparation.

## Author

Abbas Rajaei
