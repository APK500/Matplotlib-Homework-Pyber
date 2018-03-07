

```python
# Import the dependencies#

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import csv



#import our CSV data files and set the paths#
ride_csv= "raw_data/ride_data.csv"
city_csv= "raw_data/city_data.csv"

#read csvs into df for reference#
ride_df = pd.read_csv(ride_csv)
city_df = pd.read_csv(city_csv)

#merge dataframes, using an outer merge#
data = pd.merge(ride_df,city_df, on='city', how='outer')



```


```python
#Reset our index to the "City" column#
data = data.set_index('city')
data
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
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
      <th>driver_count</th>
      <th>type</th>
    </tr>
    <tr>
      <th>city</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Sarabury</th>
      <td>2016-01-16 13:49:27</td>
      <td>38.35</td>
      <td>5403689035038</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-07-23 07:42:44</td>
      <td>21.76</td>
      <td>7546681945283</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-04-02 04:32:25</td>
      <td>38.03</td>
      <td>4932495851866</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-06-23 05:03:41</td>
      <td>26.82</td>
      <td>6711035373406</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-09-30 12:48:34</td>
      <td>30.30</td>
      <td>6388737278232</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-08-04 00:25:52</td>
      <td>27.20</td>
      <td>2429366407526</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-07-25 10:44:01</td>
      <td>17.73</td>
      <td>4467299640441</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-06-22 16:24:01</td>
      <td>23.94</td>
      <td>6153395712431</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-01-27 17:46:45</td>
      <td>16.39</td>
      <td>8220809448298</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-04-26 11:31:30</td>
      <td>21.80</td>
      <td>5969441875705</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-08-14 19:56:59</td>
      <td>7.83</td>
      <td>4979570237054</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-01-06 03:02:55</td>
      <td>5.19</td>
      <td>9988466326333</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-03-29 15:47:35</td>
      <td>17.00</td>
      <td>3574423871181</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-11-20 11:44:23</td>
      <td>28.47</td>
      <td>3793266633941</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-07-17 20:41:06</td>
      <td>17.79</td>
      <td>9661023488490</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-11-06 02:23:59</td>
      <td>19.48</td>
      <td>7305651789766</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-09-26 07:30:31</td>
      <td>26.71</td>
      <td>6310253827816</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-06-04 20:50:52</td>
      <td>14.19</td>
      <td>8765571028809</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-01-22 23:12:06</td>
      <td>38.40</td>
      <td>1176229756048</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-03-29 19:07:55</td>
      <td>20.56</td>
      <td>7019491956393</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-10-18 04:33:23</td>
      <td>37.50</td>
      <td>1054393799736</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-09-30 20:41:18</td>
      <td>44.32</td>
      <td>2103508227691</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-07-30 10:37:38</td>
      <td>25.99</td>
      <td>5233926699781</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-04-01 07:15:24</td>
      <td>6.94</td>
      <td>1931215121299</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-11-23 03:08:59</td>
      <td>37.17</td>
      <td>9141412183460</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-10-23 02:40:28</td>
      <td>17.23</td>
      <td>1977978528067</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>Sarabury</th>
      <td>2016-04-06 21:02:54</td>
      <td>7.14</td>
      <td>6096364843852</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>South Roy</th>
      <td>2016-01-02 18:42:34</td>
      <td>17.49</td>
      <td>4036272335942</td>
      <td>35</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>South Roy</th>
      <td>2016-12-03 08:39:02</td>
      <td>32.88</td>
      <td>7098916182845</td>
      <td>35</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>South Roy</th>
      <td>2016-11-20 02:09:58</td>
      <td>6.81</td>
      <td>6512612750531</td>
      <td>35</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>2016-11-28 09:09:15</td>
      <td>37.76</td>
      <td>804829686137</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>2016-09-08 19:19:38</td>
      <td>30.59</td>
      <td>8211833105097</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>2016-03-02 22:09:34</td>
      <td>36.61</td>
      <td>5500269118478</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>2016-06-22 07:45:30</td>
      <td>34.54</td>
      <td>684950063164</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-04-01 21:21:37</td>
      <td>51.01</td>
      <td>612689673941</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-04-26 09:35:48</td>
      <td>42.09</td>
      <td>9465134041656</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-06-24 21:09:09</td>
      <td>50.03</td>
      <td>9224879345166</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-06-10 18:27:03</td>
      <td>29.25</td>
      <td>4071225680519</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-02-21 18:20:14</td>
      <td>42.01</td>
      <td>3306522110065</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-11-14 10:46:11</td>
      <td>55.07</td>
      <td>8000095653619</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-01-24 09:14:51</td>
      <td>24.37</td>
      <td>7069044920500</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-03-24 10:27:00</td>
      <td>29.72</td>
      <td>3818227780479</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-11-11 16:24:16</td>
      <td>22.99</td>
      <td>3454326063039</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>North Whitney</th>
      <td>2016-01-26 01:06:41</td>
      <td>34.92</td>
      <td>4165974278063</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Manuelchester</th>
      <td>2016-03-21 22:15:25</td>
      <td>49.62</td>
      <td>6045427401799</td>
      <td>7</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-05-24 15:29:59</td>
      <td>18.11</td>
      <td>1144791937271</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-10-17 14:47:38</td>
      <td>53.42</td>
      <td>8515375903761</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-04-21 19:22:03</td>
      <td>37.19</td>
      <td>5142074323359</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-06-12 16:57:25</td>
      <td>30.18</td>
      <td>2015025942653</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-07-22 05:59:01</td>
      <td>10.64</td>
      <td>1406024986969</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Shelbyhaven</th>
      <td>2016-01-25 01:39:16</td>
      <td>59.43</td>
      <td>8088329954312</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>South Elizabethmouth</th>
      <td>2016-04-03 11:13:07</td>
      <td>22.79</td>
      <td>8193837300497</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>South Elizabethmouth</th>
      <td>2016-03-11 12:27:01</td>
      <td>26.72</td>
      <td>4943246873754</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>South Elizabethmouth</th>
      <td>2016-11-23 07:47:18</td>
      <td>46.39</td>
      <td>1939838068038</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>South Elizabethmouth</th>
      <td>2016-07-19 09:35:59</td>
      <td>31.09</td>
      <td>2959749591417</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>South Elizabethmouth</th>
      <td>2016-04-21 10:20:09</td>
      <td>16.50</td>
      <td>5702608059064</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Matthewside</th>
      <td>2016-02-23 17:46:29</td>
      <td>59.65</td>
      <td>241191157535</td>
      <td>4</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Matthewside</th>
      <td>2016-02-23 00:43:51</td>
      <td>40.84</td>
      <td>8665248512368</td>
      <td>4</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Matthewside</th>
      <td>2016-05-18 02:00:30</td>
      <td>48.67</td>
      <td>2049161404256</td>
      <td>4</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>Matthewside</th>
      <td>2016-08-08 14:02:35</td>
      <td>24.97</td>
      <td>2872494724827</td>
      <td>4</td>
      <td>Rural</td>
    </tr>
  </tbody>
</table>
<p>2407 rows × 5 columns</p>
</div>




```python
# Create the GroupBy object based on the "city column
fare_by_city = data.groupby(["city"])

