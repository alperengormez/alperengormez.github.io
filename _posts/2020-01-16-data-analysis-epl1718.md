---
title: "Data Analysis of EPL 2017-2018 Season"

categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---

Have you ever placed a bet on a football match? If you have, there is a high probability that you lost. This post will help you increase your chance of winning.

First things first: Betting is bad --at least in my opinion. This post does not mean to encourage betting. Moreover, if you keep playing a game long enough, you will eventually end up losing. Therefore, you should know when to stop betting. The neural network I trained will tell you when.

There are various options in betting. In this work, I focused on the English Premier League (EPL) 2017-2018 seasons and the number of goals scored in an EPL match being over or under 2.5 (O2.5 and U2.5). The reason is simple: There are only 380 matches (38 for each team) in the league. This number is significantly low for a neural network to have an understanding of the data and make generalizations well enough to make accurate predictions for the unseen data --in fact, it is very low for any algorithm to make an accurate prediction. So, if we are already constrained by the amount of data, why try to predict an event with lots of outcomes? If you have no prior knowledge, trying to predict whether there will be O2.5 or U2.5 in a match (50% chance of winning) is easier than trying to predict the outcome of a match (33% chance of winning).

The dataset I have used is taken from <a href="https://github.com/openfootball/england/tree/master/2017-18">here</a>. I have done some adjustments in terms of formatting and obtained [this]({{ site.url }}/assets/data_analysis_epl1718/epl1718.txt).

```python
Matchday 1

Arsenal FC               4-3  Leicester City
Watford FC               3-3  Liverpool FC
Chelsea FC               2-3  Burnley FC
Crystal Palace           0-3  Huddersfield Town
Everton FC               1-0  Stoke City
Southampton FC           0-0  Swansea City
West Bromwich Albion     1-0  AFC Bournemouth
Brighton & Hove Albion   0-2  Manchester City
Newcastle United         0-2  Tottenham Hotspur
Manchester United        4-0  West Ham United
```

It is important for our dataset to be balanced. In other words, the number of O2.5 and U2.5 matches should be close in order for the neural network to generalize well. From the figure below, we can see that we have a fairly balanced dataset.

![My helpful screenshot]({{ site.url }}/assets/data_analysis_epl1718/au.jpg)

I think a nice skill to have for a data scientist or a deep learning engineer is to extract meaningful features from the data. In fact, this is the job of the neural network. But if you have an unvectorized data as you see above (just some text and numbers), you should vectorize it in a meaningful way for the neural network. Therefore, I had to extract meaningful features that will help to predict whether a match will be O2.5 or U2.5. Obvious features are: average number of goals scored/conceded at home/away games up to that week for both teams, average number of goals scored/conceded at last 5 (arbitrary number) matches for both teams. You can obviously use the performances of the players. For example, whether Mohammed Salah will play in the match or not, and his performance for the last 2 matches are obviously important for our task. However, I had no access to these data --I mean, technically I had  access since there is something called the Internet, but it would give too little reward for too much work, so I did not include these data in my work.

In addition to the 6 features given above, we should take into account which teams are playing the match. For instance, even though Chelsea and Burnley have the same 6 values for the features described above, the prediction of neural network for the Manchester City - Chelsea/Burnley matches should be different. Therefore we identify the teams with 2 (one for the home team, one for the away team) one-hot-encoded vectors of length 20. The nice thing with this approach is that it takes into account the "Home" and "Away" concepts. Liverpool-Stoke City will probably have a different result than Stoke City-Liverpool in terms of O2.5/U2.5 (it is a cold rainy night).

-*-*home matches-*-*

-*-*away matches-*-*

In total, we have 380 samples and 52 features per sample. Since we are aware of the consequences of not splitting the dataset into training, validation and test sets, we split the dataset into training, validation and test sets. I discarded the matches played in the first 5 weeks since we have not enough information to make an accurate prediction. For the training, validation an test sets, I have used weeks 6-23, 24-30 and 31-38 respectively.

For the neural network, I have used RMSProp, binary cross-entropy and accuracy as optimizer, loss function and task metric respectively. I have used the following architecture:

-*-architecture plot-*-

Since the data is tabular, I did not see a need to use convolutional neural networks. I did not use recurrent neural networks because the data is not exactly sequential. There are multiple teams and number of matches each team play is very low.

First, we take a look at the training and validation losses of the network.

-*- training and validation losses-*

