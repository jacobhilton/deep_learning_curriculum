# Chapter 7: Alignment

Alignment is the problem of getting models to use their abilities in the ways that we want them to.

## Recommended reading

- [Learning to Summarize with Human Feedback](https://openai.com/blog/learning-to-summarize-with-human-feedback/) - The first main application of reinforcement learning from human feedback (RLHF) to language models. RLHF is the main technique currently used to align models that goes beyond simple fine-tuning, and has been applied to GPT-3 in [InstructGPT](https://openai.com/blog/instruction-following/).

## Optional reading

- [Iterated amplification](https://openai.com/blog/amplifying-ai-training/) - A proposal to scale RLHF beyond tasks that are too difficult for humans to evaluate, by using decomposition. This can equivalently be viewed as using AI to assist human evaluation, which is the framing taken by the closely related proposal of [recursive reward modeling](https://deepmindsafetyresearch.medium.com/scalable-agent-alignment-via-reward-modeling-bf4ab06dfd84).
- [Book summarization](https://openai.com/blog/summarizing-books/) - An application of decomposition in combination with RLHF, as a step towards iterated amplification.
- [Critiques](https://openai.com/blog/critiques/) - A study of AI-written critiques helping humans to notice flaws in summaries, as a step towards recursive reward modeling.
- [AI Safety via Debate](https://openai.com/blog/debate/) - Another related proposal to scale RLHF beyond tasks that are too difficult for humans to evaluate. A potential obstruction to debate based on experiments involving human debaters is discussed [here](https://www.alignmentforum.org/posts/PJLABqQ962hZEqhdB/debate-update-obfuscated-arguments-problem).
- [Specification gaming](https://www.deepmind.com/blog/specification-gaming-the-flip-side-of-ai-ingenuity) - Examples of misspecified objectives that have been exploited by AI systems. The problem of specifying the right objective is also called *outer alignment*.
- [Goal Misgeneralization](https://arxiv.org/abs/2105.14111) - Examples of AI systems following the wrong objective as a result of distribution shift, even though the objective was specified correctly on the training distribution. The problem of ensuring AI systems actually follow a specified objective is also called *inner alignment*, and is discussed in much greater depth in [Risks from Learned Optimization](https://arxiv.org/abs/1906.01820).
- [AGI Safety Fundamentals](https://docs.google.com/document/d/1mTm_sT2YQx3mRXQD6J2xD2QJG1c3kHyvX8kQc_IQ0ns/edit) - An in-depth alignment curriculum expanding on this chapter.
- [Why AI alignment could be hard with modern deep learning](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/) - Some high-level commentary on why simple techniques plus generalization may not be enough on their own to align superhuman models.
- [Eliciting Latent Knowledge (ELK)](https://www.alignmentforum.org/posts/qHCDysDnvhteW7kRd/arc-s-first-technical-report-eliciting-latent-knowledge) - A central focus of current alignment theory research.

## Suggested exercise

Read the ELK report (the first ~30 pages, which frame the problem) and try to come up with a solution of your own that handles all of the counterexamples in the report.

- Hint: base your solution on one of the following ideas:
    - Train a reporter that is useful to an auxiliary AI
    - Require the reporter to be continuous
    - Penalize depending on too many parts of the predictor
    - Compress the predictor's state so it can't tell what a human would believe
- Your solution will almost certainly have a counterexample of its own. Make your solution precise enough that you can give a fairly specific counterexample.
- Once you're finished, compare your solution with the ones given in [this post](https://www.alignmentforum.org/posts/zjMKpSB2Xccn9qi5t/elk-prize-results).
