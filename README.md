# Band-to-Band Tunneling in SOI MOSFETs

Optimization of BTBT current in Partially-Depleted and Fully-Depleted SOI MOSFETs for neuromorphic computing applications using Synopsys Sentaurus TCAD.

## 📋 Project Overview

This project analyzes Band-to-Band Tunneling (BTBT) in Silicon-On-Insulator (SOI) MOSFETs to optimize device parameters for ultra-low power neuromorphic hardware implementations. The study focuses on both minimizing and maximizing BTBT current for different applications in Spiking Neural Networks (SNNs).

**Course:** EE724 - Nanoelectronics (Spring 2024)
**Instructor:** Prof. Udayan Ganguly
**Institution:** Indian Institute of Technology Bombay

**Award:** 🏆 Best Project Award

## 👥 Team Members

- **Abhineet Agarwal**
- **Harsh Pujare**

**Mentor:** Jay Sonawane

## 🎯 Motivation

Neuromorphic computing architectures based on Spiking Neural Networks (SNNs) require energy-efficient and compact hardware neurons for large-scale deployment. Band-to-Band Tunneling in SOI MOSFETs offers a pathway to achieve ultra-low power operation compared to conventional CMOS implementations. This project addresses:

- **Energy Efficiency:** Minimizing BTBT current reduces power consumption, enabling large-scale SNN implementations
- **Performance Optimization:** Maximizing BTBT current enables faster charging speeds for improved device bandwidth
- **Scalability:** Understanding the effects of gate length scaling on BTBT characteristics
- **Temperature Robustness:** Analyzing temperature dependence of tunneling currents for reliable operation

## 🔬 Technical Approach

### Phase 1: BTBT Integrator (32nm PD-SOI)

**Objective:** Minimize BTBT current for ultra-low power neural integrators

**Device Specifications:**
- Gate Length (L_G): 40 nm
- Channel Height (H_CH): 40 nm
- Buried Oxide Thickness (H_BOX): 100 nm
- Channel Doping (N_CH): 6.4×10¹⁷ cm⁻³
- Source/Drain Doping (N_SD): 1×10²⁰ cm⁻³

**Design Space Analysis:**
- Varied H_CH, H_BOX, H_SUB, L_OV, T_OX, N_CH, and N_SD
- Used Nonlocal Path (NLP) BTBT model in Sentaurus TCAD
- Characterized using Agilent B1500 Semiconductor Parameter Analyzer

### Phase 2: BTBT Inverter (22nm FD-SOI)

**Objective:** Maximize BTBT current for fast switching inverters

**Device Specifications:**
- Gate Length (L_G): 25 nm
- Channel Height (H_CH): 8 nm
- Buried Oxide Thickness (H_BOX): 20 nm
- Channel Doping (N_CH): 1×10¹² cm⁻³ (base design)
- Overlap Length (L_OV): 1 nm (base design)

**Optimization Focus:**
- Drain-Gate overlap length (L_OV)
- Channel doping concentration (N_CH)
- Temperature variability analysis (300 K - 398 K)
- Gate length scaling effects (32nm → 22nm)

## 📊 Key Results

### Phase 1: Minimizing BTBT Current

1. **Geometric Parameters:**
   - H_BOX and H_CH scaling has minimal effect on BTBT current (tunneling predominantly occurs in D-G overlap region)
   - Slight increase in BTBT current with increased D-G overlap length (L_OV)

2. **Doping Effects:**
   - **Critical Finding:** Lower N_CH and N_SD significantly reduce BTBT current
   - Higher doping reduces depletion width → steeper energy band profile → shorter tunnel lengths → higher BTBT current

3. **Optimal Parameters for Low BTBT:**
   - Low L_OV
   - Low N_SD
   - Low N_CH

### Phase 2: Maximizing BTBT Current

1. **Optimal Design Achieved:**
   - **L_OV = 1.4 nm**
   - **N_CH = 1×10¹⁷ cm⁻³**
   - Represents maximum achievable BTBT current before convergence issues

2. **Parameter Sensitivities:**
   - Increasing L_OV: Slight increase in BTBT current
   - Increasing N_CH: Large increase in BTBT current
   - N_SD already at maximum (10²⁰ cm⁻³) in base design

