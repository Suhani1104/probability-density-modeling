# NO₂ Probability Density Modeling

## Project Overview

This project analyzes the statistical behavior of the NO₂ air quality feature by applying a roll-number-dependent nonlinear transformation and learning its probability density function. To ensure reliable modeling, a robust drift stabilization step is performed before estimating the parameters of a Gaussian distribution.

The notebook demonstrates:

- Stabilizing feature distribution using robust drift reduction (median–IQR method)
- Applying a personalized nonlinear mathematical transformation
- Learning Gaussian distribution parameters from data using Maximum Likelihood Estimation (MLE)
- Visual comparison between empirical data distribution and learned probability model
- Understanding probabilistic representation of real-world environmental data

---

## Objective

The goal is to transform the NO₂ feature using a roll-number-controlled nonlinear function and estimate the parameters of a Gaussian probability density function that best describes the transformed feature.

The transformation applied is:

$$
z = x + a_r \sin(b_r x)
$$

where:

$$
a_r = 0.05 \times (r \bmod 7)
$$

$$
b_r = 0.3 \times \left( (r \bmod 5) + 1 \right)
$$

After transformation, the probability density function is modeled as:

$$
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
$$

where:

- $\mu$ represents the mean of the transformed data  
- $\lambda = \frac{1}{2\sigma^2}$ controls the spread of the distribution  
- $c = \frac{1}{\sqrt{2\pi}\sigma}$ ensures proper normalization  

---

## Methodology

### 1. Data Preparation and Drift Stabilization

- Load NO₂ values from dataset
- Remove missing entries
- Apply median–IQR scaling to stabilize the distribution and reduce drift caused by outliers

---

### 2. Feature Transformation

- Apply sinusoidal transformation using parameters derived from roll number
- Introduce controlled nonlinear variation while preserving feature structure

---

### 3. Parameter Estimation

- Compute mean and variance of transformed feature
- Derive Gaussian distribution parameters using Maximum Likelihood Estimation
- Construct the probability density function using estimated parameters

---

### 4. Visualization and Verification

- Plot histogram of transformed feature
- Overlay learned Gaussian probability density curve
- Evaluate how well the distribution represents the data

---

## Key Concepts Demonstrated

- Drift stabilization in data preprocessing
- Nonlinear feature transformation
- Gaussian probability density modeling
- Maximum Likelihood Estimation
- Statistical characterization of real-world data

---

## Conclusion

This project demonstrates how drift-stabilized feature transformation and statistical estimation techniques can be used to construct a reliable probabilistic model of NO₂ air quality data, enabling accurate representation of its underlying distribution.
