# B1RK4 solver for the bilinear single-degree-of-freedom	oscillator response to arbitrary base acceleration excitation

# 1. Introduction

B1RK4 is a standalone executable program written in C++ that calculates the response of a bilinear single-degree-of-freedom oscillator to an arbitrary base acceleration input via the fourth-order Runge-Kutta formulation. It can be used in standalone mode, or in conjunction with third-party software. It may find application in parametric, stochastic analysis and optimisation, and can assist learning on the subject of structural dynamics.

# 2. System requirements
The program runs on Windows operating system directly from the command prompt, without the requirement to use any other software. 

# 3. Formulation

The following equation is solved [1]:


http://mathurl.com/y2f3kpgg

![](https://latex.codecogs.com/svg.latex?x_y)
