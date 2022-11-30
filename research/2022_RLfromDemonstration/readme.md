Reinforcement Learning, although has plenty of advantages and applications, is time-consuming and sample inefficient in many problems. Learning from Demonstrations, which alone is limited to only reach what it observes, is used together with Reinforcement Learning to improve learning in many applications, including but not limited to robot learning and self driving cars. However, in most of the literature, it is assumed that the provided demonstrations are optimal and if not optimal, are sub optimal, or at least, are performing what our agent wants to do, with different qualities. This is time consuming and costly to obtain in many tasks and requires human effort. In this work, we are going to use a heterogeneous set of demonstrations that are not directly related to our agent's goal, as behavioural policies, in the mentioned applications. In order to do so, we add a new term to the policy loss off Soft Actor Critique method, using Free Energy framework.
We assume that each demonstrator's policy is a point in the policy space that can guide us to improve our learning, similar to the following figure, and we will choose a behaviour policy to bias our decisions towards it. We use the idea of Free Energy frame work \cite{Ortega2015InformationTheoreticBR}, and evaluate different methods of finding a behavioural policy that decreases the cost of policy search. We show that assuming the demonstrator with maximum evaluated return, evaluated using off policy evaluation methods, and update the behavioural policy, reduces the search cost considerably. 

# Problem Formulation

