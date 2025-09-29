---
layout: post
title: "Less is More: Recursive Reasoning with Tiny Networks"
---

  \|\| [Paper](https://arxiv.org/abs/xxxxx) \| [Code](https://github.com/SamsungSAILMontreal/TinyRecursiveModels)  \|\|

In this new paper, I propose Tiny Recursion Model (TRM), a new type of recursive reasoning model that achieves an incredible score of ?% on ARC-AGI-1 with a tiny 8M parameters neural network. My prediction for the future is that recursive reasoning models, such as TRM and the recent Hierarchical Reasoning Model (HRM), will soon take over Large Language Models (LLMs) on many tasks given enough time. It turns out that "less is more", you don't always need to crank up model size in order for a model to reason and solve hard problems. What you need is a tiny model recursing on itself and updating its answers over time.

This work came to be after I learned about the recent innovate Hierarchical Reasoning Model (HRM). I was amazed that such a small model could do so well on hard tasks like the ARC-AGI competition (reaching 40% accuracy when normally only Large Language Models could compete). But I kept thinking that its way too complicated, relying too much on biological arguments about the human brain, and that this recursive reasoning process could be greatly simplified and improved. Tiny Recursion Models (TRM) simplifies recursive reasoning to its core essence, which ultimately has nothing to do with the human brain, does not require any mathematical (fixed-point) theorem, nor any hierarchy.

### How TRM works

Tiny Recursion Model (TRM) recursively improves its predicted answer $y$ with a tiny network. It starts with the embedded input question $x$ and initial embedded answer $y$ and latent $z$. For up to $N_{sup}$ improvements steps, it tries to improve its answer $y$. It does so by i) recursively updating $n$ times its latent $z$ given the question $x$, current answer $y$, and current latent $z$ (recursive reasoning), and then ii) updating its answer $y$ given the current answer $y$ and current latent $z$. This recursive process allows the model to progressively improves its answer in an extremely parameter-efficient manner while minimizing overfitting.

<div class="row">
  <div class="column">
    <img src="{{ site.baseurl }}/assets/images/TRM_fig.png" alt="TRM-Figure" style="width:100%">
  </div>
  <div class="column">
    <img src="{{ site.baseurl }}/assets/images/TRM_pseudocode.png" alt="TRM" style="width:100%">
  </div>
</div>

See the [paper](https://arxiv.org/abs/xxxxx) for more details.

### ARC-AGI benchmark

ARC-AGI is trivial for humans, but very hard for AI models. The benchmark has existed for 6 years now and is unbeaten. Large Language Models (LLMs) such as GPT-5, o3, Grok-4 still struggle with it. The current top score is at 79.6% using massive expensive Test-Time Compute methods with Grok-4. Nobody has yet to reach the 85% required to official pass the test. 

HRM managed to achieve an impressive 40.3% accuracy (which dropped to 32.0% on the semi-private evaluation set) on ARC-AGI-1. This may seem small, but for a model pretrained from scratch with only 27M parameters, this is extremely impressive when almost everybody else is fine-tuning LLMs with at least 1,000 to 10,000 times more parameters (from billions to trillions of parameters). 

TRM took a massive step up by achieving ?% accuracy using a single tiny network of only 8M parameters!