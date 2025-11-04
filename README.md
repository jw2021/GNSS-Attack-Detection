# GNSS-Attack-Detection
This repository presents a pseudorange-based spoofing detector for UAVs that leverages spatial correlation from antenna motion. A disturbance observer and an LMS filter mitigate multipath and motion disturbances, and a GLRT performs final spoofing detection.

**How the platform works？**
1. The UAV receives GNSS signals and extracts epoch-by-epoch pseudorange measurements.
2. Motion of the antenna produces spatial correlation and motion-dependent multipath.
3. A disturbance observer estimates low-frequency environmental effects (e.g., wind).
4. An LMS filter adaptively suppresses multipath-induced pseudorange fluctuations.
5. Filtered measurements and model-based pseudorange predictions are formed.
6. A composite GLRT compares measured and predicted pseudoranges.
7. Significant deviations are flagged as spoofing.
8. The whole pipeline is designed for real-time onboard operation.

**The contents of this repository**

simulink/
Simulink model for the UAV control and sensor simulation.
Includes trajectory scripts used in the experiments (circular motion, speed profiles).

stm32/
STM32 firmware for epoch-level pseudorange acquisition and local estimation.
Code includes data logging and a lightweight predictor used during onboard preprocessing.

data/
Contains GNSS pseudorange solution data collected from UAV experiments.

**Notes on reproducibility**
The Simulink models run in MATLAB/Simulink (R2019b or later recommended).
STM32 code targets the STM32F1 family. 
