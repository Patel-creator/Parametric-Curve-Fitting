# Parametric-Curve-Fitting using Dieffrential Equation
This project focuses on estimating the unknown parameters of a non-linear parametric curve using real data points and optimization.
The goal was to find the best values of θ (theta), M, and X that make the mathematical curve match the observed (x, y) points.

**Problem Overview**
The curve is defined as:   
      x=tcos(θ)−eM∣t∣sin(0.3t)sin(θ)+X
      y=42+tsin(θ)+eM∣t∣sin(0.3t)cos(θ)
We needed to determine the values of θ, M, and X that best fit the dataset xy_data.csv, which contains real points on this curve.

**Step by Step Approach**
1. Understanding the data
  The dataset had only two columns — x and y.
  No t values were provided, but the problem statement mentioned that data corresponds to t        values between 6 and 60.
  So, I generated t uniformly in that range to associate one parameter value with each data        point.

2. Building the model
  Using the given equations, I wrote a Python function that can generate predicted (x, y) values   for any combination of θ, M, and X.
  This function essentially draws the curve for a specific parameter set.

3. Measuring Error(Loss Function)
To check how well the model matches the observed data, I used Mean Squared Error (MSE):
        Loss=mean[(xobs​−xpred​)2+(yobs​−ypred​)2]
A lower loss means the predicted curve is closer to the actual data.

4. Optimization
   Because the relationship is nonlinear, I used Differential Evolution from SciPy — a global optimization method that’s great at avoiding local minima.
It searches over the following ranges:
    Parameter	Range
          θ:	0° → 50°
          M:	−0.05 → 0.05
          X:	0 → 100
   
**Final Results**
θ = 0.5236 rad (≈ 30°)
M = 0.030
X = 55.0009
Mean L1 Distance = 25.31
Fit Score ≈ 60.28 / 100

Both positive (M = 0.03) and negative (M = −0.05) values gave similar numeric results, but M = +0.03 matched the dataset visually better (slight oscillation growth rather than damping).
**Final Parametric Equation**
\left(
t*\cos(0.5236)
- e^{0.030|t|}\cdot\sin(0.3t)\sin(0.5236)
+ 55.0009,
\;
42 + t*\sin(0.5236)
+ e^{0.030|t|}\cdot\sin(0.3t)\cos(0.5236)
\right)
