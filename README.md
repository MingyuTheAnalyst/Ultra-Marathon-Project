# Ultra-Marathon-Project

### Project Overview

In this analytical project, we look into the 'The Big Dataset of Ultra-Marathon Running' from Kaggle to explore the performances of athletes who participated in 50km and 50-mile races in the USA during 2020. Our objective is to understand how variables such as age, gender, and season impact the performance of these ultra-marathon runners.


### Data Sources
The big dataset of ultra-marathon running
 - A huge collection of over 7M race records registered between 1798 and 2022
 - https://www.kaggle.com/datasets/aiaiaidavid/the-big-dataset-of-ultra-marathon-running/discussion/420633

### Tools

- Python
  - Pandas
  - Seaborn(histplot, displot, violinplot, lmplot)

- Jupyter Notebook

### Data Cleaning/Preparation
- Show and combine 50km/51mi with isin in 2020
  ```python
  df[(df['Event distance/length'].isin(['50km','50mi'])) & (df['Year of event'] == 2020)]
  ```
- Clean up athlete age
  ```python
  df2['athlete_age'] = 2020 - df2['Athlete year of birth']
  ```
- Clean up null value
  ```python
  df2.isna().sum()
  df2[df2['athlete_age'].isna()==1]
  df2 = df2.dropna()
  ```
- Check for duplicates
  ```python
  df2[df2.duplicated() == True]
  ```
- Rename Columns
  ```python
  df2 = df2.rename(columns = {'Year of event':'year' ,
                            'Event dates':'race_day' ,
                            'Event name':'race_name',
                            'Event distance/length':'race_length',
                            'Event number of finishers':'race_number_of_finishers',
                            'Athlete performance':'athlete_performance',
                            'Athlete gender':'athlete_gender',
                            'Athlete average speed':'athlete_average_speed',
                            'Athlete ID':'athlete_id'
                           })
  ```

### Exploration Data Analysis

- Race Length Distribution: This histogram provided a basic overview of the distribution of race lengths in our dataset. It helped us understand the most common distances that athletes competed in.

  <img width="500" alt="Screenshot 2024-01-31 at 9 21 19 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/27f0b905-691f-4fc9-a0c2-94346a8aed53">

- Race Length by Gender: By adding a hue for athlete gender, this histogram allowed us to compare the frequency of different race lengths for male and female athletes. This visual highlighted any disparities in participation between genders across different race lengths.

  <img width="500" alt="Screenshot 2024-01-31 at 9 22 01 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/0618c64d-0135-41ff-bf2b-cc5089be0d6f">

- Speed Distribution for 50-Mile Races: This distribution plot focused on athletes who ran 50-mile races, showcasing how their average speeds varied. It was useful in understanding the range and commonality of speeds in this specific race length.
  
  <img width="500" alt="Screenshot 2024-01-31 at 9 22 51 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/bc50ffb4-7767-49cb-bebd-7aa32000b5d2">

- Average Speed by Race Length and Gender: The violin plot provided a nuanced view of the distribution of average speeds for different race lengths, split by gender. This plot was instrumental in highlighting differences in performance between male and female athletes in various race lengths.

  <img width="500" alt="Screenshot 2024-01-31 at 9 24 12 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/f6074150-94c7-4e14-8ef4-eb7b5e9b88f2">

- Average Speed versus Age by Gender: This linear regression plot showed the relationship between athlete age and average speed, with a separate line for each gender. It helped in identifying trends and potential correlations between age and performance, differentiated by gender.

  <img width="500" alt="Screenshot 2024-01-31 at 9 25 25 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/2aa68feb-a6f8-4452-93c1-d31f9e85d386">

- Difference in speed for the 50k, 50mi male to female

  <img width="352" alt="Screenshot 2024-01-31 at 9 30 01 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/3747db47-51d9-47cc-a67d-4e02bbc22bd2">

- What age groups are the best or worst in the 50mi Race
  
  <img width="223" alt="Screenshot 2024-01-31 at 9 30 22 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/14c1c910-29aa-4c8a-8010-1d432fd8d3f8">
  
  <img width="224" alt="Screenshot 2024-01-31 at 9 30 33 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/a4727c2d-24d9-409f-a13d-e7df89663921">

- Difference in season

  <img width="226" alt="Screenshot 2024-01-31 at 9 30 49 PM" src="https://github.com/MingyuTheAnalyst/Ultra-Marathon-Project/assets/88122148/c1d445c1-65e6-44f5-8f2e-5fc4d2b5435f">


### Results/Findings

Our analysis, informed by a series of charts and graphs, yielded several significant insights into the ultra-marathon races held in the USA in 2020:

- Race Participation: We discovered that the number of athletes participating in 50km races was notably higher than those in 50mi races. This suggests a greater preference or accessibility among ultra-marathon runners towards the shorter of the two ultra distances.

- Gender Disparity in Participation: The data revealed a significant gender gap in race participation, with male athletes participating at more than double the rate of female athletes. This finding indicates a considerable disparity in engagement between genders in ultra-marathon running.

- Average Speed in 50mi Races: For the 50mi races, a large proportion of athletes maintained an average speed between 6-8. This range appears to be a common performance benchmark in these endurance events.

- Overall Average Speed by Gender: The analysis showed that on average, male athletes ran faster than their female counterparts. Specifically, in 50km races, the average speed for men was 7.73 compared to 7.08 for women. This highlights potential physiological and performance differences between genders.

- Peak Performance by Age: A notable peak performance was observed from a 29-year-old athlete who clocked an impressive speed of 7.90. On the other end of the spectrum, the slowest recorded speed was 5.47 by a 70-year-old participant, illustrating the impact of age on endurance running capabilities.

- Speed Variation by Season: Seasonal analysis indicated that autumn races had the highest average speed at 7.51, while the summer, typically hotter, recorded the lowest average speed at 6.50. This variation suggests a potential influence of weather conditions on runner performance.

- These findings provide a comprehensive overview of the performance dynamics in the ultra-marathon races and highlight important factors such as gender, age, and season, which seem to play a significant role in the athletes' performance.

### Limitations

In our analysis of the ultra-marathon data, we faced a few challenges:

- Mixed Distance Units: The data used both kilometers and miles for race distances, making it hard to compare them directly.

- Unclear Speed Units: It was not clear if the speed was in miles per hour or kilometers per hour, which made understanding the athletes' performance tricky.

- Incomplete Age Information: We only had the athletes' birth years, not their exact birthdays, so calculating their exact age during the races was difficult.

These issues limited how deeply we could understand and analyze the data.
