# What Drives Car Fuel Efficiency? An R Analysis

Which characteristics of a car explain its highway fuel economy? This project uses exploratory analysis, a statistical test and linear regression in R to find out.

## Data
The `mpg` dataset that ships with ggplot2: 234 car models from 1999 and 2008, with engine size, cylinders, drive type, vehicle class and highway mpg. There are no missing values.

## Approach
- Explored the distribution of highway mpg and how it varies by engine size, vehicle class and drive type
- Ran a Welch t-test comparing front-wheel-drive and 4-wheel-drive cars
- Built two linear regression models (engine size alone, then engine size, cylinders, drive type and class) on an 80/20 train/test split and compared test RMSE
- Checked model assumptions with residual diagnostic plots

## Tools
R, tidyverse (dplyr, ggplot2), R Markdown

## Key findings
- Engine size is the strongest single predictor. Highway mpg drops by about 3.4 for every extra litre of displacement (R² of 0.56)
- Front-wheel-drive cars average about 28.2 mpg versus 19.2 for 4wd (p far below 0.001), but most of that gap is explained by vehicle class, since 4wd is common in heavy SUVs and pickups
- Adding cylinders, drive type and class raised R² to about 0.83 and cut test RMSE from about 3.5 to 2.3 mpg
- The model underpredicts a few very efficient diesel cars (VW Jetta and New Beetle)

## How to run
1. Open `mpg_fuel_efficiency_r.Rmd` in RStudio or posit.cloud
2. Run `install.packages("tidyverse")` once
3. Click Knit

The knitted output is also included as `mpg_fuel_efficiency_r.html`.

## Limitations
Only 234 cars from two model years, with no weight or fuel type in the model. The results show association, not causation, and shouldn't be applied to modern cars.

## Next steps
Add fuel type and transmission as predictors, try a log-transformed model, use cross-validation, and repeat the analysis for city mpg.
