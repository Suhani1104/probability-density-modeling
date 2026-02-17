# NO2 Probability Density Modeling

## Project Overview

This project models the NO₂ air quality feature using a roll-number-based nonlinear transformation and learns a Gaussian-form probability density function (PDF) from the transformed data.

The notebook demonstrates:

- Robust drift reduction using median and interquartile range (IQR)
- Feature engineering using mathematical transformation
- Parametric density estimation using Maximum Likelihood Estimation (MLE)
- Statistical modeling of real-world environmental data
- Visualization and validation of the learned probability distribution

---

## Objective

Given NO₂ values \(x\), apply the transformation:

\[
z = x + a_r \sin(b_r x)
\]

Where:

\[
a_r = 0.05 \cdot (r \bmod 7), \quad b_r = 0.3 \cdot (r \bmod 5 + 1)
\]

Then estimate the Gaussian-form probability density function:

\[
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
\]

Where parameters \(\mu\), \(\lambda\), and \(c\) are learned from data.

---

## Methodology

### 1. Data Preprocessing and Drift Reduction

- Remove missing NO₂ values
- Apply robust drift reduction using median and IQR to stabilize the distribution and reduce outlier influence

\[
x_{stable} = \frac{x - \text{median}}{\text{IQR}}
\]

---

### 2. Feature Transformation

Apply roll-number-parameterized nonlinear transformation:

\[
z = x_{stable} + a_r \sin(b_r x_{stable})
\]

This introduces controlled nonlinearity and personalized feature transformation.

---

### 3. Statistical PDF Learning (MLE)

Estimate Gaussian parameters using Maximum Likelihood Estimation:

- Mean (\(\mu\))
- Variance (\(\sigma^2\))
- Lambda (\(\lambda = \frac{1}{2\sigma^2}\))
- Normalization constant (\(c\))

This fully defines the probability density function.

---

### 4. Visualization and Validation

- Plot histogram of transformed feature
- Plot learned Gaussian PDF
- Compare empirical distribution with theoretical model

This validates the accuracy of probabilistic modeling.

---

## Key Concepts Demonstrated

- Drift reduction for stable statistical modeling
- Nonlinear feature transformation
- Probability density estimation using MLE
- Gaussian distribution modeling
- Statistical learning from real-world data

---

## Conclusion

This project demonstrates robust probability density modeling of NO₂ air quality data by applying drift reduction, nonlinear transformation, and Gaussian parameter estimation, ensuring accurate and reliable statistical representation of the data.
