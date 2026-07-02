# GPS/INS Sensor Fusion: 2D Land-Vehicle Navigation

A MATLAB implementation of inertial navigation and GPS/INS hybridization for a land vehicle, using a simplified 2D strapdown mechanization and a linearized Kalman filter.

## Overview

Real GPS and IMU data were collected from a car driven around a fixed loop. The project implements:

1. A **simplified 2D inertial mechanization** — reconstructing position, velocity, and heading from a single accelerometer and gyrometer axis via trapezoidal integration, propagated in a local-tangent-plane navigation frame
2. A **linearized Kalman filter** estimating IRS drift errors (position, velocity, heading, and sensor biases) using GPS position as the observation, both in **open-loop** (feedforward correction) and **closed-loop** (feedback correction of the mechanization) configurations
3. **Robustness testing** under simulated GPS signal masking, to evaluate how the hybridized solution degrades — and recovers — when GPS aiding is temporarily unavailable

## Key Concepts

- **Strapdown IRS mechanization**: converting raw accelerometer/gyrometer measurements (in the platform frame) into position, velocity, and heading estimates (in the vehicle and navigation frames), accounting for sensor bias modeled as a first-order Markov process
- **Kalman filter design**: derivation of the continuous-time state transition model (position, velocity, heading, and bias error states) and the discrete GPS measurement model
- **Open- vs. closed-loop hybridization**: comparing feedforward correction (errors estimated but not fed back into the mechanization) against feedback correction (errors reset at each step), and how this affects long-term drift
- **GPS outage resilience**: analyzing navigation solution degradation during simulated masking intervals

## Tech Stack

MATLAB
