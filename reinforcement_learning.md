---
layout: page
---
# Reinforcement Learning Notes

Notes based on [lectures](https://www.youtube.com/watch?v=qaMdN6LS9rA&list=PLAdk-EyP1ND8MqJEJnSvaoUShrAWYe51U)


## Markov Decision Process

Markov decision process is defined as:

| **S**            | A set of of states |  
| **A**            | A set of actions   |
| **P(s'\| s, a)** | Transition probabilities. Probability of transition to state <br/> s' given (s,a) i.e. action taken in state s |
| **R(s, a, s')** | Reward when a action *a* in state *s* results in transition ot state *s'* |
| **$$s_0$$** | Start state |
| **$$\gamma$$** | Discount factor. One would want to discount future rewards on action taken now. |
| **H** | Horizon or number of time steps |


**Goal**

$$max_{\pi}E[\sum_{t=0}^{H}\gamma^{t}R(s_{t}, a_{t}, s'_{t+1})]$$

where $$\pi : S \mapsto A$$ is a policy. Goal is to find  $$\pi$$ which will maximize the above expression.

Optimal Value function $$V^{*}$$ is given by

$$V^{*}(s) = max_{\pi}E[\sum_{t=0}^{H}\gamma^{t}R(s_{t}, a_{t}, s'_{t+1}) | \pi, s_{0}=s]$$


### Value Iteration Intuition

- $$V_{0}^{*}(s)$$ = optimal value for state s when H=0

$$V_{0}^{*}(s) = 0 \forall s$$

- $$V_{1}^{*}(s)$$ optimal value for state s when H=1

$$V_{1}^{*}(s) = max_{a}\sum_{s'}P(s'|s,a)(R(s,a,s') +\gamma V_{0}^{*}(s'))$$

- $$V_{2}^{*}(s)$$ optimal value for state s when H=2

$$V_{2}^{*}(s) = max_{a}\sum_{s'}P(s'|s,a)(R(s,a,s') +\gamma V_{1}^{*}(s'))$$

- $$V_{k}^{*}(s)$$ optimal value for state s when H=k

$$V_{k}^{*}(s) = max_{a}\sum_{s'}P(s'|s,a)(R(s,a,s') +\gamma V_{k-1}^{*}(s'))$$


### Q-Values

$$Q^{*}(s,a)$$ = expected utility starting in state s, taking action and thereafter acting optimally

Q-Value bellman equation:
$$Q^{*}(s,a) = \sum_{s'} P(s'|s,a)(R(s,a,s') + \gamma max_{a'}Q^{*}(s',a'))$$

Q-value Iteration:
$$Q_{k+1}(s,a) = \sum_{s'} P(s'|s,a)(R(s,a,s') + \gamma max_{a'}Q_{k}(s',a'))$$

### Policy Evaluation

The value for a given $$\pi(s)$$ is given by

$$V_{k}^{\pi}(s) = \sum_{s'}P(s'|s,a)(R(s,a,s') + \gamma V_{k-1}^{\pi}(s'))$$

For a stochastic policy 
$$\pi (a|s)$$
 the value is given by

$$V_{k=1}^{\pi}(s) = \sum_{s'}\sum_{a} \pi(a|s)P(s'|s,a)(R(s,a,s') + \gamma V_{k}^{\pi}(s'))$$


<!---
$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$
--->
