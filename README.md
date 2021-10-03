# Analysis on Entering the Real Estate Market in King County
The goal of this repository is to provide business recommendations to a group of real estate brokers who are considering starting a new real estate firm in King County. This analysis examines thousands of house sales over the past 100 years to provide these real estate brokers key insights to keep in mind as they enter the real estate industry.
![kings%20county.jpg](attachment:kings%20county.jpg)

## Business Problem
This group of realtors want to enter the real estate market in King County, but they are unsure what type of houses their new firm will focus on. There are a plethora of options based on the different categories houses can fall under such as price, # of bedrooms and bathrooms, square footage, and location. This analysis was conducted to provide this new company with insights into the trends, performances, history, and future predictions of house prices based on the specific categories these houses fall under.

## Data
This analysis was conducted using data from 1 main source:
- King County House Sales dataset.

The raw csv file of this data can be found in the ```zipped_data``` folder.

The metrics analyzed dealt primarily with each house's descriptive factors such as price, square footage, bedrooms, bathrooms, etc.

The key metrics analyzed were ```log_price```, ```sqft_living```, ```grade_bins```, and ```zipcode_bins```.

This analysis was performed using Python and the code can be found in ```Data Cleaning.ipynb```, ```Data Understanding.ipynb```, and ```Data Analysis.ipynb```.

## Results

### 1. The average house price considering the key metrics analyzed is $519,063.82
![Hist%20Price-2.png](attachment:Hist%20Price-2.png)

### 2. The mean squared error is $166,301.08.

This means that for any given predictions there will be a +/- $166,301.08 margin of error for the real value of the home. I recognize that this is a considerable margin for error, but given the R-squared score for this metric is 0.654, I can confidently confirm that this degree of variance is not significant enough to discount the model as a whole.

### 3. Given the average house price and mean squared error, the following indicates the expected values of homes depending on the key variables examined:

![%25%20change%20in%20price.png](attachment:%25%20change%20in%20price.png)


```python
import pandas as pd
df1 = pd.read_csv('C:/Users/User/Documents/Flatiron/Phase2/Final_Model_OLS_df.csv')
df1=df1.drop(columns = ['Unnamed: 0'])
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Key Variables</th>
      <th>Coefficient</th>
      <th>Percentage Change</th>
      <th>Dollar Change</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Square Foot Living</td>
      <td>0.0003</td>
      <td>0.03</td>
      <td>155.72</td>
      <td>519219.54</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Grade 2: Average</td>
      <td>0.2013</td>
      <td>20.13</td>
      <td>104487.55</td>
      <td>623551.37</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Grade 3: Above Average</td>
      <td>0.4200</td>
      <td>42.00</td>
      <td>218006.80</td>
      <td>737070.62</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Grade 4: Excellent</td>
      <td>0.4512</td>
      <td>45.12</td>
      <td>234201.60</td>
      <td>753265.42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Zipcode: Quad 2</td>
      <td>-0.0778</td>
      <td>-7.78</td>
      <td>-40383.17</td>
      <td>478680.65</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Zipcode: Quad 3</td>
      <td>-0.3378</td>
      <td>-33.78</td>
      <td>-175339.76</td>
      <td>343724.06</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Zipcode: Quad 4</td>
      <td>-0.0377</td>
      <td>-3.77</td>
      <td>-19568.71</td>
      <td>499495.11</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Zipcode: Quad 5</td>
      <td>-0.0355</td>
      <td>-3.55</td>
      <td>-18426.77</td>
      <td>500637.05</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Zipcode: Quad 6</td>
      <td>-0.2265</td>
      <td>-22.65</td>
      <td>-117567.96</td>
      <td>401495.86</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Zipcode: Quad 7</td>
      <td>-0.4331</td>
      <td>-43.31</td>
      <td>-224806.54</td>
      <td>294257.28</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Zipcode: Quad 8</td>
      <td>-0.5408</td>
      <td>-54.08</td>
      <td>-280709.71</td>
      <td>238354.11</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Zipcode: Quad 9</td>
      <td>-0.3321</td>
      <td>-33.21</td>
      <td>-172381.09</td>
      <td>346682.73</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Zipcode: Quad 10</td>
      <td>-0.6747</td>
      <td>-67.47</td>
      <td>-350212.36</td>
      <td>168851.46</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Zipcode: Quad 11</td>
      <td>-0.6297</td>
      <td>-62.97</td>
      <td>-326854.49</td>
      <td>192209.33</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Zipcode: Quad 12</td>
      <td>-0.5376</td>
      <td>-53.76</td>
      <td>-279048.71</td>
      <td>240015.11</td>
    </tr>
  </tbody>
</table>
</div>



# Conclusions

This analysis provides insight to 3 key variables identified: ```Square Footage```, ```Grade```, and ```Zipcode```.

The expected value of homes in King County according to each of the key variables have been analyzed and presented.

# Next Steps

I advise the members of the new real estate firm to evaluate their limitations to evaluate what types of investments they can make given the results of my analysis. 
Once the firm has established their core limitations, I will be able to provide more exact recommendations.

Specifically, if the new firm wanted to target certain zipcodes, I would be able to clean my data further to provide more relevant pricing by zipcode.


```python
README.ipynb.nbconvert
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-9-cb6442643437> in <module>
    ----> 1 README.ipynb.nbconvert
    

    NameError: name 'README' is not defined



```python

```
