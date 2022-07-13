# Chapter 4: Optimization

It's helpful to have an intuition for how SGD and its variants optimize models, and a number of theoretical pictures are informative here.

## Recommended reading

- [An Empirical Model of Large-Batch Training](https://arxiv.org/abs/1812.06162) - Studies the *critical batch size*, above which training becomes less-data efficient. Section 2 explains the theoretical picture well.

## Optional reading

- [Noisy Quadratic Model](https://arxiv.org/abs/1907.04164) - The NQM is the second-order Taylor expansion of the loss discussed in the critical batch size paper, and accounts for surprisingly many deep learning phenomena. This paper uses this model to explain the effect of curvature and preconditioning on the critical batch size.
- [Adam](https://arxiv.org/abs/1412.6980) - The most popular optimization algorithm in deep learning today. It's worth understanding the update rule. Some intuition about how Adam is adjusting for signal-to-noise ratios can also be found [here](https://www.jacobh.co.uk/preconditioning_for_sgd.pdf).
- [Does batch size matter?](https://blog.janestreet.com/does-batch-size-matter/) - Some helpful intuition about how SGD behaves below the critical batch size.
- [Edge of Stability](https://arxiv.org/abs/2103.00065) - Studies the effect of optimization on the Hessian, an interesting phenomenon that the NQM cannot account for (since it assumes the Hessian is constant).
- [Neural Tangent Kernel](https://arxiv.org/abs/1806.07572) - An analysis of the infinite-width limit of neural networks. The limit actually depends on how things like the learning rate are parameterized, and alternative limits account for feature learning, as discussed [here](https://arxiv.org/abs/2003.05884).
- [Double Descent](https://openai.com/blog/deep-double-descent/) - A revision of the classical bias-variance trade-off for deep learning. Further investigation of the phenomenon can be found [here](https://arxiv.org/abs/2002.11328).
- [Lottery Ticket Hypothesis](https://arxiv.org/abs/1803.03635) - A well-known counterintuitive result about pruning.

## Suggested exercise

Run your own set of noisy quadratic model experiments.

- Set up a testbed using the setup from the NQM paper, where the covariance matrix of the gradient and the Hessian are both diagonal. You can use the same defaults for these matrices as in the paper, i.e., diagonal entries of 1, 1/2, 1/3, ... for both (in the paper they go up to 10^4, you can reduce this to 10^3 if experiments are taking too long to run). Implement both SGD with momentum and Adam.
- Create a method for optimizing learning rate schedules. You can either use dynamic programming using equation (3) as in the paper (see footnote on page 7), or a simpler empirical method such as black-box optimization (perhaps with simpler schedule).
- Check that at very small batch sizes, the optimal learning rate scales with batch size as expected: proportional to the batch size for SGD, proportional to the square root of the batch size for Adam.
- Look at the relationship between the batch size and the number of steps to reach a target loss. Study the effects of momentum and using Adam on this relationship.
