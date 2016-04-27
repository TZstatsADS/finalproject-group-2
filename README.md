# A Million Song Dataset
Ziyue JIN, Ziyue WU, Yimin ZHANG, Jingying ZHOU and Yibo ZHU

## Data
##### Source 1. Sound Analysis
* [Million Song Dataset](http://labrosa.ee.columbia.edu/millionsong/)
* Format: .h5 [Hierarchical Data Format](https://en.wikipedia.org/wiki/Hierarchical_Data_Format)  
* How we utilized our data:   
1) Made exploratory data analysis on the metadata for all 1,000,000 songs (Meta Data: 300 MB)  
2) Extracted sound analysis data from a random subset, consiting of 10,000 songs (Sound Analysis: 1.8 GB)  
          - Temporal structures: eg.beats/bar lengths distribution  
          - Loudness, timbre and pitches  
*A brief glimpse of all the blood and tears we've been through...*
```
          group                       name       otype   dclass       dim
0             /                   analysis   H5I_GROUP                   
1     /analysis            bars_confidence H5I_DATASET    FLOAT       194
2     /analysis                 bars_start H5I_DATASET    FLOAT       194
3     /analysis           beats_confidence H5I_DATASET    FLOAT       979
      ...         ...         ...         ...         ...
21    /metadata            similar_artists H5I_DATASET   STRING       100
22    /metadata                      songs H5I_DATASET COMPOUND         1
23            /                musicbrainz   H5I_GROUP                   
24 /musicbrainz              artist_mbtags H5I_DATASET   STRING         0
25 /musicbrainz        artist_mbtags_count H5I_DATASET  INTEGER         0
26 /musicbrainz                      songs H5I_DATASET COMPOUND         1

```
##### Source 2. User Preference
* [Echo Nest Tase Profile Data](The Echo Nest Taste Profile Subset)
* Format: Play count per song per user:
* How we utilized our data:  
We used this play-count data to generate a "user defined" song similiarity mesure, and then tried random forest and LASSO to select the sound features (from dataset 1) that play the most important roles in determining thi

##### Source 3. Lyrics BoW
* Source: [musiXmatch dataset](http://labrosa.ee.columbia.edu/millionsong/musixmatch)
* Format:.txt(BoW)
* How we utilized our data:   
We implemented a topic model using Laten Dirichlet Allocation with 10 and 15 topics. This cluster is generated purely independently from the rest of the clusters, and we would like to see if the clusters generated from the sound features are indeed "literally" different from each other.

##### Source 4. Genre
* [Tagtraum Genre Annotations](http://www.tagtraum.com/msd_genre_datasets.html)
* Format: .cls 
* How we utilized... Fancy Plots!

## Methodology
#### To make a long story short,  
We used playcount data to select song features that play an important role in deciding the "crowd defined similarity", and then clustered our songs using the sound features.  
Using the lyrics Bag-of-Words data, we did topic modelling and assigned "topics" to the songs we have.   
We then looked into how these two cluster results differ/resembles each other.

## Exploratory Data Analysis
## Building up Our Model  
### Feature Selection
![Random Forest](https://github.com/TZstatsADS/finalproject-group-2/blob/master/lib/web/img/rf.jpg?raw=true "Logo Title Text 1")
### Hierachical Clustering
By calculating silhoutte distance, and visualizing clustering in first two pc plots, we think five clusterings will be a good result. From the two cluster plot, we also can see 5 plot makes sense.
![Selecting Number of Clusters](https://github.com/TZstatsADS/finalproject-group-2/blob/master/lib/web/img/select_dimension.png?raw=true "Logo Title Text 1")
```
## 2 0.6098073 
## 3 0.44251 
## 4 0.03555164 
## 5 0.02601014 
## 6 0.02841965 
## 7 0.02566342 
## 8 0.02302715 
## 9 0.02371691 
## 10 0.0224799
```
* Clustering Result   
![HCLUST](https://github.com/TZstatsADS/finalproject-group-2/blob/master/lib/web/img/hclust.jpg?raw=true)

### Topic Modelling 

## Reference
Capturing the Temporal Domain
in Echonest Features
for Improved Classification Effectiveness [*On Feature Selection*](http://www.ifs.tuwien.ac.at/~schindler/pubs/AMR2012.pdf)
