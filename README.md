
# Digital Metastability Analyzer for Clock Domain Crossing (CDC) Reliability Assessment

A comprehensive tool for detecting, analyzing, and visualizing metastability risks in clock domain crossing paths in digital systems.

## Overview

Modern digital systems often contain multiple asynchronous clock domains. When signals cross between these domains, setup and hold time violations can occur, causing flip-flops to enter a metastable state. This analyzer helps:

- **Detect** metastability risks in CDC paths
- **Analyze** synchronization reliability using MTBF calculations
- **Visualize** timing violations and metastability probability
- **Evaluate** multi-stage flip-flop synchronizer effectiveness

## Features

- MTBF (Mean Time Between Failure) calculation for synchronizers
- Metastability probability estimation
- Setup/hold time violation detection
- Multi-stage synchronizer evaluation (2-flop, 3-flop, etc.)
- Interactive visualizations of timing diagrams
- CDC path risk assessment and reporting

## Installation

```bash
git clone <your-repo-url>
cd Digital_Metastability_Analyzer_CDC
pip install -r requirements.txt
```

## Quick Start

```python
from src.metastability_analyzer import MetastabilityAnalyzer

# Create analyzer instance
analyzer = MetastabilityAnalyzer()

# Add CDC path with clock frequencies
analyzer.add_cdc_path(
    source_clock=100e6,      # 100 MHz source clock
    dest_clock=200e6,        # 200 MHz destination clock
    setup_time=0.2e-9,       # 200 ps setup time
    hold_time=0.1e-9,        # 100 ps hold time
    resolution_time=1e-9     # 1 ns flip-flop resolution time
)

# Calculate MTBF
mtbf = analyzer.calculate_mtbf(stages=2)
print(f"MTBF for 2-stage synchronizer: {mtbf:.2f} years")
```

## Core Components

| Module | Description |
|--------|-------------|
| `metastability_analyzer.py` | Core MTBF and metastability probability calculations |
| `cdc_detector.py` | CDC path detection and timing violation analysis |
| `synchronizer_evaluator.py` | Multi-stage synchronizer effectiveness evaluation |
| `visualizer.py` | Timing diagrams and risk visualization |

## MTBF Formula

The analyzer uses the standard metastability MTBF equation:

$$MTBF = \frac{e^{T_{res}/\tau}}{f_{clk} \cdot f_{data} \cdot T_0}$$

Where:
- \(T_{res}\) = resolution time (synchronization stages × clock period)
- \(\tau\) = flip-flop time constant (technology-dependent)
- \(f_{clk}\) = destination clock frequency
- \(f_{data}\) = data transition frequency
- \(T_0\) = flip-flop constant (technology-dependent)

## Requirements

- Python 3.8+
- NumPy
- Matplotlib
- Pandas (optional, for reporting)

