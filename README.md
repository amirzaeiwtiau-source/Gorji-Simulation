# Gorji-Simulation
Source code for the Gorji 
# H-CSMO: Hybrid Carbon-Aware Sustainable Multi-Objective Optimization

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21699220.svg)](https://doi.org/10.5281/zenodo.21699220)
[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository contains the simulation source code, workload configurations, and verification datasets for the **H-CSMO** framework, supporting the manuscript submitted to *Scientific Reports*.

---

## 📌 Repository Structure
```text
├── code/                         # Core algorithm and simulation modules
│   ├── hcsmo_method_v2.py
│   ├── hcsmo_simulator_core.py
│   ├── hcsmo_rolling_horizon_engine_v1_1.py
│   └── hcsmo_rolling_coupled_v1_1.py
├── config/                       # Simulation and environment parameter profiles
│   └── environment_configuration_v1.json
├── inputs/                       # Processed cluster workloads and trace data
│   ├── Alibaba2017_nodes_n030_v1.csv
│   ├── alibaba_workload_n3000.csv
│   ├── Google2011v2_nodes_n030_v1.csv
│   ├── google_workload_n4000.csv
│   ├── six_region_network_matrix_v1.csv
│   ├── carbon_region_mapping_v1.csv
│   └── neso_six_region_carbon_forecast_v1.csv
├── evidence/                     # Frozen raw simulation run outputs and statistical evidence
│   ├── 140_run_level.csv         # Run-level records across 140 PASS evaluation runs
│   ├── 140_group_reference.csv   # Aggregated baseline reference metrics
│   ├── 140_pareto_nondominated.csv
│   ├── 140_wilcoxon_holm.csv     # Non-parametric hypothesis testing with Holm adjustment
│   ├── 140_integrity.json
│   └── 62_followup_index_derived.csv
├── tools/                        # Reproduction and validation utilities
│   └── rebuild_ablation_from_frozen_runs.py
├── RELEASE_STATUS.json           # Integrity status and component metadata
├── SHA256SUMS                    # Checksums for all archived assets
└── README.md                     # Project documentation

---

## ⚙️ Prerequisites & Environment Setup

The verification tools and core simulation routines require **Python 3.9+** and rely exclusively on Python standard libraries or standard scientific packages.

bash
# Clone the repository
git clone https://github.com/Abbas-Mirzaei/AIT2-FRL-Simulation.git
cd AIT2-FRL-Simulation

# Verify file integrity using SHA-256
sha256sum -c SHA256SUMS

---

## 🔬 Reproducibility & Verification

To verify the frozen 140-run statistical ablation study and reconstruct the summary tables from run-level execution records:

bash
python3 tools/rebuild_ablation_from_frozen_runs.py --out reconstructed_ablation.csv

### What this tool does:
1. Loads the 140 complete evaluation records (`evidence/140_run_level.csv`) across Alibaba and Google workload profiles with 10 random seeds per configuration.
2. Computes sample mean, sample standard deviation ($SD$), and key multi-objective trade-offs across 8 performance metrics (carbon emission, makespan, energy, fairness, and reliability).
3. Compares reconstructed values against `evidence/140_group_reference.csv` to confirm statistical exactness.

---

## 📊 Dataset & Workload References

- **Google Cluster Trace (2011v2):** Sampled task-level resource demands mapped across heterogeneous node structures (`inputs/google_workload_n4000.csv`).
- **Alibaba Cluster Trace (2017):** Batch workload arrival profiles with multi-tier execution requirements (`inputs/alibaba_workload_n3000.csv`).
- **Grid Carbon Intensity:** Regional grid emissions forecast profiles derived from National Energy System Operator (NESO) datasets (`inputs/neso_six_region_carbon_forecast_v1.csv`).

---

## 📝 Citation

If you use this codebase or the provided data in your research, please cite:

bibtex
@article{mirzaei2026hcsmo,
  title   = {H-CSMO: Hybrid Carbon-Aware Sustainable Multi-Objective Optimization for Geo-Distributed Cloud Workloads},
  author  = {Mirzaei, Abbas and Alimorad, Mohammad},
  journal = {Scientific Reports},
  year    = {2026},
  doi     = {10.5281/zenodo.21699220}
}

---

## 📄 License
This project is made available under the [MIT License](LICENSE).


---

