# 1. CONGESTION PATTERNS
Supervised by Prof. B. Hong at PNU 🙌
<br><br>**&lt;ABSTRACT&gt;**
<p align="justify">
&nbsp;&nbsp;This mini-project aims to <strong>find out patterns from highway velocity data</strong>, collected and distributed by Korea Expressway Corporation 
through <a href="https://data.ex.co.kr/">its open data portal</a>. To be specific, the velocity of vehicles on highway is said to be measured and logged by
the so-called VDS, Vehicle Detection System, installed all over the highway in Korea. Due to the shear amount of data, only average values of velocity are available on the portal 
and thereby the ones per the shortest interval(five minutes) are used for this project. After a series of preprocesses, some velocity patterns are found 
  with the use of one of the widely used clustering algorithms, K-Means.  
</p>

**&lt;METHOD&gt;**
<p align="justify">
<strong>PREPROCESSING</strong>
<ol>
  <li>COMBINE DATA</li>
  <p align="justify">As an effort to provide a deep-learning model with sufficient data to train itself, five months' worth data are combined. In this process,
  the ones collected during weekdays and in the weekend were treated separately to compare their velocity patterns.</p>
  <li>CLEANSING</li>
  <p align="justify">The raw data contain a lot of missing values represented by -1.0 and noise. As the data given by the corporation are more than enough, the former were simply droped,
    wheras the latter was mitigated by interpolation algorithm <strong>Smoothing Splines</strong> with the use of scipy.interpolate.
    What's worse is that the VDS seems to log 0.0 [km/h] whenever they malfunction, which makes it about impossible to tell real zero velocity which can appear
    when an accident happends on highways. Though to figure out some characteristic patterns in case of accidents is one of main purposes of this project, data having zero value
    needed erasing to improve a model's performance.
  </p>
  <li>STANDARDIZATION</li><p>After becoming smooth, the date were transformed by <strong>MinMaxScaler</strong> included in sklearn.preprocessing so that
    their values range from their minimum to maximum values.
  </p>
</ol>
<strong>MODEL:KMEANS ALGORITHM</strong>
<ol>
  <li>FIND AN OPTIMAL K</li><p>As the K-Means algorithm can be excecuted only after a value of k, i.e., the number of clusters, is given, an optimal
  value of k needs finding at first. This was done by plotting inertial against k and finding the so-called ellbow. Though the plot does not have a distinct
  ellbow, it is observed that from some k values the inertia does not dramatically decrease any loger.
  </p>
  <li>FIND CLUSTERS</li><p>Velocity patterns were found with respect to three different k values, namely, 20, 30 and 40.</p>
</ol>
</p>





