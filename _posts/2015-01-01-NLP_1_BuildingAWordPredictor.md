---
title: 'NLP-Project: Building a Word Predictor'
output: html_document
layout: page
author: "Dawine"
date: "Saturday, August 22, 2015"
---



## The intended audience.

This page will serve as a sort of navigation index to all the various parts involved in getting a Word Prediction app up and running. The intended audience is someone looking to get into NLP (natural language processing), has an understanding of `R` or at least enough programming experience to read through snippets or `R` code, look around for online resources, and get a general understanding of what's going on.
That being said I'll keep any technical jargon limited and ideally anyone with an interest in word prediction will be able to take something away from the pages ahead.


## The Aim

The aim is to start from raw, English: News, Blog and Twitter data and produce an NLP data product (interactive online word prediction app) hosted at [ShinyApps](http://www.shinyapps.io/) . 
Throughout the project I found that `R` on its own isn't enough to produce an word predictor with. You'll find quite a few CSS, jquery, HTML based solutions. 


## Abstract

This application predicts the next word given a set of words, using a **customized** “Stupid Backoff” algorithm. The basic idea is to compute the probability of a word given some previous set of words. This application

1. Initializes in less than five (5) seconds
2. Has automated predictions
3. Predicts word and appends them to text input
3. Has an accuracy prediction between 60% - 70%
4. Displays data table, plot, and wordcloud


## Explanation of the algorithm

1. The user input is processed [see milestone report](http://rpubs.com/pdawine/tm_nlp), and splitted to have the last 3, 2, or 1 word. If the length is >= than 3, I use the 4-gram probability, if it is equal to 2, I use the trigram, if equal to 1, I use the bigram
2. I use the maximum likelihood estimator(the count of the word divided by the count of the prefix), if that count is greater than zero
3. I start with the quadgram,  if it occurs, I just use its count, If not, I take the trigram probability multiplied by 0.4, If not, I get back to the bigram, and when I get back to the highest bigram that has an approximate string matching, if I do not get any prediction, I just use the unigram.

The formula of the N-grams probability algorithm is expressed as follows:

$$S(w_i | w_{i-k+1}^{i-1}) =\begin{cases}count(w_{i-k+1}^{i})/count(w_{i-k+1}^{i-1}),  & \text{if } count(w_{i-k+1}^{i})>0    \\[4ex]0.4S(w_i | w_{i-k+2}^{i-1}), & \text{otherwise}\end{cases}  $$

$$S(w_i|w_{i-1}) = \begin{cases}count(w_{i-1},w_i)/count(w_{i-1}), \text{ }  \text{if } count(w_{i-1})>0, \text{ }\text{and if not }
\\[4ex]\frac{count(w_{i-1},w_i)}{count(w_{i-1})}, \text{ }  \text{if } count(w_{i-1}) \text{ }\text{has an approximate string matching, otherwise}\end{cases}$$

$$S(w_i)=\frac{count(w_i)}{N}$$
<br>
S emphasizes that these are not probabilities but scores

Description and instructions
========================================================
1. Click on the download text button to open or save the text input in the selected format
2. Select appropriate tab by clicking on "Smart typing", "Technical" or "Demo manual"
3. The numeric input change the number of words to predict
4. Click on the predicted word to append it in the text input
5. Resize the text area if you are typing a large document
6. Type you first word: "I" and see in ranked order the predicted words: *have*, *was*, *am*, *think*, *love* below the text input, in the frequency table and in both charts


<img src="/assets/pictures/NLP_Project2014/LetsGetStarted.png" alt="LetsGetStarted" style="width: 720px;"/>
