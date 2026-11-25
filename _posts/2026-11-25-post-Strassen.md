---
title: "Strassen, AI, and neuromorphic?"
date: 2026-11-25
mathjax: true
categories:
  - Blog
tags:
  - Artificial Intelligence
  - neuromorphic
---


I don't have anything clever to say about Navier Stokes or the Riemann Hypothesis. To me, the former is a hard for simulation computational physics problem (I don't care about the math stability / instability) and the latter is one of those "I've read about it on Wikipedia when glancing over the Millennium Prize problems, shrugged, and moved on." I know some mathematicians want to spend their lives chasing prime numbers, I know they generally don't ask for a lot of money to do that, and so that's all fine by me. We all get our kicks somewhere. 

But I do [have a paper on Strassen multiplication](https://arxiv.org/pdf/2006.14652), which apparently got an [AI-assisted lower bound yesterday](https://github.com/openai/math/tree/main/preprints/The-matrix-multiplication-exponent-is-nine-fourths-November-24-2026), and I have spent time thinking about that problem. I've also had reviewers tell me "you should come up with something Strassen-like if you want to make neuromorphic interesting," which was both ironic (since I have a neuromorphic-like Strassen algorithm) and kind of a high bar for feedback for a paper.

Anyway, if you don't know the [Strassen algorithm](https://en.wikipedia.org/wiki/Strassen_algorithm), you should go look it up right now. It's clever; and I mean clever in the "this is what computer science / applied math should be doing" sort of clever, and not in the "I wonder if there is a nice way to know if 5,362,416,575,611 is prime" sort of way. We live in a world where *everything* is a matrix multiplication in one form or another, so making that cheaper and more efficient seems important.  At the same time, people don't use Strassen in real life because the constant factors kill you, or something like that.  

Anyway, this AI kerfuffle about math, and my Strassen experience, makes me wonder three things

1 - Proving bounds is different than identifying the insight in the first place.  And I'm still not convinced that AI has the capability of figuring that sort of trick out in the first place.  Still haven't read about Strassen yet?  Well, here is the simple neuroscientist description for you.  Say you have two matrices of the same size, $A$ and $B$.  Even easier, let's say you have a single matrix, $A$ of size $n \times n$, and you want to square it $A^2$.  Then multiplying $A$ by itself, naively, requires $n^3$ operations. This is easy to see: every row ($1 \times n$ elements) times every column ($n \times 1$ elements) is $n$ pair-wise multiplications, and there are $n$ rows and $n$ columns. 

At first glance, how can you simplify that?  There are obviously $n^2$ elements you have to write in the product matrix, so you cannot possibly do lower than $n^2$ operations.  But can you get by with fewer than $n^3$?  Well, turns out you can.  Strassen realized that once you've done most of the piece-wise element multiplications, some of the multiplications are entirely determined. Specifically, he realized that for a $2 \times 2$ matrix, you can do 7 of the 8 original element-wise multiplications and add and subtract them in different combinations to fill in the resulting $2 \times 2$ product. This $2 \times 2$ trick can be done recursively, and so you can get away with $O(n^{2+\epsilon})$ multiplications.  


2 - Once you make that insight, there is a lot of headroom for improvement.  Going from $O(n^3)$ to $O(n^{2.8})$ isn't a huge savings if the constant factor is enormous (which it is).  None the less, since Strassen, every so often someone would identify some other schedule of combinations to make things a bit better, a lower $\epsilon$. The AI-result is that the lower bound is $O(n^{9/4})$, which is bigger than $O(n^2)$, but kind of in the area of where the incremental improvements were approaching empirically.  So I'm guessing we haven't really learned a lot theoretically here; like the other results, the AI is telling us something that we all kind of would have known.      

The thing is, the constant factors matter. And overcoming those probably will require some level of insight beyond just proving some asymptotic bound. But this kind of revealed to me the nature of what a lot of pure math and theoretical computer science research is. Some brilliant person comes up with a trick, something truly innovative and kind of mind-blowing. And then for decades people poke and prod at that trick until finally someone says "this is how far this trick gets you".  


3 - This was a long time ago, and fast multiplication algorithms have been around a while and people still largely don't use them. There are a few reasons for this; the constant factors are part of it - if you save 10000 multiplications but have to do 100,000 additions, did you save anything? There are also economic and social pressures away from using them: the LINPACK benchmark for supercomputers?  Not allowed to use fast multiplication algorithms. I got into a fight once with someone who does Top500 about this; they aren't budging. But ultimately, the big issue is architectural. 

As Nvidia knows, the beauty of straight linear algebra is that it is structured and homogeneous. Think about the vanilla matmul problem - $O(n^2)$ rows and column multiplications.  Same operation repeated many, many, many times.  Well, if I have a SIMD architecture that has memory and routing structured to allow me to do that vector product efficiently and I can parallelize it to my heart's content since every row/column operation is independent and identical, then why do I want to mess with that?  Straight linear algebra is really really good on GPUs, the brilliant folks at Nvidia and AMD have co-designed their software stacks and architectures to be increasingly effective at doing that, so why mess with it?   

Strassen messes with this at its core. Every element of the product matrix now has a different formula. In the conventional formulation, there is recursion but of different sized matrices. It takes a simple SIMD-friendly algorithm and makes it extremely SIMD-unfriendly.

This is where my little dabble in Strassen came into play. Years ago, I had a chance to work with Ojas Parekh and Cindy Phillips (two very smart computing theorists), and we looked at how Strassen could map to threshold gates, which are basically like neurons without time (high fan-in/fan-out; binary activations; etc). Our paper showed that you can map Strassen to constant-depth threshold gate circuits; basically by using threshold gates, you can compress all of those intermediate additions and subtractions into a few layers rather than relying on recursion to get to the larger network.  In effect, trading off extremely simple operations for fewer more complex operations; something we *know* the brain is doing and we really need to figure out how to take advantage of in neuromorphic algorithms.

Again, not the most useful algorithm given that the vanilla operation on the GPU on my home desktop can outrace Strassen on any neuromorphic system, but it is useful to illustrate the difference in philosophy. There is a value for being homogeneous, and a value for being heterogeneous.  We are only now getting architectures that can accelerate the heterogeneous.

Anyway, that is my Strassen story. It's mostly interesting to me because it just shows how few truly innovative algorithms there are, and it just highlights to me that there is a difference between finding and proving bounds and doing something truly novel.
