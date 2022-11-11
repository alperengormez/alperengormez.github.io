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
<img src="https://alperengormez.github.io/assets/whatsapp_chat/family_sunburst.png" alt="family_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/family_weekday.png" alt="family_weekday" width="300"/>

Naturally the peak time is the afternoon for me due to time zone difference, and we text before I go to bed too. Except Tuesday, the distribution over days is pretty much uniform.

### Mom
<img src="https://alperengormez.github.io/assets/whatsapp_chat/mom_sunburst.png" alt="mom_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/mom_weekday.png" alt="mom_weekday" width="300"/>

We text throughout the day and the frequency increases towards afternoon. Tuesday is again the day with the least amount of texting.

### Dad
<img src="https://alperengormez.github.io/assets/whatsapp_chat/dad_sunburst.png" alt="dad_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/dad_weekday.png" alt="dad_weekday" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/dad_wordcloud.png" alt="dad_wordcloud" height="400"/>

Daily pattern has two peaks. Weekly texting pattern is much different compared to the one with my mom.

### Girlfriend
<img src="https://alperengormez.github.io/assets/whatsapp_chat/girlfriend_sunburst.png" alt="girlfriend_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/girlfriend_month.png" alt="girlfriend_month" width="300"/>

Hourly texting distribution is pretty much uniform. I was not in the U.S. during last summer, so the frequency peaked there.

### Friend 1
<img src="https://alperengormez.github.io/assets/whatsapp_chat/friend1_sunburst.png" alt="friend1_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friend1_month.png" alt="friend1_month" width="300"/>

10+ years of friendship. Interesting monthly plot. I really do not know the reason behind it.

### Friend 2
<img src="https://alperengormez.github.io/assets/whatsapp_chat/friend2_sunburst.png" alt="friend2_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friend2_weekday.png" alt="friend2_weekday" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friend2_month.png" alt="friend2_month" width="300"/>

High school friend. We talk a lot about football (soccer). The frequency peaks on Tuesday-Wednesday and in the weekend at ~2pm Chicago time because of the matches. Monthly frequency increases starting in January and peaks in June, overlapping the end of the football season.

### Friend 3
<img src="https://alperengormez.github.io/assets/whatsapp_chat/friend3_sunburst.png" alt="friend3_sunburst" width="300"/>

A friend in the U.S., apparent from the hourly plot.

### Friend group 1
<img src="https://alperengormez.github.io/assets/whatsapp_chat/friendgroup1_sunburst.png" alt="friendgroup1_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friendgroup1_month.png" alt="friendgroup1_month" width="300"/>

High school friends from Turkey. Irregular frequencies, both hourly and monthly.

### Friend group 2
<img src="https://alperengormez.github.io/assets/whatsapp_chat/friendgroup2_sunburst.png" alt="friendgroup2_sunburst" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friendgroup2_weekday.png" alt="friendgroup2_weekday" width="300"/> <img src="https://alperengormez.github.io/assets/whatsapp_chat/friendgroup2_wordcloud.png" alt="friendgroup2_wordcloud" height="400"/>

Friends in Chicago. Mostly weekend plans.