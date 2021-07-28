# Blending

Blending satellite and stationary data

## Rainfall
CHIRP rasters & stationary raingage data

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
  - kriging with `backend = 'loop'`

**LTA**

## Temperature
LST MODIS data with stationnary data
Normal
LTA
