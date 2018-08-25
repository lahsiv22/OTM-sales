# OTM-sales

The aim of this task is to build a model capable of classifying different companies and organizations into one of the 9 pre-defined categories such as a tourist organization, Chain of Hotels, etc., using nothing but the company's name.

The Long-Short-Term-Memory (LSTM) neural networks was identified as the best method to carry this classifictaion forward.

The LSTM is a supervised learning algorithm. The LSTM Neural Networks have some internal contextual state cells that act as long-term or short-term memory cells. The output of the LSTM network is modulated by the state of these cells.

The following model is built in such a way that when the name of a company is given as the input in a sequence of words, it will be able to classify the company into one of the defined categories. 

### Building the Model
#### 1. Import and Cleaning the Categorised Data
The categorized data is first read. The feature column i.e, 'Company name' is separated from the label column i.e, 'Category'.
The elements in the feature column are then cleaned. The unnecessary punctuation marks and other symbols are removed. After that we are left with clean company names in the feature set.

#### 2. Tokenizing and creating a Sequence
Tokenization is one of the essential parts in natural language processing. It divides a company name into a list of words. This is done using the Keras tokenizer.

So the companies are tokenized and converted into a sequnce of tokenized words. The length or the number of words in a company's name may vary. On an average most companies had about 4 - 5 words in them. So to be on the safe side, 5 is taken as the number of words in the sequence.

The pad_sequences function is used to pad and truncate the sequence. When the number of words is lesser than 5, O is added to the end, to bring up the number of words to 5 and when there are more words than 5, the words are deleted from the front to bring down the total words to 5.

Eg: Company : 	Barcelona Convention Bureau -> [67,  1,  2] -> [67,  1,  2,  0,  0].
Here since only 3 words are present, two 0s are aded to the end.

#### 3. Building the LSTM
The Keras library is used to build the LSTM model.Its a sequential model starting with an Embedding layer, followed by the LSTM layer which is finally followed by the Dense layer. 

The Embedding layer has an input dimension of 1500 which is also the size of the input vocabulary. It has an output dimension of 100. The input length is set to 5, which is the number of words allocated per company in the sequence.

The LSTM layer has an input dimension of 100 and the dropout is set to 0  and the reccurent dropout is set to 0.2 after fine tuning the model.

Finally the Dense layer uses the 'ReLU'actiavtion fuction and has an output dimension of 9 which is the number of pre-defined categories present in the dataset. 

The labeled data is label encoded and then further encoded using One Hot Encoding. Here the categories are basically encoded into 0s and 1s. This One Hot Encoded labeled data is fed into the model as labeled data.

The model is run with a validation split of 70:30 i.e, 70% of the data is used for training the model and 30% of the data is used for testing the model.

##### The model gives an Accuracy of 89.45% and a validation accuracy of 90.9%.

### Data Description
Initial Datset : 670 values

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

### Testing

It is tested against some uncategorised data. (NoCat.xlsx)
Since it is not categorised we oursleves have only limited knowledge about the categories and validation is done based intuition.

#### The Initial model barely gave 30% acceptable predictions. (OTM sales - LSTM.ipynb)

#### The 2nd model gave an ~60% acceptable prediction. (OTM sales - LSTM 2.ipynb)

#### The Final model however gives a ~80% acceptable prediction. (OTM sales - LSTM Final.ipynb)
