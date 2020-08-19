# Introduction to RL

We are not born with any knowledge we attain this knowledge by interacting with the world around us, when we interact with the world we learn about cause and effect and understand how the world responds to our actions. Once we understand how the world responds to our interaction we use this knowledge to attain specific goals. The real world is very complex so we create a learning environment with specific set of rules we make algorithms to tech agents in this world to learn from interactions and use this knowledge to obtain a certain goal.

---

# Application
The application of RL vary a lot ranging from 

The AI bot that plays Alpha GO

RL algorithm that plays Atari games

Teaching robots to walk 

and even self driving cars

---
# The Setting
In a RL environment there should be something that takes a particular decision this something is called and Agent. The Agent interacts with the environment and based on the feedback received by the environment make strategies to maximise its reward.

As an analogy we can consider our Agent to be a puppy who is new born and has only started to explore the environment. It knows that it has to follow what the owner says and when it does something right it gets a treat or a positive reinforcement or when it does something wrong it gets a negative reinforcement. It does not know how do something on its own when the owner says a command it does something randomly and the wait for the owner to give a feedback in the form or a reward based on the reward it acquires some knowledge and prepared itself for the next command.

After a lot of trial and error the puppy learns strategies to maximise the amount of treats it can get over the course of its lifetime there by understanding how to preform correctly to what its master is saying.

---

# Exploration-Exploitation Dilemma

## Exploration

Exploring potential hypothesis on how to perform an action.

## Exploitation

Exploring limited knowledge about what is already known to work well.

Consider a situation where our puppy learn to do 5 tricks now it is knows doing this tricks correctly will get it rewards but what if the owner gives an other command and the puppy try to do one of the five tricks this is called exploration-exploitation dilemma.

---

# The RL Framework: The Problem

# Introduction

This session is mostly to discuss about how we can take a real world problem and convert it into a specific method such that we can use reinforcement learning to solve them.

---

## The Setting

Earlier we have taken the example of a dog which learns through trail and error and waits for a reward and action from the owner. To change this to a reinforcement learning problem not much changes we can replace the dog with a robot or driverless car in general we call them a reinforcement learning agent.

To put this in RL Term we say that the Agent interacts with the Environment and that time involves in discrete time steps.

In the first time step the Agent waits for an Observation from the Environment then according the observation the agent must select an appropriate action in response. In the next time step the environment presents with a new observation and also gives a reward which indicates weather the agent has responded correctly or incorrectly.

This process continues for some time step where the environment sends a reward and observation and at each step the agent should present a action to the environment.

![assets/Screenshot_2020-08-03_at_4.44.28_AM.png](assets/Screenshot_2020-08-03_at_4.44.28_AM.png)

In RL terms we do not say that the agent receives an observation instead we refer to it as a state.

To represent this is a more mathematical way we can say that in the time-step 0 the environment septs state S0 to the agent the agent then responds with an action A0. In the next time step 1 the environment sends the agent with a state A1 and a Reward R1 then the agent sends back and action A1 to the environment.

This continues for the next state too

![assets/Screenshot_2020-08-03_at_4.49.42_AM.png](assets/Screenshot_2020-08-03_at_4.49.42_AM.png)

So generally we can say that when the agent interacts with the environment it manifest a series of state action and reward.

The Reward is the most relevant quantity to the Agent.

The goal of the Agent is to maximize expected cumulative reward.

 

---

# Episodic Tasks

The real world problems that we say have a well defined end point for example if we are considering playing a game when the agent looses or wins the task ends. If we consider a self driving car the task ends when the car crashes.

When we are considering such scenarios The agent learns by the reward in each of its life and the next live the agent has the added knowledge which allows it to perform better to achieve its goal.

---

# Continuous Tasks

Some tasks are not like this and does not have a well defined endpoint like an agent that buys and sells stocks such agents life without a lifetime and are called continuous tasks.

---

