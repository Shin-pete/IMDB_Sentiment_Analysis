# IMDB_Sentiment_Analysis

Nowadays there is such a vast amount of data available to people, certainly too much for any one individual to look through. Text itself presents a specific problem where reading and understanding text. I seek to try to solve this problem using NLP and Neural Networks to determine if we can comphrehend the underlying sentiment of the text presented. 

[My_notebook](https://github.com/Shin-pete/IMDB_Sentiment_Analysis/blob/master/LSTM_model.ipynb)

Step by step procedure: 

Today we will be looking at deep learning and learn about how we can use deep learning and natural language processing to try to create a system that can read a user's review and analyze whether they found the film to be a positive or negative experience. We first begin by importing our necessary databases as well as pandas. ​

![dataframe](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/mparbwd_1_orig.png)

We then concatenate our two dataframes and then begin the process of cleaning and preparing the data. First, I suppose it's important to explain why cleaning and preparing our data are so important. Basically, it would take a tremendous amount of work to teach a learning algorithm on how all the rules of the English language work. A computer can't readily tell that 'car', 'Car', 'car.' and 'Car.' could all be the same thing. The best thing for it is to lowercase all terms within the dataframe and remove all punctuation from it so that it can more easily identify the same word. Another thing we notice in our work is the presence of line breaks, which are present here as '<br>'. Removing these poses an additional challenge because simply removing the brackets outside of it will cause 'br' to be left, either alone, or depending or spacing, it can even concatenate itself onto another word, thereby preventing it from being correctly tokenized. We address this problem by using the strip function and stripping all instances of linebreaks from the strings. 

![df_list](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/nndswj5_1_orig.png)

Now that we have properly cleaned the dataset, we can move on to the business of exploring the data more and gaining some insights. First, to do this, we will run a loop through our entire set of reviews and append each instance of a word showing up into a list. Our next step is to import and use the counter to count how many times each word was used in our 50000 reviews. 

Unfortunately, we come to see that this isn't immediately useful because of all the filler words used in the reviews. Words like 'the', 'and', 'a' and 'of' are used far more frequently than terms that provide actual insights about the films we are watching and the terminology people may be used to talk about and describe them.

![viz_0](https://arpitbajpai.weebly.com/uploads/1/1/7/2/117229466/hv6blgt_1_orig.png)
