# Brainteasers
Challenging puzzles or problems used to evaluate analytical thinking and problem-solving skills, common in quant interview assessments.

## **Table of Contents** <a name="top"></a>

1. [**Bridge Crossing**](#bridge-crossing)

<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>

## [**Bridge Crossing**](https://quantquestions.io/problems/bridge-crossing)

### Problem Description
Alice, Bob, Charlie, and Daniel need to get across a river. The only way to cross the river is by an old wooden bridge, which holds at most two people at a time. Because it is dark, they can't cross the bridge without a lantern, of which they only have one. Each pair can only walk at the speed of the slower person. They need to get all of them across to the other side as quickly as possible. Alice takes 10 minutes to cross; Bob takes 5 minutes; Charlie takes 2 minutes; Daniel takes 1 minute. What is the minimum time to get all of them across to the other side?

### Answer
__The minimum time to get all four across the river is$$17$$ minutes.__

### Solution Explanation

#### Re-Stating the Problem Statement:
Alice, Bob, Charlie, and Daniel need to cross a river using a bridge. The bridge can only hold at most two people at a time. They also have only one lantern, and since it's dark, they can only cross when someone is carrying the lantern. Each pair crossing the bridge walks at the speed of the slower person in the pair. Their individual times to cross the bridge are as follows:

- Alice: 10 minutes
- Bob: 5 minutes
- Charlie: 2 minutes
- Daniel: 1 minute

The goal is to find the minimum total time for all four to cross the river.

#### Solution Strategy:

This problem is a variation of a **greedy algorithm** problem combined with some elements of optimization. We need to devise a strategy that minimizes the total time to get everyone across the bridge.

##### Step 1: Consider All Possible Moves

We start by examining the fastest and slowest people:

- Daniel (1 minute) and Charlie (2 minutes) are much faster than Alice (10 minutes) and Bob (5 minutes).
- When two people cross the bridge together, they walk at the speed of the slower person. So, pairing Alice (10 minutes) and Daniel (1 minute) will take 10 minutes because they move at Alice's slower speed.

The challenge here is to minimize the total time while respecting the need for the lantern to always be on the correct side of the river.

##### Step 2: Key Observations

1. The key constraint is that **only one or two people can cross at a time**, and **someone must return with the lantern after each crossing**. 
2. Pairing the fastest people (Daniel and Charlie) with the slower ones (Alice and Bob) to bring them across efficiently is crucial. The fast people should often shuttle the lantern back to the start so that the slower people can cross in pairs.

##### Step 3: Analyzing Possible Strategies

A naïve approach might be to always pair the fastest person with the slowest, but this doesn’t necessarily minimize the time. Instead, let’s break the problem into steps:

1. **Send the two fastest (Daniel and Charlie) across first**:
   - Daniel and Charlie cross together, taking 2 minutes (the slower of the two, Charlie, dictates the time).
   - **Total time so far**: 2 minutes.
   - Daniel will return with the lantern.
   - **Total time**:$$2 + 1 = 3$$ minutes.

2. **Send Alice and Bob across together**:
   - Now Alice (10 minutes) and Bob (5 minutes) cross the bridge together, taking 10 minutes.
   - **Total time**:$$3 + 10 = 13$$ minutes.
   - Charlie returns with the lantern.
   - **Total time**:$$13 + 2 = 15$$ minutes.

3. **Send Daniel and Charlie across again**:
   - Daniel and Charlie cross the bridge again, taking 2 minutes.
   - **Total time**:$$15 + 2 = 17$$ minutes.

Thus, the minimum total time for all four to cross the river is **17 minutes**.

##### Step 4: Detailed Breakdown

1. **Initial Cross**: Daniel (1 minute) and Charlie (2 minutes) cross the bridge together. This takes 2 minutes, and Daniel returns with the lantern (1 minute). Total so far:$$2 + 1 = 3$$ minutes.
2. **Second Cross**: Alice (10 minutes) and Bob (5 minutes) cross the bridge together, taking 10 minutes. Charlie returns with the lantern (2 minutes). Total so far:$$3 + 10 + 2 = 15$$ minutes.
3. **Final Cross**: Daniel and Charlie cross again, taking 2 minutes. Final total:$$15 + 2 = 17$$ minutes.

#### Solution and Formulae:

- Let$$T_A$$,$$T_B$$,$$T_C$$, and$$T_D$$ be the times taken by Alice, Bob, Charlie, and Daniel, respectively. 
- The total time can be optimized by following the strategy that minimizes waiting and returning times. 
- The total minimum time is given by:

```math
T_{\text{min}} = 2T_C + T_B + T_A = 2(2) + 5 + 10 = 17 \text{ minutes}
```

This formula reflects the sequence of moves that minimizes the time: using the fastest person to ferry the lantern and limiting the slowest crossings to one.

#### Conclusion:

The minimum time to get all four across the river is **17 minutes**.


<div align="right"><a href="#top" target="_blacnk"><img src="https://img.shields.io/badge/Back To Top-orange?style=for-the-badge&logo=expo&logoColor=white" /></a></div>