# The Reward Hypothesis

Earlier we discussed that the reward is like the number of treat that a puppy gets , the state is interaction with the owner and the action is the puppies response to the owners command. The task of the puppy here is to maximise the amount of treats that the puppy gets.

This is true for any reinforcement learning agents in general works this way the goal of the agent is to maximise the expected cumulative reward.

![assets/Screenshot_2020-08-03_at_8.28.12_PM.png](assets/Screenshot_2020-08-03_at_8.28.12_PM.png)

The reward hypothesis is that all goals can be framed as the maximisation of expected cumulative reward.

---

# Discounted Return

Lets us take a look at our puppy agent again, The goal of all agent is to maximise the cumulative reward but if we consider the lifetime of the puppy the puppy would be more interested in immediate reward compared to future reward this is where the concept of discount return comes in.

![assets/Screenshot_2020-08-12_at_12.24.26_PM.png](assets/Screenshot_2020-08-12_at_12.24.26_PM.png)

This is how we can represent the cumulative reward but here the future reward have same value as that of the present one so in-order to train the model efficiently we can introduce discounted returns

![assets/Screenshot_2020-08-12_at_12.31.03_PM.png](assets/Screenshot_2020-08-12_at_12.31.03_PM.png)

How we select this value is by using a discount rate represented by gamma, which would always be a value between 0 and 1.

then we multiply these values increasing by one in there power for each step.

![assets/Screenshot_2020-08-12_at_12.32.40_PM.png](assets/Screenshot_2020-08-12_at_12.32.40_PM.png)

We can even use the value 0 or 1 to change the meaning of the whole return for example

![assets/Screenshot_2020-08-12_at_12.37.13_PM.png](assets/Screenshot_2020-08-12_at_12.37.13_PM.png)

if gamma is 1 we would have the same return for each time-step and if we choose 0 the reward would only be applicable for the first time step.

---

# MDPs

Let us take the example of a robot that picks up garbage cans, this robot runs on battery and has a docking station. When the robot is not docked its purpose is to collect as much as cans as possible.

The robot has three actions

1. search
2. recharge 
3. wait

The robot can either search for garbage cans or be in the docking stand recharging else stay still and wait for someone to bring the can to the robot.

The robot also have two states 

1. High
2. Low

This corresponds to the amount of charge the robot has left on his battery , when it has high amount of charge left we can set it free to go and look for garbage cans but when the robot is in low state we should probably refrain from doing so reason being in this case the robot might end up turning off when in no charge and we having to go manually and pick up the garbage.

![assets/Screenshot_2020-08-13_at_2.44.57_AM.png](assets/Screenshot_2020-08-13_at_2.44.57_AM.png)

The picture below shows a state space diagram of the robot we are talking about earler,

Let us look at it individually 

when we are at high let say we are in the docking station and we have two actions that we can do that is 

1. Wait
2. Search

We are not considering recharge in this state since that does not make sense.

The next state is low that is lets say the robot is going on collecting cans in this state the robot can choose to do three action

1. Search
2. Wait
3. Recharge

Let us focus on High component for now,

We are assigning rewards for each decision that the robot takes if the robot is in high sate in the docking station and waits there and does not choose to move lets say the probability of doing this is 0.1 we give it a reward of 1 let say since someone brought a can to the robot. But lets say that the robot decides to search with a probability of 0.7 and collects 4 cans so we give it a reward of 4 assuming the robot still has high charge but if the robot goes to low charge that mean there is a probability of 0.3 that it goes to low charge but still manages to collect 4 cans we give it a reward of 4.

Now let us focus on the low state,

Assuming the robot is in low state and decides to wait and collects 1 can given that the probability of the robot waiting is 0.1 we give it a reward of 1, lets say the robot decided to search and collect some more can and the robot depletes its battery in this case we have to carry the robot to the docking station then lets say the probability of this happening is 0.8 and we give the robot a negative reward of -3. But instead if the robot goes on searching and still manages to be in low state and finds 4 cans we give it a reward of 4 given that the probability of this happening is 0.2.

