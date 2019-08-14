# Natural_Language_Processing

The use of natural language processing has exploded over the last decade. Appilcations that require machines to understand natural human speech patterns are abundant and substantial improvements in these systems has increased their utility. Within the educational space NLP is used to interpret human speech for the prupose of understanding human problems and recently an online tutor passed a limited version of the [Turing Test](https://en.wikipedia.org/wiki/Turing_test) when it was [indistinguishable from teaching assistants in a college class](http://www.news.gatech.edu/2017/01/09/jill-watson-round-three).

In this project, I completed three main tasks: processing a set of documents, running a sentiment analysis of these documents and then generating topic modelling of those documents. The documents used were student notes from class HUDK4050 (Education Data Mining) made last semester. 

## Datasets

### csv.files from class-notes document
The files were classnotes from HUDK 4050. The variables we used were Title and Notes. Title indicates the topic and Notes indicates the content. 

### week-list.csv
The variables contain Title and week. Week indicates on which week the topic was learned. 

## Pacakages Required
```
install.packages("tm")
install.packages("SnowballC")
install.packages("wordcloud")
install.packages("topicmodels")
```

## Procedures

### Making Wordcloud
1. Import all document files and then list of weeks file
2. Clean the html tags from the text
3. Process text using tm package with alternative processing.
  * Convert the data frame to the corpus format used in tm package 
  * Remove spaces, pre-defined stop words ('the', 'a', etc...), numbers and punctuation
  * Convert upper case to lower case, words to stems for analysis 
  * Convert corpus to a term document matrix so that each word can be analyzed indiviudally 
4. Find common words by creating a data frame of word count
5. Generate a word cloud by setting the minimum frequency, scale, max word numbres and proportion words with 90 degree rotation (vertical words). 
6. Merge with week list to have a variable representing weeks for each entry.
7. Create a Term Document Matrix and repeat step 5. 

### Sentiment Analysis
1. Match words in corpus to lexicons of positive and negative words
2. Generate an overall pos-neg score for each matched line between each word and the two lexicons
3. Geneate a visualization of the sum of the sentiment score over weeks with ggplot

### LDA Topic Modelling
1. Term Frequency Inverse Document Frequency
2. Remove very uncommon terms (TFID freq < 0.1)
3. Remove non-zero entries, find the sum of words in each document, and divide by sum across rows
4. We then find out the most common terms in each topic and which documents belong to which topic
5. Generate sentiment for each week and one important topic for that week

## Author
[Meijuan Zeng](https://github.com/tomato018), MS student in Learning Analytics at Columbia University 
