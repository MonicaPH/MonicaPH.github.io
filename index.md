---
title       : Sentiment analysis
subtitle    : Course Project
author      : MonicaPH
job         : Developing Data Products
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Sentiment Analysis

This small project intends to identify the sentiment in the opinion of a person about a cetain epidemic disease.

Five epidemic diseases were presented to trigger an opinion:
- Ebola
- VIH
- Cholera
- Influenza
- Dengue
- Cancer

--- .class #id 

## Sentiment identification

The type of sentiment of the opinion and its polarity (positive or negative) was determined using the Sentiment Package by Timothy Jurka. 

A naive Bayes classifier trained on Carlo Strapparava and Alessandro Valitutti's emotions lexicon was used to determine the emotion in the text. Six types of emotion are possible: anger, disgust, fear, joy, sadness, and surprise.

Furthermore, a naive Bayes algorithm trained on Janyce Wiebe's subjectivity lexicon was used to determine the polarity of the sentiment in the text.


--- .class #id 

## Example

For example: ***"I think Ebola is a horrid disease"*** is analyzed with the following code:


```r
#classify Emotion
class_emo = classify_emotion("I think Ebola is a horrid disease", algorithm="bayes", prior=1.0)
# get emotion best fit
emotion = class_emo[,7]
emotion
```

```
## BEST_FIT 
##   "fear"
```


--- .class #id 

## Example

```r
# classify polarity
class_pol = classify_polarity("I think Ebola is a horrid disease", algorithm="bayes")
# get polarity best fit
polarity = class_pol[,4]
polarity
```

```
##   BEST_FIT 
## "negative"
```

In this case, the classifier correctly determines that I feel fear from my statement, and that the sentiment is negative.

In future versions, I plan to improve the App to get the opinions from a Twitter Feed.