There is one more scenario here if the current state is low and the agent decides to go to the docking station by itself with a probability of 1 (it does go there no matter what) the robot is not awarded any reward. 

This method of decision problems is called Markov decision problem and this is the underlying principle we use to design a RL problem. Some of the allocation of reward might seem a bit weird but we would get deeper into this.

To summarise

We can say that 

A finite Markov decision problem is defined by:

- a (finite) set of states S
- a (finite) set of actions A
- a (finite) set of rewards R
- the one step dynamic of the environment
- a discount rate

Things like the state action and discount rate is known to the agent but the one step dynamics and rewards in unknown.

---

# The RL Framework : The Solution

# Policies

We know that we use a MDP to make the framework for a RL problem. If we look at examples of training a humanoid robot how to walk we would notice that how the robot has to behave depends on lot of factors like the change in environment for example walking in a hilly terrain is different to walking in a normal terrain this is where the concept of policies come in.

There are two kinds of policies

1. Deterministic
2. Stochastic

 

## Deterministic Policy

Deterministic policy can be defined as the mapping of a state to the action basically we can think of it as a factory that takes in the state and outputs the action.

## Stochastic Policy

Stochastic policy is the mapping of the state and action to the probability of the agent taking the said action. We can think of it as a factory given an action and a state outputting the probability that the agent takes the action in the given state.

Let us see this on the concept of our waste collecting robot example.

![assets/Screenshot_2020-08-14_at_9.09.31_AM.png](assets/Screenshot_2020-08-14_at_9.09.31_AM.png)

---

# Gridworld Example

Let us consider a very small world which are grids of green grassy patches of which two of these grids have mountains on them. 

![assets/Screenshot_2020-08-14_at_9.18.44_AM.png](assets/Screenshot_2020-08-14_at_9.18.44_AM.png)

The locations in this world can be considered as states in the environment.

Let us say that the agent in any given time-step can move up,down,left or right and can only do actions which will not let it fall off the grid. We can represent this using arrows.

![assets/Screenshot_2020-08-14_at_9.20.50_AM.png](assets/Screenshot_2020-08-14_at_9.20.50_AM.png)

Let us say that the goal of the agent is to reach the bottom right corner and this task can be considered as an episodic task and when the agent reaches the goal an episode ends. Here we can leave out the possibility of the agent going out of the right bottom corner as the task ends there.

![assets/Screenshot_2020-08-14_at_9.22.27_AM.png](assets/Screenshot_2020-08-14_at_9.22.27_AM.png)

Now we need to assign rewards to actions the agent takes

if the agent moves to a grassland let us give it a reward of -1

If it moves to a mountain area let us give it a reward of  -3 

If the agent reaches the goal let us give it a reward of 5.

This reward structure encourages the agent to reach the goal as soon as possible since for every step it takes outside the goal it is receiving some kind of penalty.

![assets/Screenshot_2020-08-14_at_9.25.06_AM.png](assets/Screenshot_2020-08-14_at_9.25.06_AM.png)

When the agent reaches the goal it gets a reward of 5 and the episode ends.

---

# State-Value function

Let us say before we start our learning we follow a very bad model to reach our goal we start from the top left corner and then we move through all the states and reach the last grid.

![assets/Screenshot_2020-08-14_at_12.44.41_PM.png](assets/Screenshot_2020-08-14_at_12.44.41_PM.png)

Now the we need to calculate the cumulative reward when we reach the final stage , we are not using the concept of discounted rate here or lets say we are using discount rate of 1, now the cumilative reward is -6.

We can assign this number to the grid on top left corner.

![assets/Untitled.png](assets/Untitled.png)

Now let us start from the next adjacent grid and do the same and continue for all the grids, since this is an episodic tasks the task will stop when we reach the last grid or if we start from the last grid also the episode stops and we can just associate this with a reward of 0.

