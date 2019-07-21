# B1RK4 solver for the bilinear single-degree-of-freedom	oscillator response to arbitrary base acceleration excitation

# 1. Introduction

B1RK4 is a standalone executable program written in C++ that calculates the response of a bilinear single-degree-of-freedom oscillator to an arbitrary base acceleration input via the fourth-order Runge-Kutta formulation. It can be used in standalone mode, or in conjunction with third-party software. It may find application in parametric, stochastic analysis and optimisation, and can assist learning on the subject of structural dynamics.

# 2. System requirements
The program runs on Windows operating system directly from the command prompt, without the requirement to use any other software. 

# 3. Formulation

The following equation is solved [1]:

![](https://latex.codecogs.com/gif.latex?%5Cddot%7Bu%7D%28t%29&plus;2%5C%2C%5Czeta%5Comega%5C%2C%5Cdot%7Bu%7D%28t%29&plus;%5Cpsi%5C%2C%5Comega%5E2u%28t%29&plus;a%281-%5Cpsi%29z%28t%29%3D-%5Cddot%7B%5Cxi%7D%28t%29%20%5C%2C%3B%20%5C%3B%5C%3B%5C%3B%20u%280%29%3D%20%7B%5Cdot%7Bu%7D%7D%280%29%3D0%20%5C%2C%2C)


