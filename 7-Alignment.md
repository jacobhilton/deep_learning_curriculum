# Chapter 7: Alignment

Alignment is the problem of getting models to use their abilities in the ways that we want them to.

## Recommended reading

- [Deep Reinforcement Learning from Human Preferences](https://arxiv.org/abs/1706.03741) - The paper that introduced reinforcement learning from human feedback (RLHF), the main technique currently being used to align models that goes beyond simple fine-tuning.

## Optional reading

- [Learning to Summarize with Human Feedback](https://openai.com/blog/learning-to-summarize-with-human-feedback/) - The first main application of RLHF to language models. RLHF has been applied to GPT-3 in [InstructGPT](https://openai.com/blog/instruction-following/).
- [Iterated amplification](https://openai.com/blog/amplifying-ai-training/) - A proposal to scale RLHF beyond tasks that are too difficult for humans to evaluate. The version discussed in the paper, which uses supervised fine-tuning for the distillation step, is usually called *imitative amplification* or *HCH* (short for "Humans Consulting HCH"), and is equivalent to iteratively decomposing the task and using supervised fine-tuning on the subtasks.
- [Recursive reward modeling](https://deepmindsafetyresearch.medium.com/scalable-agent-alignment-via-reward-modeling-bf4ab06dfd84) - Recursively using AI to assist human evaluation in RLHF. This can be thought of as the version of iterated amplification in which reinforcement learning is used for the distillation step.
- [Book summarization](https://openai.com/blog/summarizing-books/) - An application of decomposition in combination with RLHF, which can also be thought of as simple instance of iterated amplification/recursive reward modeling.
- [AI Safety via Debate](https://openai.com/blog/debate/) - Another related proposal to scale RLHF beyond tasks that are too difficult for humans to evaluate. A potential obstruction to debate based on experiments involving human debaters is discussed [here](https://www.alignmentforum.org/posts/PJLABqQ962hZEqhdB/debate-update-obfuscated-arguments-problem).
- [Critiques](https://openai.com/blog/critiques/) - A study of AI-written critiques helping humans to notice flaws in summaries, which can be thought of as a one-step version of iterated amplification/recursive reward modeling/debate.
- [Specification gaming](https://www.deepmind.com/blog/specification-gaming-the-flip-side-of-ai-ingenuity) - Examples of misspecified objectives that have been exploited by AI systems. The problem of specifying the right objective is also called *outer alignment*.
- [Goal Misgeneralization](https://arxiv.org/abs/2105.14111) - Examples of AI systems following the wrong objective as a result of distribution shift, even though the objective was specified correctly on the training distribution. The problem of ensuring AI systems actually follow a specified objective is also called *inner alignment*, and is discussed in much greater depth in [Risks from Learned Optimization](https://arxiv.org/abs/1906.01820).
- [AGI Safety Fundamentals](https://docs.google.com/document/d/1mTm_sT2YQx3mRXQD6J2xD2QJG1c3kHyvX8kQc_IQ0ns/edit) - An in-depth alignment curriculum expanding on this chapter.
- [Without specific countermeasures, the easiest path to transformative AI likely leads to AI takeover](https://www.alignmentforum.org/posts/pRkFkzwKZ2zfa3R6H/without-specific-countermeasures-the-easiest-path-to) - An explanation of why catastrophe is in some sense the default outcome if we fail to align superhuman AI systems. A more accessible post expressing similar ideas can be found [here](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/).
- [Eliciting Latent Knowledge (ELK)](https://www.alignmentforum.org/posts/qHCDysDnvhteW7kRd/arc-s-first-technical-report-eliciting-latent-knowledge) - A central focus of current alignment theory research.

## Suggested exercise

This chapter has two suggested exercises, a practical exercise and a theoretical exercise. They are both pretty challenging, but the practical exercise will be easier if you have already completed chapters 1 and 6.

Practical exercise: fine-tune your Shakespeare transformer from [Chapter 1](1-Transformers.md) using RLHF to get it to output samples with positive sentiment. (If you didn't do that exercise, you might be able to find some code to help you from the [solutions page](Solutions.md)).

- Collect some unconditional samples from your model, and label them as positive, negative or neutral in sentiment yourself. You will probably need at least few hundred labels, so keep the samples fairly short so that this isn't too laborious. (Consider pooling your labels if working with others, or mixing in some snippets from the original corpus whose sentiment is less ambiguous.)
- Fine-tune your model to obtain a reward model that predicts the sentiment of a sample. You can treat this as a sequence-modeling problem by having a model predict special tokens such as "happy" and "sad" based on the sentiment, treating neutral labels as soft 50% labels. Remember to mask all but the last token of the sample.
- Fine-tune your original model using PPO, with rewards given by the log probability of positive sentiment predicted by the reward model.
    - To make things simpler, don't bother with a value function or GAE. Just use the reward itself as the advantage estimate at every token.
    - Recenter and normalize the rewards. Just use fixed constants taken from a few thousand samples instead of implementing running estimates.
    - As in chapter 6, track the fraction of ratios clipped. If it is below 1%, then increase the iteration batch size, i.e., the number of samples in each alternation between rollouts and optimization. The iteration batch size might need to be a few thousand completions or more.
    - Measure KL(current model || original model). If the fraction of ratios clipped is high enough, you shouldn't need to penalize this directly to prevent it growing too fast. Square root KL should grow roughly linearly over the course of training. Stop training once you reach 10 nats per completion, but keep hold of plenty of intermediate checkpoints at lower KLs.
- Look at some samples from your different checkpoints, and try to get a sense of which one is the best, and where overoptimization started to occur.
- Evaluate your preferred model by blindly rating 20 samples from your original model and 20 from your final model, to see whether it really is better. Maybe even ask a friend to do the ratings in case you think you can recognize the model. You can also try comparing it to a model that was trained to optimize negative sentiment (note: don't flip the sign of the reward function when training AGI).
- Extension/alternative: do the same thing but with conditional rather than unconditional samples (using prompts from the original Shakespeare dataset), and training a comparison reward model instead of an absolute reward model.

AND/OR

Theoretical exercise: read the first 49 pages of the ELK report (up until "Why we're excited about tackling worst-case ELK"). Try to come up with a proposal of your own that handles all of the counterexamples in the report.

- For guidance on what counts as a valid proposal, see [this post](https://www.alignmentforum.org/posts/QEYWkRoCn4fZxXQAY/prizes-for-elk-proposals). You should try to come up with a proposal that would have been a valid competition entry.
- Hint: base your proposal on one of the following ideas:
    - Train a reporter that is useful to an auxiliary AI
    - Require the reporter to be continuous
    - Penalize depending on too many parts of the predictor
    - Compress the predictor's state so it can't tell what a human would believe
- Your proposal will almost certainly have a counterexample of its own. Make your proposal precise enough that you can give a fairly specific counterexample.
- Once you're finished, compare your proposal with the ones given in [this post](https://www.alignmentforum.org/posts/zjMKpSB2Xccn9qi5t/elk-prize-results).
