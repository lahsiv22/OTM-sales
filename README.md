# OTM-sales

### Data Description
Initial Datset : 511 values

2nd Attempt : 895 values

Final Dataset : 1209 values

The Initial Dataset had a very high number of Wedding Planner(WP) data causing the model to be heavily biased towards the Wp category.

The 2nd dataset was created by adding more real world data of several categories to the first dataset in such a manner that it is not biased.
This reduced the bias of the model greatly and the accuracy when tested on real world data was much better but wasn't very acceptable yet.

The Final data set was created by adding more real world data for each category to the 2nd dataset. This model when tested against real world data gave an ~80% accuracy.

The value splot of the initial dataset:

WP    228

H     124

TO     70

TB     62

CB     57

TA     49

CH     35

R      19

EP     18

A       4

CC      4

The value Split of the final dataset: 

WP    166

TO    150

CB    143

TB    140

H     132

CH    130

EP    119

R     117

A     112

NOTE : The Categrory Center(CC) has been merged to Convention Bureau(CB) and the Category Travel Agency(TA) has been merged with Tourist Organization(TO) due to low data count for the formers and they also more or less mean the same/  refer to similar organizations.

### Model
The data is first cleaned by removing unnecessary punctuation marks.
The data is then Tokenized and fit into sequences.
These sequences are then fed as the input to the LSTM model.

#### The model gives an Accuracy of 89.45% and a validation accuracy of 90.9%.

### Testing

It is tested against some uncategorised data. (NoCat.xlsx)
Since it is not categorised we oursleves have only limited knowlwdge about the categories of the categrories.

#### The Initial model barely gave 30% acceptable predictions.

#### The 2nd model gave an ~60% acceptable prediction.

#### The 3rd model however gives a ~80% acceptable prediction.
