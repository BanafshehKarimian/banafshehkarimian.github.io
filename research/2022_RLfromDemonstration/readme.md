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
