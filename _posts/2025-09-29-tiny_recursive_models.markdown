---
layout: post
title: "Less is More: Recursive Reasoning with Tiny Networks"
---

  \|\| [Paper](https://arxiv.org/abs/xxxxx) \| [Code](https://github.com/SamsungSAILMontreal/TinyRecursiveModels)  \|\|

In this new paper, I propose Tiny Recursion Model (TRM), a recursive reasoning model that achieves amazing scores of 45% on ARC-AGI-1 and ?% on ARC-AGI-2 with a tiny 7M parameters neural network. My prediction for the future is that recursive reasoning approaches will soon take over Large Language Models (LLMs) with Chain-of-thought (CoT). Currently, there is too much focus on exploiting LLMs rather than devising and expanding new lines of direction. With recursive reasoning, it turns out that "less is more"; you don't always need to crank up model size in order for a model to reason and solve hard problems. What you need is a tiny model recursing on itself and updating its answers over time.

This work came to be after I learned about the recent innovative Hierarchical Reasoning Model (HRM). I was amazed that such a small model could do so well on hard tasks like the ARC-AGI competition (reaching 40% accuracy when normally only Large Language Models could compete). But I kept thinking that it is way too complicated, relying too much on biological arguments about the human brain, and that this recursive reasoning process could be greatly simplified and improved. Tiny Recursion Models (TRM) simplify recursive reasoning to its core essence, which ultimately has nothing to do with the human brain, does not require any mathematical (fixed-point) theorem, nor any hierarchy.

### How TRM works

<img src="{{ site.baseurl }}/assets/images/TRM_fig.png" alt="TRM-Figure" style="width:50%" class="center">

Tiny Recursion Model (TRM) recursively improves its predicted answer y with a tiny network. It starts with the embedded input question x and initial embedded answer y and latent z. For up to 16 improvements steps, it tries to improve its answer y. It does so by i) recursively updating n times its latent z given the question x, current answer y, and current latent z (recursive reasoning), and then ii) updating its answer y given the current answer y and current latent z. This recursive process allows the model to progressively improves its answer in an extremely parameter-efficient manner while minimizing overfitting.

<img src="{{ site.baseurl }}/assets/images/TRM_pseudocode.png" alt="TRM" style="width:80%" class="center">

See the [paper](https://arxiv.org/abs/xxxxx) for more details.

