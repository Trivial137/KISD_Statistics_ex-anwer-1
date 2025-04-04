# Exercise 1: Signal-Background Mixture Analysis

**Author**: Longjie Chen  
**Date**: 4-4-2025 
**Python Version**: 3.13.1  
**Dataset**: Dataset 3 (provided in `raw_data_3_tau5.npy`)  


## Overview
This repository contains the analysis for **Exercise 1**, using a **binned least-squares (LS) method** with a $\chi^2$ statistic. Key modifications include increasing the histogram bin resolution from `nbins = 10` to **`nbins = 25`** to refine sensitivity to distribution features.


### Code Modifications  
- **Critical Change**:  
  ```python
  nbins = 25  # Increased from 10 for finer resolution
