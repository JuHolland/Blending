# Blending 

## Rainfall
CHIRP rasters & stationary rain gauge data

**Data**
- spatial resolution: 5km 
- temporal resolution: dekadal (36/month)

**Normal**

- Data cleaning parameters:
  - `threshold = 400mm` (when remonving outliers, diff between CHIRP and station)
  - unbiasing CHIRP data with ratio `r = mean(station) + c / mean(CHIRP) + c` with `c = 1`
  - Computing residuals `res = CHIRP_U - stations`
- Kriging parameters:
  - Exponential variogram
  - number of neighbours `n = 10`
  - Gaussian smoothing of residuals with `sigma = 2`
  - kriging with `backend = 'C'`

**LTA**

- Data cleaning parameters:
  - Ordinary Linear regression (global for [April - October] dry season)
  - Use OLS to compute residuals
- Kriging parameters:
  - Exponential variogram
  - number of neighbours `n = 10`
  - Gaussian smoothing of residuals with `sigma = 2`
  - kriging with `backend = 'C'`



## Temperature
LST Modis rasters + stationary data

**Data**
- spatial resolution: 1km 
- temporal resolution: dekadal (36/month)

**Normal**

- Data cleaning parameters:
  - unscaling `TDA = TDA * 0.02 - 273.15`
  - OLS to compute residuals
- Kriging parameters:
  - Spherical variogram
  - no neighbours
  - no Gaussian smoothing

**LTA**

- Data cleaning parameters:
  - unscaling `TDA = TDA * 0.02 - 273.15`
  - OLS to compute residuals
- Kriging parameters:
  - Spherical variogram
  - no neighbours
  - no Gaussian smoothing


