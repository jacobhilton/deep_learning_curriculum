# Deep Learning Curriculum

This is an advanced curriculum for getting up to speed with some of the latest developments in deep learning, as of July 2022. It is heavily biased towards my own research interests, especially large language model alignment, but it should be of general interest. It is targeted at people with a strong quantitative background who are familiar with the basics of deep learning, but may otherwise be new to the field.

**WARNING**: this curriculum may be extremely challenging to take on alone. It is highly recommended to find a more experienced mentor, or at the very least a study partner. There are suggestions for more accessible alternatives, which have the same prerequisites, below.

I do not intend to try to keep this curriculum up-to-date, but PRs are welcome, although I reserve the right to be picky about what gets included to avoid it becoming too bloated.

Credit to John Schulman for an older curriculum which inspired this and from which I cribbed bits and pieces.

## Pre-prerequesites

Before studying deep learning, I recommend being comfortable with the very basics of the following topics:

- **Linear algebra**: It's essential to understand how vectors and matrices work, and helpful to understand eigenvalues and eigenvectors.
- **Probability**: It's essential to understand the rules of probability, expected value and standard deviation, and helpful to understand independence and the normal distribution.
- **Calculus**: It's essential to understand differentiation and partial differentiation, and helpful to understand the basics of vector calculus including the chain rule and Taylor series.
- **Programming**: I recommend getting to know Python and numpy.
- Optional extras:
    - **Statistics**: It's helpful to understand estimators and standard errors.
    - **Information theory**: It's helpful to understand information, entropy and KL divergence.

You do not by any means need to understand the whole of these subjects in great depth in order to approach deep learning, but being very familiar with the basic ideas will make your life easier. The benefit of studying these subjects in depth is that you will gain this familiarity by thinking a lot about the relevant ideas.

There are many resources for studying these topics. Here are some suggestions:

