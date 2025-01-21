![image](https://github.com/user-attachments/assets/d04fb572-59c3-4826-b83d-5a91247c8903)

# Introduction
HELP International is an international humanitarian NGO that is committed to fighting poverty, and providing the people of developing countries with basic amenities and relief during the time of disasters
and natural calamities.  The NGO desires to Improve The Health and Wealth Of Marginalized Nations all around the Globe. Their aim is to use data insights to identify countries at the epicenter of their target issues. With $30M in donations, the CEO requested to prioritize countries with low GDP (gdpp) and life expectancy for aid distribution, ensuring impactful resource allocation. 


## Data Dictionary
- country: Name of Country
- exports: Exports of goods and services per capita. Given as percentage of the GDP per capita
- Imports: Imports of goods and services per capita. Given as percentage of the GDP per capita
- Income: Net income per person
- Inflation: The measurement of the annual growth rate of the Total GDP
- gdpp: The GDP per capita. Calculated as the Total GDP divided by the total population.
- life_expec: The average number of years a newborn child would live if the current mortality patterns are to remain the same
- child_mort: Death of children under 5 years of age per 1000 live births
- health: Total health spending per capita. Given as percentage of GDP per capita
- total_fer: The number of children that would be born to each woman if the current age-fertility rates remain the same.

## Task

From the NGO's problem statement, I identified and grouped the data 2:

- Countries in critical Conditions grouped together for easy identification
- Determine Countries to priotize in allocating resources

## Action

#### Data Cleaning:
- Handling missing values - This particular dataset provided by the NGO contained no missing values
- Duplicates and/or irrelevant columns - Upon review there were also no duplicated rows in the data set
- Check for and correct anomalies - There were values presented as outliers noted upon review, however looking at the data, they are different data points and different scale of values based on the different countries involved, looking at different GDPs and economic powers, and our aim is to group the data, therefore I decided not to treat them as outliers and left them in the data.

#### Exploratory Data Analysis (EDA):
- Visualize distributions and relationships between features - This was done extensively and it was noted that our data distribution is skewed to both the right, left and uniform. This was also handled in later steps.
- Identify patterns, trends, and potential anomalies - It was seen that the features were strongly correlated to each other, some positively and some negatively. For example, as Child Mortality incresed there was a corresponding increase in Total Fertility. Also as Exports noted higher volumes, they were associated with higher Income levels suggesting that Countries with strong export economies generally enjoy higher incomes.

#### Data Preprocessing:
- Scale/normalize numerical features and encode categorical data -  The standard scaler was used in scaling and normalizing the skewness of the data as all data needs to be presented in size proportionate to their scale for easy interpretation and modelling. 
- Feature Engineering - Some features were grouped together as they have similarity with some other features, I then created new features that fall into three categories:
    - Health: child mortality, health, life expectancy, total fertility rate
    - Trade: imports, exports and 
    - Finance: income, inflation, GDP per capita

## Result
#### Model Evaluation (Interpreting Results):
- Visual Inspection: I proceeded to visualize the clustering results / reduced features to evaluate if meaningful patterns emerge.
  ![image](https://github.com/user-attachments/assets/4920beed-5fb2-4df3-a30b-df2ef6980934)

## Conclusion
The clusters as seen above showed that it was safe to group the countries in the classes listed below:
- 0 : Not a priority (as the values on Child Mortality and Income are almost equal(or on same level) and not low).
- 1 : Requires foreign aid (because it has a high child mortality(low health index) and least income (low wealth index)
- 2 : Do NOT requires foreign aid (this class have the least child mortality (high health index) and the highest income (high wealth index))

I then renamed the different classes to reflect the interpretation stated above and visualized in a map showing the countries in critical Conditions with low GDP (gdpp) and life expectancy and countries to priotize in allocating resources.
