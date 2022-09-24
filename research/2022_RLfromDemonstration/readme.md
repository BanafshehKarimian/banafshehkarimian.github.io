Reinforcement Learning, although it has plenty of advantages and
applications, is time-consuming and sample inefficient in many problems.
Learning from Demonstrations, which alone is limited to only reach what
it observes, is used together with Reinforcement Learning to improve
learning in many applications including but not limited to robot
learning and self driving cars. However, in most of the literature, it
is assumed that the demonstrations provided are optimal and if not
optimal, they are sub optimal or at least are performing what our agent
wants to do, with different quality. This is time consuming and costly
to obtain in many tasks and requires human effort. In this thesis, we
are going to analyze our ideas on how we can use a heterogeneous set of
demonstrations that are not directly related to our agent's goal in the
mentioned applications.

# Introduction

Machine Learning methods are from the most used methods in fields such
as robot learning, self driving cars, medication, and etc. Using its
methods, human kind was able to explore the deep sea
[@cannata2019exploring] and other planets such as mars
[@momennasab2021machine], assign tasks that are risky or dangerous for
humans to autonomous agents [@bhondve2014mobile], save forests from fire
[@richey2019machine], clean the oceans [@adarsh2021ocean], and in
general improve humans life [@munawar2019after]. Although machine
learning methods have improved our life greatly, they are still lacking
compared to humans in performing everyday tasks in a real environment
and need further improvements.\
One of the most important method from machine learning methods is
reinforcement learning which is inspired from human and animal learning
[@collins2019reinforcement]. The goal of the reinforcement learning
agent is to maximize its expected reward, which is appropriate for many
applications including robot learning [@kober2013reinforcement], game
playing [@szita2012reinforcement], self driving cars [@Sallab_2017],
among many other. Allowing agents to learn through interacting with the
environment [@lin2019distributional], reinforcement Learning is
considerably successful in addressing decision-making problems
[@lin2019distributional]. However, it still has some disadvantages,
including being time-consuming for complex problems, unable to reach the
optimal result, sample inefficiency, and dependency to reward shaping.\
Inspired from humans and animals, learning from demonstration is used to
address the mentioned problems and reduce the search space of
reinforcement learning methods [@borsa2017observational]. Learning from
demonstration is well studied in the literature both individually and
merged with reinforcement learning, but in most of the literature the
demonstrations are assumed to be optimal or at least sub-optimal and
directly relevant to what our agent wants to achieve. Gathering this
sort of demonstrations is costly and time-consuming and in some cases
not even possible. Thus, in this thesis we want to check how we can use
diverse demonstrations to improve the performance of reinforcement
learning.
# Related work

