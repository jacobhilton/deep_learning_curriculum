# Chapter 3: Training at Scale

There are a number of techniques that are helpful for training large-scale models efficiently.

This chapter may be helpful if you're going to be working with large-scale models, but it's also reasonable to skip and come back to it if and when it becomes relevant.

## Recommended reading

- [How to Train Really Large Models on Many GPUs](https://lilianweng.github.io/posts/2021-09-25-train-large/) - An overview of many relevant topics, including data parallelism, pipelining and mixed-precision training.

## Optional reading

- [Megatron-LM 2](https://arxiv.org/abs/2104.04473) - A detailed analysis of different model parallelism techniques.
- [ZeRO](https://arxiv.org/abs/1910.02054) - A way to make data parallelism more memory-efficient (at the cost of additional communication), by partitioning optimizer states, gradients and parameters across data-parallel processes.
- [Mixed Precision Training](https://arxiv.org/abs/1710.03740) - Using reduced floating-point precision is important for training efficiency, but comes with a risk of errors and instabilities. This paper describes a typical mixed-precision setup, including a technique called loss scaling used to help minimize underflow.
- [MPI tutorial](http://mpitutorial.com/tutorials) (can skip the "Introduction and MPI installation" section) - MPI is an interface for passing messages that is often used to implement different kinds of parallelism.
- [Triton tutorial](https://triton-lang.org/master/getting-started/tutorials/01-vector-add.html) - Most of the numeric operations used to train models are performed on GPUs, which can perform parallel computation efficiently. Triton provides a Python-based programming environment for writing code that can be compiled to run on a GPU.

## Suggested exercise

Make a parallelized version of your MNIST script or transformer implementation:

- Install [mpi4py](https://mpi4py.readthedocs.io/en/stable/) and play around with it to check you understand how it works.
- Implement data parallelism. Some things to remember:
    - The dataset needs to be sharded
    - The random initialization needs to be broadcast
    - Gradients need to be allreduced
- Run your code on 2 GPUs in parallel and check that you get the same learning curve as with 1 GPU (with the same global batch size).
- (Optional) Implement pipeline parallelism and/or op sharding - these are harder

OR for a fun but less useful exercise:

Write an implementation of [Adam](https://arxiv.org/abs/1412.6980) using Triton, which is "fused" in the sense that the entire update is performed by a single call to low-level GPU code.

- First write the code for the update rule that can be compiled using `@triton.jit` decorator.
- Then write the PyTorch function that calls the compiled update rule.
- Benchmark your implementation and compare it to `torch.optim.Adam`.
