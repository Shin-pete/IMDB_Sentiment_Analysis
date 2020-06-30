# IMDB_Sentiment_Analysis

Nowadays there is such a vast amount of data available to people, certainly too much for any one individual to look through. Text itself presents a specific problem where reading and understanding text takes a different set of skiils than a traditional machine learning challenge. I seek to try to solve this problem using NLP and Neural Networks to determine if we can comphrehend the underlying sentiment of the text presented. 

[My_notebook](https://github.com/Shin-pete/IMDB_Sentiment_Analysis/blob/master/LSTM_model.ipynb)

Step by step procedure: 

Today we will be looking at deep learning and discover how we can use deep learning and natural language processing to try to create an algorithm that can analyze a user's review to infer whether the reviewer found it to be a positive or negative experience. We first begin by importing our necessary databases as well as pandas. 

![dataframe](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/mparbwd_1_orig.png)

We then concatenate our two dataframes and then begin the process of cleaning and preparing the data. First, I suppose it's important to explain why cleaning and preparing our data are so important. Basically, it would take a tremendous amount of work to teach a learning algorithm on the rules of the English language work. A computer can't readily tell that 'car', 'Car', 'car.' and 'Car.' could all be the same thing. The best thing for it is to lowercase all terms within the dataframe and remove all punctuation from it so that it can more easily identify the same word. Another thing we notice in our work is the presence of line breaks. Removing these poses an additional challenge because simply removing the brackets outside of it will cause 'br' to be left, either alone, or depending or spacing, it can even concatenate itself onto another word, thereby preventing it from being correctly tokenized. We address this problem by using the strip function and stripping all instances of linebreaks from the strings. 

![df_list](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/nndswj5_1_orig.png)

Now that we have properly cleaned the dataset, we can move on to the business of exploring the data more and gaining some insights. First, to do this, we will run a loop through our entire set of reviews and append each instance of a word showing up into a list. Our next step is to import and use the counter to measure how many times each word was used in our 50000 reviews. 

Unfortunately, we come to see that this isn't immediately useful because of filler words used in the reviews. Words like 'the', 'and', 'a' and 'of' are used far more frequently than terms that provide actual insights about the films we are watching and the terminology people may be used to talk about and describe them.

![viz_0](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/hv6blgt_1_orig.png)

So the next thing we're going to do is get rid of all the stopwords. To do this, we will import stopwords from nltk.corpus and set the stopwords to be in English. Once that is done, we're going to take the previous list and whenever we find an instance of a stopword in that list, we will remove it. Having removed the fillers, we will run the counter on our new list to get a sense of what non-filler words are most common and this can provide us some useful insights. Once that is done, we get to see that the actually most often used words in the set are terms like 'movie' and 'film'. Another thing we can notice here is that things like 'good' and 'great' and 'better' and 'best' are used quite frequently whereas the only word for describing a negative characteristic is 'bad'. To me, this suggests that when people are talking up a film, they tend to use pretty similar terms and when they are criticizing a film, the terminology seems to be more diverse as bad is the only 'negative' term in the top 50 most used terms.

![viz_1](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/o2viij6_1_orig.png)

We can then look to word vectorization to gain some more insights into how IMDB users tend to review films. To do that, we run a word2vec model over our list of cleaned words to see what we can learn. We see that when an individual mentions editing, the words most similar to it are also things that tend to have to do with technical aspects of filmmaking like lighting and camerawork. On the other hand, words like 'story' are most similar to terms like 'plot' and 'tale' and 'narrative' and other terms there to describe the events of the story. 

![viz_2](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/ho4yu5u_1_orig.png)

Now that we have a good idea of what our data is like, we can now look at beginning the modeling process. Let's begin by importing the necessary libraries. We then create our y variable for our model by getting the 0s or 1s from the dataset that are there and set them to our y variable. Let's start with a pretty basic model and see how it performs. 

![viz_3](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/xbclvry_1_orig.png)

Not bad! Our model had a validation accuracy of .9008, and to think that it took only 2 epochs. Let's see how increasing the number of epochs will affect validation accuracy. And it seems like it significantly decreases the accuracy down to .86, and we see that taking it to 20 has an even more negative effect, going as far down as to .83. Instead of trying to randomly find the configuration that works best, let's try to find the optimal set of conditions and for this, we will run a grid search that optimizes for epochs and batch size. 

![viz_4](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/wu8mpjw_1_orig.png)
