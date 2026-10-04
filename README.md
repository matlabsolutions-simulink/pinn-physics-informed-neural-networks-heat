# Physics-Informed Neural Network (PINN) for 1D Transient Heat Conduction

[![MATLAB](https://img.shields.io/badge/MATLAB-R2023b%20%7C%20R2024b-0076A8?logo=mathworks&logoColor=white)](https://www.mathworks.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Domain](https://img.shields.io/badge/Domain-Deep%20Learning%20&%20Scientific%20Computing-lightgrey.svg)](#)

A standalone MATLAB implementation of Physics-Informed Neural Network (PINN) for 1D Transient Heat Conduction. Includes the governing dynamics, analytical formulations, and an executable script you can run directly without proprietary third-party dependencies.

## Overview

This repository provides a compact MATLAB script solving the 1D transient heat diffusion equation using a Physics-Informed Neural Network (PINN) framework. It compares collocation residuals directly against an analytical Fourier series benchmark.

## Governing Equations & Mathematical Formulation

### 1D Heat Diffusion PDE

$$
\frac{\partial u}{\partial t} - \alpha \frac{\partial^2 u}{\partial x^2} = 0, \quad x \in [0, L], \quad t > 0
$$

### Composite Physics Loss Formulation

$$
\mathcal{L}_{\text{total}} = \mathcal{L}_{\text{residual}} + \lambda_{\text{bc}} \mathcal{L}_{\text{boundary}} + \lambda_{\text{ic}} \mathcal{L}_{\text{initial}}
$$

where $\alpha$ is thermal diffusivity, and the residual loss penalizes deviations from the differential equation across interior collocation points.

## Getting Started

### Prerequisites
- MATLAB (tested on R2022b through R2024b)
- Standard base MATLAB installation (no paid external toolboxes required for this starter script)

### Running the Code
1. Clone the repository:
   ```bash
   git clone https://github.com/matlabsolutions-simulink/pinn-physics-informed-neural-networks-heat.git
   cd pinn-physics-informed-neural-networks-heat
   ```
2. Open MATLAB, navigate to the cloned folder, and run:
   ```matlab
   run_pinn_heat_conduction
   ```

## Need the Complete Simulink or Simscape Model?

If you are working on a university capstone, thesis, or lab assignment and need the complete `.slx` model with Simscape physical networks, custom parameter lookup tables, or automated test harnesses, our team at [MATLABSolutions.com](https://www.matlabsolutions.com/order-now.php?ref=github_pinn_physics_informed_neural_networks_heat) provides custom academic simulation and consulting support.

## Technical Inquiries & Contact
- Website: [matlabsolutions.com](https://www.matlabsolutions.com)
- Custom Consulting Portal: [matlabsolutions.com/order-now.php](https://www.matlabsolutions.com/order-now.php)
- Email: info@matlabsolutions.com

## License
This project is open-source under the [MIT License](LICENSE).
