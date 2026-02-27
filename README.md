# EV Charging DCE (Ngene + Biogeme) for Gothenburg, Sweden

This repository contains the experimental design (Ngene) and discrete choice model estimation (Biogeme) used to quantify EV users’ charging preferences and willingness-to-pay (WTP) for charging service attributes in Gothenburg/Sweden.

The project focuses on two main decision contexts:
- **Daily/commute charging** (urban AC/work/public-type context)
- **Long-trip en-route charging** (highway DC/HPC context)

The codebase supports:
1) generating D-efficient (or Bayesian D-efficient) choice designs in **Ngene**, with realism constraints;
2) preparing DCE response, including long-to-wide reshaping when required);
3) estimating baseline **Multinomial Logit (MNL)** models in **Biogeme**, and extensions (pooled models with context interactions; potential multi-class / latent-class workflows).

---

## Repository structure

- `ngene/`  
  Ngene design scripts for:
  - urban/commute choice tasks
  - long-trip tasks (amenities and/or detour variants)

- `notebooks/`  
  Biogeme estimation notebooks (baseline MNL; pooled specifications; scenario splits).

- `models/`  
  Helper scripts:
  - `biogeme/` Biogeme Model, cleaning, coding checks
  - `ngene/`  Ngene model specs

- `data/`
  - `data/example/` small, de-identified example dataset for reproducibility
  - `data/processed/` cleaned/analysis-ready data (tracked only if non-sensitive)

- `outputs/` (NOT tracked)
  Estimation outputs and exported tables.

---

## Data format (important)

Biogeme estimation is run on a **choice-situation (wide) table**:
- one row per respondent × choice task,
- alternative-specific columns (`price_A`, `price_B`, `price_C`, ...),
- a single `CHOICE` column storing the chosen alternative index.

---

## Installation

Recommended: Python 3.9+.

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
