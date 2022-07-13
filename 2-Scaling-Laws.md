# Chapter 2: Scaling Laws

Studying how properties of networks vary with scale is important for drawing generalizable conclusions about them.

## Recommended reading

- [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361) - A study of how transformer language models scale with model size, dataset size and compute. Section 1 has a good summary of the main results.

## Optional reading

- [Scaling Laws for Autoregressive Generative Modeling](https://arxiv.org/abs/2010.14701) - A study of how transformers trained on different data distributions scale, introducing the idea of the irreducible loss.
- [Scaling Laws for Transfer](https://arxiv.org/abs/2102.01293) - A study of how pre-training on natural language improves fine-tuning on Python. In the low-fine-tuning-data regime, pre-training acts as an effective multiplier on the amount of fine-tuning data.
- [Unified Scaling Laws for Routed Language Models](https://arxiv.org/abs/2202.01169) - Scaling laws for MOEs
- [Scaling Scaling Laws with Board Games](https://arxiv.org/abs/2104.03113) - Scaling laws for AlphaZero on Hex
- [Chinchilla](https://arxiv.org/abs/2203.15556) - A correction to the original scaling laws paper: parameter count scales linearly with token budget for compute-optimal models, not ~quadratically. The difference comes from using a separately-tuned learning rate schedule for each token budget, rather than using a single training run to measure performance for every token budget. This highlights the importance of hyperparameter tuning for measuring scaling law exponents.

## Suggested exercise

Perform your own study of scaling laws for MNIST.

- Write a script to train a small CNN on MNIST, or find one you have written previously.
- Training for a single epoch only, vary the model size and dataset size. For the model size, multiply the width by powers of sqrt(2) (rounding if necessary - the idea is to vary the amount of compute used per forward pass by powers of 2). For the dataset size, multiply the fraction of the full dataset used by powers of 2 (i.e. 1, 1/2, 1/4, ...). To reduce noise, use a few random seeds and always use the full validation set.
- The learning rate will need to vary with model size. Either tune it carefully for each model size, or use the rule of thumb that for Adam, the learning rate should be proportional to the initialization scale, i.e. 1/sqrt(fan_in) for the standard Kaiming He initialization (which is what PyTorch generally uses by default).
- Plot the amount of compute used (on a log scale) against validation loss. The compute-efficient frontier should follow an approximate power law (straight line on a log scale).
- How does validation accuracy behave?
- Study how the compute-efficient model size varies with compute. This should also follow an approximate power law. Try to estimate its exponent.
- Repeat your entire experiment with 20% dropout to see how this affects the scaling exponents.
