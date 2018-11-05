# -*- coding: utf-8 -*-

import tweepy,re
from textblob import TextBlob
import matplotlib.pyplot as plt
#import matplot.animmation as animation
#from matplot import style
#import time
#import pandas as pd

class SentimentAnalysis:

    def __init__(self):
        self.tweets = []
        self.tweetText = []

    def DownloadData(self):
        
        consumerKey = '98lccjL0uWEsAffOHVOJAEkN1'
        consumerSecret = 'tDuLdEmxhu6yK9sI16FSSlBlyKTuR5Bdsd7WsXlLCVI4tMZIDI'
        accessToken = '1055579022749388800-glmUwrk0apW8r3Kd2uJgeOZaaWqMmx'
        accessTokenSecret = 'KU6AQy9lyOEWmY4PTVLv8NPnufEymKt0RTPntMV16Ce1g'
        auth = tweepy.OAuthHandler(consumerKey, consumerSecret)
        auth.set_access_token(accessToken, accessTokenSecret)
        api = tweepy.API(auth)

        searchTerm = input("Enter Keyword/Tag to search about: ")
        NoOfTerms = int(input("Enter how many tweets to search: "))

        self.tweets = tweepy.Cursor(api.search, q=searchTerm, lang = "en").items(NoOfTerms)


        polarity = 0
        positive = 0
        negative = 0
        neutral = 0


        for tweet in self.tweets:
            '''
            print (tweet)
            print(tweet.text)
            '''
            analysis = TextBlob(tweet.text)
            polarity += analysis.sentiment.polarity  

            if (analysis.sentiment.polarity == 0): 
                neutral += 1
            
            elif (analysis.sentiment.polarity > 0.0):
                positive += 1
            
            
            elif (analysis.sentiment.polarity < 0.0):
                negative += 1
            


      
        positive = self.percentage(positive, NoOfTerms)
        
        negative = self.percentage(negative, NoOfTerms)
        
        neutral = self.percentage(neutral, NoOfTerms)

        polarity = polarity / NoOfTerms

        print("How people are reacting on " + searchTerm + " by analyzing " + str(NoOfTerms) + " tweets.")
        print()
        print("General Report: ")

        if (polarity == 0):
            print("Neutral")
       
        elif (polarity > 0.0 ):
            print("Positive")
        
        elif (polarity < 0.0):
            print("Negative")
        
        print()
        print("Detailed Report: ")
        print(str(positive) + "% people thought it was positive")
        
        print(str(negative) + "% people thought it was negative")
        
        print(str(neutral) + "% people thought it was neutral")

        self.plotPieChart(positive,  negative,  neutral, searchTerm, NoOfTerms)


    def cleanTweet(self, tweet):
        return ' '.join(re.sub("(@[A-Za-z0-9]+)|([^0-9A-Za-z \t]) | (\w +:\ / \ / \S +)", " ", tweet).split())

    def percentage(self, part, whole):
        temp = 100 * float(part) / float(whole)
        return format(temp, '.2f')

    def plotPieChart(self, positive, negative, neutral, searchTerm, noOfSearchTerms):
        labels = ['Positive [' + str(positive) + '%]',  'Neutral [' + str(neutral) + '%]',
                  'Negative [' + str(negative) + '%]']
        sizes = [positive,  neutral, negative]
        colors = ['red','blue','green']
        patches, texts = plt.pie(sizes, colors=colors, startangle=90)
        plt.legend(patches, labels, loc="best")
        plt.title('How people are reacting on ' + searchTerm + ' by analyzing ' + str(noOfSearchTerms) + ' Tweets.')
        plt.axis('equal')
        plt.show()
'''
fig =plt.figure()
ax1=fig.add_subplot(1,1,1)
    
def animate(i):
    takedata = open('')
    
    
'''
if __name__== "__main__":
    sa = SentimentAnalysis()
    sa.DownloadData()
