# Final-Project-Tableau

## Project/Goals
The goal of this project was to utilize my knowledge of data analysis to uncover trends in "Causes of Death" data using Tableau and a Kaggle dataset which contains 40 years of data across 210 countries.

**Live Visualizations can be found on Tableau Public** (or see `.twb` file included above):
- [Most Influential Cause of Death (by Year, Category and/or Region)](https://public.tableau.com/app/profile/matthew.corr6019/viz/MostInfluentialCauseofDeathbyCategory/DeathsbyCapitaperRegion?publish=yes)
- [Advancments in Infectious Disease Control](https://public.tableau.com/app/profile/matthew.corr6019/viz/AdvancementsinInfectiousDiseaseControl/AdvancementsinMedicalReasearch?)
- [Most Common way to Die by Country](https://public.tableau.com/app/profile/matthew.corr6019/viz/TopCauseofDeathperCountry/MostDeathsRecordedbyCause)
- [Visuals Used for EDA](https://public.tableau.com/app/profile/matthew.corr6019/viz/CauseofDeathEDAVisuals/EDAVisuals?publish=yes)

## Process

### Initial Data Collection & Setup
1. Downloaded [Cause of Death dataset from Kaggle](https://www.kaggle.com/datasets/ivanchvez/causes-of-death-our-world-in-data) (see `20222703 Causes Of Death Clean Output V2.0.csv` in `data/`).
2. Decided on using the countries [ISO-3166 Alpha-3](https://www.iban.com/country-codes) code as a unique identifier for relating my databases to one another.
3. Exported country information records from [statisticstimes.com](https://statisticstimes.com/geography/countries-by-continents.php). Used to associate each Alpha-3 code (e.g. CAN for Canada) to a continent & region for better analysis (see `country_info.csv` in `data/`)
4. Used World Population dataset from [kaggle.com](https://www.kaggle.com/datasets/iamsouravbanerjee/world-population-dataset?resource=download) (see `world_population.csv` in `data/`), this provided me with additional datapoints such as:
   - Area (KM<sup>2</sup>)
   - Density (KM<sup>2</sup>)
   - Population Growth Rate
   - Population (1 column per each decade)
5. Finally I created my own "Cause of Death Category" table (see `cause_of_death_categories.csv` in `data/`). This table segments the 33 causes of death into 7 categories for easier analysis and even inter-category comparison (i.e. Which infectious disease is more deadly).

### EDA
1. Thankfully due to the trusted sources of this data ("10.0" usability according to Kaggle), there were very few issues with the data
2. Removed rows from the cause of death data that did not contain an Alpha-3 country code.
3. Created a custom population column that calculates the average population from 1980-2020 for any given country (same time frame as the Cause of Death dataset). This will be used later for per capita calculations. Achieved with `([2020 Population]+[2010 Population]+[2000 Population]+[1990 Population])/4`. This had to be done as the population data did not have a per breakdown. _This means all per capita breakdowns are based on a 40 year population average_

### Creation of Visualizations
1. Straight forward process once Tableau interface is understood, some custom measures were needed to remove certain values/aggregate others.
2. Visualizations can be found in the attached presentation, `.twb` file or by using the links listed under the "Project/Goals" heading

## Results

I decided to go with option #2, choosing the [Cause of Death dataset](https://www.kaggle.com/datasets/ivanchvez/causes-of-death-our-world-in-data) from Kaggle. When I started poking around the data Immediatly noticed that I would need to bring in population data as trying to perform any analysis with India or China included blew the graphs out of proportion. Once I had gathered the population data and performed the `number of deaths/population` calculation the visuals became much more insightful. I ended up utilizing the map visual heavily because of the geographical nature of the data, however I also took advantage of heatmaps, segmented bar graphs, scatter plots and line chats with forecasting.

I found that the use of categorizing causes of death was a useful technique that let me hone in on various trends, here are some general patterns I found:

- Cardiovascular-related diseases caused the overwhelming majority of deaths with 500,000,000 listed over 40 years
- There was no strong correlation between the size of a country and the number of deaths per capita
- Countries that have higher population growth tend to have more deaths per capita (makes sense logically, more people = more death.). Validated with a 0.85 R-Squared factor
- It became very easy to spot diasters that resulted in large amount of casualties when limiting to a specific time period, region and category of death. See [Most Influential Cause of Death (by Year, Category and/or Region)](https://public.tableau.com/app/profile/matthew.corr6019/viz/MostInfluentialCauseofDeathbyCategory/DeathsbyCapitaperRegion?publish=yes) or slide 4 in `cause_of_death_exploration_slides.pdf` for examples

I decided to take a slightly deeper dive into the Infectious deeases category as I found the number to vary quite dramatically over time depending on the region. I then comparison between overall death rate (which should steadily rise over time as population preportionally increases) compared deathrate relating to infectious diseases (see [Advancments in Infectious Disease Control](https://public.tableau.com/app/profile/matthew.corr6019/viz/AdvancementsinInfectiousDiseaseControl/AdvancementsinMedicalReasearch?)). What you'll see is that while death rate does tend to increase over time, deaths due to infectious diseases tends to fall (Except for periods of outbreaks like the HIV/AIDS crisis in Africa, which peaked in the early 2000's).

## Challenges 
- Took a bit of time to get used to Tableaus interface as a user of Power BI in the past.

- Finding sufficient & detailed population data
  - The one I found only had population once per decade which made it harder to do per capita calculations and made the results less accurate

- Forming a story with the data I had been given. It was easy to make visuals, but hard to make meaningful connections between them.

## Future Goals

- If I had a little more time I would have looked through additional data sources that I could have pulled in, such as GDP, Unemployment or Education statistics.

- I would have liked to connect my visuals together a little better to tell a more cohesive story