As we see, even though the training loss decreases monotonically, the validation loss stops decreasing at some point. This is a typical overfitting plot. Even though I have anticipated overfitting and tried to reduce it by using Dropout layers and L2 regularization, the amount of data we have is still low and not enough to fight overfitting.

The training and validation accuracies of the network can be seen below.

-*- training and validation accuracies-*

Because of the overfitting, the increase in the validation accuracy stops at some point.

From the plots above, we see that it is a nice idea to stop training after 10 epochs. After modifying the number of epochs to train the network, we train the network again and obtain the following plots.

*--loss and acc plots**-

We evaluate our model in the test set: 8 weeks (80 matches). There will be high variance in the result since the number of samples in the test set is too low. Every time we run the whole code, we will get different results in the range 57-75%.

*-*test set evaluation-*-*

This is the best we can do.
All children, except one, grow up. They soon know that they will grow up, and the way Wendy knew was this. One day when she was two years old she was playing in a garden, and she plucked another flower and ran with it to her mother. I suppose she must have looked rather delightful, for Mrs. Darling put her hand to her heart and cried, "Oh, why can't you remain like this for ever!" This was all that passed between them on the subject, but henceforth Wendy knew that she must grow up. You always know after you are two. Two is the beginning of the end.

Mrs. Darling first heard of Peter when she was tidying up her children's minds. It is the nightly custom of every good mother after her children are asleep to rummage in their minds and put things straight for next morning, repacking into their proper places the many articles that have wandered during the day.



This post has a manual excerpt `<!--more-->` set after the second paragraph. The following YAML Front Matter has also be applied:



If you could keep awake (but of course you can't) you would see your own mother doing this, and you would find it very interesting to watch her. It is quite like tidying up drawers. You would see her on her knees, I expect, lingering humorously over some of your contents, wondering where on earth you had picked this thing up, making discoveries sweet and not so sweet, pressing this to her cheek as if it were as nice as a kitten, and hurriedly stowing that out of sight. When you wake in the morning, the naughtiness and evil passions with which you went to bed have been folded up small and placed at the bottom of your mind and on the top, beautifully aired, are spread out your prettier thoughts, ready for you to put on.

I don't know whether you have ever seen a map of a person's mind. Doctors sometimes draw maps of other parts of you, and your own map can become intensely interesting, but catch them trying to draw a map of a child's mind, which is not only confused, but keeps going round all the time. There are zigzag lines on it, just like your temperature on a card, and these are probably roads in the island, for the Neverland is always more or less an island, with astonishing splashes of colour here and there, and coral reefs and rakish-looking craft in the offing, and savages and lonely lairs, and gnomes who are mostly tailors, and caves through which a river runs, and princes with six elder brothers, and a hut fast going to decay, and one very small old lady with a hooked nose. It would be an easy map if that were all, but there is also first day at school, religion, fathers, the round pond, needle-work, murders, hangings, verbs that take the dative, chocolate pudding day, getting into braces, say ninety-nine, three-pence for pulling out your tooth yourself, and so on, and either these are part of the island or they are another map showing through, and it is all rather confusing, especially as nothing will stand still.

Of course the Neverlands vary a good deal. John's, for instance, had a lagoon with flamingoes flying over it at which John was shooting, while Michael, who was very small, had a flamingo with lagoons flying over it. John lived in a boat turned upside down on the sands, Michael in a wigwam, Wendy in a house of leaves deftly sewn together. John had no friends, Michael had friends at night, Wendy had a pet wolf forsaken by its parents, but on the whole the Neverlands have a family resemblance, and if they stood still in a row you could say of them that they have each other's nose, and so forth. On these magic shores children at play are for ever beaching their coracles [simple boat]. We too have been there; we can still hear the sound of the surf, though we shall land no more.

Of all delectable islands the Neverland is the snuggest and most compact, not large and sprawly, you know, with tedious distances between one adventure and another, but nicely crammed. When you play at it by day with the chairs and table-cloth, it is not in the least alarming, but in the two minutes before you go to sleep it becomes very real. That is why there are night-lights.

Occasionally in her travels through her children's minds Mrs. Darling found things she could not understand, and of these quite the most perplexing was the word Peter. She knew of no Peter, and yet he was here and there in John and Michael's minds, while Wendy's began to be scrawled all over with him. The name stood out in bolder letters than any of the other words, and as Mrs. Darling gazed she felt that it had an oddly cocky appearance.