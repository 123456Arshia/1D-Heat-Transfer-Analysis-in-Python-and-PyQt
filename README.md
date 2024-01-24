# 1D-Heat-Transfer-Analysis-in-Python-and-PyQt


---

# 1D Heat Transfer Analysis in an Iron Wire

## Project Overview

### Objective
This project aims to analyze the temperature distribution in a one-dimensional iron wire, which is subjected to different temperatures at each end. The analysis is done using both analytical and numerical methods.

### Fundamental Concepts

1. **Heat Transfer Mechanism:** The project is centered around conductive heat transfer, where heat is transmitted through a material without the material itself moving.

2. **Steady-State Conduction:** It is assumed that the temperature distribution in the wire does not change over time, leading to a simplified form of the heat conduction equation.

### Governing Formula

The core equation for steady-state, one-dimensional heat conduction without internal heat generation is:

\[ \frac{d^2T}{dx^2} = 0 \]

where \( T \) represents the temperature and \( x \) is the spatial coordinate along the wire.

### Analytical Solution

With given boundary conditions (temperature \( T_{\text{hot}} \) at one end and \( T_{\text{cold}} \) at the other), the analytical solution is a linear temperature gradient:

\[ T(x) = T_{\text{hot}} + (T_{\text{cold}} - T_{\text{hot}}) \frac{x}{L} \]

Here, \( L \) denotes the length of the wire.

## Numerical Solution - Finite Difference Method (FDM) & Forward Time Centered Space (FTCS)

### Finite Difference Method (FDM)
FDM is a numerical technique for solving differential equations by approximating them with difference equations. In this method, the continuous domain (the wire) is discretized into a grid.

### Forward Time Centered Space (FTCS) Scheme
FTCS is a specific technique in FDM for solving partial differential equations, particularly useful in heat transfer:

1. **Time Discretization (Forward Time):** The time derivative in the heat equation is approximated using forward differencing:

   \[ \frac{\partial T}{\partial t} \approx \frac{T_i^{n+1} - T_i^n}{\Delta t} \]

2. **Space Discretization (Centered Space):** The spatial derivatives are approximated using centered differencing:

   \[ \frac{\partial^2 T}{\partial x^2} \approx \frac{T_{i+1}^n - 2T_i^n + T_{i-1}^n}{(\Delta x)^2} \]

Combining these gives the FTCS discretization of the heat equation:

\[ T_i^{n+1} = T_i^n + \alpha \frac{\Delta t}{(\Delta x)^2} (T_{i+1}^n - 2T_i^n + T_{i-1}^n) \]

where \( \alpha \) is the thermal diffusivity, \( \Delta t \) is the time step, and \( \Delta x \) is the spatial step.

## Python and PyQt Implementation

- **HeatTransfer1D Class:** Encapsulates both analytical and numerical solution methods, calculating temperature distributions using the analytical formula and the FTCS scheme.

- **GUI with PyQt:** Provides an interactive user interface for parameter input, such as wire length, temperatures, and physical constants. It features input fields, a 'Run Analysis' button, and a canvas for result display.

- **Plotting Functions:** `plot_solution` and `plot_error` are used to visualize the temperature distributions and the error between the analytical and numerical solutions, respectively.

## Conclusion

This project demonstrates the practical application of both analytical and numerical methods to solve a classical problem in heat transfer. The Python implementation, enhanced by a PyQt GUI, offers an interactive platform for exploring how different parameters affect heat distribution in a one-dimensional medium.

---

