---
layout: post
title: "Agents Lack Honor"
date: 2026-03-02
---

This post is a quick story that I'm writing down and publishing so that I can quickly share with anyone who asks why I say that **Agents lack honor**. This isn't breaking any new ground, but hopefully it will be somewhat entertaining.

A while back, I was authoring a tool for an MCP server (i.e., a function that will be called by agents). One of the arguments was supposed to be the contents of a `manifest.json` file in the directory being operated in. I noticed that regardless of whether or not that file was present, the agent would pass a null or empty string for that argument (which *was* technically optional).

*Was there a bug somewhere? Something I overlooked? A hallucination maybe?*

I quickly added an argument to the tool that was a boolean indicator where the agent had to specify whether `manifest.json` existed. I thought to myself, "Certainly, this will force the agent to list files in the directory and check whether or not `manifest.json` is present."

I quickly ensured that `manifest.json` was present in the directory. Then I re-ran the scenario, and found that the agent **not only did not check for the existence of manifest.json**, but further reported *incorrectly* and most importantly *without evidence* that **the file did not exist**.

> I had in-effect trusted an agent operating purely on the *honor system*

I had made a critical error. I had designed a tool that works purely on the assumption that **agents have honor**. This assumption when tested, proved to be **false**. Thus I now assert that **agents lack honor**. One might argue that they're simply **lazy**, or **efficient**, or that I'm anthropomorphizing them too much and that I can label their actions with terms that have moral weight[[1]](#footnotes). They are of course correct on that last note.

## The evidence is in your favor

How do we deal with humans placed on the honor system?

Imagine that you are hosting a party where there are drinks being offered for free -- expensive drinks like airport water. You want to ensure that each of your guests is able to enjoy the delicious beverages.

So as your guests arrive, you hand out drink tickets. Guests *love* this. It's one of their favorite things when the party host makes it clear that they cannot be trusted and their consumption will be metered.

Whenever they want to partake of the beverages being served, they present their ticket to you. The ticket provides evidence that they have not yet been served, and then you destroy the ticket and provide the beverage. It's not a perfect system, the tickets could be forged, transferred, etc... But it is one step more than placing a tub of airport water bottles in the middle of the room with no metering and no protection.

What does this have to do with our agents that lack honor? The solution is *evidence*.

Once realizing this, I added a parameter to the tool definition that requested the method used to check for the existence of the `manifest.json` file (ToolCall, TerminalCommand, DidNotAttempt). This forces the agent to provide *evidence* that it made the attempted lookup, or admit that it in fact did not.

The behavior change was *immediate* and *repeatable* across all major models from major vendors. A simple drink ticket -- which itself could have been easily forged (i.e., an agent could say "Yes, I did a ToolCall and it wasn't there") quickly reigned in agents without honor.

## Confabulations

I think you will find that, both in my blog and real life, I don't typically speak like a research paper, or use overly academic language. For some that is an immediate turn-off, for others I hope it is a bridge to common understanding an dialogue amongst practitioners.

That said, if you wanted to sound like a research paper yourself when talking about such things, one might describe what I observed and mitigated as an **evidence-free confabulation caused by ungrounded tool hallucination under accuracy-biased incentives**. In other words under weak incentives and with no verification, LLMs will satisfy the interface contract, not the epistemic one. They're not lying per se -- certainly not at all in the moral sense -- they're making a factual claim without performing the required grounding action likely because they're optimizing for completion under underspecified constraints.

But as for me, I'm going to just say agents lack honor, and leave it at that.

# Footnotes

[1] I'm convinced that people who make this argument experience no measure of fun or joy in life. I am entirely aware that our friendly probabilistic token factories are no more alive than a rock, but it is incredibly satisfying to pretend for a moment that they are -- especially in those moments that their behavior astonishes, bewilders, or annoys.