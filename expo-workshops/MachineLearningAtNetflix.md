# Expo: Machine Learning at Netflix 

## Introduction, Machine Learning at Netflix
- Speaker: Yves Raimond
- Leads Algorithms Team at Netflox

- 14 years ago, Netflix AI challenge was introduced to predict 5 star ratings 
- Now: From DVD by mail to worldwide, streaming and original content
- Applied ML Research has grown impressively as well 
- This expo: **Spotlight of the research Netflix cares about and some of their solutions**

- Netflix focus on these areas:
    -> Personalization
    -> Content
    -> Systems & Infrastructure 
    -> Studio, streaming, ML Platform (Not covered in these workshops)


## Recent Trends in Personalization at Netflix
- Speaker: Justin Basilico 

### Why do we personalize? 
- Help members find content for member satisfaction and retention -> "Spark joy"
- Netflix personalizes everything: Every Row + every selection in row + search queries + frames that are a good recommendation of a show
- Netflix: Everything is a recommendation and recommendation is hard!
  -> Every person is unique
  -> A lot of people are not even sure what they want
  -> Large dataset but small data per user
  -> Cold start problem: lots of new users

### How do we tackle personalization?
4 Trends 

 **Causality**
- Most recommendation algos are correlationalm but tis leads to problems: ***Did you watch a movie because you liked it or because we recommended it to you?***
- Small error or bias explodes through feedback loops, because more recommendations lead to more plays lead to more recommendations -> Everything is a feedback loop at Netflix
- There is a lot of high variance in in many causal models
- Causal inference at scale is computationally challenging
- How to we introduce randomization in the process?

**Bandits**
- Used to break feedback loops, as a way to explore and learn
- Bandits handle sparse and indirect feedback 
- Used in f.e. Which show artwork do we show to a user?
- Bandit finds good images a lot more than random, contextual bandit (personalization) works even better! 
- Challenges in the real world: Designing a good exploration scheme is an art, very very challenging.

**Reinforcement Learning Recommendations**
- Long-term member joy is important -> many user visits and delayed rewards -> sounds like a good way for RL!
- RL can be done in a page, in a session and across multiple sessions
- High dimensional action space (possible shows), states are also high dimensions (user histories)
- Right reward function is hard
- Lots of interesting stuff is happening in this space: embeddings for actions, etc. 

**Objectives for recommendation**
- What is your recommender trying to optimize? -> In Netflix's case: joy
- Layers of metrics: Training objective, Offline metric (historical data), Online metric A/B (as proxy), Goal
  -> What if your metrics are misaligned towards your end goal? -> This is extremely critical: **your recommendations can only be as good as the metrics you measure it on**
- Another problem: some multi-task learning improves performance, other task-bundling can hurt performance.
- Challenges in objective: How do you measure joy at scale? 
- A/B tests over weeks to months even, try to estimate what if we keep th
- We want

**Fairness of recommendations**
- Fairness: Match distribution of user interest
- Often fails: f.e. person likes 70% romance movies, 30% action -> Recommender system trained on accuracy will give 100% romance movies
- Handling fairness without demographic information is an open challenge

**Personalizing how (not what) we recommend**
- Algorithm level: balance diversity etc. per person

### Conclusion
- Lots of improvements still possible
