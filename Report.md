# Predicting the Role of Political Trolls-in Social Media
 
 <!-- TABLE OF CONTENTS -->
## Table of Contents

* [Data](#Data)
  * [Overview](#Overveiw)
  * [Pre-processing](#Pre-processing)
* [Embeddings](#Embeddings)
  * [U2H](#U2H)
    * [U2H Requirements](#U2H-Requirements)
    * [U2H Result](#U2H-Result)
  * [U2M](#U2M)
    * [U2M Requirements](#U2M-Requirements)
    * [U2M Result](#U2M-Result)
  * [BERT](#BERT)
    * [Text Pre-processing](#Text-Pre-processing)
    * [BERT Pre-processing](#BERT-Pre-processing)
    * [BERT Result](#BERT-Result)

<!-- DATA -->
## Data 
The dataset contains 2 973 371 tweets by 2848 Twitter users

### Overview

#### Sample

|    |   external_author_id | author   | content                                                                                                                                                      | region   | language   | publish_date    | harvested_date   |   following |   followers |   updates | post_type   | account_type   |   retweet | account_category   |   new_june_2018 |    alt_external_id |           tweet_id | article_url                                                       | tco1_step1                                                            |   tco2_step1 |   tco3_step1 |
|---:|---------------------:|:---------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:-----------|:----------------|:-----------------|------------:|------------:|----------:|:------------|:---------------|----------:|:-------------------|----------------:|-------------------:|-------------------:|:------------------------------------------------------------------|:----------------------------------------------------------------------|-------------:|-------------:|
|  0 |   906000000000000000 | 10_GOP   | "We have a sitting Democrat US Senator on trial for corruption and you've barely heard a peep from the mainstream media." ~ @nedryun https://t.co/gh6g0D1oiC | Unknown  | English    | 10/1/2017 19:58 | 10/1/2017 19:59  |        1052 |        9636 |       253 | nan         | Right          |         0 | RightTroll         |               0 | 905874659358453760 | 914580356430536707 | http://twitter.com/905874659358453760/statuses/914580356430536707 | https://twitter.com/10_gop/status/914580356430536707/video/1          |          nan |          nan |
|  1 |   906000000000000000 | 10_GOP   | Marshawn Lynch arrives to game in anti-Trump shirt. Judging by his sagging pants the shirt should say Lynch vs. belt https://t.co/mLH1i30LZZ                 | Unknown  | English    | 10/1/2017 22:43 | 10/1/2017 22:43  |        1054 |        9637 |       254 | nan         | Right          |         0 | RightTroll         |               0 | 905874659358453760 | 914621840496189440 | http://twitter.com/905874659358453760/statuses/914621840496189440 | https://twitter.com/damienwoody/status/914568524449959937/video/1     |          nan |          nan |
|  2 |   906000000000000000 | 10_GOP   | Daughter of fallen Navy Sailor delivers powerful monologue on anthem protests, burns her NFL packers gear.  #BoycottNFL https://t.co/qDlFBGMeag              | Unknown  | English    | 10/1/2017 22:50 | 10/1/2017 22:51  |        1054 |        9637 |       255 | RETWEET     | Right          |         1 | RightTroll         |               0 | 905874659358453760 | 914623490375979008 | http://twitter.com/905874659358453760/statuses/914623490375979008 | https://twitter.com/10_gop/status/913231923715198976/video/1          |          nan |          nan |
|  3 |   906000000000000000 | 10_GOP   | JUST IN: President Trump dedicates Presidents Cup golf tournament trophy to the people of Florida, Texas and Puerto Rico. https://t.co/z9wVa4djAE            | Unknown  | English    | 10/1/2017 23:52 | 10/1/2017 23:52  |        1062 |        9642 |       256 | nan         | Right          |         0 | RightTroll         |               0 | 905874659358453760 | 914639143690555392 | http://twitter.com/905874659358453760/statuses/914639143690555392 | https://twitter.com/10_gop/status/914639143690555392/video/1          |          nan |          nan |
|  4 |   906000000000000000 | 10_GOP   | 19,000 RESPECTING our National Anthem! #StandForOurAnthem🇺🇸 https://t.co/czutyGaMQV                                                                          | Unknown  | English    | 10/1/2017 2:13  | 10/1/2017 2:13   |        1050 |        9645 |       246 | RETWEET     | Right          |         1 | RightTroll         |               0 | 905874659358453760 | 914312219952861184 | http://twitter.com/905874659358453760/statuses/914312219952861184 | https://twitter.com/realDonaldTrump/status/914310901855129601/video/1 |          nan |          nan |

#### Categories distribution

|  Category   |   Count   |
|------------:|----------:|
| RightTroll  |    704953 |
| NewsFeed    |    596593 |
| LeftTroll   |    422141 |
| HashtagGamer|    236092 |
| Commercial  |    112580 |
| NonEnglish  |    26562  |
| Fearmonger  |    11001  |
| Unknown     |    6945   |

### Pre-processing
- Droped NaNs
- Removed all non-english tweets
- Kept the three main categories (RightTroll, NewsFeed, LeftTroll)

## Embeddings

I used two graph-based (user-to-hashtag and
user-to-mentioned-user) and one text-based
(BERT) embedding representations.

## U2H

### U2H Requirements

- Users nodes
- Hashtags nodes
- Edges between them

Note: I trained and saved the U2H model, you can find it in the attached files `"U2H_model.model"`

### U2H Result
most_similar('#Saudi'): #Yemen, #US ,#Libya ,#Aleppo, #SaudiArabia, #UN, #Putin, #NASA, #Palestine, #UAE

#### Classification Report

|           | precision |   recall | f1-score |  support  |
|----------:|----------:|---------:|---------:|----------:|
| LeftTroll  |       0.78|      0.86|      0.82|        21|
|    NewsFeed|       0.86|      0.86|      0.86|         7|
|  RightTroll|       0.97|      0.94|      0.95|        64|
|            |            |         |           |         | 
|    accuracy|            |         |        0.91|        92|
|   macro avg|       0.87|      0.88|      0.88|        92|
|weighted avg|       0.92|      0.91|      0.91|        92|


## U2M

### U2M Requirements

- Users nodes
- Mentions nodes
- Edges between them

### U2M Result
Duo to the lack of resources, I couldn't train the U2M model which was requiring a GPU.

## BERT

### Text Pre-processing:

- Change 't to 'not'
- Remove @name
- Isolate and remove punctuations except '?'
- Remove some special characters
- Remove stopwords except 'not' and 'can'
- Remove trailing whitespace

### BERT Pre-processing:

- Tokenize the sentence
- Add the `[CLS]` and `[SEP]` token to the start and end
- Truncate/Pad sentence to max length
- Map tokens to their IDs
- Create attention mask
- Return a dictionary of outputs

### BERT Result

#### Classification Report

|           | precision |   recall | f1-score |  support  |
|----------:|----------:|---------:|---------:|----------:|
| LeftTroll  |       0.29|      0.15|      0.20|        67|
|    NewsFeed|       0.56|      0.28|      0.37|         18|
|  RightTroll|       0.71 |     0.86 |     0.78 |      191|
|            |            |         |           |         | 
|accuracy     |           |           |0.65       |276|
|   macro avg |      0.52 |     0.43      |0.45|       276|
|weighted avg |      0.60 |     0.65      |0.61 |      276|

Note: This is the first attempt, the accuracy could go higher easily
