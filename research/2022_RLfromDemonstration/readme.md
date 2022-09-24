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
