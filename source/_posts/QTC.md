---
title: 🌟QTC Camp 2021/01/25~2021/01/27
date: 2021-01-27 17:35:00
tags:
	- Quantitative Trading
	- Jane Street
categories: 
	- Experience
keywords: “Jane Street,Quantitative Trading,量化”
cover: https://tva1.sinaimg.cn/large/008eGmZEgy1gn2cdtagg4j30tc0jwdmc.jpg
top_img: https://tva1.sinaimg.cn/large/008eGmZEgy1gn2e6er78zj30zo0a1mxj.jpg
---

Quantitative Trading Camp(QTC) is a 3-day camp held by Jane Street, basically for students unfamiliar with trading to get a primary understanding of it. 

In these 3 days, we played games for most of the time and had some lectures regarding market and quantitative trading. This post mainly talks about all the games we played and some of my thoughts on them. 

# Why I applied for QTC

I applied for QTC by accident. I took part in a poker game at school and got a good place (given that I haven't played poker for years). At the poker game, there was a quantitative trading company seeking for students to apply for their winter camp. 

I had never thought of working in finance-related fields. But this poker afternoon made me want to have a try. So I asked a senior student whether I should apply, and he said: 'Then why don't you directly try to apply for QTC by Jane Street?'

I've heard of QTC from [lwpie](https://r.bin.sh.cn/). He had great time there last year. So I applied, and got in mysteriously. Sadly due to COVID-19, no offline camps any more. All games were held online using ZOOM and temporary websites.

I could tell after these three days that I had great fun, felt myself fully devoted, and got to know a bunch of smart guys and passionate Jane Streeters. Even though I am still not clear what my career would become, this camp is absolutely a great experience for this winter. 

**Many thanks to JS🧡.**



# Games

Some games are specifically designed for recruiting and teaching, while some are worldwide games related with trading. 

I've asked about the legitimacy of sharing these games in this blog. Good news are that I am free to write them down and people who are interested in these games could try to apply for QTC 2022. Bad news are that websites used in these 3 days may not be available then, so some games can only be held offline if you want to play (but gladly detailed rules are given below).

Here are all the games I experienced at QTC:

## Intro to trading games: Market is not zero-sum

### Rule

![image-20210125095158089](https://tva1.sinaimg.cn/large/008eGmZEgy1gn22rrng32j31iw0u0ae8.jpg)

### Play

The game is not zero-sum. We start with total profits $2\times(5+15+5+15+5) = 90$. See, now we are making the total profits way higher. 

![image-20210127110740418](https://tva1.sinaimg.cn/large/008eGmZEgy1gn235j2rvvj309y05yjrp.jpg)

Cuz we all have our own goals. Color players have **gains from trade**, so their score rises from 5 to much higher. Actually market makers don't have gains from trade; instead, they intermediate the trade and profit from the services they provide.

#### Why do trades happen (in stock market)?

The entire purpose of the stock market is to **facilitate the capitals between lenders and seekers**. Entrepreneurs, for example, need funds when founding companies. Later on, not only the traders get benefit from the booming of the company, but also the services the company is providing make customers better-off.

As for some minor reasons, in stock market, some want fluidity while some want stocks. For instance, the young might want more gains in the stock market while old guys need more cash to spend. 

**Trades move resources more broadly.**

---

# Estimathon

(I am especially not good at this one, though not surprised.)

### Rule

We were given 13 problems to estimate in 30 minutes. Problems are like *The number of times the word 'battery' appears in the owner's manual for the Tesla Model 3*. Our goal is to give the interval that might contain the right answer in it. The final score is determined by both the confidence of the interval (max/min) and the number of problems got solved.

Detailed rules can be found here (Might not available now. Just Youtube *Estimathon* is fine.): [Rules for Estimathon](https://estimathon.com/how-to-play).

Here's an example of the real-time scoreboard:

![image](https://tva1.sinaimg.cn/large/008eGmZEgy1gn22ugqusxj30nh099wfd.jpg)

**X** means a wrong guess of interval with no answer in it; a number **N** indicates a correct guess with the ratio $max/min = N$. The final score is calculated by:
$$
\left(10+\sum_{\text {good intervals }}\left\lfloor\frac{\max }{\min }\right\rfloor\right) \cdot 2^{13-(\# \text { of good intervals })}
$$

### Play

Our team did not do well on estimation, probably because we hesitated too much on problem choices and wasted chances for not being brave enough to guess the numbers in limited time.

---

## Bayes

![image-20210125140807381](https://tva1.sinaimg.cn/large/008eGmZEgy1gn22rqtfrhj31660a2760.jpg)

### Rule

Suppose that there is a good model and a bad model. You earn \$1000 for a good one and lose \$2000 for a bad one.

 We now know that $P(Good) = 2/3$ and $P(Bad) = 1/3$. Each time a model is settled, we can pay 20 dollars for a message, which is either '+' or '-'. We know in advance that $P(+\mid Good) = 0.8,P(-\mid Good) = 0.2$; $P(+\mid Bad) = 0.4,P(-\mid Bad) = 0.6$. We should decide whether to ask for a message, or to trade/stop.

### Play

What really matters here is setting a threshold or a margin of expectation gains that you are comfortable with. For instance, if you've already had 2 pluses, the chance that $P(Good \mid Data) / P(Good \mid Data) =8/1$ sounds good, but the expectation gain is only 666.67. 

You might think that $1/8$ is not likely to be risky for a trade; however, one more message with a plus would increase the probability to $16/1$, which is an expectation of around 800. And you will find out that even more pluses acquired, the expectation gain would not increase that much as the gap between 666.67 and 800. 

Hence, it is worthy to raise the expectation at the cost of merely \$20, and maybe stop and trade given one more plus. Cases are the same for bad model predictions.

---

## 4\*5 Mock

![image-20210127115617982](https://tva1.sinaimg.cn/large/008eGmZEgy1gn246rikxdj30uo0imqc7.jpg)

### Rule

There are 5 players. Each player throws a 20-sided die (which means each holds a number between 1 to 20) and holds secret. There are 6 rounds in the game shown above. In each round, all 5 players bet on one of the 20 boxes. Every box indicates a guess on the property of the 5 numbers.

All 5 numbers will become public after 6 rounds, so the bool value of the 20 boxes would become clear. For each box, if it is correct, all bets on it will gain +1/2/3/5 according to the #row of the box. But if it is wrong, all bets will get a minus one on the total score.

In 4\*5 Mock, **players need to cooperate with each other**, since the goal is to maximize the total gains of the group. The problem is that everyone needs to hold their own number secret, so we need to **offer as much information as possible by our choices of bets**. Thus, other players can get information from our choices and follow the bets that are more likely to gain points in the end.

### Play

We need to try not misleading others. For example, simultaneously betting on *5. #prime > #composite* and *2. #even > 3* should convey the information that you are holding the number 2. If not, you are misleading others.

In practice, the number rolled is important, because there ARE some cases that the five numbers are easier to determined through several rounds of bets. Nevertheless, those rollings are all by chances. This is why I did not enjoy much in this game, because it highly depends on what number every player holds and is not robust (one single miss of a player would largely affect the situation).

---

## Figgie

### Language for trading

-   I want to buy X for N chips: **N bid for diamond** <== Sell a diamond / 'sold'
-   I want to sell heart at N chips: **heart** (offered) **at N** <== Buy a heart / take them / take 'em

### Rule (abstracted from the website)

In Figgie, players buy and sell suits from each other: spades and clubs are black suits, hearts and diamonds are red suits.

Each Figgie deck contains 40 cards: two 10-card suits, one 8-card suit, and one 12-card suit. The suit matching each count is random and is not known to the players until the end of the hand.

**Only one special suit, the Goal suit, has any value. The Goal Suit is the suit that is the same color (black or red) as the 12-card suit.** The Goal Suit can contain either 8 or 10 cards. All other suits are worth nothing.

Players trade cards within a 4 min game. When the game ends: 

-   Players collect $10 from the pot for each Goal Suit card that they own at the end of trading
-   The owner or owners of the most Goal Suit cards win the rest of the pot (called the bonus)
    -   The bonus is $100 if the Goal Suit has 10 cards
    -   The bonus is $120 if the Goal Suit has 8 cards

### Play

There are 2 normal cases of the initial cards we get: 

1.  ≈5 cards of the same color.
2.  Uniformly distributed colors.

In the first case, suppose that you have 5 spades, then you probably consider spades as the common suit, so you could trade for more clubs at the beginning.

In the second case, maybe it is a better choice to sell all your cards at a reasonable price, since  you are less likely to speculate the goal suit, as well as to have a majority of the goal suit.

During trading, you are able to tell what suit each player wants, hence you might know what others' guesses are.

![image-20210127163951135](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2cdtagg4j30tc0jwdmc.jpg)

Here, I showed a picture of a game result. Heart is the goal suit, so players holding 4 hearts share the bonus of \$100, and got \$10 for each heart they hold. Note that in the most cases, it is a better choice to keep a majority of the goal suit (that you guess) and sell the useless cards to others. So 4-0-0-4 is a reasonable ending (at least to me).

---

## Metals Mock

(Normal but maybe the most interesting and fully-devoted game for me.)

### Rule

A team consists of 3 people. We have three market rooms to choose from: Gold, Silver, and Bronze. The fixed conversion rate is: 1 Gold = 15 Silver, 1 Silver = 25 Bronze, 1 Gold = 375 Bronze. We start with 3000 JS Dollars. 

### Play

For communication, we first divide the work in the breakout room, and then use Skype for text communication.

In each market room, we share the current gold/silver/bronze rate with teammates through Skype. In gold room, for example, the rate was at first 960-980, 3 by 3 (which means 960 bid for 3 gold and 3 gold at 980). Meanwhile, the price of silver is relatively low. Hence, **we bought silver, convert it to gold, and sell it as soon as possible**. 

Things were simple at the beginning. We only have to figure out which road of buying, converting, and selling is making the most profits. Here, **speed really matters**, since the price of gold is lowering rapidly. By speed, I mean the decision speed as well as the website updating speed. So we have to leave time for website refreshing, which means our costs and gains should leave a **margin** for the time delay.

Later on, changes happen. Silver market is closed. Gold market starts to lower the price even more quickly, but chances are that **robbery** happens during the conversion between gold and other commodities at 25%. Normally, we buy gold, convert it to bronze, and sell bronze. But we now need to **compute the expectation gains taking robbery into consideration**. Hence, we decide to stop when the margin between costs and gains is smaller than 100.

We keep making profits except the last several trades. We were buying golds but bronze market kept going down after the conversion. So we had to sell those golds for JS dollars.

Our trades were pretty good. For better results, perhaps more efficient trades at the beginning and confident stop at the end will do. And thank god no robbery happens to our team. I speculate other teams' website, robbery does happen. Sad story:(

![https-qtc-trading-janestreet-com-November-html](https://tva1.sinaimg.cn/large/008eGmZEgy1gn29z2q32oj30u00we7wh.jpg)

---

## A-10 Mock

### Rule

10 cards from 1 to 10. 5 players each holds a card, and 5 left are called undealt cards. Take the sum of undealt cards as A-10. We trade contracts that are actually worth the exact number of A-10. 

When trade begins, we prefer to buy at a price lower than A-10 and sell at a price higher than A-10. But since we do not know A-10, we would try to guess given our own card and the trades happening.

### Play

Monitoring on trades happening would normally reveal the information about someone who has a boundary number. This will largely narrow the guess of A-10. 

But cases do exist where people make guesses when bidding. Thus, misleading sometimes happen in the whole market. In one of our games, we all presume that 2 is held by a player, so the bidding price is relatively high. 

![image-20210127162300199](https://tva1.sinaimg.cn/large/008eGmZEgy1gn2bwfb0kcj31hx0u0490.jpg)

We all consider A-10 to be around 800, so bidding price around 600 in the above picture is just fine. But it turns out that 2 is an undealt number, so everyone selling is profiting a lot while everyone buying are losing money. The losses still make sense though, since the expectation value is what we normally rely on. 2 as the last number does not happen that often.

---

# Some Insights

-   **Trading is not a zero-sum game.** Trading does create value, where both sides can benefit from it, mostly because both sides have different goals to pursue.

-   **Market makers** start with nothing (By nothing, I mean no real commodities.) They **gain profits from offering services to seekers and lenders**. They are bridge builders. And they ARE necessary, because when large number of seekers and lenders occur in the market, they are not able to find each other without the help of market makers.

-   Some games need cooperation, while others need fighting alone. But here, the way of **cooperation** varies:

    -   For Estimation, cooperation might be work division.
    -   For Bayes, cooperation might be discussion for a common threshold.
    -   For 4*5 Mock, cooperation might be offering as much information as you can through your trades (bets). 
    -   For Metals Mock, cooperation might be instant information sharing and quick decision making.

    Though games like Figgie and A-10 Mock do not seem to have cooperation in them, they are similar to 4\*5 Mock. That is to say, this kind of game requires **information gain in the process of trading**. Everyone starts with partial information, and **trading itself will convey more information**.

-   Metals Mock might be my favorite game, cuz it was the most intense one with frequently used trade language. Also, my 2 teammates were both nice guys and it was probably the game most similar to real-world arbitrage.

-   I got most insights from the kind of game I mentioned in the 3rd bullet point, namely Figgie, A-10 Mock, and 4\*5 Mock. We don't trade after we have gathered all the information. Instead, we trade during thinking, and we **observe all the trades on table to shift our biases**.

-   **Probability really matters**. It's the first time I find so many **applications of probability on real life**. I used to rely more on personal biases, or some rough feelings. Like, *I think the risk is not that high so maybe I can trade now.* But the truth is that I could have cultivated a more rational mind by relying on probability more, so that I can be more confident at each trade I make.

-   These games REALLY require much **mental energy**. Every single day after QTC I felt quite sleepy😪. Partly because of sitting for the whole day, yes, but mostly for being highly focused all the time.



If you are interested in more about QTC or the games, feel free to contact me!



