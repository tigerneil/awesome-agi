---
description: >-
  This paper proposesa definition of these environmental “attitudes” based on an
  characterization ofthe environment’s ability to react to the agent’s private
  strategy
---

# Modeling Friends and Foes

> **Pedro A. Ortega**
>
> **Shane Legg**
>
> DeepMind

**keywords:** AI safety; friendly and adversarial; game theory; bounded rationality.

## $$\alpha$$ 壹

Discovering whether an environment \(or a part within\) is a friend or a foe is a poorly understood yet desirable skill for safe and robust agents. Possessing this skill is important for a number of situations, including:

1. _**Multi-agent systems**_: Some environments, especially in multi-agent systems, might have incentives to either help or hinder the agent \[[1](ai-safety-gridworlds.md)\]. For example, an agent playing football must anticipate both the creative moves of its team members and its opponents. Thus, learning to discern between friends and foes might not only help the agent to avoid danger, but also open the possibility to solving taks throught collaboration that it could not solve alone otherwise. 
2. _**Model uncertainty**_: An agent can choose to impute “adversarial” or “friendly” qualities to an environment that it does not know well. For instance, an agent that is trained in a simulator could compensate for the innaccuracies by assuming that the real environment differs from the simulated one—but in an adversarial way, so as to devise countermeasures ahead of time \[[2](concrete-problems-in-ai-safety.md)\]. Similarly, innacuracies might also originate in the agent itself—for instance, due to bounded rationality \[[3](rationality-and-intelligence.md), [4](thermodynamics-as-a-theory-of-decision-making-with-informationprocessing-costs.md)\].

> Typically, these situations involve a _knowledge limitation_ that the agent addresses by responding with a _risk-sensitive_ policy.

**Contributions:**

1. we offer a _**broad definition of friendly and adversarial behavior**_. Furthermore, by varying a single real-valued parameter, one can select from a continuous range of behaviors that smoothly interpolate between fully adversarial and fully friendly.
2. we derive the agent’s \(and environment’s\) _**optimal strategy**_ under friendly or adversarial assumptions. To do so, we treat the agent-environment interaction as a one-shot game with information-constraints, and characterize the optimal strategies at equilibrium.
3. we provide an _**algorithm to find the equilibrium strategies**_ of the agent and the environment

We also demonstrate empirically that the resulting strategies display non-trivial behavior which vary qualitatively with the information-constraints.

## $$\beta$$ 贰

intuitive example using multi-armed bandits

game theory is the classical economic paradigm to analyze the interaction between agents. \[[5](a-course-in-game-theory.md)\]

## $$\gamma$$ 叄

## $$\delta$$ 肆

## $$\epsilon$$ 伍

