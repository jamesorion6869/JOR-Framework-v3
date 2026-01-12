# JOR Framework v3 — Bayesian UAP Triage Tool

## Overview

This repository contains the reference implementation of the James Orion Report (JOR) Bayesian Fusion Framework, a structured probabilistic system for evaluating UAP cases.

The framework separates:

- **Solid Object Probability (SOP)**
- **Non-Human Probability (NHP)** (conditional on SOP)

This separation prevents conflation of anomalous observations with unsupported origin claims.

---

## Intended Use

- Government and institutional triage
- Historical case reevaluation
- Research into technological surprise detection
- Internal analytic consistency checks

**Note:** This tool is not designed to assert extraterrestrial origin.

---

## Requirements

All dependencies are FIPS-compliant and MIT licensed
- Python 3.10 or higher
- numpy>=1.25,<2 
- pymc>=5.15,<6 # Apache-2, FIPS-safe, no GPL deps
- arviz>=0.15,<1
- matplotlib>=3.8,<4 (optional, for visualization)

---

## Installation

To install the required Python packages, run:

```bash
pip install pymc arviz matplotlib
```

---

## Running the Script

Run the interactive script from the project directory:

```bash
python jor_fusion.py
```

The script will prompt for rubric-based scoring inputs, including:

- Witness credibility
- Environmental conditions
- Physical/sensor evidence
- Prior skepticism setting (K-constant)

Manual override is available: the user can skip full scoring and enter SOP and NHP directly if desired.

---

## Output

The script produces:

- Posterior SOP
- Posterior NHP
- Optional CSV export for record-keeping or comparative analysis
- Optional visualization comparing prior vs posterior probabilities

---

## Interpretation Guidance

- SOP must be evaluated first as an evidentiary foundation
- NHP should never be interpreted independently of SOP
- Posterior NHP is a conditional risk indicator, not an origin claim
- Users may refer to the JOR Framework v3 Organizational User Manual for full triage guidance

---

## Organizational Triage Notes (Optional)

- Posterior NHP 0.00 – 0.25: Low priority, likely conventional explanation
- Posterior NHP 0.26 – 0.45: Monitor, anomalous, cross-reference with historical or sensor data
- Posterior NHP 0.46 – 0.56: Priority, active investigation recommended

---

## Conservative vs Exploratory Use Modes

- **Standard reporting mode:** PRIOR_NH = 0.20, K = 0.20, for public-facing or institutional reports
- **Exploratory/R&D mode:** lower PRIOR_NH or K may be used for internal testing and sensitivity analysis

---

## Citation

If using this tool in research or analysis, please cite the associated JOR Fusion Paper (v3) on Zenodo.




