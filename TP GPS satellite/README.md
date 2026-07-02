# GPS Satellite Navigation: Position Estimation via Nonlinear Least Squares

A MATLAB implementation of GPS receiver positioning from satellite pseudorange measurements, including robustness analysis against interference and multipath, and precision characterization via Dilution of Precision (DOP).

## Overview

Given pseudorange measurements from GPS satellites, the receiver position and clock bias are estimated at each time step by solving a nonlinear least-squares problem with the Gauss-Newton algorithm — linearizing the measurement model around the current estimate and iterating until convergence, using the previous timestep's solution as the initial guess.

## Key Components

- **Reference frame transformation**: derivation of the rotation matrix from the Earth-Centered Earth-Fixed (ECEF) frame to a local (North-East-Down) frame centered on a reference point
- **Trajectory reconstruction**: vehicle position estimated from real GPS pseudorange data, converted to the local frame and compared against ground truth
- **Robustness analysis**:
  - Interference — modeled as Gaussian noise on pseudoranges; position error increases smoothly with noise variance
  - Multipath — modeled as a constant bias on a single satellite's pseudorange; produces a systematic position offset that grows sharply with bias amplitude, proving more damaging than random noise since it isn't absorbed by clock bias estimation
- **Dilution of Precision (DOP)**: analytical derivation of DOP from the least-squares error covariance, then computed along the full trajectory (DOP, PDOP, HDOP, VDOP) to explain periods of degraded positioning accuracy tied to satellite geometry

## Results

- Estimated trajectory closely matches the reference trajectory in both the local (N, E) plane and 3D ECEF frame
- Position error (RMSE) tracked over time, with spikes directly explained by DOP degradation during specific time windows — confirming the link between satellite constellation geometry and achievable positioning accuracy

## Tech Stack

MATLAB
