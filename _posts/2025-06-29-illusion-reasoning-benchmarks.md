---
layout: post
title: The Illusion of Reasoning Benchmarks
date: 2025-06-29
description: A response to "The Illusion of Thinking"
tags: LLMs reasoning benchmark
---

In [*The Illusion of Thinking*](https://machinelearning.apple.com/research/illusion-of-thinking) (Shojaee et al., 2025), the authors investigate
whether LLMs truly exhibit reasoning capabilities. Using controlled puzzle
environments like the Tower of Hanoi, Blocks World, and River Crossing, they
systematically vary problem complexity and analyze both final answers and the
intermediate reasoning steps (or “thought traces”) of several LLMs and LRMs. For
example, the River Crossing problem is defined as (Shoajaee et al. 2025):

<blockquote style="font-size: 1em;">
River Crossing is a constraint satisfaction planning puzzle involving <strong>n</strong>
actors and their corresponding <strong>n</strong> agents who must cross a river using a boat.
The goal is to transport all <strong>2n</strong> individuals from the left bank to the right
bank. The boat can carry at most <strong>k</strong> individuals and cannot travel empty.
Invalid situations arise when an actor is in the presence of another agent
without their own agent present, as each agent must protect their client from
competing agents.
</blockquote>

Their findings show that while reasoning models can outperform standard LLMs on
moderately complex tasks, both types collapse when facing higher complexity. The
models not only fail to generate correct final answers but also reduce the
number of tokens spent thinking, despite having ample inference budget. The
authors conclude that these models do not possess robust, generalizable
reasoning abilities and often resort to pattern matching or heuristics.

This evaluation paradigm has a critical limitation: *it equates reasoning with
successful execution on large-scale planning tasks*. In reality, even humans
rarely attempt to fully *execute* high-complexity problems (like the 20-disk
Tower of Hanoi). They describe a recursive *strategy* and, if needed, prove its
correctness. Reasoning should not be judged solely by whether an agent can
follow through every step, but by whether it can understand and articulate a
generalizable plan.

Reasoning is about **forming mental models and generalizing patterns**, not
brute-force enumeration. There’s a distinction between *declarative knowledge*
(“I know how it works”) and *procedural knowledge* (“I can carry it out”).
Models may exhibit the former without the latter. Yet even within declarative
reasoning, there is plenty of meaningful cognitive work that can occur,
identifying structure, articulating valid solution paths, proving why a certain
approach works, or recognizing edge cases and constraints. These are core
components of intelligent reasoning, and evaluating them provides richer
insights into a model’s capabilities than simply measuring whether it can follow
through every step of an execution-heavy task.

Current puzzle-based benchmarks (like in the paper) measure step-by-step
**correctness** under token limits and planning bandwidth. This punishes models
for lack of *execution capacity*, not for lack of *strategic insight*. A better
test of reasoning would focus on whether a model can generalize rules, derive
patterns, or prove properties whose complexity scales with the problem. For
example, logical inference tasks (“Given a set of rules and premises, what
follows?”) become progressively harder as the rule set grows deeper or more
entangled. Similarly, problems like “prove that the number of ways to tile a 2×n
grid with dominoes is the nth Fibonacci number” require models to identify
recurrences, construct generalizations, and articulate inductive reasoning, none
of which require executing each instance. These tests move away from mere
simulation and toward the kind of scalable symbolic abstraction that more
closely mirrors human reasoning.

In sum, the collapse of LLM performance on highly complex procedural puzzles may
say more about their execution limits than their reasoning potential. If we want
to understand whether LLMs can reason, we must move beyond testing their ability
to follow steps and toward testing their ability to generate, explain, and
generalize *strategies*. Reasoning is not about grinding through complexity,
it’s about seeing through it. Until benchmarks evolve to reflect this, we risk
underestimating what LLMs already do well, and misunderstanding what reasoning
truly requires.

<!-- <span style="color:gray">Euxhen Hasanaj</span> -->

#### References

[1] Shojaee, P. *et al.* The illusion of thinking: Understanding the strengths
and limitations of reasoning models via the lens of problem complexity. *arXiv
[cs.AI]* (2025).
