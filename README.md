# Reinforcement Learning based Path Planning Algorithm for Robots in Stochastic Environment

## Overview
Path planning for robotics and needs more emphasis on algorithms in order to optimize the total distance travelled and energy spent by the system.
For unexplored Environment with multiple Destinations to cover, Deterministic Algorithms like Kruskal’s Algorithm and Dijkstra's Algorithms fail to perform efficiently.
Other Algorithms concerning Stochastic Algorithms also fail to understand the environment and plan the path accordingly.
This project aims to design and test a customized Markov Decision Process Problem for path planning and attempt to solve it using Q-Learning, one of prominent research areas of Reinforcement Learning Algorithms.

## Problem Definition:

#### Consider P, set of ‘N’ points on a 2D plane
#### P = { p1, p2, p3, … pN } 
#### Let ‘D’ be the set of values of all possible distances between any two points in the set P.
#### Task is to generate a matrix Y which gives the sequence of points needed by the bot to reach the goal in most optimized way

## Past Attempts:

### Conventional Kruskal's Algorithm:
Create a forest F (a set of trees), where each vertex in the graph is a separate tree.
Create a set S containing all the edges in the graph
While S is nonempty and F is not yet spanning
Remove an edge with minimum weight from S
If the removed edge connects two different trees then add it to the forest F, combining two trees into a single tree
At the termination of the algorithm, the forest forms a minimum spanning forest of the graph. 
If the graph is connected, the forest has a single component and forms a minimum spanning tree.

## Description of the Q Learning algorithm:

### Description of Variables:
#### The Matrix R, of dimension NxN, describes the reward for the agent, given the current state and action.
#### Alternatively, R[‘State’,’Action’] gives the reward that agent will receive when the agent performs the action ‘Action’ given the current state as ‘State’.
#### The Matrix Q of dimension NxN, describes the quality for the agent, given the current state and action.
#### Alternatively, Q[‘State’,’Action’] gives the quality of the action ‘Action’ given the current state as ‘State’.
#### There are ‘N’ possible states, which represent ‘N’ point in the considered environment.
#### ‘E’ is the number of episodes that the algorithm will train for.
#### ‘G’ or Gamma is the learning Rate 
#### The aim of the algorithm is to find the path of states from given state ‘i’ to a final state ‘N’ in optimized manner.

## Algorithm:
  ##### 1. Initialize Q Matrix to 0
  ##### 2. Initialize ‘initial_state’ with a given value
  ##### 3. Obtain the Reward function as Normalized Inverse of the Distances between two points in plane. 
#### Actions:
  ##### 1. For the given state, check Set of Visible and uncovered Points
  ##### 2. For all visible points/actions chosen at random, Compute Q value of it as follows:
    i) Add reward for the action
    ii) Add the Subsequent Cumulative sum of Q
  #### 4. Find the best action possible based on the Q values as maximum values of columns of Q matrix.