- 3Blue1Brown's video series on [linear algebra](https://www.3blue1brown.com/topics/linear-algebra) and [calculus](https://www.3blue1brown.com/topics/calculus) - Accessible and focused on the essentials.
- [Mathematics for Machine Learning Coursera course](https://www.coursera.org/specializations/mathematics-machine-learning) - A math course with a machine learning focus.
- [Python for Data Science and Machine Learning Bootcamp](https://www.udemy.com/course/python-for-data-science-and-machine-learning-bootcamp/) - A Python course with a machine learning focus.
- [Linear Algebra Done Right](https://link.springer.com/book/10.1007/978-3-319-11080-6) - A first-principles approach to linear algebra that covers much more than you need to know.
- [Cover and Thomas](http://staff.ustc.edu.cn/~cgong821/Wiley.Interscience.Elements.of.Information.Theory.Jul.2006.eBook-DDU.pdf) - A classic textbook on information theory, also covering much more than you need to know.
- [Cracking the Coding interview](https://github.com/Avinash987/Coding/blob/master/Cracking-the-Coding-Interview-6th-Edition-189-Programming-Questions-and-Solutions.pdf) - Covers the computer science essentials that you might actually use when programming in the real world, and has a lot of exercises. Also useful for interview preparation.
- [LeetCode](https://leetcode.com/) - Programming challenges designed for interview preparation. A good way to get general programming practice.
- [Project Euler](https://projecteuler.net/) - A series of increasingly challenging mathematical programming puzzles. A fun way to get programming practice for the mathematically inclined.
- [Learning the Shell](https://linuxcommand.org/lc3_learning_the_shell.php) - A tutorial for the Unix command line.

I recommend putting a significant fraction of your study time into exercises – problems for math, and implementation for programming – since it forces you to think through the ideas for yourself.

## Prerequesites

Before embarking on this curriculum (or one of the alternatives suggested below), it is necessary to understand the basics of deep learning, including basic machine learning terminology, what neural networks are, and how to train them. Here are some suggested resources for this:

- [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/) - An online textbook introducing deep learning, with a theoretical focus. Has some nice theoretical exercises.
- [3Blue1Brown on Neural Networks](https://www.3blue1brown.com/topics/neural-networks) - A video series explaining neural networks in an intuitive way.
- [Machine Learning Coursera course](https://www.coursera.org/learn/machine-learning) - An online lecture series covering both theoretical and practical topics. Has some practical exercises, but they may be a bit too "fill in the blanks".
- [Practical Deep Learning for Coders from fast.ai](https://course.fast.ai/) - An online textbook with a practical focus. Has practical exercises.

In addition to this, I recommend learning [PyTorch](https://pytorch.org/tutorials/beginner/deep_learning_60min_blitz.html), and, as an exercise, using it to train a small neural network to do [MNIST](http://yann.lecun.com/exdb/mnist/) classification. You should be able to achieve around 99% test accuracy using a 3-layer [convolutional neural network](https://cs231n.github.io/convolutional-networks/). You can also use your setup to run a few experiments on some simple methods of [regularization](https://cs231n.github.io/neural-networks-2/).

## How to use this curriculum

The curriculum is divided into 8 chapters:

- [Chapter 1: Transformers](1-Transformers.md)
- [Chapter 2: Scaling Laws](2-Scaling-Laws.md)
- [Chapter 3: Training at Scale](3-Training-at-Scale.md)
- [Chapter 4: Optimization](4-Optimization.md)
- [Chapter 5: Modeling Objectives](5-Modeling-Objectives.md)
- [Chapter 6: Reinforcement Learning](6-Reinforcement-Learning.md)
- [Chapter 7: Alignment](7-Alignment.md)
- [Chapter 8: Interpretability](8-Interpretability.md)
- [Chapter 9: Adversarial Training](9-Adversarial-Training.md)

Chapter 1 is helpful for understanding chapters 2, 3, 8 and 9, but otherwise the chapters can be completed in any order. Chapter 6 may also be somewhat helpful for understanding chapter 7. Chapters 1 and 6 are probably the most important overall.

Each chapter has three sections:

- **Recommended reading**: A small amount of material covering the most basic or important ideas of the chapter. Often a particular section of a paper will be singled out, and it's not necessary to read the rest of the paper.
- **Optional reading**: Related material that's still very relevant to the chapter, but can be either skimmed or skipped entirely and used as a reference later on.
- **Suggested exercise**: An idea for an exercise, generally implementation-focused, to help drive some of the ideas of the chapter home. **Most of the exercises have not been test-run**, so take them with a pinch of salt. It is generally more important to do some sort of exercise than to follow the exact exercise suggested.

Each chapter should take between half a week and 2 weeks of full-time study, depending on the chapter and how much depth you go into, but don't be discouraged if it takes longer than this.

## Alternatives to this curriculum

This curriculum may be very challenging, especially without mentorship. A more realistic alternative for most people is to work on larger programming projects involving deep learning, and/or to work through more advanced textbooks or online courses. These can be engaging, provide structure, and last a long time. The downside is that they may be less focused on the most relevant material. But it's always possible to return to this curriculum at a later date.

An example of a larger programming project I worked on was training a neural network to play [backgammon](https://github.com/jacobhilton/backgammon) using TD-learning, but you should choose something you're motivated by. It's also a good idea to create a short write-up of the project and any experiments involved.

Some textbook suggestions:

- [Goodfellow et al](https://www.deeplearningbook.org/) - Probably still the best deep learning-specific textbook, although it can be unclear in places. Has no exercises.
- [Jared Kaplan's notes for physicists](https://sites.krieger.jhu.edu/jared-kaplan/files/2019/04/ContemporaryMLforPhysicists.pdf) - An extended introduction to deep learning from a fairly theoretical perspective. Also has no exercises.
- [Sutton & Barto](http://www.incompleteideas.net/book/the-book.html) - A good introduction to reinforcement learning from first principles. Has exercises.
- [Murphy](https://www.google.com/search?q=machine+learning+a+probabilistic+perspective), [Bishop](https://www.google.com/search?q=pattern+recognition+and+machine+learning) and [ESL](https://www.google.com/search?q=elements+of+statistical+learning) - Classic machine learning textbooks. These cover a lot of material that isn't that relevant to deep learning, but it can be nice to have a broader perspective, and they have plenty of exercises. Overall they wouldn't be my first choice but they can be useful.

Some suggestions for more advanced online courses:

- [Deep Learning Specialization from deeplearning.ai](https://www.deeplearning.ai/program/deep-learning-specialization/) - A much longer extension of the machine learning Coursera course linked above.
- [Deep Learning Udacity course](https://www.udacity.com/course/deep-learning-nanodegree--nd101) - Another longer deep learning course.
- [Reinforcement Learning Coursera course](https://www.ualberta.ca/admissions-programs/online-courses/reinforcement-learning/index.html) - A reinforcement learning course based on Sutton & Barto.

## Additional advice

These are miscellaneous opinions based on personal experience, so take them with a pinch of salt. [An Opinionated Guide to ML Research](http://joschu.net/blog/opinionated-guide-ml-research.html) is also worth a read.

I've emphasized exercises throughout this page, because they force you to think ideas through in a way that passive learning doesn't. In my experience, this is especially important when learning about unfamiliar topics. Once you have built up experience in an area, it's much easier to remember something in that area that you've only seen or heard once, because of how it fits into your existing web of knowledge.

To be productive, physical and mental health are paramount. Beyond that, there's no good substitute for intrinsic motivation. Productivity tricks can be useful for getting laborious work done when necessary, but can only do so much. Intrinsic motivation can come both from higher-level excitement about a project, as well as from lower-level flow states (which can be common with programming). When it doesn't matter much what you're working on because you're mostly learning, choose things you'll be intrinsically motivated by, as that's the easiest way to excel. But exciting areas aren't always important, and so in the long run, you'll need to cultivate excitement about important areas by learning more about them.

Vertical integration can be powerful, because abstractions are generally leaky. The most effective researchers have an understanding of their entire research stack, from the ins and outs of different benchmarks through to the details of GPU caches. Especially early on in your career, learning as much as you can about everything that's relevant is probably a better strategy than focusing only on what you need to get by.

As an important special case of the above principle, if you want to have a positive impact on the world with your research, I highly recommend focusing on how best to achieve this as part of your studies. Choosing the right problems to work on can be just as important as the quality of your execution, even if you end up spending most of your time on the latter. Moreover, it's not always enough to defer to others on such questions, since your higher-level motivations will influence your lower-level decisions, not to mention the fact that other people can be wrong or hard to understand.

I personally expect AI to have a far greater impact on the world in the coming decades than it is having now, and that this is enough to outweigh the urgency and tractability of present-day problems (though I also see a lot in common between both sets of problems). For more discussion of this perspective, I recommend [Cold Takes's "most important century" series](https://www.cold-takes.com/most-important-century/). Consider also signing up to the [Alignment Newsletter](https://rohinshah.com/alignment-newsletter/) to stay up-to-date with related research.
