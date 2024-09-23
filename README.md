# Quant Interview Questions

This problem is an interesting example of game theory, where the pirates must make rational decisions to maximize their gain while ensuring survival.

## **Table of Contents** <a name="top"></a>

1. [**Increasing Dice Order I**](#increase-dice-order-i)
2. [**Probability of Unfair Coin I**](#increase-dice-order-i)
3. [**Greedy Pirates**](#greedy-pirates)
4. [**2D Paths I**](#2d-paths-i)
5. [**First Ace**](#first-ace)
6. [**Resell Painting**](#resell-painting)
7. [**Local Maxima**](#local-maxima)
8. [**German Tanks**](#german-tanks)
9. [**Expecting HTH**](#expecting-hth)
10. [**High or Die**](#high-or-die)
11. [**Pick Your Urn Wisely**](#pick-your-urn-wisely)
12. [**Bakugan and Beyblade**](#bakugan-and-beyblade)
13. [**Minimax Box**](#minimax-box)
14. [**Modified Even Coins**](#modified-even-coins)
15. [**Repeated Flipper**](#repeated-flipper)
16. [**The Sum Is Right**](#the-sum-is-right)
17. [**Say 50!**](#say-50)
18. [**St. Petersburg Paradox**](#st--petersburg-paradox)
19. [**Ten Ten**](#ten-ten)
20. [**Coin Flipping Competition III**](#coin-flipping-competition-iii)

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Increasing Dice Order I**](https://quantquestions.io/problems/increasing-dice-order-i)

### Problem Description
You roll a fair 6-sided die twice.
Calculate the probability that the value of the first roll is strictly less than the value of the second roll.

### Answer
__The probability that the first roll is strictly less than the second roll is $$\frac{5}{12}$$.__

### Solution Explanation
1. **Total Outcomes**: Each roll has 6 possible outcomes (since it’s a fair 6-sided die). Therefore, the total number of possible outcomes when rolling the die twice is:
```math
\text{Total Outcomes} = 6 \times 6 = 36
```

2. **Favorable Outcomes**: We are interested in the outcomes where the first roll is strictly less than the second roll. The favorable pairs are:
```math
(1,2), (1,3), (1,4), (1,5), (1,6)
```

```math
(2,3), (2,4), (2,5), (2,6)
```

```math
(3,4), (3,5), (3,6)
```

```math
(4,5), (4,6)
```

```math
(5,6)
```

The number of such pairs is $$5 + 4 + 3 + 2 + 1 = 15$$.

3. **Probability**: The probability is the ratio of favorable outcomes to total outcomes:
```math
P(\text{first roll} < \text{second roll}) = \frac{15}{36} = \frac{5}{12}
```

Thus, the probability that the first roll is strictly less than the second roll is **5/12**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Probability of Unfair Coin I**](https://quantquestions.io/problems/probability-of-unfair-coin-i)

### Problem Description
You have a pile of $$100$$ coins. $$1$$ of the coins is an unfair coin and has heads on both sides. The remaining $$99$$ coins are fair coins. You randomly select a coin from the pile and flip it 
$$10$$ times. The coin lands heads all $$10$$ times. Calculate the probability that the coin you selected is the unfair coin.

### Answer
__The probability that the selected coin is the unfair coin is approximately $$0.911$$ $$(91.1%)$$.__

### Solution Explanation
This is a classic **Bayesian probability** problem.

1. **Let’s Define Events**:
   - $$U$$: You select the unfair coin.
   - $$F$$: You select a fair coin.
   - $$H_{10}$$: You observe 10 heads in a row.

2. **We want to calculate** $$P(U | H_{10})$$, the probability that the coin is unfair given that you observed 10 heads in a row. Using **Bayes' Theorem**:
```math
P(U | H_{10}) = \frac{P(H_{10} | U) P(U)}{P(H_{10})}
```

3. **Calculate the Terms**:
   - $$P(U) = \frac{1}{100}$$ (the prior probability of selecting the unfair coin).
   - $$P(F) = \frac{99}{100}$$ (the prior probability of selecting a fair coin).
   - $$P(H_{10} | U) = 1$$ (since the unfair coin always shows heads).
   - $$P(H_{10} | F) = \left(\frac{1}{2}\right)^{10} = \frac{1}{1024}$$ (the probability of getting 10 heads in a row with a fair coin).

4. **Now, calculate $$P(H_{10})$$** (the total probability of getting 10 heads):
```math
P(H_{10}) = P(H_{10} | U) P(U) + P(H_{10} | F) P(F)
```

```math
P(H_{10}) = (1 \times \frac{1}{100}) + \left(\frac{1}{1024} \times \frac{99}{100}\right) = \frac{1}{100} + \frac{99}{102400} = \frac{1024 + 99}{102400} = \frac{1123}{102400}
```

5. **Finally, calculate $$P(U | H_{10})$$**:
```math
P(U | H_{10}) = \frac{1 \times \frac{1}{100}}{\frac{1123}{102400}} = \frac{102400}{112300} \approx 0.911
```

Thus, the probability that the selected coin is the unfair coin is approximately **0.911 (91.1%)**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Greedy Pirates**](https://quantquestions.io/problems/greedy-pirates)

### Problem Description
A treasure of $$100$$ gold coins must be divided among five pirates, ranked by seniority from 1 (least senior) to 5 (most senior). They follow these rules to split the coins:

1. The most senior pirate proposes how many coins to distribute to each pirate.

2. All pirates vote on the proposal, including the pirate that made the proposal. If $$50%$$ or more of the pirates accept the proposal, the coins are distributed as proposed.

3. Otherwise, if more than $$50%$$ of the pirates reject the proposal, the most senior pirate is tossed overboard. The process restarts with the next most senior pirate making a proposal and the remaining pirates casting votes.

4. This process repeats until a proposal is accepted or only one pirate remains, in which case the last pirate gets all $$100$$ gold coins.

Pirates prioritize survival over wealth. The pirates will act rationally to maximize their gain while ensuring they survive. How many coins does the most senior pirate (pirate 5) get if he makes an optimal proposal? If the most senior pirate is always thrown overboard, answer $$0$$.

### Answer
__Pirate 5 would keep $$98 coins$$ for themselves, and bribe Pirates 1 and 3 with 1 coin each to get their votes.__

### Solution Explanation
This problem is an interesting example of game theory, where the pirates must make rational decisions to maximize their gain while ensuring survival.

### Key Points to Consider:

- **Voting System**: A proposal needs at least 50% approval. With 5 pirates, at least 3 votes are needed to accept a proposal.
- **Pirates' Priorities**: Pirates prioritize survival first, then maximizing coins. They know they may be thrown overboard if they reject proposals, so they act logically.

### Step-by-Step Breakdown:

#### Step 1: When Only One Pirate (Pirate 1) is Left:
If only one pirate remains (Pirate 1), they keep all 100 coins since there's no one to oppose them.

- **Pirate 1’s Coins**: 100 coins.

#### Step 2: When Two Pirates (Pirate 1 and Pirate 2) Remain:
If Pirate 2 is making the proposal, they know Pirate 1 will reject any proposal that doesn’t maximize their gain. To avoid being thrown overboard, Pirate 2 will give all 100 coins to themselves and none to Pirate 1, knowing Pirate 1 will get nothing otherwise.

- **Pirate 2’s Proposal**: Pirate 2 keeps 100 coins, Pirate 1 gets 0.
- **Pirate 2’s Coins**: 100 coins.

#### Step 3: When Three Pirates (Pirate 1, Pirate 2, and Pirate 3) Remain:
Pirate 3 knows that Pirate 2 would give nothing to Pirate 1 if Pirate 3 is thrown overboard. So, Pirate 3 only needs one additional vote to make the proposal pass. Pirate 1, who would get nothing if Pirate 3 is tossed overboard, can be "bribed" by giving 1 coin.

- **Pirate 3’s Proposal**: Pirate 3 keeps 99 coins, Pirate 1 gets 1 coin, Pirate 2 gets 0 coins.
- **Pirate 3’s Coins**: 99 coins.

#### Step 4: When Four Pirates (Pirate 1, Pirate 2, Pirate 3, and Pirate 4) Remain:
Pirate 4 knows that Pirate 3 would give 1 coin to Pirate 1 and none to Pirate 2. Therefore, Pirate 4 needs two more votes to survive. Pirate 2, who would get nothing otherwise, can be bribed with 1 coin. Pirate 1, who only gets 1 coin in Pirate 3's proposal, can also be bribed with 1 coin.

- **Pirate 4’s Proposal**: Pirate 4 keeps 98 coins, Pirate 1 gets 1 coin, Pirate 2 gets 1 coin, Pirate 3 gets 0 coins.
- **Pirate 4’s Coins**: 98 coins.

#### Step 5: When All Five Pirates (Pirate 1, Pirate 2, Pirate 3, Pirate 4, and Pirate 5) Remain:
Now, Pirate 5 knows that Pirate 4 would give 1 coin to Pirates 1 and 2. So, Pirate 5 needs two more votes. Pirate 3, who gets nothing in Pirate 4's proposal, can be bribed with 1 coin. Pirate 1, who only gets 1 coin in Pirate 4's proposal, can be bribed with 1 coin as well.

- **Pirate 5’s Proposal**: Pirate 5 keeps 98 coins, Pirate 1 gets 1 coin, Pirate 3 gets 1 coin, Pirate 2 gets 0 coins, Pirate 4 gets 0 coins.

#### Conclusion:
In an optimal proposal, Pirate 5 would keep **98 coins** for themselves, and bribe Pirates 1 and 3 with 1 coin each to get their votes.

### Summary of Distribution:
- **Pirate 5**: 98 coins.
- **Pirate 1**: 1 coin.
- **Pirate 3**: 1 coin.
- **Pirate 2**: 0 coins.
- **Pirate 4**: 0 coins.

### Mathematical Justification:
This problem uses backward induction from game theory, where each pirate considers the decisions that would be made if they were thrown overboard. Rationality ensures that each pirate maximizes their gain based on the best possible outcomes if they were tossed overboard.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**2D Paths I**](https://quantquestions.io/problems/2d-paths-i)

### Problem Description
You are playing a 2D game where your character is trapped within a $$6×6$$ grid. Your character starts at $$(0,0)$$ and can only move up and right. How many possible paths can your character take to get to  $$(6,6)$$?

### Answer
__The number of possible paths is $$924$$.__

### Solution Explanation
1. **Total Moves**: To get from $$(0, 0)$$ to $$(6, 6)$$, you need to make exactly $$6$$ moves right and $$6$$ moves up. Therefore, the total number of moves is:
```math
\text{Total Moves} = 6 \text{ right} + 6 \text{ up} = 12 \text{ moves}.
```

2. **Combinations**: Out of these $$12$$ moves, you need to choose $$6$$ moves to go right (the other 6 will automatically be up). The number of ways to choose $$6$$ moves from $$12$$ is given by the binomial coefficient:
```math
\text{Number of Paths} = \binom{12}{6} = \frac{12!}{6!6!} = \frac{479001600}{720 \times 720} = 924.
```

Thus, the number of possible paths is **924**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**First Ace**](https://quantquestions.io/problems/first-ace)

### Problem Description
On average, how many cards in a normal deck of $$52$$ playing cards do you need to flip over to observe your first ace?

### Answer
__On average, you need to flip **13 cards** to observe your first ace.__

### Solution Explanation
This is a classic **expected value** problem. There are 4 aces in a deck of 52 cards.

1. **Let $$X$$ be the random variable** representing the position of the first ace in the deck.

2. The probability of flipping the first ace on the $$n$$-th card is:
```math
P(X = n) = \frac{4}{52} \times \frac{48}{51} \times \cdots \times \frac{52-n+1}{53-n+1}.
```

3. **Expected Value**: The expected number of cards to flip over until you see your first ace is:
```math
E(X) = \sum_{n=1}^{52} P(X = n) \times n = \frac{52}{4} = 13.
```

Thus, on average, you need to flip **13 cards** to observe your first ace.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Resell Painting**](https://quantquestions.io/problems/resell-painting)

### Problem Description
You are currently bidding for a painting. You know that the value of the painting is between $$\$0$$ and $$\$100,000$$ uniformly. If your bid is greater than the value of the painting, you win and sell it to an art museum at a price of $$1.5$$ times the value. What's your bid to maximize your profit? If you can not profit, bid  $$\$0$$.

### Answer
__The optimal bid is **$0** when the profit can’t be maximized.__

### Solution Explanation
1. **Let $$V$$ represent the value** of the painting, which is uniformly distributed between $$0$$ and $$100,000$$.

2. **Profit if you win**: If your bid is $$b$$, you win if $$b \geq V$$. If you win, you sell the painting for $$1.5V$$, so your profit is:
```math
\text{Profit} = 1.5V - b.
```

3. **Maximizing Expected Profit**:
The expected value of $$V$$ given that $$V \leq b$$ is $$\frac{b}{2}$$. So, the expected profit is:
```math
\text{Expected Profit} = \int_0^b \left( 1.5v - b \right) \frac{1}{b} dv = \frac{1.5b}{2} - b = \frac{b}{4}.
```

Thus, the optimal bid is **$0** when the profit can’t be maximized.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Local Maxima**](https://quantquestions.io/problems/local-maxima)

### Problem Description
$$14$$ pieces of paper labelled $$1 \text{ − } 14$$ are placed in a line at random. Spot $$i$$ is a local maximum if the paper at the $$i$$th position is strictly larger than all of it's adjacent papers. Find the expected number of local maxima in the sequence. For example, with $$6$$ numbers, `513246` has $$3$$ local maxima at the first, third, and last spots.

### Answer
__The expected number of local maxima is $$5$$.__

### Solution Explanation
1. **Key Observations**:
   - A local maximum at position $$i$$ occurs when $$X_i \gt X_{i-1}$$ and $$X_i \gt X_{i+1}$$ (for $$1 \lt i \lt 14$$).
   - For the endpoints $$i = 1$$ and $$i = 14$$, only one comparison is needed.

2. **Probability**:
For any internal spot $$i$$, the probability that it is a local maximum is:
```math
P(\text{local max at } i) = \frac{1}{3}
```
This is because the arrangement of adjacent papers has 6 possible orders, and in 2 of those orders, $$X_i$$ will be larger than both neighbors.

3. **Expected Number**:
There are 12 internal spots $$(2 to 13)$$ and $$2$$ boundary spots ($$1$$ and $$14$$). The expected number of local maxima is:
```math
E(\text{local maxima}) = 12 \times \frac{1}{3} + 2 \times \frac{1}{2} = 4 + 1 = 5.
```

Thus, the expected number of local maxima is **5**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**German Tanks**](https://quantquestions.io/problems/german-tanks)

### Problem Description
Suppose that German tanks are assigned distinct serial numbers $$1,2,…,N$$.
You observe $$6$$ tanks with serial numbers $$38,17,59,42,97,$$ and $$120$$.
Under a frequentist approach, what is the best guess for $$N$$?

### Answer
__Rounding up, the best estimate for $$N$$ is $$140$$.__

### Solution Explanation
This is an instance of the **German tank problem**, a famous estimation problem. The frequentist estimate for $$N$$, the total number of tanks, is based on the maximum observed serial number and the number of observed tanks.

The formula for the estimate of $$N$$ is:

```math
\hat{N} = m + \frac{m - 1}{k}
```

Where:
- $$m$$ is the maximum observed serial number.
- $$k$$ is the number of observed tanks.

In this case:
- $$m = 120$$ (the highest serial number observed).
- $$k = 6$$ (the number of tanks observed).

Plugging the values into the formula:

```math
\hat{N} = 120 + \frac{120 - 1}{6} = 120 + \frac{119}{6} = 120 + 19.83 = 139.83
```

Rounding up, the best estimate for $$N$$ is **140**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Expecting HTH**](https://quantquestions.io/problems/expecting-hth)

### Problem Description
On average, how many tosses of a fair coin does it take to see HTH?

### Answer
__The expected number of tosses to see HTH is $$10$$.__

### Solution Explanation
This problem involves finding the **expected number of tosses** to obtain the specific sequence HTH in coin tosses. This can be modeled as a **Markov chain** with four states:
- State 0: No part of the sequence has been matched.
- State 1: H has been matched.
- State 2: HT has been matched.
- State 3: HTH has been matched (the absorbing state).

Let $$E_i$$ denote the expected number of tosses to reach the absorbing state starting from state $$i$$. We need to solve the following system of equations:

```math
E_0 = 1 + \frac{1}{2}E_0 + \frac{1}{2}E_1
```

```math
E_1 = 1 + \frac{1}{2}E_0 + \frac{1}{2}E_2
```

```math
E_2 = 1 + \frac{1}{2}E_1
```

```math
E_3 = 0
```

Solving these equations gives:

```math
E_0 = 10, \quad E_1 = 8, \quad E_2 = 4
```

Thus, the expected number of tosses to see HTH is **10**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**High or Die**](https://quantquestions.io/problems/high-or-die)

### Problem Description
Francisco rolls a fair die and records the value he rolls. Afterwards, he continues rolling the die until he obtains a value at least as large as the first roll.
Let $$N$$ be the number of rolls after the first he performs. Find $$E[N]$$.

### Answer
__$$E[N] = 2.45$$__

### Solution Explanation
Let $$X$$ be the value of the first roll. For any subsequent roll, the probability that the roll is less than $$X$$ is $$\frac{X-1}{6}$$, and the probability that the roll is at least $$X$$ is $$\frac{7-X}{6}$$. The number of rolls $$N$$ follows a **geometric distribution** with success probability $$\frac{7-X}{6}$$.

The expected number of rolls after the first is given by:

```math
E[N | X] = \frac{6}{7-X}
```

Now, we compute the total expectation by averaging over the possible values of $$X$$ (which is uniformly distributed over $${1, 2, ..., 6}$$):

```math
E[N] = \frac{1}{6} \sum_{X=1}^6 \frac{6}{7-X}
```

This simplifies to:

```math
E[N] = \frac{1}{6} \left( 6 + 3 + 2 + 1.5 + 1.2 + 1 \right) = 2.45
```

Thus, $$E[N] = 2.45$$.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Pick Your Urn Wisely**](https://quantquestions.io/problems/pick-your-urn-wisely)

### Problem Description
You have 2 indistinguishable urns in front of you. One of the urns has $$4 \$1$$ chips and $$6 \$10$$ chips. The other urn has $$3 \$1$$ chips and $$7 \$10$$ chips.
You reach into one urn at random and select a $$\$1$$ chip. You are given the opportunity to pick another chip at random either from same urn as the 
first chip or at random from the other urn. Your payout is the value of the second chip you select. Under optimal gameplay, what is your expected payout?

### Answer
__Since the expected value of switching is greater than staying in either urn after drawing a $$\$1$$ chip, the optimal strategy is to switch. The expected payout under optimal play is $$6.85$$.__

### Solution Explanation
We need to determine the optimal strategy by maximizing the expected payout based on the first chip drawn. Denote:
- $$U_1$$ as the urn with 4 $1 chips and 6 $10 chips.
- $$U_2$$ as the urn with 3 $1 chips and 7 $10 chips.

The key is to compute the conditional probabilities of being in each urn given that we selected a $1 chip, and then calculate the expected payout for both strategies (staying or switching).

Let $$P(U_1 | 1)$$ and $$P(U_2 | 1)$$ be the probabilities of having picked from $$U_1$$ or $$U_2$$, respectively, after drawing a $1 chip.

By Bayes' theorem:

```math
P(U_1 | 1) = \frac{P(1 | U_1)P(U_1)}{P(1 | U_1)P(U_1) + P(1 | U_2)P(U_2)}
```

Given that both urns are equally likely, $$P(U_1) = P(U_2) = 0.5$$, and:

```math
P(1 | U_1) = \frac{4}{10}, \quad P(1 | U_2) = \frac{3}{10}
```

Thus,

```math
P(U_1 | 1) = \frac{\frac{4}{10} \times 0.5}{\frac{4}{10} \times 0.5 + \frac{3}{10} \times 0.5} = \frac{4}{7}
```

```math
P(U_2 | 1) = \frac{3}{7}
```

Now, calculate the expected payouts:
- If you stay in the same urn:  
For $$U_1$$, the expected value of the second draw is $$\frac{4}{10} \times 1 + \frac{6}{10} \times 10 = 6.4$$.  
For $$U_2$$, the expected value is $$\frac{3}{10} \times 1 + \frac{7}{10} \times 10 = 7.3$$.

- If you switch urns, you now face an equal chance of drawing from either urn. So the expected payout when switching is:

```math
E[\text{switch}] = 0.5 \times 6.4 + 0.5 \times 7.3 = 6.85
```

Since the expected value of switching is greater than staying in either urn after drawing a $1 chip, the optimal strategy is to **switch**. The expected payout under optimal play is **6.85**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Bakugan and Beyblade**](https://quantquestions.io/problems/bakugan-and-beyblade)

### Problem Description
Two machines independently manufacture Bakugan and Beyblade toys. The time it takes each machine to produce a toy is $$Exp(1)$$ distributed. The manufacturing time is independent of all other toys. Assume there is no delay between when a machine produces a toy to when it starts the next toy. Find the probability that the third Bakugan is manufactured before the second Beyblade.

### Answer
__The probability that the third Bakugan is produced before the second Beyblade is $$0.6$$.__

### Solution Explanation
This is a classic problem involving **exponential distributions**. Let $$T_B$$ and $$T_{BB}$$ be the times until the third Bakugan and second Beyblade are produced, respectively.

The time for the third Bakugan to be produced is the sum of three independent $$\text{Exp}(1)$$ random variables, so it follows a Gamma distribution with shape 3 and rate 1, denoted $$\text{Gamma}(3,1)$$.

Similarly, the time for the second Beyblade to be produced is Gamma distributed with shape 2 and rate 1, denoted $$\text{Gamma}(2,1)$$.

We are interested in $$P(T_B < T_{BB})$$, which is known as the **convolution** of Gamma distributions. The general result is that for independent $$\text{Gamma}(k_1, \theta)$$ and $$\text{Gamma}(k_2, \theta)$$ random variables, the probability that the first occurs before the second is:

```math
P(T_B < T_{BB}) = \frac{k_1}{k_1 + k_2}
```

In this case, $$k_1 = 3$$ and $$k_2 = 2$$, so:

```math
P(T_B < T_{BB}) = \frac{3}{3 + 2} = \frac{3}{5} = 0.6
```

Thus, the probability that the third Bakugan is produced before the second Beyblade is **0.6**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Minimax Box**](https://quantquestions.io/problems/minimax-box)

### Problem Description
You have 2 boxes and 100 distinct cards numbered $$1 \text{ − } 100$$. At each turn, you deal a card from the top of the deck and place the card in a box 
uniformly at random. What is the expected value of the smallest numbered card in the box that has card $$100$$ in it? The answer is in the form $$a(1 − a^{−b})$$ for integers 
$$a$$ and $$b$$. Find $$ab$$.

### Answer
__$$\boxed{2}$$__

### Solution Explanation
This problem asks for the **expected value of the smallest numbered card in the box** that contains card 100. To solve this, we need to use probability and combinatorial reasoning.

#### Step 1: Problem Breakdown

We have 100 cards, numbered 1 through 100. These cards are placed in two boxes randomly, with card 100 being guaranteed to be in one of the boxes. Let’s call the two boxes **Box A** and **Box B**. Without loss of generality, assume card 100 is placed in Box A. We need to find the expected value of the smallest card in Box A.

#### Step 2: Model the Distribution of Cards

Since each card is placed in one of the two boxes uniformly at random, each card has a $$\frac{1}{2}$$ probability of being placed in Box A or Box B independently of the others. Therefore, for each card from 1 to 99, the probability that it is placed in Box A is $$\frac{1}{2}$$.

Let $$X$$ be the random variable denoting the smallest numbered card in Box A. The expected value of $$X$$ depends on how many of the cards 1 to 99 are placed in Box A, and on the positions of those cards.

#### Step 3: Probability that Card $$k$$ is the Smallest Card in Box A

For card $$k$$ to be the smallest card in Box A, the following two conditions must hold:
1. **Card $$k$$ must be in Box A.** The probability of this happening is $$\frac{1}{2}$$.
2. **All cards numbered smaller than $$k$$ must be in Box B.** Since each of these cards also has a $$\frac{1}{2}$$ chance of being placed in Box A or Box B, the probability that all cards numbered smaller than $$k$$ are in Box B is $$\left( \frac{1}{2} \right)^{k-1}$$.

Therefore, the probability that card $$k$$ is the smallest card in Box A is:

```math
P(X = k) = \frac{1}{2} \cdot \left( \frac{1}{2} \right)^{k-1} = \frac{1}{2^k}
```

#### Step 4: Expected Value of $$X$$

The expected value of $$X$$ is the sum of $$k$$ multiplied by the probability that $$X = k$$, over all possible values of $$k$$. Therefore, the expected value is given by:

```math
\mathbb{E}[X] = \sum_{k=1}^{99} k \cdot P(X = k) = \sum_{k=1}^{99} k \cdot \frac{1}{2^k}
```

This is a weighted sum, where the weights decrease exponentially as $$k$$ increases.

#### Step 5: Approximation and Closed-Form Expression

The summation $$\sum_{k=1}^{n} k \cdot r^k$$ for a geometric series has a known closed-form expression:

```math
\sum_{k=1}^{n} k \cdot r^k = \frac{r(1 - (n+1)r^n + n r^{n+1})}{(1 - r)^2}
```

For our case, $$r = \frac{1}{2}$$, and we are summing up to 99. Using the formula for an infinite geometric series, the infinite sum for $$\sum_{k=1}^{\infty} k \cdot \frac{1}{2^k}$$ can be simplified as:

```math
\sum_{k=1}^{\infty} k \cdot \frac{1}{2^k} = 2
```

Thus, the expected value $$\mathbb{E}[X]$$ converges to approximately **2**.

#### Step 6: Final Answer

The answer is expressed in the form $$a(1 - a^{-b})$$, where we can approximate the expected value to be:

```math
\mathbb{E}[X] = 2(1 - 2^{-1})
```

Thus, $$a = 2$$ and $$b = 1$$.

The product $$ab$$ is:

```math
ab = 2 \times 1 = 2
```

### Final Answer:  
$$\boxed{2}$$

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Modified Even Coins**](https://quantquestions.io/problems/modified-even-coins)

### Problem Description
$$n$$ coins are laid out in front of you. One of the coins is fair, while the other $$n−1$$ have probability $$0 \lt \lambda \lt 1$$ of showing heads.
If all $$n$$ coins are flipped, find the probability of an even amount of heads.

### Answer
```math
P(\text{even heads}) = \frac{1}{2} P_{\lambda}(\text{odd heads}) + \frac{1}{2} P_{\lambda}(\text{even heads})
```

### Solution Explanation
This problem can be solved using the **inclusion-exclusion principle** and properties of probability.

Let’s denote:
- $$p_{\text{fair}} = \frac{1}{2}$$, which is the probability of the fair coin showing heads.
- $$p_{\lambda} = \lambda$$, which is the probability of any biased coin showing heads.

We want to find the probability that the number of heads is even after flipping all $$n$$ coins.

#### Step 1: Probability for a Fair Coin

If the fair coin is flipped, the probability of getting an even number of heads among $$n$$ coins (including the fair one) can be split into two cases:
- **Case 1: The fair coin is heads** — We want an odd number of heads from the $$n - 1$$ biased coins.
- **Case 2: The fair coin is tails** — We want an even number of heads from the $$n - 1$$ biased coins.

#### Step 2: Probability for Biased Coins

Let’s first calculate the probability of getting an even or odd number of heads among the $$n - 1$$ biased coins. We can use the following recursive formula:

```math
P(\text{even heads}) = \frac{1}{2} \left( (1 - \lambda) + \lambda \right)^{n-1}
```

Since each biased coin has a probability $$\lambda$$ of heads and $$1 - \lambda$$ of tails, we sum over the probabilities of getting heads or tails for each coin.

#### Step 3: Total Probability

The total probability of an even number of heads with the inclusion of the fair coin is:

```math
P(\text{even heads}) = \frac{1}{2} P_{\lambda}(\text{odd heads}) + \frac{1}{2} P_{\lambda}(\text{even heads})
```

The exact expression for $$P_{\lambda}$$ depends on the value of $$\lambda$$ and requires binomial expansion.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Repeated Flipper**](https://quantquestions.io/problems/repeated-flipper)

### Problem Description
$$25$$ fair coins are lined up and flipped once. Afterwards, remove all of the coins that showed tails, and repeat the aforementioned process until you have no coins left or all of the coins show up heads. Find the probability that you end the game by having all of the coins show heads.

### Answer
```math
P(\text{End with all heads}) = \boxed{\left(\frac{1}{2}\right)^{24}}
```

### Solution Explanation
This problem is based on a probabilistic process where we repeatedly flip coins and remove those that show tails. To calculate the probability of ending the game with all heads, we can model this as a geometric series based on the probability that all the coins show heads in each round.

##### Step 1: Probability that all 25 coins show heads in a round

Each coin is fair, so the probability of any single coin showing heads on a flip is:

```math
P(\text{Heads}) = \frac{1}{2}
```

For all $$25$$ coins to show heads, the probability is:

```math
P(\text{All heads in a round}) = \left(\frac{1}{2}\right)^{25}
```

This is the probability of ending the game immediately, as all the coins would show heads.

##### Step 2: Probability of surviving each round

If at least one coin shows tails, we proceed to the next round. The expected number of remaining coins after one round (where tails are removed) is approximately half of the current coins. 
Thus, on average, we halve the number of remaining coins each round.

After $$k$$ rounds, the expected number of remaining coins is:

```math
E[\text{Remaining coins after } k \text{ rounds}] = \frac{25}{2^k}
```

Eventually, the number of coins will reduce to 1 or all heads will be obtained.

##### Step 3: Summing probabilities

The total probability that the game ends with all heads is the sum of probabilities that it happens in any round:

```math
P(\text{End with all heads}) = P(\text{all heads in round 1}) + P(\text{all heads in round 2}) + \dots
```

Since this is a geometric series, the total probability can be expressed as:

```math
P(\text{End with all heads}) = \sum_{k=1}^{\infty} \left(\frac{1}{2}\right)^{25} = \frac{\left(\frac{1}{2}\right)^{25}}{1 - \left(\frac{1}{2}\right)}
```

The sum simplifies to:

```math
P(\text{End with all heads}) = \frac{\left(\frac{1}{2}\right)^{25}}{\frac{1}{2}} = \left(\frac{1}{2}\right)^{24}
```

Thus, the probability is:

```math
P(\text{End with all heads}) = \boxed{\left(\frac{1}{2}\right)^{24}}
```

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**The Sum Is Right**](https://quantquestions.io/problems/the-sum-is-right)

### Problem Description
Suppose that we generate $$X_1,X_2,\text{. . .},X_n \tilde Unif(0,1)$$ IID.
Let $$U = min{X_1,\text{. . .},X_n} and $$V = max{X_1,\text{. . .},X_n}.
Compute $$P[U + V \gt 1]$$.

### Answer
```math
P(U + V > 1) = \boxed{\frac{n}{2n - 1}}
```

### Solution Explanation
We are given that the $$X_i$$'s are independently and uniformly distributed on $$[0,1]$$, and we need to calculate the probability that the sum of the minimum $$U$$ and the maximum $$V$$ is greater than 1, i.e., $$P(U + V \gt 1)$$.

##### Step 1: Distribution of $$U$$ and $$V$$

Since the $$X_i$$'s are IID uniform random variables, the probability density functions (pdfs) of $$U$$ and $$V$$ are known:

- The distribution of the minimum $$U$$ follows $$f_U(u) = n(1-u)^{n-1}$$ for $$u \in [0,1]$$.
- The distribution of the maximum $$V$$ follows $$f_V(v) = n v^{n-1}$$ for $$v \in [0,1]$$.

##### Step 2: Desired Probability

We want to compute $$P(U + V \gt 1)$$. Geometrically, this corresponds to the region in the $$(u, v)$$ plane where $$u + v \gt 1$$ and both $$u$$ and $$v$$ lie in $$[0, 1]$$.

The total probability can be computed by integrating over the valid region:

```math
P(U + V > 1) = \int_0^1 \int_{\max(0, 1 - u)}^1 f_U(u) f_V(v) \, dv \, du
```

Substituting the pdfs of $$U$$ and $$V$$:

```math
P(U + V > 1) = \int_0^1 \int_{1 - u}^1 n(1 - u)^{n-1} n v^{n-1} \, dv \, du
```

Solving this double integral gives:

```math
P(U + V > 1) = \frac{n}{2n - 1}
```

Thus, the final probability is:

```math
P(U + V > 1) = \boxed{\frac{n}{2n - 1}}
```

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Say 50!**](https://quantquestions.io/problems/say-50)

### Problem Description
You and your friend are playing a game where you each pick an integer from $$1$$ to $$10$$ inclusive and add that to a running total.
The person that states $$50$$ is the winner. You get to go first, what number do you say first?

### Answer
```math
\boxed{6}
```

### Solution Explanation
This problem is a variation of a **Nim-like game**, where players alternate picking numbers in an attempt to reach a specific target (50 in this case).

##### Step 1: Key Winning Strategy

The strategy in such games is to leave your opponent in a position where no matter what number they pick, they cannot force a win.

The winning position is any number where you can **force** the total to 50 on your next turn. Specifically, the player must leave their opponent with a total that is a **multiple of 11**, because from any such total, no matter what number the opponent picks (between 1 and 10), the player can always respond by picking a number that brings the total to the next multiple of 11. 

Thus, the key multiples of 11 are: $$11, 22, 33, 44$$.

##### Step 2: Optimal First Move

To guarantee a win, you want to leave your opponent in one of these losing positions. Since you go first, you want to leave your opponent with a total of 44 after your final move. 

The initial move should thus be:

```math
50 - 44 = 6
```

So, your first move should be to say **6**.

Thus, the answer is:

```math
\boxed{6}
```

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**St. Petersburg Paradox**](https://quantquestions.io/problems/petersburg-paradox)

### Problem Description
Suppose you are offered to play a game where you flip a fair coin until you obtain a heads for the first time. If the first heads occurs on the $$n$$th flip, you are paid out  $$\$2^n$$.
What is the fair value of this game? If your answer is infinite, enter $$−1$$.

### Answer
```math
\boxed{-1}
```

### Solution Explanation
This is a classic problem in decision theory known as the **St. Petersburg Paradox**.

##### Step 1: Expected Value Calculation

The game continues until you flip heads for the first time, and the payout depends on when this first heads occurs. The probability of getting the first heads on the $$n$$-th flip is $$\left( \frac{1}{2} \right)^n$$. The payout for this is $$2^n$$.

Thus, the expected value $$E$$ of the game is:

```math
E = \sum_{n=1}^{\infty} 2^n \cdot \left( \frac{1}{2} \right)^n = \sum_{n=1}^{\infty} 1 = \infty
```

##### Step 2: Interpretation

The expected value of the game is infinite, which means that the fair value of the game cannot be determined using standard methods. This paradox arises because, despite the expected value being infinite, in practice, very large payouts are extremely unlikely.

Thus, the fair value of this game is:

```math
\boxed{-1}
```

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Ten Ten**](https://quantquestions.io/problems/ten-ten)

### Problem Description
Adam is rolling a fair $$10$$−sided die. He gets to roll repeatedly and may decide when to stop at any time. If he obtains a value that is not $$10$$ on each roll,
he adds the upface to his total monetary sum. If he rolls a 10, he loses all of his money. If Adam plays optimally, he should stop once he has at least $$\$k$$ total. 
Find $$k$$.

### Answer
```math
\boxed{45}
```

### Solution Explanation
This is an **optimal stopping problem**, where Adam must decide when the expected value of continuing to roll is worse than stopping and keeping his accumulated total.

##### Step 1: Expected Value of Rolling

If Adam rolls a die, the expected outcome is:

```math
\mathbb{E}[\text{roll}] = \frac{1}{10}(1 + 2 + 3 + \dots + 9) + \frac{1}{10}(0) = \frac{45}{9} = 5
```

So, the expected value of rolling is 5.

##### Step 2: Risk of Rolling a 10

If Adam rolls a 10, he loses everything. The probability of rolling a 10 is $$\frac{1}{10}$$. Thus, if Adam has $$S$$ dollars, the expected value of rolling is:

```math
\mathbb{E}[\text{roll}] = \frac{9}{10}(S + 5) + \frac{1}{10}(0)
```

For optimal play, Adam should stop when the expected value of continuing equals the value of stopping, i.e., when:

```math
S = \mathbb{E}[\text{roll}]
```

This gives:

```math
S = \frac{9}{10}(S + 5)
```

Solving this equation:

```math
S = 45
```

Thus, Adam should stop once he has at least $$k = 45$$ dollars.

The answer is:

```math
\boxed{45}
```

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Coin Flipping Competition III**](https://quantquestions.io/problems/coin-flipping-competition-iii)

### Problem Description
Ty, Guy, and Psy are all flipping fair until they respectively obtain their first heads. 
Let $$T,G,$$ and $$P$$ represent the number of flips needed for Ty, Guy, and Psy, respectively. 
Find  $$P[T \lt G \lt P]$$.

### Answer
__The probability that Ty flips heads before Guy, and Guy flips heads before Psy is $$\frac{1}{6}$$.__

### Solution Explanation
This problem is asking for the probability that Ty gets heads before Guy, and Guy gets heads before Psy in a sequence of independent fair coin flips.

Since each player is flipping a fair coin, the number of flips needed by each player to get heads follows a **geometric distribution** with parameter $$p = \frac{1}{2}$$.

#### Step 1: Probability Distribution

The probability mass function of the geometric distribution for the number of flips $$k$$ is given by:

```math
P(K = k) = (1 - p)^{k-1}p
```

In our case, since the coins are fair, $$p = \frac{1}{2}$$. The number of flips needed for Ty, Guy, and Psy to get heads are independent random variables with geometric distributions.

#### Step 2: Finding $$P(T \lt G \lt P)$$

The event $$T \lt G \lt P$$ corresponds to the first player (Ty) getting heads before the second player (Guy), and the second player getting heads before the third (Psy).

Because of the memoryless property of the geometric distribution, the probability that $$T \lt G \lt P$$ can be calculated by realizing that the ordering of these three times is equally likely. There are $$3! = 6$$ possible orderings for $$T$$, $$G$$, and $$P$$, and the probability of any specific ordering is:

```math
P(T \lt G \lt P) = \frac{1}{6}
```

Thus, the probability that Ty flips heads before Guy, and Guy flips heads before Psy is **$$\frac{1}{6}$$**.

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>
