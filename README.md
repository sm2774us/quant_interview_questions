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