In this section, we are going to mathematically formulate the problem
that we intend to address in our further studies. We consider a Markov
decision process (MDP), defined by ![image](https://user-images.githubusercontent.com/19387425/192095160-e4db8e0a-1281-4cbd-97cf-08ac1834cfb4.png), in which
![image](https://user-images.githubusercontent.com/19387425/192095169-6c20df51-55aa-40f5-944c-2cb50866ff79.png)
 is the reward function,
![image](https://user-images.githubusercontent.com/19387425/192095188-9132ef94-14d7-43d5-963a-6cf5734a6214.png)
 is the transition function,
![image](https://user-images.githubusercontent.com/19387425/192095210-efe424a5-476f-463d-aff2-bf94f700c148.png) is the discount factor, $\mu$ is initial state
distribution, and $S$ and $A$ denote the state space and action space
respectively that are defined for discrete and continues cases as
follows:<br />
![image](https://user-images.githubusercontent.com/19387425/192095127-d937e935-ad54-4c4e-93b7-75c6c5ba93e5.png)<br />
A policy ![image](https://user-images.githubusercontent.com/19387425/192095225-9ddffecb-c2f0-47a7-a79e-e0786c0919b5.png) is map from a state to
action probabilities and a trajectory
tau = <s_0,s_1,a_1,...,s_T,a_T>, where T denotes terminal state,
can be generated from pi. Reinforcement learning algorithms try to
find an optimal policy pi* that maximizes the discounted return,
i.e.:<br /> ![image](https://user-images.githubusercontent.com/19387425/192095141-34de867a-af94-4f85-9883-db8733048811.png) <br /> Our
agent has initially access to pairs of heterogeneous demonstrations
Demo = {demo_i; i in (0,D)} collected from multiple agents
performing multiple tasks. These demonstrations can be considered as the
input of our problem or they can be derived from a policy or a data set
of videos, V = {v_1, ..., v_k}, where $v_i$ is video of an agent
performing a task. We first assume that these demonstrations are from
another MDP with isomorphic transition function $P$, state space and
action space, but different reward function. We can further analyse the
case that state space and action space is also different.
Our main idea is to minimize the information cost through minimizing the distance of our policy to a behaviour policy, in addition to maximizing the expected utility, similar to Free Energy methods. We do this by adding a new term to the policy loss of Soft Actor Critique, which is an off-policy method and tries to maximize the expected utility.

# preliminaries


## Soft Actor Critic

Soft Actor Critic or SAC is an off policy policy gradient method that
uses value function approximation to better train the policy
[@haarnoja2018soft]. SAC
maximizes long-term rewards in addition to action randomness which the objective function can be formulated as:
![image](https://user-images.githubusercontent.com/19387425/192099718-3ab6b7d4-0162-4c1a-9171-c0ed51eebb9c.png)<br/>
The method has a policy network, that returns mean and variance which the actions are sampled from. The update of the policy network is based on Q value estimations, which is itself another network. The Q value update is also related to value function which is again estimated using another network. The objective function of policy network, Q network and value network are as follows:
![image](https://user-images.githubusercontent.com/19387425/192099763-682ff14f-2715-48a9-a67a-b40a8674d9fa.png)<br/>
## Free Energy
Free energy is used as the objective function for bounded-rational decision-makings and is used to model information constrained decision-making. The goal in it is to minimize the information cost while maximizing the expected utility as follows:
![image](https://user-images.githubusercontent.com/19387425/204818487-186e0429-2953-4d65-a358-9c3e099b4d15.png)
Where U (s, a) is the utility function, πβ (a|s) is our policy that we are learning, α is the inverse
temperature that controls the trade-off between information cost and maximizing utility, and πβ is the
behaviour policy, or prior knowledge.
## Proposed Method
The idea is to use the demonstrators policy  using Free Energy Minimization method \[Ortega2015InformationTheoreticBR\]. We could assume that the policies we obtained from observations are points on the policy space that can guide us to the optimal policy. 
As we mentioned before, the free energy of a policy is defined as:
![image](https://user-images.githubusercontent.com/19387425/204844767-e0d4db0c-993f-41fb-b5c0-97792cf8174a.png)
In reinforcement learning π(a, s) can be a representative of our policy and πβ (a|s) can be assumed as a behavioural policy. If we had one demonstrator we could have assumed its policy as πβ (a|s), but here we have multiple demonstrators.
We could maximize our expected reward similar to SAC using minimizing DKL(πφ|| exp(Qθ (st,.))
Zθ ) and define our information cost as the weighted some of our policy to the policies of the demonstrators or ∑ λi ∗ DKL(πφ||πi). Thus, we change the policy objective function of SAC as follows:
![image](https://user-images.githubusercontent.com/19387425/204845144-f2eb0774-6fe3-4b1f-9914-3bd49c289e68.png)
However, The problem with above formula is that if the other policies are spread across the policy
space, one of the KL distance terms could become infinity and decreasing the weights will not prevent
the objective function to become infinity. Thus, we need to define or select a behavioural policy
using demonstrated policies. We will show in the result that the best method is to use off-policy
evaluation and set the policy with maximum evaluated utility as our behavioural policy. In simple
words, it means that to choose the policy that is the closest to the optimal policy as our behaviour
policy that we want to get close to. Thus, we will write the policy loss as follows:
![image](https://user-images.githubusercontent.com/19387425/204845272-f94ed75d-56b6-4326-8b48-2a756335b768.png)
Where πβ is the policy of the demonstrator with maximum evaluated utility, using off-policy method.
As it is shown in Algorithm1, after rolling out and saving the experience in the common experience
buffer, we use the experience to update the demonstrated policies using off policy SAC, and use off
policy evaluation to evaluate them. Then we set the demonstrated policy with maximum evaluated
utility as the behaviour policy and use the above formula to update our policy.
![image](https://user-images.githubusercontent.com/19387425/204845465-74a34cde-4c0c-4812-b7bd-3203a4b7a8d4.png)
## Result
In order to test our method, we need to design our own environments, and we use PyBullet to design
the environments. We will discuss these environments in details.
* E1: reach_goal_min_energy The agent is a Franka Panda arm, which aims to reach the goal with
minimum usage of energy.
* E2: reach_goal_avoid_obstacle The same robotic arm, which aims to reach the goal, while
avoiding an obstacle.
* E3: push_box_to_goal Again, the same agent aims to push a box to the destination.
* E4: pick_and_place_box The Franka Panda arm agent, with the purpose of picking a box and
placing it in the destination.</br>
We train three demonstrator policies (E1, E2, E3), and use them in the training of the E4 environment.
We let the agent to train for 300 trials and repeat it 10 times. The result of comparing simple
SAC method with our method is visible at Figure 2. We can see that our method improved SAC
considerably. Also, it is obvious that the SAC was unable to learn the task, considering its inability to
achieve the goal, in contrast to our method that was able to successfully learn the pick and place task
in limited trials.
![image](https://user-images.githubusercontent.com/19387425/204846245-4e418c5c-83a8-43fd-bbe5-3422fdf3a93a.png)