![assets/Screenshot_2020-08-14_at_1.31.17_PM.png](assets/Screenshot_2020-08-14_at_1.31.17_PM.png)

Hence the grid formed from this method is corresponds a number to the action the agent takes if it starts on that state.

![assets/Screenshot_2020-08-14_at_1.32.25_PM.png](assets/Screenshot_2020-08-14_at_1.32.25_PM.png)

We refer to this function as a state value function.

We call the sate-value function for policy pie The value of state s under a policy pie,

For each of the state s it yields the expected return if the agent starts in state s and then uses a policy pie to choose its action for all time-steps.

---

# Bellman Equation

As we said above calculating the reward one by one would be very hard, bu what we can do is if we know the reward of a particular sate it is easy for us to calculate the discount of the nearby states.

If we look closely the value function has a nice recursive property,

![assets/Screenshot_2020-08-15_at_9.24.30_AM.png](assets/Screenshot_2020-08-15_at_9.24.30_AM.png)

Let us erase some of the values then we would be left with something like this,

here since we are using a discount rate of 1 to find the value of the intermediate grid we can just sum with the reward consider 2 if you add -1 we will get 1 which is the value for the adjacent grid we can continue this for all the grid.

This applies to our simple world but how can we express this for a more complex world ?

![assets/Screenshot_2020-08-15_at_9.27.10_AM.png](assets/Screenshot_2020-08-15_at_9.27.10_AM.png)

We use the bellman expectation equation.

---
# Optimally

![assets/Screenshot_2020-08-15_at_11.20.59_AM.png](assets/Screenshot_2020-08-15_at_11.20.59_AM.png)

Let us compare two state value policies, we can see a pattern here the one on the left is the values are less that that of on the right or the once on the right are greater than or equal to the once on the left, this means the the one on the right offers a better reward function than the one on the left.

Similarly the goal of the agent would be to find the optimal policy in this, by definition we can say

![assets/Screenshot_2020-08-15_at_11.23.16_AM.png](assets/Screenshot_2020-08-15_at_11.23.16_AM.png)

This defines optimality and the goal of the agent is to find the optimal solution to the MVP that is defined.

The optimal policy function is denoted by 

$V*$

---
# Action Value Functions

![assets/Screenshot_2020-08-15_at_11.57.45_AM.png](assets/Screenshot_2020-08-15_at_11.57.45_AM.png)

basically here also we are calculating a grid but instead of using denoting by one value we use 4 values to represent what happens when each action is taken by the agent this would look something like,

![assets/Screenshot_2020-08-15_at_12.01.04_PM.png](assets/Screenshot_2020-08-15_at_12.01.04_PM.png)

---

# Optimal Policy

The goal is basically for the agent to construct an action value function by interacting with the environment and uses

![assets/Screenshot_2020-08-15_at_12.20.09_PM.png](assets/Screenshot_2020-08-15_at_12.20.09_PM.png)

This is what we have right now.

All we have to do to find the optimal value is to follow the grid in each step for the higher value this would give us the optimal policy.

![assets/Screenshot_2020-08-15_at_12.27.02_PM.png](assets/Screenshot_2020-08-15_at_12.27.02_PM.png)

This is what that would look like , in the grid where it is 1 for all values we can actually follow any path and would yield the optimal result.

---
# Dynamic Programming

This is a problem which is more simple than the RL problem here the agent has full knowledge about the environment.

Let us consider a more simpler example

with just 4 grids and one mountain and by applying similar reward funcitons

![The%20RL%20Framework%20The%20Solution%20be876f21ee54498b8b99e23b975f6965/Screenshot_2020-08-15_at_6.15.08_PM.png](assets/Screenshot_2020-08-15_at_6.15.08_PM.png)

As discussed earlier we need to define the action value function for each of the state in the world

