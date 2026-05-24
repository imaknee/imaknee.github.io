---
title: "The Foundations of a Framework for Neuromorphic Computing: Part 2"
date: 2026-05-24
mathjax: true
categories:
  - Blog
  - Tutorial
tags:
  - Neuromorphic 
  - Framework
---
*To kick off this site, over a series of posts I am going to explain narratively the rationale behind the development of my proposed [neuromorphic computing framework]( https://arxiv.org/abs/2507.17886) and the implications of it. I encourage you to read the framework itself for the technical details and results.  This series will work to build towards a more conversational understanding of neuromorphic computing and how that relates to neuroscience, AI, and computer science in general.*

# Part 2: So what has gone wrong?

## Is it a lack of clarity?

I mentioned in my previous post I talked about the ‘why’ for neuromorphic; but while that is strong subjectively, it hasn’t stuck widely.  The reason for this, I believe, comes down to something that everyone who has written or reviewed a grant can appreciate. 

The single most important thing for writing a proposal is being able to communicate clearly ‘what success looks like’ to the reader.  The details of the research are important, but ultimately they’re irrelevant if the reviewer does not know where the investigator wants to go.    

This is something the neuromorphic computing field (and indeed, probably neuroscience as well) has never quite figured out.  We all have ideas and feelings about what success will be, but without clearly defined goalposts we’re all kind of grabbing the ball running in different directions. 
Compare that to quantum computing, which has clear “if you can get X qubits with less than Y noise, you can do Z with a formally proven benefit” statements. 
That provides clarity to researchers (scientists and engineers both) and a rigorous set of metrics, and that rigor allows people external to the field to trust it and want to either join it or fund it.
It is not that individual neural computing researchers don’t have goals and objectives; it is just they’re just inconsistent and sometimes at odds with one another. 
For example, some of my spiking algorithm results do not use internal neuron dynamics (the “leakiness” in leaky integrate-and-fire neurons); so people whose work focuses on analog circuit dynamics do not see the point. There is an intrinsic misalignment of goals, and when goals are not explicit people get confused.  
Perhaps we all should do a better job of communicating, but when value remains in the eye of the beholder, we cannot expect the value to be shared.  This incidentally is also why ‘The goal is to understand X better’ is not a good objective for a grant, and it is why basic research funding is often a tough sell without strong justification.  

## Or do we keep fighting the wrong battles?

Unfortunately, this lack of a clear value proposition is incredibly confusing to everyone not in the neuromorphic field, and it leads to awkward questions and interactions as well as things like the *absolutely terrible* ‘bird—plane’ metaphors. I cannot count the number of times someone has asked me “what is neuromorphic better at?”, and even within the field we struggle to espouse the ‘why are we doing this,’ even though we’ve dedicated our careers to it.
In many ways these challenges are self-inflicted, and they set up the field to fail. Going head-to-head in a debate with Bill Dally about whether today’s neuromorphic can beat GPUs at deep learning is the equivalent of debating the potential value of air travel in the 1890s by challenging hot air balloons to outrace a train.  This is also why I am skeptical of the trend towards benchmarking in the neuromorphic space.  
While efforts like NeuroBench are commendable, I worry that they’re an ‘own goal’: we all know the neuromorphic computing technology stack is too immature to compete on mainstream benchmarks (nevermind the intrinsic mismatch to modern AI in general), but picking application corner cases that are if interest only within our community makes benchmarking a software and hardware engineering ranking rather than a fundamental technology assessment.  

In what universe should a research chip with a limited software stack, few (if any) established algorithms, and no compiler optimization outperform a commercial product with billions of dollars and decades of time invested in a robust software ecosystem? Nonetheless, people routinely say “why can’t <insert neuromorphic algorithm here> beat H100 GPUs with CUDA optimization?” 

Yet despite these incredible differences in maturity, we have still seen empirical advantages.  Frankly, that should not be possible given the relative maturity of the technologies. So why is that?  

## A fresh perspective

To get to that question, it is worth bringing up something that has, for whatever reason, been largely missing from neuromorphic computing---theoretical computer science.

One of the highlights of my somewhat unique career trajectory is that I have had the opportunity to work with theoretical computer scientists.  Not just a random comp sci major who took a theory elective; but real members of the TCS community who go to conferences with funny names like STOCS and FOCS, alphabetize authors, rarely ever use figures in papers, don’t really trust a result unless it is a formal proof, and have very low Erdős numbers. 

Coming from neuroscience, I am not shy to say that this field was entirely foreign to me.  While working with some TCS folks got me a handful of “Aimone et al.” alphabetized first author papers and a decently low Erdős number of my own (by my count ‘3’); the best thing I got from these collaborations is that I got to see the brain from a new perspective that I never realized even exists.

Simply stated, the main point of theoretical computer science is to ignore the details of current implementations, for which costs are typically dominated by current technology limitations, and focus on the underlying math related to the scaling of algorithms and architectures.  
Can a rudimentary hot air balloon beat a steam engine train between New York and Philadelphia?  Probably not.  Can air flight, which is not limited to travel along a one-dimensional track, outperform trains between arbitrary points at arbitrary distances?  That’s an entirely different question.  

Because neuromorphic computing is not a mature technology yet, its value is theoretical.  And because its value is theoretical, we need to at least consider theoretical computer science.

## So what would a formal computing advantage look like?

From a theoetical computing perspective, there are three ways for a computing paradigm to be an improvement over alternatives.  

The first, and by far the most common in practice, is that it provides a **constant factor advantage**.  A constant can be tiny (e.g., 1.01) or huge (e.g., 1.32^21).  
Constants can apply to time, space, or energy. Moore’s Law and Dennard Scaling were really just a series of constant factor improvements to hardware that looked exponential because they kept happening over many decades.  
The transistors in my PC’s 486 processor were about half the size as in my 386 processor, so the processor could have about four times as many of them and they could run roughly twice as fast at a constant energy.  
Do this every couple of years and good things happen. 

Constant factors are the domain of engineering and optimization. But as such, they often track extrinsic factors, such as investment, technology maturity, and engineers’ ingenuity, rather than the intrinsic methods themselves. This is also the story of Nvidia's GPU improvements over the last couple of decades, gaining optimizations in everything from better memory management to reducing precision to unprecedented levels. Of course, there is no assurance that another constant factor improvement will come tomorrow, one can cut precision in half only so many times before you can't do it anymore. 
For this reason, as a general rule, theorists ignore these constant factors. That’s what the ‘Big-O’ notation does. There is nothing wrong with a constant factor benefit, but it isn’t what theory is about.

In contrast, the Holy Grail is a **complexity class difference**.  Most people have heard of the <P=NP or P!=NP?> problem. P and NP are complexity classes of algorithms, P being those that can be solved in polynomial time (as a problem size, N, increases, the time it takes to solve that problem is no worse than O(N^k)), and NP are (simply stated) those problems for which a solution can be verified in no worse than polynomial time.  

A problem, such as traveling salesman, is an NP-complete problem but not P.  All known solutions to the problem are exponential with the size of the problem (even though checking if a solution is valid is trivially cheap). Fiddling with the architecture or the algorithm won’t change this; if we want to solve problems like these we have to either pay the full cost or use approximate algorithms.  

We can only see exponential speedups in a computer architecture when we change the physics somehow.  Quantum computing does this, which is best exemplified by Shors algorithm in which the Quantum Fourier Transform (QFT) allows an exponentially more efficient transformation of an input distribution.  QFT exists in a different complexity class (BQP) that is efficient for quantum physics but not classical physics, but this is all way beyond the scope of this writeup.   

Here is the bad news: there is no reason to believe that neuromorphic computing can provide a complexity class advantage over conventional computing.  That isn’t to say it is impossible (the brain has a lot of tricks), and learning and ubiquitous stochasticity muddy the waters quite a bit.  But there is no reason to believe today that a neuromorphic computer, implemented with classical components with real-world limitations, can provide complexity class advantage over conventional computing.  
I can always simulate the neuromorphic computer on a normal computer in, at worse, polynomial time.

The good news is that it isn’t complexity class win or bust. In between are **formal separations**; an algorithm or architecture that provides a polynomial or logarithmic advantage (or similar).  The approach doesn’t change the complexity class, but it does provide an advantage that can show scalable performance advantages beyond a certain problem size.  

So long as Moore’s Law was going strong there were not a whole lot of advantages to polynomial complexity improvements.  The microelectronics industry was giving us effectively exponential scaling through repeated application of constant factors that dwarfed any sub-exponential architectural improvements.  Moreover, for all but the most trivial workloads Amdahl’s Law would kick in eventually, meaning that as if you optimize one part of your calculation, some other computation would start to dominate the overall cost.  
And the ‘No Free Lunch’ theorem meant that you probably can’t simultaneously optimize all computations at the same time through architecture manipulation. Moore’s Law didn’t care about Amdahl’s Law and No Free Lunch; but any exotic architecture’s polynomial value sure did. So there.

Of course, Dennard Scaling (energy scaling of smaller transistors) stopped almost twenty years ago, and at this point Moore’s Law is really a marketing narrative.  The era of ‘free’ constant factors is over.  So suddenly those polynomial factors look good.  And while ‘No Free Lunch’ still applies, it is entirely realistic to hypothesize that there will be classes of algorithms for which neuromorphic computing may provide a polynomial win over Von Neumann computing.  

## How do we get to a formal framework for neural computing?

So why isn’t there a neat formal framework for neural computing?

A lot of answers come to mind, some cultural, some cynical.  Even the “time is never right” argument has validity: so long as Moore’s Law was going, no one really cared about something with at most a polynomial win, and now that Moore’s Law is over we have quantum that gets all the attention. 

But as I sat down to write this, I thought of a simpler answer that is probably true.  
If there is going to be a framework for neural computation, it probably needs to come out of neuroscience.  Von Neumann was a mathematician, as were most of colleagues who developed the stored-program architecture.  
The stored-program architecture, powerful and generic as it is, was developed in large part to solve the linear algebra systems that were developed in the preceding decades.  Feynman was a quantum physicist, as were most of his colleagues who first envisioned a quantum computer.  
As powerful as quantum appears to be, it was first envisioned as a way to solve quantum chemistry problems.

The value of theoretical computer science in both of these cases has been to abstract the computation away from its origins to understand it as something more generally powerful.  But the field itself has to define it.  
Theoretical computer science can only abstract a paradigm once its core primitives are defined. Is there a way to define neuromorphic computing that does not “bake in” all of the real-world baggage that today’s neuromorphic technologies, and for that matter the brain, carry with them?
