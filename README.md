# Exercise 1: Signal-Background Mixture Analysis

**Author**: Longjie Chen  
**Date**: $\today$ 
**Python Version**: 3.13.1  
**Dataset**: Dataset 3 (provided in `raw_data_3_tau5.npy`)  

---

## Overview
This repository contains the analysis for **Exercise 1**, which models a mixture of signal (Gaussian) and background (exponential) events using a **binned least-squares (LS) method** with a $\chi^2$ statistic. Key modifications include increasing the histogram bin resolution from `nbins = 10` to **`nbins = 25`** to refine sensitivity to distribution features.

---

## Methodology
### $\chi^2$ Minimization Framework
- **Objective**: Estimate the signal yield ($N_S$) by minimizing the $\chi^2$ statistic between observed and expected bin counts.  
- **PDFs**:  
  - **Signal**: Truncated Gaussian ($\mu = 10$, $\sigma = 3$).  
  - **Background**: Truncated Exponential ($\tau = 5$).  
- **Binning**:  
  - Increased from `nbins = 10` to **`nbins = 25`** to balance bias-variance trade-offs.  
  - Range: $x \in [0, 30)$.  

### Uncertainty Estimation  
- **$\chi^2$ Profiling**: Asymmetric uncertainties derived from $\Delta\chi^2 = 1$ threshold (68% CL).  
- **Linear Interpolation**: Refines confidence bounds between discrete grid points.  

---

## Implementation Details
### Key Steps  
1. **Data Loading**:  
   - Dataset 3 loaded from `raw_data_3_tau5.npy`.  
2. **PDF Normalization**:  
   - Signal/background PDFs truncated to $[0, 30)$ and normalized.  
3. **Binned $\chi^2$ Calculation**:  
   - Expected counts per bin: $N_S \cdot f_S(x) + (N - N_S) \cdot f_B(x)$.  
   - $\chi^2$ minimized using `scipy.optimize.minimize`.  
4. **Uncertainty Analysis**:  
   - $\chi^2$ evaluated over a grid of $N_S$ values.  
   - 1σ bounds interpolated from profile.  

### Code Modifications  
- **Critical Change**:  
  ```python
  nbins = 25  # Increased from 10 for finer resolution
