# Blending 

## Rainfall
CHIRP rasters & stationary rain gauge data

**Data**
- spatial resolution: 5km 
- temporal resolution: dekadal (36/month)

**Normal**

- Data cleaning parameters:
  - `threshold = 400mm` (removing outliers with |CHIRP - station| > threshold)
  - unbiasing CHIRP data with ratio `r = (mean(station) + c) / (mean(CHIRP) + c)` with `c = 1`
  - Computing residuals `res = CHIRP_U - stations`
- Kriging parameters:
  - Exponential variogram
  - number of neighbours `n = 10`
  - Gaussian smoothing of residuals with `sigma = 2`
  - kriging with `backend = 'C'`

**LTA**

- Data cleaning parameters:
  - Ordinary Linear regression (global for dry season)
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


## Countries

**Mozambique**

- Rainfall (exponential): 
  - [1.0, 0.7032	0.4505] - dry season (June - September)
  - [1.0, 3.6629, 0.2701] - wet season (October - May)
- TDA (spherical):
  - [1.0, 5.0386, 0.3083]
- TNA (spherical):
  - [1.0, 1.8506, 0.4516]

**Namibia**

- Rainfall (exponential): 
  - [1.0, 1.3166	0.6115]


**Zimbabwe**

- Rainfall (exponential): 
  - [1.0, 1.8122,	0.5763]

**Cuba**

RESAMPLING: Resampling 5km rasters to 1km rasters
- Rainfall (exponential): (EYE FIT)
  - [1.0, 0.335, 0.3] - dry season (April - November)
  - [1.0, 0.419, 0.3] - wet season (December - March)
  - LTA computed with 1991-2020 data

**Sri Lanka**

- Rainfall (exponential): 
  - [1.0, 0.1197, 0.2218] - dry months (2,3,6,7,8)
  - [1.0, 0.2629, 0.2344] - wet months (1,4,5,9,10,11,12)
  - LTA computed with 2016-2020 data
- TDA (exponential): 
  - [1.0, 1.566, 0.4017] 
  - LTA computed with 2016-2020 data
- TNA (exponential)
  - [1.0, 1.3283, 0.4756]
  - LTA computed with 2016-2020 data


## degree-km conversion

- Mozambique: 109.5
- Namibia:    106.5
- Zimbabwe:   108
- Cuba:       107.5
- Sri Lanka:   111



