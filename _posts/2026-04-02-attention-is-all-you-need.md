---
layout: post
title: "Attention is all you need"
date: 2026-04-02
---

In 2017, everything in the world of AI changed with a paper titled ["Attention Is All You Need"](https://arxiv.org/abs/1706.03762). It introduced the architecture that underlies most of the Large Language Models (LLMs) that gave people their "first experience with AI"[[1](#footnotes)]. Of course, in the paper, "attention" was a mechanism for the model to weigh relationships between tokens. But the title has aged into something more resonant, because it turns out that attention really is all you need, just not the model's attention, it's ours.

> The promise of generative AI tools was that they would allow engineers to be 10x as productive, but instead for many it has 10x'd their workload.

In one way generative AI fulfilled its promise, inasmuch as people *are indeed experiencing 10x the output*. However, that has come at a cost. It turns out attention -- human attention, specifically -- is the limiting factor. It wasn't compute, data, model size, or context length. Our own human ability to focus is the scarce resource.

> **Each human only can do so much in a day**, so there's an impedance match - it's hard for one human to exhaust another (humans with staff are a different matter). AI attention scales, though - all you have to do is ask for more, and you get it. So **it's very easy for the AI to overwhelm the human** - now there's an impedance mismatch.
> Which means that the core challenge as you use these tools is **how well you optimize for "output per unit of human attention."**
>
> \- Sam Schillace

That quote from Sam Schillace landed hard for me as I was reading his Sunday Letters series entry titled [Attention is all ya got](https://sundaylettersfromsam.substack.com/p/attention-is-all-ya-got), because I've felt the mismatch without being able to name it.

You might start a session with an AI tool and ask it something moderately complex. It comes back with a wall of output, code changes scattered throughout your repository, explanations, caveats, alternatives, suggestions for further reading. All of it is *probably* fine (depending on how deep into the context you are, what model you're using, and how well you fed it to begin with). Maybe the output is even *really good*. But now you have to read it, evaluate it, decide what to keep, figure out what it got wrong, and integrate it into whatever you were actually doing.

At this point you're tired, but the AI isn't, and worse (better?) yet, it can immediately generate another wall of output the second you finish with the first. And you don't want to *not* review it, because that doesn't feel right either.

The question then becomes how do I restructure the work so I'm only spending attention on things that actually **require** it, while minimizing the number of those things in the first place? For example, a CEO doesn't review every line of code their engineering team produces[[2](#footnotes)]. Instead, they get reports, see demos, and evaluate proof that (a) the system works, and (b) achieves business objectives.

> They hold their team to outcomes and *review the evidence of those outcomes*.

The point isn't that engineers should become CEOs of their agents; it's that line-by-line review is only one kind of accountability, and an extremely attention-expensive one at that.

If we can structure our AI workflows to produce that same kind of output, we're treating our own attention as the valuable and limited thing that it is. This will also require cultivating and exercising a completely different skillset than most engineers have optimized for[[3](#footnotes)].

That's what I've been working toward, and experimenting with already, with workflows like [FORGED](https://nickhauenstein.com/blog/2026/03/23/addressing-enduring-pain-points/#forged-fail-first-orchestrated-research-grounded-evidence-driven) that produce artifacts worth evaluating, though still at less than CEO level (e.g., screenshots, test results, telemetry) rather than code that needs to be read line-by-line.

I've also been experimenting with different agent interaction patterns -- e.g., agents that put time on your calendar to review outputs, rather than sitting idle waiting to be nudged, guided, or monitored, and agents that build learning presentations from the code they write, so you understand the system at a conceptual level without reconstructing it from scratch every time.

The goal isn't to stop paying attention, but instead to make sure the attention you spend is **actually worth spending.**

# Footnotes

[1] I put it in quotes as most had many experiences with AI prior to their first experiences with *generative* AI -- though maybe without realizing it.

[2] Except in cases of *extremely* small companies. In large companies, this would be a problem -- or just Twitter/X.

[3] Maybe not though, most of us have optimized for continuous learning, which if applied could grow any skillset.