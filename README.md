# Analysis Introduction: Anti-Cancer Medication Analysis

You're just joined Pymaceuticals, Inc., a new pharmaceutical company that specializes in anti-cancer medications. Recently, it began screening for potential treatments for squamous cell carcinoma (SCC), a commonly occurring form of skin cancer.

As a senior data analyst at the company, you've been given access to the complete data from their most recent study. In this study, 249 mice who were identified with SCC tumors received treatment with a range of drug regimens. Over the course of 45 days, tumor volume development was observed and measured. The purpose of this study was to compare the performance of Pymaceutical's drug of interest, Capomulin, against the other treatment regimens.

The executive team has tasked you with generating all of the tables and figures needed for the technical report of the clinical study. They have also asked you for a top-level summary of the study results.

Included in this analysis, is our [Pymaceutical's presentation](https://revealjs.com/demo/?view=scroll). In this presentation, you will see a interactive summary of this report.

# Instructions

This assignment is broken down into the following tasks:

- Prepare the data

- Generate summary statistics

- Create bar charts and pie charts

- Calculate quartiles, find outliers, and create a box plot

- Create a line plot and a scatter plot

- Calculate correlation and regression

- Submit your final analysis

# Prepare the Data

1. Run the provided package dependency and data imports, and then merge the `mouse_metadata` and `study_results` dataframes into a single dataframe

2. Display the number of unique mice IDs in the data, and then check for any mouse ID with duplicate time points. Display the data associated with that mouse ID, and then create a new dataframe where this data is removed. Use this cleaned dataframe for the remaining steps.

3. Display the updated number of unique mice IDs.



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age_months</th>
      <th>Weight (g)</th>
      <th>Timepoint</th>
      <th>Tumor Volume (mm3)</th>
      <th>Metastatic Sites</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1880.00</td>
      <td>1880.00</td>
      <td>1880.00</td>
      <td>1880.00</td>
      <td>1880.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>12.76</td>
      <td>25.66</td>
      <td>19.61</td>
      <td>50.44</td>
      <td>1.02</td>
    </tr>
    <tr>
      <th>std</th>
      <td>7.18</td>
      <td>3.94</td>
      <td>14.09</td>
      <td>8.91</td>
      <td>1.14</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.00</td>
      <td>15.00</td>
      <td>0.00</td>
      <td>22.05</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.00</td>
      <td>25.00</td>
      <td>5.00</td>
      <td>45.00</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>13.00</td>
      <td>27.00</td>
      <td>20.00</td>
      <td>48.93</td>
      <td>1.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>19.25</td>
      <td>29.00</td>
      <td>30.00</td>
      <td>56.32</td>
      <td>2.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>24.00</td>
      <td>30.00</td>
      <td>45.00</td>
      <td>78.57</td>
      <td>4.00</td>
    </tr>
  </tbody>
</table>
</div>





    

# Generate Summary Statistics

Create a dataframe of summary statistics. Remember, there is more than one method to produce the results you're after, so the method you use is less important than the result.

Your summary statistics should include:

- A row for each drug regimen. These regimen names should be contained in the index column.

- A column for each of the following statistics: mean, median, variance, standard deviation, and SEM of the tumor volume.



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Mean Tumor Volume</th>
      <th>Median Tumor Volume</th>
      <th>Tumor Volume Variance</th>
      <th>Tumor Volume Std. Dev.</th>
      <th>Tumor Volume SEM</th>
    </tr>
    <tr>
      <th>Drug Regimen</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Capomulin</th>
      <td>40.68</td>
      <td>41.56</td>
      <td>24.95</td>
      <td>4.99</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>Ceftamin</th>
      <td>52.59</td>
      <td>51.78</td>
      <td>39.29</td>
      <td>6.27</td>
      <td>0.47</td>
    </tr>
    <tr>
      <th>Infubinol</th>
      <td>52.88</td>
      <td>51.82</td>
      <td>43.13</td>
      <td>6.57</td>
      <td>0.49</td>
    </tr>
    <tr>
      <th>Ketapril</th>
      <td>55.24</td>
      <td>53.70</td>
      <td>68.55</td>
      <td>8.28</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Naftisol</th>
      <td>54.33</td>
      <td>52.51</td>
      <td>66.17</td>
      <td>8.13</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Placebo</th>
      <td>54.03</td>
      <td>52.29</td>
      <td>61.17</td>
      <td>7.82</td>
      <td>0.58</td>
    </tr>
    <tr>
      <th>Propriva</th>
      <td>52.32</td>
      <td>50.45</td>
      <td>43.85</td>
      <td>6.62</td>
      <td>0.54</td>
    </tr>
    <tr>
      <th>Ramicane</th>
      <td>40.22</td>
      <td>40.67</td>
      <td>23.49</td>
      <td>4.85</td>
      <td>0.32</td>
    </tr>
    <tr>
      <th>Stelasyn</th>
      <td>54.23</td>
      <td>52.43</td>
      <td>59.45</td>
      <td>7.71</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>Zoniferol</th>
      <td>53.24</td>
      <td>51.82</td>
      <td>48.53</td>
      <td>6.97</td>
      <td>0.52</td>
    </tr>
  </tbody>
</table>
</div>





<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="5" halign="left">Tumor Volume (mm3)</th>
    </tr>
    <tr>
      <th></th>
      <th>mean</th>
      <th>median</th>
      <th>var</th>
      <th>std</th>
      <th>sem</th>
    </tr>
    <tr>
      <th>Drug Regimen</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Capomulin</th>
      <td>40.68</td>
      <td>41.56</td>
      <td>24.95</td>
      <td>4.99</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>Ceftamin</th>
      <td>52.59</td>
      <td>51.78</td>
      <td>39.29</td>
      <td>6.27</td>
      <td>0.47</td>
    </tr>
    <tr>
      <th>Infubinol</th>
      <td>52.88</td>
      <td>51.82</td>
      <td>43.13</td>
      <td>6.57</td>
      <td>0.49</td>
    </tr>
    <tr>
      <th>Ketapril</th>
      <td>55.24</td>
      <td>53.70</td>
      <td>68.55</td>
      <td>8.28</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Naftisol</th>
      <td>54.33</td>
      <td>52.51</td>
      <td>66.17</td>
      <td>8.13</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Placebo</th>
      <td>54.03</td>
      <td>52.29</td>
      <td>61.17</td>
      <td>7.82</td>
      <td>0.58</td>
    </tr>
    <tr>
      <th>Propriva</th>
      <td>52.32</td>
      <td>50.45</td>
      <td>43.85</td>
      <td>6.62</td>
      <td>0.54</td>
    </tr>
    <tr>
      <th>Ramicane</th>
      <td>40.22</td>
      <td>40.67</td>
      <td>23.49</td>
      <td>4.85</td>
      <td>0.32</td>
    </tr>
    <tr>
      <th>Stelasyn</th>
      <td>54.23</td>
      <td>52.43</td>
      <td>59.45</td>
      <td>7.71</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>Zoniferol</th>
      <td>53.24</td>
      <td>51.82</td>
      <td>48.53</td>
      <td>6.97</td>
      <td>0.52</td>
    </tr>
  </tbody>
</table>
</div>



# Creating the Bar Chart

Generate two bar charts. Both charts should be identical and show the total number of rows (Mouse ID/Timepoints) for each drug regimen throughout the study.

   - Create the first bar chart with the Pandas `dataframe.plot()` method.
  
   - Create the second bar chart with Matplotlib's `pyplot` methods.





    
![bar_chart](https://github.com/adelao747/drug_analysis/assets/113153195/0322dc65-1927-4663-b2c9-a483a63ce63b)


# Creating the Pie Chart

Generate two pie charts. Both charts should be identical and show the distribution of female versus male mice in the study.

    - Create the first pie chart with the Pandas `dataframe.plot()` method.

    - Create the second pie chart with Matplotlib's `pyplot` methods.





    
![pie_chart](https://github.com/adelao747/drug_analysis/assets/113153195/746d3868-7e7c-4f92-822d-5f0a19c7404b)





# Calculate Quartiles and Finding Outliers

Calculate the final tumor volume of each mouse across four of the most promising treatment regimens: Capomulin, Ramicane, Infubinol, and Ceftamin. Then, calculate the quartiles and IQR, and determine if there are any potential outliers across all four treatment regimens.

Use the following subsets:
    - Create a grouped dataframe that shows the last (greatest) time point for each mouse. Merge this grouped dataframe with the original cleaned dataframe.

    - Create a list that holds the treatment names as well as a second, empty list to hold the tumor volume data.

    - Loop through each drug in the treatment list, locating the rows in the merged dataframe that correspond to each treatment. Append the resulting tumor volumes for each drug to the empty list.

    - Determine outliers by using the upper and lower bounds, and then print the results.

    Values below 25.35% could be outliers.
    Values above 87.67% could be outliers.
    

# Creating the Box Plot

Using Matplotlib, generate a box plot that shows the distribution of the final tumor volume for all the mice in each treatment group. Highlight any potential outliers in the plot by changing their color and style.

Hint: All four box plots should be within the same figure. Use this [Matplotlib documentation page](https://matplotlib.org/stable/gallery/statistics/boxplot_demo.html) for help with changing the style of the outliers.


![box_plot](https://github.com/adelao747/drug_analysis/assets/113153195/aa9ec6cb-a185-44f8-89d1-a8994730374f)


    


# Creating a Line Plot

Select a single mouse that was treated with Capomulin, and generate a line plot of tumor volume versus time point for that mouse.





    
![line_plot](https://github.com/adelao747/drug_analysis/assets/113153195/897c2a4c-ea0f-48e2-81b0-de350c0b4b3f)


# Creating a Scatter Plot

Generate a scatter plot of mouse weight versus average observed tumor volume for the entire Capomulin treatment regimen.





    
![scatter_plot](https://github.com/adelao747/drug_analysis/assets/113153195/011eefeb-da46-443e-b953-76556800a0c0)


# Calculate Correlation and Regression

1. Calculate the correlation coefficient and linear regression model between mouse weight and average observed tumor volume for the entire Capomulin treatment regimen.

2. Plot the linear regression model on top of the previous scatter plot.





    
![linear_regression](https://github.com/adelao747/drug_analysis/assets/113153195/54662015-74ec-47f3-88d0-d373c2c8322f)


    The correlation between the mouse weight and the average tumor volume is 0.84
    

# Hints and Considerations

- Use the code comments in the provided starter file to guide you through this assignment.

- Use proper labeling for your plots. Include plot titles, axis, labels, legend labels, x-axis and y-axis limits, etc.

- As you work on this assignment, refer to Stack Overflow and the Matplotlib documentation for guidance. These are essential tools in every data analyst's tool belt.

- Remember that there are many ways to approach a data problem: One way is to break up your task into micro tasks. For example, ask yourself questions like the following:

    - How does my dataframe need to be structured so it has the correct x-axis and y-axis?
 
    - How do I build a basic scatter plot?
 
    - How do I add label to a scatter plot?
 
    - Where in the dataframe can I find the names that will go into the labels?
 
    - Get help when you need it! Your instructional team is there for you.

# References

Data generated by [Mockaroo](https://mockaroo.com/), LLC (2022). Realistic Data Generator.



