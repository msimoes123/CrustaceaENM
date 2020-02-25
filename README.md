# CrustaceaENM
This script contains the R code used to perfom the pre-modeling, modeling and post-modeling analysis of the project "Estimating the future shift patterns of shallow-water and deep-sea Crustacea" by Marianna V. P. Simões, Hanieh Saeedi, Marlon Cobos & Angelika Brandt. The three modeling steps include:

A. Pre modeling: 1. Distribution data capture and cleaning from open-source databases (GBIF and OBIS); 2. Distribution data thinning;3. Oragnization of species folders;4. Split of occcurence into train and test;5. Creation of calibration area ("M") 

B. Modeling: 1. Creation of candidate models; 2. Evaluation of candidate models;  3. Selecting best model base don aic and ROC; 4. Creation of Final models; 5. Transforming final models to binary.

C. Post modeling: 1. Projection changes; 2. Variance in model predictions; 3. Extrapolation analysis (MOP); 
4. Binary MOPs;  5. Subtracting MOP from Final models (post-MOP models); 6. Calculating centroid shift; 7. MOPs summary 
 
## Pre-modeling: 

The pre- modeling phase includes steps on the preparation of occurence data and environemntal data for the creation of ecological niche models. It includes: 

1. Distribution data capture and cleaning from open-source databases (GBIF and OBIS); 
2. Distribution data thinning;
3. Oragnization of species folders;
4. Split of occcurence into train and test;
5. Creation of calibration area ("M") 

## Modeling 

The modeling phase includes:

1. Creation of candidate models; 
2. Evaluation of candidate models;
3. Selecting best model base don aic and ROC;
4. Creation of Final models;
5. Transforming final models to binary.
 
 
 The creation of candidate models (kuenm_cal) concerns the creation of a set of  models that test a broad suites of parameter combinations, such as, distinct regularization multiplier values, various feature classes, and different sets of environmental variables. In this study we tested  126 candidate models per each species, with parameterizations resulted from the combinations of nine regularization multipliers (0.1–1.0 at intervals of 0.2, 2–5 at intervals of 1), seven feature classes representing combinations of linear, quadratic and product, two distinct sets of variables (without topography, ‘set 1’ and including topography, ‘set 2’), with projections created allowing extrapolation and clamping.  
 Following this step we evaluated the models (kuenm_ceval), to select candidate models and their associated parameters to identify the best models based on three distinct criteria: statistical significance (based on partial ROC analyses), prediction ability (we use omission rates, but other metrics, such as overall correct classification rate, can also be used), and model complexity (here evaluated using AICc).
 Selected model parameterizations were the ones that resulted in significant models (partial ROC with E = 5%, 500 iterations, and 50 percent of data for bootstrapping; Peterson et al. 2008), that had omission rates lower than a previously defined error rate (E = 5%, Anderson et al 2003), and the lowest AICc value per each species (Warren et al. 2010), in that order. 
 Then, after selecting parametrizations that produce best models, we created final models (kuenm_mod) for the present and globally projected to 2050 and 2100 for two representative concentration pathway emission scenarios (RCP 26 and 85). 
 
 ## Post-modeling 
The post-modeling phase includes: 

 1. Projection changes; 
 2. Variance in model predictions;
 3. Extrapolation analysis (MOP); 
 4. Binary MOPs; 
 5. Subtracting MOP from Final models (post-MOP models);
 6. Calculating centroid shift
 7. Summarizing the contribution and permutation relevance of variables 
 8. Summarizing the variability found in models (RCPs and Replicates)
 9. Summarizing model changes 
 
 After iobtaining the final models, we performed map algebra to represent how and where models projected in time change compared to the current one (kuenm_projchanges).Moreover, we model variation was assessed and represented geographically following the amount of variance in model predictions that came from replicates and emission scenarios (RCPs). 
 
 To assess the risks of strict extrapolation, we used the mobility-oriented parity metric (MOP; Owens et al. 2013), which consists of measuring similarity between the closest 5% of the environmental conditions of M to each environmental condition in the area of transference.  Areas with higher extrapolative values indicate higher uncertainty; and caution is required when interpreting likelihood of species presence in such areas (Alkishe et al. 2017). 
 Then, we threshold MOP results, considering only areas with zero similarity as strict extrapolation, and masked areas of extrapolation from binary final models, using binary MOPs, creating final binary models with no extrapolation (post-MOP projections). 
 
 ## References 

1. Brandt, A. & Malyutina, M. V. The German–Russian deep-sea expedition KuramBio 
(Kurile Kamchatka biodiversity studies) on board of the RV Sonne in 2012 following
the footsteps of the legendary expeditions with RV Vityaz. Deep Sea Research Part II: 
Topical Studies in Oceanography 111, 1–9 (2015).

2.	Malyutina, M. V. & Brandt, A. Introduction to sojabio (sea of japan biodiversity 
studies). Deep Sea Research Part II: Topical Studies in Oceanography 86–87, 1–9 (2013).

3.	Brandt, A. & Malyutina, M. V. The German–Russian deep-sea expedition KuramBio 
(Kurile Kamchatka biodiversity studies) on board of the RV Sonne in 2012 following
the footsteps of the legendary expeditions with RV Vityaz. Deep Sea Research Part II:
Topical Studies in Oceanography 111, 1–9 (2015).

4.	Malyutina, M. V., Chernyshev, A. V. & Brandt, A. Introduction to the SokhoBio 
(Sea of Okhotsk Biodiversity Studies) expedition 2015. Deep Sea Research Part II: 
Topical Studies in Oceanography 154, 1–9 (2018).

5.	Cobos, M. E., Jiménez, L., Nuñez-Penichet, C., Romero-Alvarez, D. & Simoes, M. 
Sample data and training modules for cleaning biodiversity information. Biodiv. Inf.
13, 49–50 (2018).

6.	Aiello-Lammens, M. E., Boria, R. A., Radosavljevic, A., Vilela, B. & Anderson, R. P. 
spThin: an R package for spatial thinning of species occurrence records for use in 
ecological niche models. Ecography 38, 541–545 (2015).

7.	Barve, N. et al. The crucial role of the accessible area in ecological niche modeling 
and species distribution modeling. Ecol. Modell. 222, 1810–1819 (2011).

8.	Peterson, A. T., Papeş, M. & Soberón, J. Rethinking receiver operating characteristic 
analysis applications in ecological niche modeling. Ecol. Modell. 213, 63–72 (2008).

9.	Anderson, R. P., Lew, D. & Peterson, A. T. Evaluating predictive models of species’ 
distributions: criteria for selecting optimal models. Ecol. Modell. 162, 211–232 (2003).

10.	Warren, D. L. & Seifert, S. N. Ecological niche modeling in Maxent: the importance of 
model complexity and the performance of model selection criteria. Ecol. Appl. 21, 335–342 
(2011).

11.	Owens, H. L. et al. Constraints on interpretation of ecological niche models by 
limited environmental ranges on calibration areas. Ecol. Modell. 263, 10–18 (2013).

12.	Alkishe, A. A., Peterson, A. T. & Samy, A. M. Climate change influences on the 
potential geographic distribution of the disease vector tick Ixodes ricinus. PLoS ONE 
12, e0189092 (2017).

```