### Temperature Analysis

- **Regular and substantial increase** in BTBT current with increasing temperature (300 K → 398 K)
- Physical mechanism: Higher temperature → reduced bandgap → increased tunneling probability
- Trend consistent for both 32nm PD-SOI and 22nm FD-SOI devices

### Gate Length Scaling (32nm → 22nm)

- **Critical Insight:** Geometric scaling alone is insufficient
- Channel doping must be adjusted to maintain desired depletion characteristics:
  - 32nm PD-SOI: Partially depleted channel (N_CH ~ 6.4×10¹⁷ cm⁻³)
  - 22nm FD-SOI: Fully depleted channel (N_CH ~ 1×10¹² cm⁻³)

## 🛠️ Tools & Methodology

### Simulation
- **Synopsys Sentaurus TCAD** - Device physics simulation
- **BTBT Models:** Nonlocal Path (NLP) model
  - More accurate than Hurkx and Schenk models for realistic geometries
  - Accounts for multiple tunneling paths with varying lengths

### Characterization
- **Agilent B1500 Semiconductor Parameter Analyzer** - Electrical measurements
- **Process Technology:** GlobalFoundries (GF) fabrication
- I-V characteristic measurements under various bias conditions

### Analysis Parameters
- **Design Space Exploration:** Systematic variation of geometric and doping parameters
- **Temperature Sweep:** 300 K, 358 K, 398 K
- **Convergence Analysis:** Identifying optimal parameter combinations within simulation stability limits

## 📈 Applications

### BTBT Integrator (Low Current)
- **Leaky integrator** for neural spike generation
- Body potential rises due to hole accumulation from electron tunneling
- Ultra-low power consumption enables large-scale SNN hardware
- Biologically plausible neuron implementation with low spiking frequency

### BTBT Inverter (High Current)
- **Fast switching** inverter for neuromorphic circuits
- Quick rise time at low V_IN voltages
- Subthreshold regime transistor provides reset functionality
- Energy-efficient logic operations in neuromorphic systems

## 📄 Documentation

This repository contains:
- **EE724_finalreport.pdf** - Comprehensive project report with detailed analysis
- **EE724_Project_Stage_1-1.pdf** - Phase 1 interim report
- **EE724_Template(2).pptx** - Project presentation

## 🎓 Learning Outcomes

This project provided deep insights into:
- Quantum mechanical tunneling phenomena in nanoscale devices
- TCAD simulation methodology for advanced device physics
- Trade-offs between power, performance, and area in neuromorphic hardware
- Design space exploration techniques for semiconductor device optimization
- Temperature and scaling effects in ultra-scaled MOSFETs

## 🔑 Key Takeaways

1. **Design Parameter Impact:** N_CH and N_SD have the strongest influence on BTBT current
2. **Optimization Trade-off:** Different applications require opposite optimization objectives
3. **Temperature Sensitivity:** BTBT devices show significant temperature dependence
4. **Scaling Complexity:** Gate length scaling requires holistic design parameter adjustment
5. **Application-Specific Design:** Optimal parameters depend on target application (integrator vs. inverter)

## 📚 References

Key papers that informed this work:

1. **Sonawane et al.** (2023) - Design Space and Variability Analysis of SOI MOSFET for Ultra-Low Power Band-to-Band Tunneling Neurons
2. **Chavan et al.** (2020) - Band-to-Band Tunneling Based Ultra-Energy-Efficient Silicon Neuron
3. **Singh et al.** (2022) - Quantum Tunneling Based Ultra-Compact and Energy Efficient Spiking Neuron
4. **Hurkx, Schenk, Fukuda** - BTBT modeling approaches (Hurkx, Schenk, Nonlocal Path models)

*For complete references, see the final report.*

## 🙏 Acknowledgments

We thank Prof. Udayan Ganguly for his guidance throughout this project, Jay Sonawane for mentoring, and the EE724 course team for their support.

---

**Note:** This project demonstrates practical applications of nanoelectronics in emerging neuromorphic computing architectures, contributing to the development of energy-efficient hardware for artificial intelligence.
