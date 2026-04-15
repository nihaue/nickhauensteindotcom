---
layout: post
title: "Will AI learn how planning actually works?"
date: 2026-04-14
---

There is a mistake I am starting to see everywhere in AI-assisted software engineering, and unfortunately it is not even a new mistake -- which means I'm old enough to have seen it made twice, and will likely be here for us to collectively re-learn the lesson a second time.

In a [previous post](https://nickhauenstein.com/blog/2026/03/23/addressing-enduring-pain-points/), I described FORGED -- a workflow for getting high-quality outputs from AI at feature scale. But FORGED assumes the problem fits inside one workflow instance. What happens when it doesn't? What happens when the work is an entire project, and someone (or something) asks AI to plan the whole thing up front?

You might find that if you ask AI to plan an entire project, it will confidently produce a beautiful, comprehensive, numbered plan. The plan has phases (sometimes it even shouts `PHASE`, or creates wild alphanumeric labels for the phases, as if there's a convention we agreed on for how they ought to be denoted). The phases have tasks. The tasks have dependencies. The dependencies look reasonable. The whole thing gives off the comforting smell of competence.

The first line of code has not even been written, and yet, we've already begun lying to ourselves.

> That may sound harsh, but this is one of the oldest lessons in software engineering: the plan is wrong.

The plan is not wrong because the people making it are incompetent. The plan is wrong because the world it describes does not exist yet. The act of building the thing changes what you know, what is possible, where the risk lives, and what the next correct step should be.

If we are serious about AI helping with serious engineering work -- not just vibe coding or generating plausible diffs -- then we have to ask whether AI is going to learn the planning lessons humans already paid for, or whether we are committing to repeat all of them at machine speed.

## The Gantt Chart on the Wall

For years, software teams used waterfall-style planning because it felt responsible. When I first joined Microsoft as an "orange badge" in the world of gaming, I walked into one of Microsoft's offices for the first time and saw a printed Gantt chart on the wall.

It was beautiful.

Someone had taken an entire project[[1]](#footnotes) and fit it into one mental model. This was not a little status slide. This was a multi-year effort printed on paper using a plotter and mounted on the wall like a declaration of intent. It had the aura of someone saying: here is the project; here is the whole thing; here is the map.

And then, all over it, there were scribbles. Pen marks. Pencil marks. Corrections. Adjustments. Little artifacts of reality intruding on the plan. I remember looking at it and feeling two things at once:
1. This is genuinely impressive. Someone understood enough of the moving pieces to produce this at all.
2. This is clearly, beautifully, and inevitably wrong.

That second reaction was not a criticism of the person who made it. At a sufficient scale, every plan is a lie. The interesting question is whether the lie is even useful.

## Compound Probability Eats the Plan

The problem with a large software plan is not that one item might be wrong. The problem is that every item has a non-zero probability of being wrong.

If a plan has ten meaningful steps, each step has to survive contact with reality. The requirement has to be understood. The dependency has to exist. The estimate has to be *close enough*. The technical assumption has to hold. The person or team doing the work has to be available. The external system has to behave as expected. The previous step has to leave the project in the state the next step assumed would exist.

Even if each step is individually extremely likely to be right, the combined plan degrades quickly.

> If each step has a 90% chance of being right, then ten steps in a row gives you a 34.87% chance that all ten are right. Twenty steps gives you 12.16%. Thirty steps gives you 4.24%. Forty steps gives you 1.48%. Fifty steps gives you 0.52%. By 58 steps, the chance that every step in the plan is right is 0.22%.

Sometimes we make plans with worse odds than March Madness.

And that toy math is still generous because it treats the steps as independent. Real software projects are not independent. When step three is wrong, step seven is no longer merely at risk. It may now refer to a world that no longer exists.

This is why the end of a sufficiently large plan has functionally a 100% probability of being wrong in the details. Not because planning is useless, but because the world of the project ten steps from now will have been changed by the first nine steps. We will have learned things. We will have broken things. We will have discovered constraints. We will have found simpler paths and uglier truths. The project will not be standing where the original plan imagined it would be standing.

So when an AI system emits the whole plan at once, before any assumptions have been tested, it is not doing project management magic. It is generating a high-resolution guess about a world it could not possibly have observed.

The worst part is that this is essentially self-inflicted. It's not really AI's *fault*. If we ask for the whole plan up front, we should not be surprised when it gives us the whole plan up front. If we want better plans, we have to ask for a different shape of work.

## The Lesson Was Progressive Decomposition

The lesson humans eventually learned was not "never plan." That is silly. Planning is how we coordinate intent, surface risk, allocate attention, and make decisions before the cost of those decisions becomes unbearable.

> The lesson was that large-scale intent should be progressively decomposed.

At the project level, you establish direction. You identify the meaningful constraints. You name the risks. You define what evidence would change your mind. You create enough structure for the organization to move without pretending the whole path is already known.

Then, **just in time, you decompose the next meaningful thing.**

Project to epic. Epic to feature. Feature to story. Story to task. Use whatever nouns your organization prefers, as long as you decompose the work as late as you responsibly can, when you know enough for the decomposition to be real.

## Experiments Are Suddenly Cheap

Progressive decomposition has always depended on an implied pre-requisite: that you can afford to *learn* between decompositions.

In the past, one of the ways teams tackled uncertainty via learning was through *spikes* or proof-of-concept projects. You would experiment. Build a thin version. Test the integration. Try the library. Validate the architecture. Learn whether the thing that sounds reasonable in a meeting is actually true.

Those experiments were valuable, but they were not free. They took engineering time. They created sunk-cost temptation. They sometimes turned into zombie prototypes that production systems mysteriously inherited later.

With AI, the cost of learning drops to near zero. We can build and throw away five approaches before committing to one. We can ask an agent to spike three different libraries, gather evidence, and report the tradeoffs. We can have it create a disposable integration, measure what breaks, and delete the whole thing without regret. Progressive decomposition works better when the cost of answering "should we take path A or path B?" is a 15-minute experiment instead of a two-week commitment.

## Planning at Different Scales

AI engineering needs different workflows for different scales of change, because the failure modes at each scale are fundamentally different.

**Feature scale.** The uncertainty fits inside one bounded loop. You can research, design, test, plan, implement, and verify -- and close the loop. This is [FORGED](https://nickhauenstein.com/blog/2026/03/23/addressing-enduring-pain-points/).

**Project scale.** The plan itself is the uncertainty. Progressive decomposition is the answer -- hold broad intent, resist fake precision, retire unknowns through experiments, and decompose just in time. This is what we've discussed in this post.

**Production change scale.** The uncertainty is in the *path*, not the destination. The system is already alive, and every intermediate state it passes through has to be deployable, observable, **and reversible**. That is its own discipline, and it is the subject of the next post.

Each scale fails differently:
- A project fails because the decomposition is fake.
- A story fails because the implementation is wrong.
- A production migration fails because the destination is right but the path is unsafe.

An engineer has to understand, navigate, plan, and execute against all of these. These three disciplines -- correct implementation, honest planning, and safe paths -- are what AI needs to do real engineering at any scale.

# Footnotes

[**1**] At the time I was playing a small part in the pre-certification testing process for Xbox Live Arcade, running titles through TCR tests, so my best guess is that the chart on the wall belonged to that effort -- but it was over 20 years ago and it may well have been an adjacent project sharing the same hallway. Either way, the scribbles were real.