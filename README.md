# B1RK4 solver for the bilinear single-degree-of-freedom	oscillator response to arbitrary base acceleration excitation

<p align="center">
<b>  User Instructions </b><br>
</p>

<p align="center">
<b> S. Kasinos </b><br>
</p>

<p align="center">
<b> July 21, 2019 </b><br>
</p>


## 1. Introduction

B1RK4 is a standalone executable program written in C++ that calculates the response of a bilinear single-degree-of-freedom oscillator to an arbitrary base acceleration input via the fourth-order Runge-Kutta formulation. It can be used in standalone mode, or in conjunction with third-party software. It may find application in parametric, stochastic analysis and optimisation, and can assist learning on the subject of structural dynamics.

## 2. System requirements
The program runs on Windows operating system directly from the command prompt, without the requirement to use any other software. 

## 3. Formulation

The following equation is solved [1]:

<p align="center">
<img src="https://latex.codecogs.com/gif.latex?%5Cddot%7Bu%7D%28t%29&plus;2%5C%2C%5Czeta%5Comega%5C%2C%5Cdot%7Bu%7D%28t%29&plus;%5Cpsi%5C%2C%5Comega%5E2u%28t%29&plus;a%281-%5Cpsi%29z%28t%29%3D-%5Cddot%7B%5Cxi%7D%28t%29%20%5C%2C%3B%20%5C%3B%5C%3B%5C%3B%20u%280%29%3D%20%7B%5Cdot%7Bu%7D%7D%280%29%3D0%20%5C%2C%2C">
</p>

where ![](https://latex.codecogs.com/svg.latex?%5Cinline%20u%28t%29) denotes the displacement response of the oscillator; ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29) is the base acceleration time history input, in which the overdot denotes differentiation with respect to time; ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Czeta) and ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Comega%3D%5Csqrt%7Bk/m%7D) comprise the associated equivalent viscous damping ratio and circular frequency, respectively, whereby ![](https://latex.codecogs.com/gif.latex?%5Cinline%20k) is the stiffness of a linear spring and ![](https://latex.codecogs.com/gif.latex?%5Cinline%20m) is the associated mass; ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cpsi), in the range ![](https://latex.codecogs.com/gif.latex?%5Cinline%200%5Cleqslant%5Cpsi%3C1), is the post-yield to pre-yield stiffness ratio; ![](https://latex.codecogs.com/gif.latex?%5Cinline%20a) represents the specific strength of the system, i.e. the level of ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29) required for the oscillator to yield; ![](https://latex.codecogs.com/gif.latex?%5Cinline%20z%28t%29) is an auxiliary state variable satisfying ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cleft%20%7C%20z%28t%29%20%5Cright%20%7C%20%5Cleq%201), ruled by [2]:

<p align="center">
<img src="https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cdot%7Bz%7D%28t%29%3D%20%5Cfrac%7B%5Cdot%7Bu%7D%28t%29%5C%2C%5Comega%5E2%7D%7Ba%7D%5Cleft%5B%201-H%20%5Cleft%28%20%5Cdot%7Bu%7D%28t%29%20%5Cright%29%20H%5Cleft%28%20z%28t%29-1%5Cright%29%20-H%5Cleft%28%20-%5Cdot%7Bu%7D%28t%29%20%5Cright%29%20H%5Cleft%28-z%28t%29-1%5Cright%29%20%5Cright%5D%5C%2C%2C">
</p>

where ![](https://latex.codecogs.com/svg.latex?%5Cinline%20H%28%5Ccdot%29) denotes the Heaviside unit step function (i.e. ![](https://latex.codecogs.com/svg.latex?%5Cinline%20H%28x%29%3D&plus;1) if ![](https://latex.codecogs.com/svg.latex?%5Cinline%20x%5Cgeq0), ![](https://latex.codecogs.com/svg.latex?%5Cinline%20H%28x%29%3D0) if ![](https://latex.codecogs.com/svg.latex?%5Cinline%20x%3C0)).

Setting ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cpsi%3D0), corresponds to an elastic-perfectly-plastic case; alternatively, setting ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cpsi%3D1) results in the linear regime of motion. 

## 4. Preparing the input file

Prior to running the solver, the user must provide a standard fixed-length .txt input file which must be placed in the same directory as the solver. The first line comprises of five parameters, namely ![](https://latex.codecogs.com/svg.latex?%5Cinline%20n%2C%20%5Comega%2C%20%5Czeta%2C%20a) and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cpsi), where ![](https://latex.codecogs.com/svg.latex?%5Cinline%20n) is the length of the input acceleration time history array. The remaining lines are written in two-column format, and list the instances of time ![](https://latex.codecogs.com/svg.latex?%5Cinline%20t) and the input acceleration ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29), respectively. It is noted that the parameters in each line must be separated with double white space. A consistent system of units should be chosen such as the units of ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5B%7B%5Crm%7Brad%7D%7D/%7B%5Crm%7Bs%7D%7D%5D) for ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Comega), and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5B%7B%5Crm%7Bm%7D%7D%7B%5Crm%7Bs%7D%7D%5E%7B-2%7D%5D) for ![](https://latex.codecogs.com/svg.latex?%5Cinline%20a) and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29).

## 5. Running the solver

The solver **cannot** be executed by double clicking the executable file. To run the solver, start the command prompt and navigate from the current directory to the one where the executable file is located. For example, 

  ```latex
 cd Desktop
  ```
switches the directory on the command prompt. To run the solver then use:

  ```latex
 B1RK4.exe In.txt Out.txt
  ```
  
 which instructs the command prompt to run the solver after reading the input text file In.txt and write the output to Out.txt. It is noted, that this can also be achieved by calling the system command prompt from a third-party software such as MATLAB or PYTHON. 
  
## 6. Output

Upon successful completion of the analysis the output .txt file will be found in the same directory as the solver. This file will contain four columns, namely, time ![](https://latex.codecogs.com/gif.latex?%5Cinline%20t), and the response state variables ![](https://latex.codecogs.com/gif.latex?%5Cinline%20u%28t%29), ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdot%7Bu%7D%28t%29) and ![](https://latex.codecogs.com/gif.latex?%5Cinline%20z%28t%29), respectively. The user can process this file by a third-party software to plot the results.

## 7. Support

Please contact s.kasinos@gmail.com.

## References

[1] Kasinos, S. [Seismic response analysis of linear and nonlinear secondary structures](https://dspace.lboro.ac.uk/2134/33728). PhD thesis, 2018.

[2] Giaralis, A. and Kougioumtzoglou, I. [A stochastic dynamics approach for response spectrum analysis of bilinear systems using time-dependent equivalent linear properties](http://hdl.handle.net/2429/53408). Proceedings of the 12th International Conference on Applications of Statistics and Probability in Civil Engineering, 2015.


