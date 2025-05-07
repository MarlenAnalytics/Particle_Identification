# Particle Identification

## Objective 

The goal of this project is to simulate the use of time-of-flight (TOF) techniques for particle identification (PID) based on the relativistic velocity (β) of particles with varying masses and momenta. Detector uncertainties are taken into account and the timing resoluation is estimated so that four specific particles (electrons, pions, kaons, and protons) can be distinguished.

### Constants and Kinematics 

$\beta$: particle velocity 

L: traveled path length 

c: speed of light measured in nanometers per second

Time of flight is calculated using the following equation:

$$T = \frac{L}{\beta c}$$

### Relativistic Velocity Calculation 

An evenly-spaced interval of momenta between 0.1 to 5 GeV/c is created using `linspace` array and the relativistic velocity $\beta$ for each respective particle is computed using:

$$\beta = \frac{p}{\sqrt{p^2 + m^2}}$$

### Uncertainty and Error Propagation 

The momentum and path length are assumed to have negligible uncertainties, but the time of flight (T), has an assumed uncertainty value ($\partial T$) of 0.1 nanoseconds. The uncertainty of each particle was found using the following relationship:

$$\beta = \frac{\frac{L}{T}}{c}$$

$$\partial \beta = \frac{L}{T} \frac{1}{T^2} \partial T$$

$$\frac{\partial \beta}{\beta} = \frac{\partial T}{T}$$

$$\partial \beta = \frac{\partial T \beta}{T}$$

The theoretical lines of each particle's momentum is plotted with respect to their velocities. The uncertainty calculations performed are also visualized as error bands which can be seen in the first figure in the notebook. This plot illustrates how particles with different masses approach $\beta = 1$ at different rates. It is observed that heavier particles such as protons and kaons increase in $\beta$ more slowly than lighter particles.

Given the detector timing resolution (the ability to distinguish between events that occur closely in time), the upper limit for the kaons and pions was computed to be:

$$\beta_K + \partial \beta_K$$

$$\beta_\pi + \partial \beta_\pi$$

This resulted in a large array of values, therefore the average was taken to get an estimate of the upper limit for each particle.

The required timing resolution $\partial T$ for the kaon and pion particles with a momentum
of up to 3 GeV was estimated by taking the average of the following:

$$\partial T_\pi = \frac{\partial \beta_\pi}{\beta} T$$

$$\partial T_K = \frac{\partial \beta_K}{\beta} T$$


### Gaussian Smearing

Gaussian noise was added to the momenta and $\beta$ to simulate detector error. A histogram of noisy $\beta$ values show overlapping regions where particle identification becomes more complex with increasing momenta.

### Purpose

This type of simulation is useful in the design and calibration of detectors in high-energy and nuclear physics experiments, such as those used at the Thomas Jefferson National Accelerator Facility or CERN.