If we consider the first grid let us name it s1 in this grid we can either move left or right and the probability of moving right is 0.5 and so is the probability of moving left. Let us use the same concept for all the states.

![The%20RL%20Framework%20The%20Solution%20be876f21ee54498b8b99e23b975f6965/Screenshot_2020-08-16_at_1.16.04_PM.png](assets/Screenshot_2020-08-16_at_1.16.04_PM.png)

To find the bellman equation from this what we can do is to multiply the probability of each state to the reward for the taken action and the reward at that stage

![The%20RL%20Framework%20The%20Solution%20be876f21ee54498b8b99e23b975f6965/Screenshot_2020-08-16_at_1.18.26_PM.png](assets/Screenshot_2020-08-16_at_1.18.26_PM.png)

Once we have the reward for all these states we can just use the system of equations to find the values for each states.

This is a bit cumbersome method but there is an iterative method which we can follow that is initially we can guess the value for every stage and move from one stage to another and then update the values and eventually we would converge to the result.

![The%20RL%20Framework%20The%20Solution%20be876f21ee54498b8b99e23b975f6965/Screenshot_2020-08-16_at_1.20.24_PM.png](assets/Screenshot_2020-08-16_at_1.20.24_PM.png)

What this basically means is converting the equations we have earlier to an update rule.

## [Solving Open AI Frozen Lake using Dynamic Programming](https://github.com/abhijitramesh/RL-under-the-hood/blob/master/frozenlake/Dynamic_Programming.ipynb)

---

# Monte Carlo Method

# Introduction

Previously we solved the frozen-lake environment problem from OpenAI using Dynamic Programming Now we will focus on doing something better that is for dynamic programming we assume that the agent knows everything about the environment and it takes decision now we are going to follow a different approach where the agent is not given any knowledge of the environment and since this is one of the underlying principle of reinforcement learning we are going to use this for the future methods also.

---

# MC Prediction : State Values

Lets say that the we have a very small frozen lake environment with x y and z, the goal of the agent is to reach z and thereby ending the episode. When the agent is at x or y it receives a reward and a state and chooses the next action. Similarly let us assume that the agent did the same for 3 episodes following three policies.

![assets/Screenshot_2020-08-17_at_1.46.53_PM.png](assets/Screenshot_2020-08-17_at_1.46.53_PM.png)

What monte carlo method tells us is to take observe one state determine the cumulative reward of that state then average the value to find the approximation for the value of that state.

![assets/Screenshot_2020-08-17_at_1.48.07_PM.png](assets/Screenshot_2020-08-17_at_1.48.07_PM.png)

Here we are following the state X

Let us follow the sate Y but here there are multiple occurrence of the sate in each step so we need to follow only one of them and for that we consider that each visit as an entry to the sate and we need to determine if we want to follow first entry or second entry Monte Carlo method.

![assets/Screenshot_2020-08-17_at_1.51.00_PM.png](assets/Screenshot_2020-08-17_at_1.51.00_PM.png)

Here we are considering the first visit MC method.

Another approach would be to consider all the visits to all the instances of the state Y

![assets/Screenshot_2020-08-17_at_1.52.19_PM.png](assets/Screenshot_2020-08-17_at_1.52.19_PM.png)

---

# MC Prediction : Action Value

In the dynamic programming example we converted the state value to action value similarly here also we need to obtain the action value so we have to do a bit of modificaiton insted of selecting the state we select the state action pair

![assets/Screenshot_2020-08-17_at_2.53.15_PM.png](assets/Screenshot_2020-08-17_at_2.53.15_PM.png)

But here the problem is since we are selecting the pair from the states that the agent has visited pairs such as X and down and Y and up cannot be determined so the solution to this is we only deal with stochastic policy and not deterministic policy.

![assets/Screenshot_2020-08-17_at_2.55.40_PM.png](assets/Screenshot_2020-08-17_at_2.55.40_PM.png)