Demonstrations are used for more than three decades for learning
problems, especially in fields such as robotics. At first, remotely
controlling robots was used to gather demonstrations
[@lozano1983robot; @dufay1984approach; @levas1984user; @segre1985explanation].
This remote controlling was hard and needed expertise in robot remote
controlling, thus other methods were proposed such as moving robot body
manually or using computer vision
[@kuniyoshi1991teaching; @kuniyoshi1994learning; @kang1995robot].\
At first demonstrations were used alone to only produce the exact
behaviour of the demonstrators, but this in fact had many disadvantages.
One of the disadvantages come from the fact that demonstrations could
not cover the whole state space. In addition to that the quality of
demonstrations influenced the performance of agent greatly. The idea to
solve these problems was to use other methods such as Reinforcement
Learning alongside learning from demonstrations [@argall2009survey].\
[@smart2002effective] used a two phased method to merge reinforcement
learning with learning from demonstrations. At the first phase a teacher
selects the appropriate actions and the reinforcement learning module
trained on the selected actions. The second phase selects the actions
according to reinforcement learning module and continues to learn. In
addition, [@taylor2011integrating] records the policies using remotely
controlling the agent or applying a sub-optimal policy and extracts some
rules from the demonstrations. Then the agent decides online whether to
use these rules or use its internal reinforcement learning.\
Reinforcement learning could also use learning from demonstrations to
improve its performance. One of the most important disadvantages of
reinforcement learning methods are being sample inefficient and
time-consuming. Similar to [@taylor2011integrating], in
[@rajeswaran2017learning] reinforcement learning is used together with
learning from demonstrations, but with the goal of decreasing the
learning time of reinforcement learning. The error of imitation learning
is added to the error of reinforcement learning in [@nair2018overcoming]
and when the reinforcement reached the performance of demonstrations
this error will no longer be used.\
[@salimans2018learning] also used states of demonstrations as the
starting states and [@brys2015reinforcement] biases its decision to
demonstrations using shaping reward function. In
[@abbeel2005exploration] appropriate representations are learned from
demonstrations and reinforcement learning is used to continue learning
with the learned demonstrations. Other methods such as pre-processing
using demonstrations [@cruz2017pre] and filling memory with
demonstrations [@hester2018deep; @vecerik2017leveraging] are used to
improve the learning pace of reinforcement learning algorithms.\
Another disadvantage of reinforcement learning is being unable to find
optimal policy when the state space is large. In [@cobo2011automatic]
the states that look irrelevant to the agents goal are extracted from
demonstrations to decrease the search space. In addition, spars reward
environment are difficult for reinforcement learning agents to solve,
which is addressed in [@kang2018policy] using encouraging the agent to
explore states similar to observations. [@torrey2020reinforcement] also
adds causality to reinforcement learning from demonstrations to solve
spars reward problems.\
Another method to solve disadvantages of reinforcement learning is
through using hierarchical reinforcement learning, which has its own
disadvantages such as needing for the sub goals and options to be
defined manually. [@cobo2012automatic] used demonstrations to find sub
goals and [@zang2009discovering; @konidaris2012robot; @fox2017multi] use
them to find options.\
In recent methods, there are few ones who address improving
reinforcement learning from non optimal demonstration.
[@pshikhachev2022self] uses a method named self imitation learning
[@oh2018self], which imitates from its past experiences, to imitate
demonstrations and shows that it can work well for sub optimal
demonstrations. [@zhu2022self] also uses demonstrations but improves it
using reinforcement learning to address issues of sub optimal
demonstrations. [@correia2022contrastive] assumes demonstrations to have
different point of view and tries to use them to improve its learning.\
The work that might work for heterogeneous demonstrations are
[@chen2022anomaly], [@wang2022efficient] and [@gupta2019relay].
[@chen2022anomaly] assumes that all demonstrations are from the same
task but with different quality. The method proposed is to influence
demonstrations by their correspondence weights per each state action
pair. [@wang2022efficient] creates an ensemble of demonstrations and
adds pairs that have high weight to the ensemble. Finally,
[@gupta2019relay] breaks demonstrations as sub demonstrations and uses
them as new demonstrations. Although it is not mentioned or evaluated in
the relative paper, the mentioned methods might work for heterogeneous
demonstrations and we need to compare our method with them.
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
follows:
![image](https://user-images.githubusercontent.com/19387425/192095127-d937e935-ad54-4c4e-93b7-75c6c5ba93e5.png)
A policy ![image](https://user-images.githubusercontent.com/19387425/192095225-9ddffecb-c2f0-47a7-a79e-e0786c0919b5.png) is map from a state to
action probabilities and a trajectory
$\tau = <s_0,s_1,a_1,...,s_T,a_T>$, where $T$ denotes terminal state,
can be generated from $\pi$. Reinforcement learning algorithms try to
find an optimal policy $\pi^*$ that maximizes the discounted return,
i.e.: ![image](https://user-images.githubusercontent.com/19387425/192095141-34de867a-af94-4f85-9883-db8733048811.png) Our
agent has initially access to pairs of heterogeneous demonstrations
($Demo = \{demo_i;i \in (0,D)\}$) collected from multiple agents
performing multiple tasks. These demonstrations can be considered as the
input of our problem or they can be derived from a policy or a data set
of videos, $V = \{v_1, ..., v_k\}$, where $v_i$ is video of an agent
performing a task. We first assume that these demonstrations are from
another MDP with isomorphic transition function $P$, state space and
action space, but different reward function. We can further analyse the
case that state space and action space is also different.
# preliminaries

## Generative Adversarial Networks or GANs

GANs use a generator to generate $G$ fake images and a discriminator $D$
that tries to identify fake images from real ones. In other words, the
loss function of GANs are as follows: <br /> ![image](https://user-images.githubusercontent.com/19387425/192095243-60ed21bb-a0c8-4ea6-8b40-5262d98c1edb.png) <br /> where
$G(x)$ is the output of the generator and $D(x)$ is the discriminator's
output given the real image and $D(G(x))$ is that of the discriminator's
given fake image.

## Adversarial Inverse Reinforcement Learning or AIRL

AIRL uses an idea similar to GANs [@goodfellow2014generative]. Similar
to GANs, in IRL the real data is the demonstrations and the fake data is
the trajectory generated by the policy (or the generator) that maximizes
the to be learned reward. The objective of AIRL discriminator is as
follows:<br />
![image](https://user-images.githubusercontent.com/19387425/192095285-62fee24a-5f6a-477a-bb0e-28e0336743e6.png)
<br />
where $\tau \sim p*$ means a trajectory from the demonstrations and
$\tau \sim \pi_{\theta}$ means a trajectory from the policy that
maximizes the learned reward at the current step. The policy
$\pi_{\theta}$ is updated using the advantage function multiplied by the
gradient of the log of the policy: <br />
![image](https://user-images.githubusercontent.com/19387425/192095325-1ecdecf2-9dff-44e5-8739-7022ca142de1.png) <br />
 We can use
$r(s,a,sp) = A(s,a)$ and set the reward as follows:<br />
![image](https://user-images.githubusercontent.com/19387425/192095349-7d827757-45fd-4507-a3be-163c20cc0f30.png)<br />
 Where $h(s)$ is a
shaping term to avoid undesired shaping of $g(s)$ that is a function
approximator of the reward function.

## Soft Actor Critic

Soft Actor Critic or SAC is an off policy policy gradient method that
uses value function approximation to better train the policy
[@haarnoja2018soft].
