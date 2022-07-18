# Chapter 6: Reinforcement Learning

Reinforcement learning is essentially learning by trial and error.

## Recommended reading

- [Spinning Up - Introduction to RL](https://spinningup.openai.com/en/latest/spinningup/rl_intro.html) - Explains key concepts for RL and policy gradient algorithms, which are popular because they are simple and easy to tune.

## Optional reading

- [Sutton and Barto](http://www.incompleteideas.net/book/RLbook2020.pdf) - Chapter 3 covers the standard Markov Decision Process formalism for RL and the Bellman equation for value functions, and chapter 13 covers policy gradient methods. See also [A Clearer Proof of the Policy Gradient Theorem](https://andyljones.com/posts/policy-gradient.html).
- [PPO](https://arxiv.org/abs/1707.06347) - An important RL algorithm. It is essentially vanilla policy gradient with a trained value function baseline, an entropy bonus, and a technique called "clipping" that essentially serves as a KL penalty to control the size of updates.
- [GAE](https://arxiv.org/abs/1506.02438) - The method of advantage estimation most commonly used with PPO.
- [PPO-EWMA](https://arxiv.org/abs/2110.00641) - This study helps explain why PPO clipping is helpful.
- [DQN](https://arxiv.org/abs/1312.5602) - The main class of alternatives to policy gradient methods are value-based methods, of which Q-learning is a classic example. It is an example of an *off-policy* algorithm, meaning that it can learn from trajectories produced by policies other than the current one (though it's debatable how meaningful a distinction this is). DQN was greatly improved upon by [Rainbow](https://arxiv.org/abs/1710.02298), which combined improvements from several previous pieces of work.
- [Equivalence Between Policy Gradients and Soft Q-Learning](https://arxiv.org/abs/1704.06440) - A theoretical relationship between policy and value-based methods.
- [AlphaZero](https://arxiv.org/abs/1712.01815) - Combining policy and value function optimization with Monte Carlo Tree Search to solve board games.
- [MuZero](https://arxiv.org/abs/1911.08265) - A *model-based* version of AlphaZero, in which the MCTS is performed using a learned model of the game. As a rule, model-based methods can be much more sample efficient than model-free methods, but require very accurate models to work well.

## Suggested exercise

Implement PPO and run it on [Procgen](https://github.com/openai/procgen). If you use the environments in easy mode, you'll be able to train on 1 GPU, which means you won't need to worry about data parallelism (though making a data-parallel implementation could be instructive).

- Use the hyperparameters from the [Procgen paper](https://arxiv.org/abs/1912.01588). Unless you're using the exact same architecture though, you'll need to tune the learning rate (the other hyperparameters shouldn't require much tuning).
- Remember to use both reward normalization and advantage normalization. Pseudocode for reward normalization can be found in Section 9.3 of [this paper](https://arxiv.org/pdf/1811.02553v3.pdf).
- Plot some diagnostics to help debug errors:
    - The fraction of ratios clipped by PPO. This should be between around 1% and 20%. If it is too low, then you may need to increase the iteration batch size (the number of timesteps in each alternation between rollouts and optimization). If it is too high, the learning rate could be too high.
    - The approximate KL between the policy and the "old" policy (used for clipping). We generally estimate this using the mean of 0.5 * (policy_logprob(a) - old_policy_logprob(a)) ** 2, where a is the action that was sampled. For a justification of this estimate, see [this blog post](http://joschu.net/blog/kl-approx.html). This should be fairly stable. Again, the most common cause of spikes or collapses is a poorly-tuned learning rate.
    - Policy entropy - This should fall gradually.
    - Value function explained variance (1 - Var[v_target - v_predicted] / Var[v_target]). This should quickly go above 0 and tend to something positive.
    - Mean and standard devation used for advantage normalization. The estimates should be fairly stable and the mean should be pretty close to zero.