Here the agent eventually visits all the states given enough number of episodes.

---

# MC Control : Incremental means

We will be following generalized policy evaluation here, if we follow the current evaluation policy we will need at-least 5k episodes to do an update but instead if we keep track on a running average and also update in each episode we would get a much better , to make a computationally easy algorithm we need to apply some math. 

![assets/Screenshot_2020-08-17_at_3.12.58_PM.png](assets/Screenshot_2020-08-17_at_3.12.58_PM.png)

This is the basic idea now we need to implement this in MC method.

# [Solving BlackJack using Monte Carlo Method](https://github.com/abhijitramesh/RL-under-the-hood/tree/master/blackjack)

# Temporal Difference Method

# Introduction
Imagine a humanoid robot for this robot to mimic things exactly like human beings we cannot consider the task to be episodic, Consider the example of monte carol method if it has to learning anything it needs the episode to end converting this to self driving car terms every time the algorithm needs to learn something the car needs to crash this is not acceptable and is very expensive hence we need to follow a better approach this is where temporal difference methods comes to play the agent can be learning every day and all day just like how we are interacting with the streams of data over the internet. Temporal Difference methodcan be applied to solve episodic as well as continues task.

In the heart of all the state of the art models that we read and see about in the internet lies this method.

---
# TD Prediction : TD(0)

In the MC approach we take a look at a state actin pair and if it is our first visit we update the sate, but a thing to note here is that the policy does not change between episodes.


![assets/Screenshot_2020-08-19](assets/Screenshot_2020-08-19.png)

Here is we are instead keeping track of the state values we use a different equation

![assets/Formula_1](assets/Formula_1.png)

Here we can use the bellman equation to do some modification to the update statement we can plug in the equation to obtain

![assets/Formula_1](assets/formula_2.png)


What this mean is here the update statement is not only aware of the current state but it is also taking into consideration the discounted value of a upcoming state.

Why are we doing this mainly this removed any kinds of mention of the ending of the episodic task and moreover we can update the value in each time-step.

So now before taking any action the agent only depends on the current value state but when the update is done we consider the possibility of value of new state and reward.

![assets/Formula_1](assets/formula_3.png)

We refer to this as TD target

Basically what this equation does is find a middle ground between the previous estimate and the next estimate and we can set the value of alpha according to which estimate we trust  more.

![assets/Formula_1](assets/formula_4.png)

Here we can visualize this concepts, the update statement has been updated so when the value of alpha is set to one we trust the next state and when in is it to zero we trust the pervious state also we do not ever do and ideally we set the value close to zero so that the agent learns something.

The algorithm that we implement to do the same is called one-step TD or TD(0)

![assets/Formula_1](assets/formula_5.png)

---

# TD Prediction : Action Values
In order to convert the TD prediction to Action Values all we have to do in the update statement is to move form every state to ever state action pairs.

![assets/Formula_1](assets/formula_6.png)

And also instead of waiting for each state we move to each state action pair to do the update.

And if the agent interacts with the environment long enough the agent would have a pretty good understanding of how the environment works.

---

# TD Control : Sarsa(0)
To do the control what we do here is to use an epsilon greedy algorithm. We start with selecting an epsilon as 1 and then selecting the 0 or 1 in equal probability after we update the state action pair and construct a policy to update the epsilon greedy policy the algorithm is called sarsa(0).

# TD Control : Sarsamax or Q-Learning

![assets/Formula_1](assets/formula_7.png)
Basically what we are doing here is changing the epsilon greedy method with a greedy method by choosing the reward which maximizes the state and action pair value for the next state.

---
![assets/Formula_1](assets/formula_8.png)

What expected Sarsa does is that the agent selects the probability that the agent selects an action and returns the respective action value pair.

---

# [Solving Clif Walking using Temporal Method](https://github.com/abhijitramesh/RL-under-the-hood/tree/master/clifwalking)
---