# Dynamic Collective Model (DCM)

## Overview

This repository contains the implementation of the Dynamic Collective Model (DCM) for simulating and predicting silence waves in financial markets. DCM is a computational framework designed to capture emergent, self-organized activity reductions in complex systems, with particular application to financial crisis events such as the 2008 Lehman Brothers collapse and the 2010 Flash Crash.

The model integrates three key mechanisms:

1. **Spatial resistance**: Distance-dependent influence decay across network-based structures
2. **Heterogeneous delays**: Random perception lags reflecting information asymmetries
3. **Nonlinear feedback**: Time-varying activation and inhibition functions

## Features

- Configurable model parameters for different financial events
- Silence wave simulation with quantitative metrics (propagation speed, amplitude, decay time)
- Risk indicator function for early warning prediction
- Validation against historical market data
- Visualization tools for model results, heatmaps, and sensitivity analysis

## Requirements

- Python 3.6+
- NumPy
- Pandas
- Matplotlib
- SciPy
- yfinance (for downloading financial data)

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/dcm-financial.git
cd dcm-financial

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install required packages
pip install numpy pandas matplotlib scipy yfinance
```

## Usage

The main script `dcm_validation.py` provides several validation options:

```bash
python dcm_validation.py
```

When executed, the script will display a menu:

```
Dynamic Collective Model (DCM) Financial Events Silence Wave Validation Program
================================================

Validation options:
1. Validate silence wave characteristics in 2008 Lehman Brothers crisis
2. Validate silence wave characteristics in 2010 Flash Crash
3. Run comparative analysis of both events
4. Parameter sensitivity analysis
5. Generate DCM conceptual diagram
6. Generate parameter sensitivity figure
7. Exit
```

### Example: Validating the 2008 Lehman Brothers crisis

```python
# Inside your Python script or notebook
from dcm_validation_v0.2 import validate_lehman_crisis

# Run the validation
lehman_dcm = validate_lehman_crisis()
```

### Creating a custom DCM simulation

```python
from dcm_validation_v0.2 import DCMConfiguration, DynamicCollectiveModel
import pandas as pd

# Create a custom configuration
config = DCMConfiguration()
config.width = 10
config.length = 10
config.tau = 1.0
config.k = 0.05
# Set other parameters as needed

# Initialize the model
dcm = DynamicCollectiveModel(config)

# Load your financial data
volume_data = pd.read_csv('your_volume_data.csv', index_col=0)
vix_data = pd.read_csv('your_vix_data.csv', index_col=0)

# Run the simulation
activity, risk_history = dcm.simulate(volume_data)

# Visualize results
metrics = dcm.visualize_results(volume_data, vix_data, "Custom Event")
```

## Model Components

### DCMConfiguration

Manages event-specific parameter settings for the model:

- Grid dimensions (`width`, `length`)
- Time parameters (`steps`, `dt`)
- Market behavior parameters (`tau`, `k`, `R_crit`, etc.)
- Event-specific configurations for Lehman crisis and Flash Crash

### DynamicCollectiveModel

Core implementation of the DCM framework:

- Dynamic parameter functions that evolve over time
- Spatial perception and activity calculation
- Risk indicator computation
- Simulation execution
- Results visualization and validation

### Key Parameters and Their Financial Interpretation

| Parameter            | Symbol    | Experimental Range* | Financial Interpretation      |
| -------------------- | --------- | ------------------- | ----------------------------- |
| Perception delay     | τ         | 0.01-1.2            | Information processing time   |
| Spatial decay        | k         | 0.03-0.75           | Network connectivity strength |
| Feedback sensitivity | m_initial | 2-3                 | Initial herding intensity     |
| Decay time constant  | τ_decay   | 1-5                 | Crisis evolution timescale    |
| Activation weight    | α_initial | 0.7-1.1             | Investor confidence           |
| Inhibition weight    | β_initial | 0.3-0.5             | Market cooling mechanism      |

*Note: These ranges represent values used in our experiments and are not fixed limitations. The model parameters can be adjusted beyond these ranges to study different system behaviors.

## Outputs

The model produces various visualizations and metrics:

- Activity and risk indicator time series
- Spatial heatmaps showing silence wave propagation
- Comparison between model prediction and actual market behavior
- Correlation coefficients and statistical validation
- Parameter sensitivity analysis

## Paper Reference

If you use this code in your research, please cite our paper:

```
Zhang, H. (2025). A Dynamic Collective Model for Simulating and Predicting 
Silence Waves with Applications in Financial Risk Management. Physica A.
```

## License

[GPL-3.0 license](https://github.com/L0kiii/dcm-silencewave/tree/main?tab=GPL-3.0-1-ov-file)
