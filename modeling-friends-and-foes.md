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

However, within game theory, the term adversary is justified by the fact that in zero-sum games the equilibrium strategies are maximin strategies, that is, strategies that maximize the expected payoff under the assumption that the adversary will minimize the payoffs. 

**Problems:**

when the game is not a zero-sum game, interpreting an agent’s behavior as adversarial is far less obvious, since:

1.  there are is no coupling between payoffs 
2. the strong guarantees provided by the minimax theorem are unavailable \[[6](theory-of-games-and-economic-behavior.md)\].

![Figure 1: Average rewards for 4 different 2-armed bandits under 2 different strategies: ](.gitbook/assets/image%20%281%29.png)

**explanations:**

\(I\) a uniform strategy \(arms were chosen using 1000 fair coin flips\) and \(II\) a deterministic strategy \(500 times arm 1, then 500 times arm 2\). Bandits get to choose in each turn \(using a probabilistic rule\) which one of the two arms will deliver the reward. The precise probabilistic rule used here will be explained later in Section 5 \(Experiments\).  


Two different strategies are: 

1. The agent plays all 1000 rounds using a uniformly random strategy
2. The agent deterministically pulls each arm exactly 500 times using some fixed rule.

Observations:

1. _**Sensitivity to strategy.**_  The two sets of average rewards for bandit A are statistically indistinguishable, that is, they stay the same regardless of the agent’s strategy. This corresponds to the stochastic bandit type in the literature \[[7](untitled-1.md), [8](regret-analysis-of-stochastic-and-nonstochastic-multi-armed-bandit-problems.md)\]. In contrast, bandits B–D yielded different average rewards for the two strategies. Although each arm was pulled approximately 500 times, it appears as if the reward distributions were a function of the strategy.
2. _**Adversarial/friendly exploitation of strategy.**_ The average rewards do not always add up to one, as one would expect if the rewards were truly independent of the strategy.
3. _**Strength of exploitation**_ : Notice how the rewards of both adversarial bandits \(C & D\) when using strategy II differ in how strongly they deviate from the baseline set by strategy I. This difference suggests that bandit D is better at reacting to the agent’s strategy than bandit C— and therefore also more adversarial. A bandit that can freely choose any placement of rewards is known as a non-stochastic bandit \[[9](the-nonstochastic-multiarmed-bandit-problem.md), [8](regret-analysis-of-stochastic-and-nonstochastic-multi-armed-bandit-problems.md)\].
4. _**Cooperating/hedging :**_ the nature of the bandit qualitatively affects the agent's optimal strategy. A friendly \(B\) invites the agent to cooperate through the use of predictable policy whereas adversarial bandits \(C&D\) pressure the agent to hedge through randomization.

![Figure 2: Reacting to the agent&#x2019;s strategy in RPS](.gitbook/assets/image%20%282%29.png)

The diagram depicts the simplex of the environment’s mixed strategies over the three pure strategies Rock, Paper, and Scissors, located at the corners. 

* a. When the agent picks a strategy it fixes its expected payoff \(shown in color, where darker is worse and lighter is better\). 
* b. An indifferent environment corresponds to a player using a fixed strategy \(mixed or pure\). 
* c. However, a reactive environment can deviate from the indifferent strategy \(the set of choices is shown as a ball\). A friendly environment would choose in a way that benefits the player \(i.e. try playing Paper as much as possible if the player mostly plays Scissors\); analogously, an adversarial environment would attempt to play the worst strategy for the agent.

_**5. Agent/environment symmetry**_. Let us turn the tables on the agent: how should we play if we were the bandit? A moment of reflection reveals that the analysis is symmetrical. An agent that does not attempt to maximize the payoff, or cannot do so due to limited reasoning power, will pick its strategy in a way that is indifferent to our placement of the reward. In contrast, a more effective agent will react to our choice, seemingly anticipating it. Furthermore, the agent will appear friendly if our goal is to maximize the payoff and adversarial if our goal is to minimize it.

This symmetry implies that the choices of the agent and the environment are coupled to each other, suggesting a solution principle for determining a strategy profile akin to a Nash equilibrium \[[5](a-course-in-game-theory.md)\]. The next section will provide a concrete formalization. 

## $$\gamma$$ 叄

## $$\delta$$ 肆

## $$\epsilon$$ 伍

