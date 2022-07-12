# Chapter 5: Modeling Objectives

Language models are generally trained using a log-likelihood/cross-entropy objective, but there are several other useful objectives for representation learning and generative modeling.

This chapter is included for breadth, but it can be skipped if you want to focus on language models. It is not that detailed because I am not that familiar with these topics.

## Recommended reading

- [Contrastive Representation Learning](https://lilianweng.github.io/posts/2021-05-31-contrastive/) - Contrastive objectives are an important class of training objectives that are used for representation learning.

## Optional reading

- [CLIP](https://openai.com/blog/clip/) - A contrastive image-text model.
- [Diffusion models](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/) - A training objective that works well for image generation, used by [DALL-E 2](https://openai.com/dall-e-2/).
- [VAE tutorial](https://arxiv.org/abs/1606.05908) - VAEs are a type of latent variable model with an encoder-decoder structure.
- [VAE variants](https://lilianweng.github.io/posts/2018-08-12-vae/) - An overview of the some VAE variants, including VQ-VAE.
- [GAN tutorial](https://arxiv.org/abs/1701.00160) - Generative adversarial networks are an older objective that can also be used for image generation. This tutorial also has an accompanying [video](https://www.youtube.com/watch?v=AJVyzd0rqdc).

## Suggested exercise

Train a contrastive CNN on MNIST. Measure the classification accuracy of your model by using a few held-out examples from each class to compare each test example to.
