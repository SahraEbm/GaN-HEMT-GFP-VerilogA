# GaN HEMT with Gate Field Plate Compact Model (Verilog-A)

## Overview

This repository presents a **physics-based, modular Verilog-A compact model** for **GaN High Electron Mobility Transistors (HEMTs) with Gate Field Plate (GFP) technology**, developed based on advanced EPFL-style HEMT modeling approaches.

The model is designed for **power electronics and RF/microwave circuit simulation**, incorporating intrinsic device physics, extrinsic parasitics, and multiple second-order effects required for predictive accuracy.

---

## Key Features

The proposed HEMT compact model includes a complete set of electro-thermal and high-field physical effects:

### Intrinsic Channel Physics

* Charge-based channel current formulation
* Velocity saturation effects
* Bias-dependent transconductance
* Output conductance modulation

### Gate Field Plate (GFP) Effects

* Field redistribution under gate extension
* Suppression of peak electric field
* Improved breakdown voltage modeling
* Enhanced drain-side electrostatics

### Secondary Physical Effects

* Self-heating (thermal RC network)
* Charge trapping / current collapse
* Buffer leakage and high-field tunneling
* Nonlinear capacitances (Cgs, Cgd, Cgb)
* Fringing capacitances (Guildenblatt-based formulation)

### Extrinsic Parasitics

* Geometry-dependent source/drain resistances
* Temperature-dependent resistance scaling
* Gate resistance (RF mode support)
* Bias-independent overlap capacitances

---

## Model Architecture

The model is implemented in a **modular Verilog-A structure**, allowing independent calibration of each physical mechanism.

```text
GaN-HEMT-GFP-Model/
│
├── src/
│   ├── hemt_core_channel.va
│   ├── hemt_gate_field_plate.va
│   ├── hemt_self_heating.va
│   ├── hemt_trapping_current_collapse.va
│   ├── hemt_gidl_gisl_leakage.va
│   ├── hemt_fringing_capacitances.va
│   ├── hemt_extrinsic_resistances.va
│   ├── hemt_overlap_capacitances.va
│   └── hemt_top.va
│
├── testbenches/
│   ├── dc_iv_simulation.va
│   ├── cv_characterization.va
│   ├── pulsed_iv_simulation.va
│   └── rf_s_parameters.va
│
├── python/
│   ├── parameter_extraction.py
│   ├── model_validation.py
│   └── fit_trapping_model.py
│
├── docs/
│   ├── parameter_extraction_guide.md
│   ├── model_theory.pdf
│   └── figures/
│
├── LICENSE
├── CITATION.cff
└── README.md
```

---

## Simulator Compatibility

The model is compatible with major Verilog-A supported simulators:

* Cadence Spectre
* Keysight ADS
* Synopsys PrimeSim / HSPICE (Verilog-A flow)
* Xyce
* SIMetrix / SIMPLIS (depending on Verilog-A support)

---

## Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/SahraEbm/GaN-HEMT-GFP-Model.git
cd GaN-HEMT-GFP-Model
```

### 2. Include Top-Level Model

```verilog
`include "hemt_top.va"
```
---

## Physical Modeling Approach

This compact model follows a **physics-based framework**:

* Charge-based intrinsic channel formulation
* Field-plate electrostatic modulation
* Temperature-dependent mobility and resistance scaling
* Trap-assisted tunneling and dynamic recovery
* Self-heating impacts
---

## Parameter Extraction Methodology

Model parameters are extracted using a **hierarchical fitting strategy**:

### 1. DC Characterization

* pinchoff voltage
* Mobility parameters
* Channel conductance

### 2. Pulsed I–V Measurements

* Trapping time constants
* Current collapse parameters

### 3. C–V Characterization

* Intrinsic capacitances (Cgs, Cgd, Cgb)
* Fringing capacitance coefficients

### 4. Thermal Characterization

* Thermal resistance (Rth)
* Thermal capacitance (Cth)

### 5. Leakage Extraction

* High-field tunneling parameters

### 6. Parasitic Extraction

* Source/drain resistances (RS, RD)
* Overlap capacitances

---

## Gate Field Plate Modeling (Key Innovation)

The Gate Field Plate (GFP) is modeled as:

* A modification of surface potential distribution
* A reduction of peak electric field at drain-side junction
* A stabilization factor for breakdown voltage
* A bias-dependent electrostatic smoothing term

This enables accurate prediction of:

* Breakdown voltage enhancement
* Reduced kink effect
* Improved RF linearity

---

## Validation Targets

The model is validated against:

* DC output characteristics (I–V)
* Transfer characteristics (Id–Vg)
* Capacitance–voltage (C–V)
* Pulsed I–V (dynamic effects)
* RF S-parameters (small-signal model)
* Breakdown behavior


## Python Workflow (Recommended)

This repository includes a Python-based calibration framework:

```bash
python parameter_extraction.py
python model_validation.py
```

Capabilities:

* Nonlinear least squares fitting
* Multi-objective parameter optimization
* Trapping and thermal parameter extraction
* Automated comparison with measured data

---

## Example Applications

* Power converters (DC–DC, inverters)
* RF power amplifiers
* 5G/6G RF front-end design
* Reliability and lifetime studies
* Device optimization and technology benchmarking

---

## Citation

If you use this model in academic work, please cite:

> GaN HEMT with Gate Field Plate Compact Model in Verilog-A
> AUT & EPFL Research Collaboration, 2026.

---

## License

This project is released under the **MIT License**.

See `LICENSE` file for details.

---

## Authors

* Sahra Ebrahimmagham (Researcher, AUT)
* Dr. Majid Shalchian (Assistant Professor, AUT)
* Dr. Farzan Jazaeri (Researcher, EPFL)

Affiliations:

* Amirkabir University of Technology (AUT)
* École Polytechnique Fédérale de Lausanne (EPFL)

---

## Acknowledgments

This work is inspired by advanced EPFL-style GaN HEMT compact modeling methodologies and academic research in wide-bandgap semiconductor device modeling.

---

## Contact

For questions, collaboration, or industrial licensing:

* GitHub: `SahraEbm`
* Email: `sahra.ebm@gmail.com`
