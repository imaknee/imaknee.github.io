---
title: "What is neuromorphic computing, and why should you care"
date: 2026-05-20
mathjax: true
categories:
  - Blog
  - Tutorial
tags:
  - Neuromorphic 
  - Framework
---
*To kick off this site, over a series of posts I am going to explain narratively the rationale behind the development of my proposed [neuromorphic computing framework]( https://arxiv.org/abs/2507.17886) and the implications of it. I encourage you to read the framework itself for the technical details and results.  This series will work to build towards a more conversational understanding of neuromorphic computing and how that relates to neuroscience, AI, and computer science in general.*

# Part 1: What is neuromorphic computing, and why should you care?

## The 'What', 'How', 'Who' and 'When' of neuromorphic 

The single biggest weakness of the neuromorphic computing field is that no one outside the field really knows what it is, and most everyone inside the field has their own opinions of what it is, generally centered on what it is they work on.  

At the NICE Conference earlier this year, a colleague asked the first end-of-day panel “What is neuromorphic computing?”  Groans could be heard through the audience.  I may have groaned myself.  Some panelists were a bit annoyed by the question, but they (mostly) answered it anyway. But the question was genuine, and the fact the question was asked legitimately speaks more than the answers themselves.  No other field would really have had this question asked at one of its main conferences, at least not unless it was asked as a prelude to some annoying philosophical tangent.  

At a coarse level, everyone agrees that neuromorphic computing is an ‘approach to computing that is inspired by the brain’.  The problem is that it falls apart rather quickly after that.  Pretty much every key word there can be challenged.  By ‘computing’, do we mean hardware, software, algorithms, sensors or processors or both?  By ‘brain’, do we mean the human brain? mammalian brains? any brain? cortex? or any neural circuit?  And let’s not even get started with ‘inspired.’

All this creates a mess.  And if the ‘What’ is a mess, the ‘How’ is a disaster.  I don’t even want to talk about that. We will save the analog vs digital conversation for another day. The ‘How’ is mostly self-serving opinions on all sides, which from my neuroscientist perspective is just better to ignore.

I will talk about the ‘Who’ and ‘When’ though.  Part of the problem with the ‘Who’ of neuromorphic is that since most of the field is academic; most researchers are largely focused on what they do individually and how it relates locally to those who review their papers and grants, and not really what other people do globally.  As a result, the neuromorphic field breaks down into somewhat isolated pockets of people making self-fulfilling claims.  For instance, I heard a famous neuromorphic researcher in a talk say that they had the only successful algorithm on neuromorphic hardware --- [a]( https://dl.acm.org/doi/abs/10.1145/3350755.3400258) [statement]( https://www.frontiersin.org/journals/neuroscience/articles/10.3389/fnins.2019.00260/full) [that]( https://ieeexplore.ieee.org/abstract/document/9291228) [is]( https://dl.acm.org/doi/abs/10.1145/3409964.3461813) [objectively]( https://www.nature.com/articles/s42256-025-01143-2) [not]( https://ieeexplore.ieee.org/abstract/document/9395703) [true]( https://www.nature.com/articles/s41928-021-00705-7).

The ‘Who’ has led to some funny quirks.  Until very recently neuromorphic did not have its own conferences or meetings.  It has long had workshops – specifically [Telluride]( https://sites.google.com/view/telluride-2026/home) and [CapoCaccia]( https://capocaccia.cc/) – which are from what everyone says great ways to spend a summer vacation.  But three weeks in the Rocky Mountains or two weeks in Sardinia are largely a luxury for academics and students.  Great things have come out of these meetings, and there is clearly an appeal of captive hackathons, but they’re not scalable in a way that can grow the field overall.

The ‘When’ challenge of neuromorphic is tightly coupled.  Neuromorphic exists across many timescales, but it is in everyone’s individual interest to communicate broadly that the relevant scale is whenever their particular approach will be mature.  Digital neuromorphic hardware is [available today at scale](https://www.nature.com/articles/s41586-024-08253-8), which is what algorithms researchers need; but again because the narrative that the hardware doesn’t exist yet is better for people asking for dollars to develop hardware, the messages sent to funding agencies and broader research community get diluted.  

All of this is to say that the signal in the neuromorphic field is currently too weak to overcome the noise inherent in any largely academic field.  This academic noise is rational from a game theoretic perspective – in a finite resource competitive game, it is sensible to elevate your own narrow piece at the expense of everyone else. But without the common messaging, the field is unable to transition to the broader growth state that is good for everyone and move the field out of this finite-resource competitive game.  So for the neuromorphic computing field to achieve success is critical to rise above this (largely) academic noise. 
Voltaire famously stated that the Holy Roman Empire was neither Holy nor Roman nor an Empire.  Well, you could easily argue that the neuromorphic computing field is neither “neuromorphic”, nor “computing”, nor “a field”.  
So given that neuromorphic computing flounders on the ‘what’, ‘how’, ‘who,’ and ‘when’ questions, is there a point?  Yes.  And it is because the ‘Why’ is so strong.

## Why we need neuromorphic computing

The ‘Why’ for neuromorphic computing is everything.  While not universally appreciated, the reasons are deep and fundamental.  But before we get there, it is worth discussing why neuromorphic is different than the types of computing we have today.

### What is computing today.

Arguably, neural computation is the only type of computation that occurs naturally. Lots of biology focuses on cells that exist to manipulate the organisms and the world around them.  Neurons exist specifically to manipulate information*.  This manipulation can be in the form of moving information from one location to another (communication), converting information from one modality to another (sensory-motor processing), or relating information to other information (memory, decision making, etc); but, in no uncertain terms, neurons perform computation.  
*Yes, nervous systems exist to manipulate the world along with muscles.  But they do this through neurons computing.*

Humans, in the last several centuries, have formalized how to do computation artificially. First through symbolic manipulation in mathematics, and then through computational hardware mechanically and then electronically.  The natural computation in our brains developed artificial computation external to us.  And while this natural and artificial computation both process information, they couldn’t be more different.

Things that develop organically are typically not optimized for interpretability and very often the driver of their development is not aligned to what someone today may expect. A great non-science example is the geography of cities.  While some are shaped by nature more than others, most U.S. cities are relatively planned compared to their European counterparts. American cities were designed with growth and transportation in mind, and it is far easier to drive a car into the heart of New York City than it is to drive around London.  Whether this is good or bad for society can be debated, but the thing is, no one would say Rome or Istanbul are any less of cities than Washington DC or Brasilia because they weren’t designed according to an engineer’s blueprint.  

Everyone knows this, but culturally this proves hard.  Because the computing fields largely come from engineering and math and not biology, there is a rather high barrier to entry for understanding an organically organized system. 

There are really only two widespread classes of computation that have clear and established frameworks: computation on Von Neumann (i.e., stored program) architectures (which I’ll refer to as conventional computing) and quantum computing.  Conventional computing is universal in its applicability and ubiquitous in its presence.  Quantum is more specialized in practice (though also universal in theory) but obviously is not widespread.  

Both of these approaches to computation are fully artificial, having been engineered with explicit purposes in mind.  The motivation of Von Neumann computing is widely appreciated today with its origins in the Manhattan Project during World War 2. While quantum leverages a different form of physics; it is still an artificially engineered construct; I am not aware of qubits “in the wild” implementing Hadamard gates.  Quantum computing was originally envisioned as a way to artificially simulate quantum mechanical systems whose equations prove intractable for conventional computation.  In both cases, the motivation for these established artificial computing paradigms has been modeling physics equations, but at some point along the way, people realized that such computers could do other things efficiently as well.

Other approaches to computing have been developed as well; WW2 and the years thereafter saw a bunch of computers developed for encryption and decryption, but while effective, these approaches did not readily translate to general-purpose use. The computers designed for physics could map to generic mathematical manipulations better than the other way around.  Similarly, there were many suggested approaches for quantum computing, but the general-purpose quantum circuit variety ‘won’ because it allowed the tools of computer science to be mapped to the framework.

## So why should we care??

Which brings us back to the ‘Why’ of neuromorphic computing and how to fix the field.  

In my opinion, there are two reasons to build a brain-like computing system artificially.  There is the Feynman quantum argument: by building a neuromorphic system in hardware we can gain a stronger foothold for understanding the brain.  It was only at NICE 2024, when Carver Mead won the Misha Mahowald Lifetime Achievement award, that I fully realized this is the original Mead vision for neuromorphic hardware.  

The neuroscience argument for neuromorphic hardware is not the same as the quantum computing for quantum chemistry argument, and I further believe the Carver Mead motivation should be updated in 2026.  Unlike quantum chemistry, there is no formal computational complexity reason that we cannot simulate neurons, or the brain, on conventional hardware.  While neuromorphic hardware is faster and less energy expensive to simulate neurons; we can still do it on GPUs and today’s supercomputers.  

The ‘why neuromorphic for neuroscience’ argument is more subtle than the Feynman argument.  

Evolution is tricky but suppose for a second that we can state that a neural circuit, N, in the brain exists in its form from an evolutionary genetic optimization to maximize the efficiency on some function, y=f_N(x).  The catch is we do not know what f_N(x) is.  This is clearly a simplification; as the brain has evolved through a multi-objective evolutionary optimization; but in general, this is probably a fair statement. 
Systems neuroscience, coarsely stated, can be described as trying to find f_N(x) through sampling many x’s and y’s and trying to find the f_N* that best fits the observed (x*,y*).  Until recent years, this leveraged fairly little knowledge about N itself (the neuroanatomy), but that is changing now with the connectome.

### Systems neuroscience
$$\min_{f} \sum \| y^* - f(x^*) \| \quad \text{subject to constraints of } N$$
The problem with the is that there are an infinite number of (f(x)) models that could fit that function, but most of them are not consistent with N.  The consistency with N is critical for why we are studying the brain in the first place: how do we get efficient computation, how to fix the brain, etc.   
Neuromorphic computing flips this around – it is the perfect complement.  Rather than being data driven (find a function that fits this data); neuromorphic algorithm development effectively is seeking which functions have minimal ‘cost’ on N.    

### Neuromorphic algorithms
$$\min_{f} \text{Cost}(N) \quad \text{subject to } f(x) \text{ yielding a valid/useful computation}$$

These two approaches are wonderfully complementary, combining the computation with the biology.   By merging these two perspectives; we can move away from static descriptions of the brain to something more functional; the equivalent of moving from the ‘genome’ to the ‘transcriptome’ and ‘proteome’ in cellular biology.

In my opinion, identifying the brain’s ‘computome’ is a pretty compelling ‘why’ (and in the future I will talk about this a lot more), but reasonable people can debate how to prioritize neuroscience research.  Besides, the urgency here is on years timescales; we’re all still young, right?

What cannot be denied is the urgency to fix computing’s efficiency problem.  

The amount of energy spent on computing and computing-adjacent systems is, frankly, stupid.  A quick back of envelope calculation can show that humans spend roughly the same amount of energy on external compute (data centers, edge devices, crypto) as humans spend on energy for brains. Even setting environmental concerns of ridiculous energy use aside, there is a lot of money unnecessarily being spent on scaling AI today. 

My undergraduate major is in chemical engineering.  I recall the exact moment I decided that I did not want to be a chemical engineer – it was in a senior design class, and I was pitching to make hydrogen by having algae photosynthesize water (a heretical idea in an oil-dominated Houston university).  I was told, either by the professor or by one of the oil industry judges, to stop trying so hard – chemical processed had been optimized to within 99% of their max efficiency, and even a fraction of a percentage improvement would yield millions of dollars in savings.  And I probably wouldn’t find such an advantage.

That individual was wrong (chemical engineering has been revolutionized in the last 25 years), but that kind of proves the point.  For big industries, efficiency gains are worth millions, if not billions, of dollars --- and they’re out there waiting to be seized.

This of course is a longer story as well.  But it is urgent in a different way.  Every day that goes by we are energy --- which has a direct monetary and climate and social value --- on unnecessary FLOPS that could be effectively free. Brains are not just a fraction of a percentage point more efficient, they’re orders of magnitude more efficient at the tasks we are training AI for today.  
So what is needed to sharpen focus on neuromorphic computing?  

Next time… 
