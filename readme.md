# JOR Framework v3 — Bayesian UAP Triage Tool

## Overview

This repository contains the reference implementation of the James Orion Report (JOR) Bayesian Fusion Framework, a structured probabilistic triage framework (SPTF) system for evaluating UAP cases.

The framework separates:

- **Solid Object Probability (SOP)**
- **Non-Human Probability (NHP)** (conditional on SOP)

This separation prevents conflation of anomalous observations with unsupported origin claims.

The repository now includes two scripts:

- **`jor_fusion.py`** — full interactive scoring interface for cases with human witnesses or sensor data  
- **`jor_sensor_default.py`** — variant that automatically assigns C = 0.30 for camera/system-only cases (minimal weak witness), with optional human witness scoring. This allows sensor-only cases to be processed while preserving the evidentiary logic of the framework.

## Intended Use

- Government and institutional triage
- Historical case reevaluation
- Research into technological surprise detection
- Internal analytic consistency checks

**Note:** This tool is not designed to assert extraterrestrial origin.

## Requirements

All dependencies are FIPS-compliant and MIT licensed
- Python 3.10 or higher
- numpy>=1.25,<2 
- pymc>=5.15,<6 # Apache-2, FIPS-safe, no GPL deps
- arviz>=0.15,<1
- matplotlib>=3.8,<4 (optional, for visualization)

## Installation

To install the required Python packages, run:

pip install pymc arviz matplotlib

## Running the Scripts

Run the interactive scripts from the project directory:

python jor_fusion.py  
python jor_sensor_default.py

**Notes:**

- `jor_fusion.py` is the full scoring interface, for cases with human witnesses or detailed sensor analysis  
- `jor_sensor_default.py` is optimized for sensor-only cases; it automatically sets **C = 0.30** for camera/system-only evidence, but allows scoring C higher if a human witness is present

The scripts will prompt for rubric-based scoring inputs, including:

- Witness credibility
- Environmental conditions
- Physical/sensor evidence
- Flight behavior modifiers
- Prior skepticism setting (K-constant)

Manual override is available: the user can skip full scoring and enter SOP and NHP directly if desired.

## Output

The scripts produce:

- Posterior SOP
- Posterior NHP
- Optional CSV export for record-keeping or comparative analysis
- Optional visualization comparing prior vs posterior probabilities

For the sensor-default script:

- The CSV logs whether a human witness was present and records key constants for reproducibility

## Interpretation Guidance

- SOP must be evaluated first as an evidentiary foundation
- NHP should never be interpreted independently of SOP
- Posterior NHP is a conditional risk indicator, not an origin claim
- Users may refer to the JOR Framework v3 Organizational User Manual for full triage guidance

Additional notes for the sensor-default variant:

- `C = 0.30` indicates camera/system-only evidence
- `C` will be higher if human witnesses are scored

## Organizational Triage Notes (Optional)

- Posterior NHP 0.00 – 0.25: Low priority, likely conventional explanation
- Posterior NHP 0.26 – 0.45: Monitor, anomalous, cross-reference with historical or sensor data
- Posterior NHP 0.46 – 0.56: Priority, active investigation recommended

## Conservative vs Exploratory Use Modes

- **Standard reporting mode:** PRIOR_NH = 0.20, K = 0.20, for public-facing or institutional reports
- **Exploratory/R&D mode:** lower PRIOR_NH or K may be used for internal testing and sensitivity analysis

## Citation

If using this tool in research or analysis, please cite the associated JOR Fusion Paper (v3) on Zenodo.


