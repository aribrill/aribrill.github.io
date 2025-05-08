---
layout: post
title: Computational Complexity as an Intuition Pump for LLM Generality
date: 2024-06-25 23:59:59
description: To predict AI's impact, quantify its computational efficiency.
tags: ai ai-safety computer-science
categories: writings
---

_This post was originally published on [LessWrong](https://www.lesswrong.com/posts/HxHYPJoaWD8AjaHCk/computational-complexity-as-an-intuition-pump-for-llm)._

With sufficient scale and scaffolding, LLMs will improve without bound on all tasks to become superhuman AGI, to the extent they haven’t already. No, wait! LLMs are dead-end pattern-matching machines fundamentally incapable of general reasoning and novel problem solving. Which is it?

I’ll call these opposing points of view “LLM Scaler” and “LLM Skeptic”. The first appears to be held by the big AGI labs and was recently exemplified by Leopold Aschenbrenner’s [Situational Awareness](https://situational-awareness.ai/) series, while the second is influenced by cognitive science and can be associated with researchers such as François Chollet, Gary Marcus, and Melanie Mitchell. This post loosely generalizes these two stances, so any misrepresentation or conflation of individuals’ viewpoints is my own. I recommend Egg Syntax’s [recent post](https://www.lesswrong.com/posts/k38sJNLk7YbJA72ST/llm-generality-is-a-timeline-crux) for further introduction and a summary of relevant research. We can caricature the debate something like this:

LLM Scaler: LLMs will take us to AGI. See straight lines on graphs. See correct answers to hard questions on arbitrary topics. See real customers paying real money for real value.

LLM Skeptic: LLMs achieve high skill by memorizing patterns inherent in their giant training set. This is not the path to general intelligence. For example, LLMs will never solve Task X.

LLM Scaler: They solved it.

LLM Skeptic: No kidding? That doesn’t count then, but they’ll really never solve Task Y. And you can’t just keep scaling. That will cost trillions of dollars.

LLM Scaler: Do you want to see my pitch deck?
\
\
\
Meanwhile, on Alternate Earth, Silicon Valley is abuzz over recent progress by Large List Manipulators (LLMs), which sort a list by iteratively [inserting](https://en.wikipedia.org/wiki/Insertion_sort) each item into its correct location. Startups scramble to secure special-purpose hardware for speeding up their LLMs.

LLM Scaler: LLMs are general list sorters, and will scale to sort lists of any size. Sure, we don’t quite understand how they work, but our empirical compute-optimal scaling law (N ~ C^0.5) has already held across a dozen OOMs, and we’re spending billions in venture capital to keep it going!

LLM Skeptic: That absurd expense is unsustainable. Can’t you see that? There’s no way that LLMs are truly general list sorters. Good luck getting one to sort a list with a million items.

LLM Scaler: We already have.

LLM Skeptic: Oh. Well then, LLMs will never sort a list with a BILLION items!

The “LLM” Skeptic is, literally, wrong. Insertion sort is fully general and can in principle scale to sort a list of any size. Each time the Skeptic declares that some specific list size is impossible to sort, they only embarrass themselves. But this skepticism reflects a deeper truth. The “LLM” paradigm is fundamentally inefficient. Sooner or later, hype will crash into real-world cost constraints and progress will stall. If Alternate Earth knew more computer science, the Skeptic would have told the Scaler to replace O(N^2) insertion sort with an efficient O(N log N) algorithm like [quicksort](https://en.wikipedia.org/wiki/Quicksort).
\
\
\
Returning to Large Language Models, how might computational complexity reframe our understanding of their abilities? The explicit or implicit designer of any intelligent system faces a tradeoff between allocating its model capacity into memorization – of facts, heuristics, or complex programmed behaviors – and implementing adaptive algorithms for learning or [optimization](https://arxiv.org/abs/1906.01820). Both strategies enable equivalent behavior given unlimited resources. However, the former strategy requires model capacity that scales with the diversity and complexity of possible tasks, and the real world is both diverse and complex. The latter strategy requires only constant capacity, yielding drastically improved efficiency. This is made possible by exploiting some combination of in-context data, computation time, or external memory during inference.

An efficient learning algorithm makes the most accurate predictions possible, while using the fewest resources possible. Scaling up an LLM requires increasing the model size, training dataset size, and compute (proportional to the first two’s product) in tandem following some [optimal ratio](https://arxiv.org/abs/2203.15556), limited by one of these three factors. For a chosen scaling policy, an LLM’s computational complexity in model capacity translates into efficiency using its training resources in general.

With this mental model, we can understand the LLM Skeptic as making either the strong claim that LLMs memorize exclusively, or the weaker but more believable claim that they memorize excessively, leavened with only a little in-context learning. In short, LLMs are inefficient algorithms. The Skeptic would be wrong to pinpoint any given task as impossible in principle, if given unlimited parameters, training data, and compute. But they could be right that in practice inefficiency pushes generality out of reach. The LLM Scaler might variously reply that whatever way LLMs balance memorization and in-context learning is apparently good enough; that scaffolding will patch any inefficiencies; or that more efficient in-context learning strategies will keep emerging with scale.

Will scaling up LLMs lead to AGI? And if not, what will? You can scale, but you can’t scale forever. The ultimate impact of current and future AI systems is bounded by the maximum efficiency with which they convert resources into solved problems. To understand their capabilities, we need to quantify this efficiency.
