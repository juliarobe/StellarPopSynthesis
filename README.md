# Stellar Population Synthesis

The goal of this project was to analyze the relationships between galaxy properties by simulating galaxy evolution using the Bruzual & Charlot 2003 (BC03) stellar population synthesis models.

I used different types of Star Formation Rates (SFR) and different metallicities to model the evolution of 50 galaxies. The types of SFR models I employed were:

- Istantaneous burst (the Single Stellar Population (SSP) model)
- Exponential declining with tau=1, 2 and 3 Gyrs
- Single burst of length tau=2 Gyrs
  
The BC03 models I used output tables of data (such as color and stellar mass) as a function of age. For each SFR + metallicity combination, I found the predicted age at which the model’s evolution corrected g-r color agrees with the actual age of the galaxy.

## Age-Metallicity Degeneracy:

The age-metallicity degeneracy suggests that, for a given observed property (e.g., color), there could be multiple combinations of age and metallicity that result in a similar observed value. We see there is indeed an age-metallicity degeneracy since, for a given g-r color, various SFR models + metallicity combinations give varying ages.

In the table below, which is just a snippit of a larger table that contains the predicted ages for each galaxy based on the SFR model + metallicity combination, the column names (0 - 9) each represent a different galaxy. The row names on the left hand side (i.e.ssp_m122) represent different SFR model + metallicity combinations. The data within the table all represent the best SFR-model predicted age for the galaxy given the g-r color.

<h2 style="text-align: center;">Age-Metallicity Table: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/age_met_table.png" width="500">

As we can see, based on the given g-r color value, different SFR model + metalicity combinations can give very different predicted ages.

Next, I use the evolution corrected g-r color values for 50 galaxies to find which model best fits that color. To do this, I loaded the model data, calculated the predicted colors, found the best-fit model for each galaxy, and stored the results in a data frame. Then, I can plot the best predicated age versus the true age of the galaxy sample!

<h2 style="text-align: center;">Best Age versus True Age: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/trueage_vs_bestage.png" width="500">


We see that most of the galaxies are best described by one of two SFR’s: the younger galaxies are modeled best by an Exponential declining SFR with a timescale τ = 1Gyr, while the older galaxies seem to better modeled by the Single Stellar Population (instantaneous burst) SFR. This could indicate a shift in galaxy evolution, where galaxies transition from a period of intense star formation to a more quiescent phase.

## K-correction:

Next, for each SFR, I estimated the K-correction in the r and g band for each of the same 50 galaxies using the BC03 models. The BC03 models return the K-correction as a function of redshift and age.

<h2 style="text-align: center;">R-band K-correction: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/kcorr_rband.png" width="500">

<h2 style="text-align: center;">G-band K-correction: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/kcorr_gband.png" width="500">

## $$\frac{M_*}{L}$$ vs $$L$$ in bins of $$\Delta t_{form} = 1 Gyr$$

From the age and redshift values, I compute the formation time of each galaxy. Once I have the formation times calculated, I can plot $$\frac{M_*}{L}$$ vs $$L$$ in bins of $$\Delta t_{form} = 1 Gyrs$$

<h2 style="text-align: center;">$$\frac{M_*}{L}$$ vs $$L$$ : </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/ml_vs_L_alloneplot.png" width="500">


<h2 style="text-align: center;">$$\frac{M_*}{L}$$ vs $$L$$ Bin Separated: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/ml_vs_L_tformbin_cluster.png" width="500">

We can see that M/L increases with decreasing luminosity (especially in the top left plot). We can also see that M/L is larger for older galaxies (in all plots).

This suggests that the stellar populations in these galaxies are increasingly dominated by low-mass stars over time. As a galaxy evolves, the massive stars that formed early exhaust their fuel and evolve into lower-mass stars. New generations of stars (including low-mass stars) may continue to form, and the cumulative effect is an increasing number of low-mass stars, which have lower luminosities but longer lifetimes. Thus, they continue to shine for extended periods, and their contribution becomes more significant over time.

## Color vs. Velocity Dispersion
Finally, I fit a linear function to the g-r color versus velocity dispersion and computed the residuals of the color-velocity dispersion by subtracting the fit values from the color values and plotted the residuals vs. the corresponding age of the galaxy in bins of absolute magnitude.

<h2 style="text-align: center;">Color versus Velocity Dispersion: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/colore_vs_vdisp.png" width="500">

<h2 style="text-align: center;">Residuals vs. Age in bins of Absolute Magnitude: </h2>
<img class="img-fluid" style="display: block; margin: 0 auto;" src="./images/resid_vs_age_magbins.png" width="500">

This investigation found a positive correlation between color and velocity dispersion. The residuals of the color-velocity dispersion relation showed a dependence on galaxy age, with older galaxies exhibiting larger and more positive residuals.

This project demonstrated the power of stellar population synthesis models in understanding galaxy evolution and the complex relationships between galaxy properties. The findings of this project can be used to inform future studies of galaxy evolution and the formation of galaxies in the early universe.
