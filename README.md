#  Expanding on event-based monitoring: using intensity data to quantify phenological expression

### Erin R. Zylstra, Ellen G. Denny, and Theresa M. Crimmins

### In review

### Code/Data DOI
_______________________________________________________________________________________________________________________________________

## Abstract:
The USA National Phenology Network (USA-NPN) invites observers to document the phenological status of individual plants as well as the extent to which phenological states are expressed, termed intensity. Phenological intensity data enrich our understanding of the changes plants undergo throughout the growing season, providing critical insights about ecological interactions and climate change impacts beyond what is possible by evaluating phenological onsets alone. Intensity data are reported as binned counts or percentages (e.g., 3–10 flowers, 25–49% canopy cover) and facilitate assessments of phenological “peaks”, the progression of phenological stages, and spatiotemporal variation in phenophase expression. Here, we describe the structure of USA-NPN intensity data, identify potential questions that can be addressed, and outline methods for analysis given challenges that stem from a large-scale, volunteer-based data collection process. In particular, we highlight the use of ordinal regression models, ordered beta regression models, and linear mixed-effect models and we illustrate how these data can enhance our understanding of plant phenology at broad spatial scales with three use cases. Although currently underutilized, phenological intensity data hold great potential to enhance investigations of resource availability, species interactions, and functioning of terrestrial plant ecosystems. 
_______________________________________________________________________________________________________________________________________

## Code
Here, we provide the code needed to download USA-NPN data and run analyses for each of the three case studies. 
1. [saguaro-flowers.R](saguaro-flowers.R): R code to download status-intensity data for saguaro cacti in Arizona, 2016-2015, and use ordinal regression to model the probably a saguaro produces few (<11), some (11-100), or many flowers (>100) at least once that year as a function of winter precipitation, winter temperatures, and elevation. 
2. [grsm-leaf-canopy.R](grsm-leaf-canopy.R): R code to download status-intensity data for 6 species of deciduous trees in Great Smoky Mountains NP, 2016-2025 and use beta regression models to explore spatiotemporal variation in canopy closure rates and the effects of accumulated spring warmth. 
3. [redbud-open-flowers.R](redbud-open-flowers.R): R code to download status-intensity data for eastern redbud trees in the eastern U.S., 2016-2025 and use linear mixed-effect models to explore variation in the magnitude and timing of peak flowering (open flower abundance). 

## Phenology and Weather Data
Phenological data were downloaded from USA-NPN via the <i>rnpn</i> package on 17 September 2026. R code used to download the data can be found in the scripts listed above. Original data files were slightly modified (missing state codes were filled in; unnecessary columns removed) and then saved as csv files in the [npn-data](npn-data) folder. Information about fields in the USA-NPN status-intensity data products can be found at [https://www.usanpn.org/data/observational](https://www.usanpn.org/data/observational). 

Weather data were obtained from [PRISM](https://www.prism.oregonstate.edu) at 800-m spatial resolution via their web portal on 17 September 2026. csv files with geographic coordinates for sites included in each case study, along with folders that contain the original PRISM datafiles, can be found in the [weather-data](weather-data) folder. 

## Other Data
Several shapefiles were needed to fill in missing state codes in the phenology data or create figures in the manuscript. 

- [states](states): U.S. state boundaries
- [sonoran-desert](sonoran-desert): Geographic boundary of the Sonoran Desert region in the U.S. and Mexico
- [np-boundary](np_boundary): Political boundary of Great Smoky Mountains National Park

## Output
- [output](output): folder that contains output from each of the case studies: figures (png files) and parameter estimates (csv files).
- [grsm-models](grsm-models): folder that contains RData files, each containing a brmsfit object (posterior draws, model formula, Stan code, and relevant data from a model run using the <i>ordbetareg</i> package).
