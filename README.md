Exploring a Dynamic Weighting Method to Improve the Accuracy of AI Models for Atmospheric Profile Retrieval

This project explores methods to improve the accuracy of atmospheric profile retrieval using deep learning. By leveraging Residual Networks, multi-output attention, and a custom dynamic weighting loss function, the model achieves significant improvements compared to both a simple baseline deep neural network and the operational NOAA MiRS model.

Objectives
- Improve prediction accuracy of atmospheric profiles.
- Introduce residual connections for more effective training of deep networks.
- Implement a Custom Weighted MSE Loss that balances convergence between temperature and water vapor profiles.
- Compare model performance against:
- A baseline 4-layer DNN.
- The operational NOAA MiRS product.
  
Data
Inputs:
- ATMS SDR and GEO fields:
- Sensor Zenith Angle
- Surface Pressure
- ATMS Brightness Temperatures
- Latitude & Longitude

Labels (Outputs):
- ECMWF fields collocated with ATMS SDR data (pixel-level).
- 91-layer temperature profile and water vapor profile.
  
Time Range:
- 2019–2020, one day per month.

Splits:
- Training / Validation / Test = 8:1:1.

Model Architectures
Baseline Model
4-layer DNN with:
- Batch Normalization
- Dropout
- LeakyReLU

Proposed Model
- Residual Network (ResNet):
  - shortcut connections for efficient gradient flow.
- Custom Weighted MSE: 
  - dynamically balances losses of temperature and water vapor predictions.
- Task-Specific Output Heads:
  - Separate heads for temperature and water vapor.
  - Six attention layers to focus on regions with higher error.

Results
Temperature Profile
- Proposed model maintains Std. Dev < 1 for most altitudes (vs. NOAA MiRS > 1).
- Bias closer to zero, with less divergence compared to MiRS.
- Predicts profiles up to 0 hPa pressure levels (vs. MiRS limited to 100 hPa).

Water Vapor Profile
- Proposed model achieves max STD error ~25% (vs. MiRS up to 45%).
- Mean bias error never exceeds 3% (vs. MiRS exceeding 5% multiple times).
- Predicts profiles up to 0 hPa pressure levels (vs. MiRS limited to 200 hPa).

Conclusion
Developed a deep learning model with ResNet, dynamic loss weighting, and multi-output attention for atmospheric profile retrieval.
Limitations: Results may not generalize to all dates; further validation with additional datasets is needed.

🔗 References

NOAA MiRS Product: https://www.star.nesdis.noaa.gov/mirs/geonwp.php

Slideshow: https://cisess.umd.edu/assets/1/7/22_-_Darek_Yu_Slides.pdf
