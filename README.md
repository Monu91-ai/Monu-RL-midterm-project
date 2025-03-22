# Playing Flappy bird with Reinforcement Learning 
Playing Flappy bird with Reinforcement Learning 

# 1. Introduction:
# The Flappy Bird Game 
Directing a flying bird moves continuously to the right, through the space between two pipes. Earn one point after passing through one set of pipes. 
Two Actions in each frame between two sets of pipes: 
Flap: bird will jump upward
Don’t Flap: bird will start falling down 
Game is over when the bird touches the lower boundary or the pipes
Goal is to score as many points as we can. It is hard for humans to play the game for a long time. 

# Reinforcement Learning
In reinforcement learning a software agent makes observations and then takes actions within an environment based on that it receives rewards. 
Agent - Software, Environment - Flappy Bird Game, Rewards - surviving (each step) - +15, Passing through pipes - +15 (same as survival), Crashing (dying) - -1000. 
Our objective is to train the agent in a way (policy) that will maximize its expected reward over time. 


# 2. Dataset Source & Description:
Dataset is not required for this project, hence we don’t need to explore the data. The agent acts in the environment and learns by trial and error. We are training the agent to know the best action in each state to maximize its expected reward.  The state representation is given as follows:
X: Horizontal distance from the bird to the next bottom pipe. 
Y: Vertical distance from the bird to the gap between the pipes.
States are discretized to keep the Q-table manageable.

# 3. Data Exploration: 
As our data is generated during the game play:
States range over different discretized X and Y positions (scaled into 7 × 21 grid cells).
Actions are binary 1 or 0 (flap or don’t flap). 
Rewards are assigned based on survival or crash events.
Rewards: 
+15 for survival at each time step.
-1000 for crashing into pipes or ground.
# 4.  Methods:
Q-Learning Algorithm 
Our objective is to maximize the expected reward and train the agent to take the best action in each state. One of the most powerful reinforcement learning algorithms is Q-learning Algorithm. 
The aim of the Q-learning is to learn a policy, which tells the agent what action to take in a state based on its Q-value. Q-value is basically the quality value of a state-action pair (s,a) which is based on the discounted future rewards the agent can expect on average. 
The agent updates Q-values using the formula:
Q(S,A)←Q(S,A)+α(R+γQ(S’,A’)–Q(S,A))
Where,
S is the current state.
A is the action taken by the agent.
S’ is the next state the agent moves to.
A’ is the best next action in state S’.
R is the reward received for taking action A in state S.
γ (Gamma) is the discount factor, which balances immediate rewards with future rewards.
α (Alpha) is the learning rate, determining how much new information affects the old Q-values
The Q-value for each action in each state would be learned through the iterative process, and in each state s, we will take the action which has the highest Q-value.
# 5. Experimentation:
The parameters considered for the implementation are as follows:
Alpha (learning rate): 0.6
Gamma (discount factor): 1
Reward for survival: +15 
Reward for crash (death): -1000
Action selection policy: Greedy (considering the maximum Q-value) 
Generations: Each generation runs until the bird crashes. After each generation the score is stored and plotted. 
Score: Number of pipes successfully passed. 
Q-Table Structure:
A 3D NumPy array Q[7][21][2] represents the state-action values.
The first dimension (7): discretized X distance to the next pipe.
The second dimension (21): discretized Y distance to the next gap.
The third dimension (2): two possible actions (flap or don’t flap). 
Q-Update Formula as per the implementation: 
Q[x_prev][y_prev][action] = (1 - alpha) * Q[x_prev][y_prev][action] + alpha * (reward + gamma * max(Q[x_new][y_new])) 
# 6. Final Result 