# Calculate averages for fares from each city using the .mean() method
fare_by_city.mean()
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
      <th>fare</th>
      <th>ride_id</th>
      <th>driver_count</th>
    </tr>
    <tr>
      <th>city</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alvarezhaven</th>
      <td>23.928710</td>
      <td>5.351586e+12</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Alyssaberg</th>
      <td>20.609615</td>
      <td>3.536678e+12</td>
      <td>67.0</td>
    </tr>
    <tr>
      <th>Anitamouth</th>
      <td>37.315556</td>
      <td>4.195870e+12</td>
      <td>16.0</td>
    </tr>
    <tr>
      <th>Antoniomouth</th>
      <td>23.625000</td>
      <td>5.086800e+12</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Aprilchester</th>
      <td>21.981579</td>
      <td>4.574788e+12</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th>Arnoldview</th>
      <td>25.106452</td>
      <td>5.021952e+12</td>
      <td>41.0</td>
    </tr>
    <tr>
      <th>Campbellport</th>
      <td>33.711333</td>
      <td>5.805424e+12</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>Carrollbury</th>
      <td>36.606000</td>
      <td>4.274615e+12</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>Carrollfort</th>
      <td>25.395517</td>
      <td>4.759008e+12</td>
      <td>55.0</td>
    </tr>
    <tr>
      <th>Clarkstad</th>
      <td>31.051667</td>
      <td>6.682745e+12</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Conwaymouth</th>
      <td>34.591818</td>
      <td>4.391649e+12</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>Davidtown</th>
      <td>22.978095</td>
      <td>5.850005e+12</td>
      <td>73.0</td>
    </tr>
    <tr>
      <th>Davistown</th>
      <td>21.497200</td>
      <td>4.361977e+12</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>East Cherylfurt</th>
      <td>31.416154</td>
      <td>3.981187e+12</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>East Douglas</th>
      <td>26.169091</td>
      <td>4.732315e+12</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>East Erin</th>
      <td>24.478214</td>
      <td>5.226259e+12</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>East Jenniferchester</th>
      <td>32.599474</td>
      <td>5.933107e+12</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>33.660909</td>
      <td>6.051052e+12</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>East Stephen</th>
      <td>39.053000</td>
      <td>5.306327e+12</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>East Troybury</th>
      <td>33.244286</td>
      <td>5.948234e+12</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Edwardsbury</th>
      <td>26.876667</td>
      <td>5.296117e+12</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>Erikport</th>
      <td>30.043750</td>
      <td>6.883015e+12</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>Eriktown</th>
      <td>25.478947</td>
      <td>4.113171e+12</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>Floresberg</th>
      <td>32.310000</td>
      <td>2.630319e+12</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>Fosterside</th>
      <td>23.034583</td>
      <td>5.101131e+12</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>Hernandezshire</th>
      <td>32.002222</td>
      <td>5.206210e+12</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>Horneland</th>
      <td>21.482500</td>
      <td>5.351789e+12</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>Jacksonfort</th>
      <td>32.006667</td>
      <td>4.610855e+12</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>Jacobfort</th>
      <td>24.779355</td>
      <td>4.099091e+12</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>Jasonfort</th>
      <td>27.831667</td>
      <td>6.439182e+12</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>South Roy</th>
      <td>26.031364</td>
      <td>4.862249e+12</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>South Shannonborough</th>
      <td>26.516667</td>
      <td>4.824875e+12</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>Spencertown</th>
      <td>23.681154</td>
      <td>4.850559e+12</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>Stevensport</th>
      <td>31.948000</td>
      <td>3.125721e+12</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>Stewartview</th>
      <td>21.614000</td>
      <td>4.936695e+12</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th>Swansonbury</th>
      <td>27.464706</td>
      <td>4.443028e+12</td>
      <td>64.0</td>
    </tr>
    <tr>
      <th>Thomastown</th>
      <td>30.308333</td>
      <td>4.525633e+12</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>Tiffanyton</th>
      <td>28.510000</td>
      <td>4.968458e+12</td>
      <td>21.0</td>
    </tr>
    <tr>
      <th>Torresshire</th>
      <td>24.207308</td>
      <td>5.117907e+12</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>Travisville</th>
      <td>27.220870</td>
      <td>3.317507e+12</td>
      <td>37.0</td>
    </tr>
    <tr>
      <th>Vickimouth</th>
      <td>21.474667</td>
      <td>4.242738e+12</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>Webstertown</th>
      <td>29.721250</td>
      <td>4.401465e+12</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>West Alexis</th>
      <td>19.523000</td>
      <td>5.133766e+12</td>
      <td>47.0</td>
    </tr>
    <tr>
      <th>West Brandy</th>
      <td>24.157667</td>
      <td>4.673435e+12</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>West Brittanyton</th>
      <td>25.436250</td>
      <td>5.796976e+12</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>West Dawnfurt</th>
      <td>22.330345</td>
      <td>5.119541e+12</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>West Evan</th>
      <td>27.013333</td>
      <td>5.445616e+12</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>West Jefferyfurt</th>
      <td>21.072857</td>
      <td>3.614437e+12</td>
      <td>65.0</td>
    </tr>
    <tr>
      <th>West Kevintown</th>
      <td>21.528571</td>
      <td>7.002171e+12</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>West Oscar</th>
      <td>24.280000</td>
      <td>4.525743e+12</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>West Pamelaborough</th>
      <td>33.799286</td>
      <td>4.081521e+12</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>West Paulport</th>
      <td>33.278235</td>
      <td>4.895520e+12</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>West Peter</th>
      <td>24.875484</td>
      <td>4.630766e+12</td>
      <td>61.0</td>
    </tr>
    <tr>
      <th>West Sydneyhaven</th>
      <td>22.368333</td>
      <td>4.432234e+12</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>West Tony</th>
      <td>29.609474</td>
      <td>5.080147e+12</td>
      <td>17.0</td>
    </tr>
    <tr>
      <th>Williamchester</th>
      <td>34.278182</td>
      <td>5.679295e+12</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>Williamshire</th>
      <td>26.990323</td>
      <td>4.937704e+12</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>Wiseborough</th>
      <td>22.676842</td>
      <td>6.046575e+12</td>
      <td>55.0</td>
    </tr>
    <tr>
      <th>Yolandafurt</th>
      <td>27.205500</td>
      <td>4.870867e+12</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>Zimmermanmouth</th>
      <td>28.301667</td>
      <td>4.618734e+12</td>
      <td>45.0</td>
    </tr>
  </tbody>
</table>
<p>125 rows × 3 columns</p>
</div>




```python
#  ********** SECOND SECTION:  BUBBLE CHARTS ************
# could not complete the set up of scatter/pie charts#


data_df = data

fare_by_city_df = fare_by_city.mean()
```


```python
plt.style.use('ggplot')
>>> df = pd.DataFrame(data_df, columns=['a', 'b', 'c'])
>>> df.plot(kind='scatter', x='a', y='b', s=df['c']*400); 

```


![png](output_4_0.png)



```python
data.plot(kind="bar", facecolor="red")
 

```


```python
plt.show()
```
