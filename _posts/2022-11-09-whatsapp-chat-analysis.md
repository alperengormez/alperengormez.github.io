---
title: "WhatsApp Chat Analysis"

categories:
  - Blog
tags:
  - analysis
  - data
  - mining
---

In this post, I will analyze some WhatsApp chats of mine. I forked <a href="https://github.com/joweich/chat-miner">this</a> repo and modified it a little bit. My fork is <a href="https://github.com/alperengormez/chat-miner">here</a>.

# Fixes
Messages that include Zoom links were causing the program to crash. I filtered these messages.

Chats that are exported without media were causing the word-cloud plot to have a giant "media omitted" phrase. Fixed this.

I added two functions for plotting the message counts per day and per month.

# Figures of my chats

Let's look at some plots now.

### Family group
![family_sunburst]({{ site.url }}/assets/whatsapp_chat/family_sunburst.png) ![family_weeekday]({{ site.url }}/assets/whatsapp_chat/family_weeekday.png)
Naturally the peak time is the afternoon for me due to time zone difference, and we text before I go to bed too. Except Tuesday, the distribution over days is pretty much uniform.

### Mom
![mom_sunburst]({{ site.url }}/assets/whatsapp_chat/mom_sunburst.png) ![mom_weeekday]({{ site.url }}/assets/whatsapp_chat/mom_weeekday.png)
We text throughout the day and the frequency increases towards afternoon. Tuesday is again the day with the least amount of texting.

### Dad
![dad_sunburst]({{ site.url }}/assets/whatsapp_chat/dad_sunburst.png) ![dad_weeekday]({{ site.url }}/assets/whatsapp_chat/dad_weeekday.png) ![dad_wordcloud]({{ site.url }}/assets/whatsapp_chat/dad_wordcloud.png)
Daily pattern has two peaks. Weekly texting pattern is much different compared to the one with my mom.

### Girlfriend
![girlfriend_sunburst]({{ site.url }}/assets/whatsapp_chat/girlfriend_sunburst.png) ![girlfriend_month]({{ site.url }}/assets/whatsapp_chat/girlfriend_month.png)
Hourly texting distribution is pretty much uniform. I was not in the U.S. during summer, so the frequency peaked there.

### Friend 1
![friend1_sunburst]({{ site.url }}/assets/whatsapp_chat/friend1_sunburst.png) ![friend1_month]({{ site.url }}/assets/whatsapp_chat/friend1_month.png) 
10+ years of friendship. Interesting monthly plot. I really do not know the reason behind it.

### Friend 2
![friend2_sunburst]({{ site.url }}/assets/whatsapp_chat/friend2_sunburst.png) ![friend2_weeekday]({{ site.url }}/assets/whatsapp_chat/friend2_weeekday.png) ![friend2_month]({{ site.url }}/assets/whatsapp_chat/friend2_month.png)
High school friend. We talk a lot about football (soccer). The frequency peaks on Tuesday-Wednesday and in the weekend at ~2pm Chicago time because of the matches. Monthly frequency increases starting in January and peaks in June, overlapping the end of the football season.

### Friend 3
![friend3_sunburst]({{ site.url }}/assets/whatsapp_chat/friend3_sunburst.png)
A friend in the U.S., apparent from the hourly plot.

### Friend group 1
![friendgroup1_sunburst]({{ site.url }}/assets/whatsapp_chat/friendgroup1_sunburst.png) ![friendgroup1_month]({{ site.url }}/assets/whatsapp_chat/friendgroup1_month.png)
High school friends from Turkey. Irregular frequencies, both hourly and monthly.

### Friend group 2
![friendgroup2_sunburst]({{ site.url }}/assets/whatsapp_chat/friendgroup2_sunburst.png) ![friendgroup2_weeekday]({{ site.url }}/assets/whatsapp_chat/friendgroup2_weeekday.png) ![friendgroup2_wordcloud]({{ site.url }}/assets/whatsapp_chat/friendgroup2_wordcloud.png)
Friends in Chicago. Mostly weekend plans, and movie suggestions over the winter.