# Chapter 8: Interpretability

Mechanistic interpretability aims to reverse-engineer the weights of neural networks into human-understandable programs.

## Recommended reading

- [Zoom In](https://distill.pub/2020/circuits/zoom-in/) - An introduction to the [Circuits](https://distill.pub/2020/circuits/) thread, a deep dive into an ImageNet classifier known as InceptionV1. This introduction provides some high-level motivation and examples.

## Optional reading

- [Feature Visualization](https://distill.pub/2017/feature-visualization/) - A method of interpreting a neuron by optimizing an input image based on the neuron's output.
- [Building Blocks](https://distill.pub/2018/building-blocks/) - Explores interfaces that combine feature visualization with attribution, which tries to identify which inputs or prior neurons are responsible for an output or a later neuron's output.
- [Multimodal Neurons](https://distill.pub/2021/multimodal-neurons/) - An exploration of [CLIP](https://openai.com/blog/clip/) neurons, which correspond to a remarkable array of concepts.
- [A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html) - A preliminary framework for transformer interpretability, which helps give an intuition for what computations transformers are actually performing. There are accompanying [exercises](https://transformer-circuits.pub/2021/exercises/index.html) and [videos](https://transformer-circuits.pub/2021/videos/index.html).
- [Induction Heads](https://transformer-circuits.pub/2022/in-context-learning-and-induction-heads/index.html) - A study of induction heads, a mechanism for copying text that appears early in language model training.
- [SoLU](https://transformer-circuits.pub/2022/solu/index.html) - An activation function that improves language model interpretability. Includes some interesting examples of language model neuron interpretations.
- [Chris Olah's views on AGI safety](https://www.alignmentforum.org/posts/X2i9dQQK3gETCyqh2/chris-olah-s-views-on-agi-safety) - Some high-level thoughts on how interpretability could help ensure the safety of advanced AI systems.

## Suggested exercise

Train a small CNN to do MNIST classification, and try your best to mechanistically understand how it is able to classify digits correctly.

- Try feature visualization, but note that it often [doesn't work](https://distill.pub/2020/understanding-rl-vision/#feature-visualization) for models trained on such a simple dataset.
- Try [attribution](https://distill.pub/2018/building-blocks/#:~:text=How%20Are%20Concepts%20Assembled), which is more likely to help.
- Use whatever other techniques you like. Consider focusing in on a small part of the network and trying to understand it as best you can.
