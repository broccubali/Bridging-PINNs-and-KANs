# Bridging PINNs and KANs to Handle Noisy Partial Differential Equations

## Overview
This repository presents an integrated framework combining Physics-Informed Neural Networks (PINNs) and Kolmogorov-Arnold Networks (KANs) to enhance the robustness of solving Partial Differential Equations (PDEs) in the presence of noise. Our approach first denoises input data using KANs before passing it to PINNs for solving forward PDEs. We demonstrate the effectiveness of this framework on three benchmark PDEs: the Burgers’ equation, the Heat equation, and the Wave equation.

While PINNs have shown great promise in solving PDEs by embedding physical laws into their loss functions, they struggle with noisy input data. Noisy conditions can lead to poor convergence, incorrect solutions, and loss of generalizability. To address this, we integrate KANs, which can effectively denoise inputs before they are fed into PINNs, improving stability and accuracy.

## Key Features
- **Hybrid Approach:** Uses KANs for noise reduction before solving PDEs with PINNs.
- **Scalability:** Handles different types of PDEs under noisy conditions.
- **Robustness:** Demonstrates improved performance over standard PINNs in the presence of measurement noise.

## Partial Differential Equations Considered
### 1. Burgers' Equation  
A nonlinear PDE commonly used to model turbulence and nonlinear wave phenomena:

$$
\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} = \nu \frac{\partial^2 u}{\partial x^2}
$$

where:  
- $$u(x,t)$$ represents velocity.  
- $$\nu$$ is the diffusion coefficient.  

### 2. Heat Equation  
Describes the diffusion of heat over time:

$$
\frac{\partial u}{\partial t} = \alpha \frac{\partial^2 u}{\partial x^2}
$$

where:  
- $$u(x,t)$$ represents temperature.  
- $$alpha$$ is the thermal diffusivity.  


### 3. Wave Equation  
Models wave propagation in a medium:

$$
\frac{\partial^2 u}{\partial t^2} = c^2 \frac{\partial^2 u}{\partial x^2}
$$

where:  
- $$u(x,t)$$ represents the wave function.  
- $$c$$ is the wave speed.  


## Implementation Details
1. **Data Preprocessing:**
   - Input data is initially passed through a KAN to reduce noise.
   - Skewed normal noise is introduced to simulate real-world measurement errors.

2. **PINN Training:**
   - The denoised data from KANs is used to train PINNs.
   - The loss function includes residuals from the governing PDEs.

3. **Evaluation:**
   - Solutions are compared against traditional numerical solvers.
   - Metrics such as Mean Squared Error (MSE) are used to quantify accuracy improvements.

## Installation
To set up the environment, clone this repository and install the required dependencies:
```bash
git clone https://github.com/broccubali/Bridging-PINNs-and-KANs.git
cd Bridging-PINNs-and-KANs
pip install -r requirements.txt
```

## Repository Structure
- `kan/`: Contains implementations and utilities related to Kolmogorov-Arnold Networks.
- `pde-gen/`: Includes tools for generating and managing partial differential equation datasets.
- `pinns/`: Houses code and resources pertinent to Physics-Informed Neural Networks.
- `pipeline/`: Provides scripts and configurations for integrating KANs with PINNs in a cohesive workflow.

## Usage
Run the main script to train and evaluate the model:
```bash
python main.py
```

## Results
- **Improved Accuracy:** The hybrid approach outperforms standard PINNs, particularly in noisy conditions.
- **Better Convergence:** PINNs converge more reliably when using KAN-denoised inputs.
- **Scalability:** The method generalizes well across different PDEs.

## Acknowledgments
We thank the contributors to this research and the open-source community for providing tools and resources that enabled this work.



