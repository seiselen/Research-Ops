# (Key Concept) PCG Method Groups and Workflows

## Overview and Introduction

It's important to distinguish between PCG methods which utilize Machine Learning (hereafter ML) versus those that do not, for the same reason why it's likewise important to partition Behavioral (i.e. 'Classic') AI from Machine Learning. This is especially directly the case in that there exists both a family of agent-oriented PCG methods (i.e. Behavioral AI), and another family of ML-oriented methods; though is generally the case WRT differences in algorithms, data structures, knowledge representation, and other features between such groups of similar methods. Of course: all of these seek to accomplish the game goal of PCG, and indeed many of the larger scale and 'more ambitious' ML methods / techniques / systems utilize a composite of various levels containing various individual generators from multiple such groups. While the textbook 'Procedural Content Generation in Games' provides a good contrast from some of the top experts in PCG, I will offer my own 'Quick-And-Dirty' definitions as follows; followed by the concept of 'Generator-Empowered Workflows' which can (and does) bridge these types together.

## Algorithmic-Based Content Generation

Basically - any content generation method that does NOT utilize ML, nor a trained network and/or generator, nor encompasses a dynamic agent. Uses 'fixed' algorithms and pre-defined / fully manually-tuned rulesets for content generation, and typically encompass offline algorithms.

## Agent-Based Content Generation

Does NOT utilize ML, nor a trained network and/or generator, but does encompass some kind of dynamic agent(s) and/or groups thereof to actively generate content as 'creatures physically interacting with it' within a simulation. Can utilize both offline and online algorithms (i.e. terrain/vegetation erosion agents)

## ML-Based Content Generation

Uses ML via a trained network and/or generator, which in turn utilize manually-tunable high-level rulesets (i.e. hyperparameters) on training examples (via offline and/or online algorithms) to tune low-level weights (i.e. network) as to inform some model representation to perform the requested task.

## Generator-Empowered Workflows

Generator-Empowered workflows encompasse combining multiple types of the above methods towards a greater implementation, for which there is a great example in the 'Terrain GAN' paper and its implementation. The system utilized ML-based methods to generate the base terrain, and then utilized algorithmic-based method to effect erosion upon the generated basic terrains as a post-processing step. As a side note: careful modularity and common interfacing between method types and their interconnections across a 'generator pipeline' could accommodate the ability of 'switching and swapping' between multiple types of multiple kinds of module 'tools'; in a manner similar to how the A* search algorithm could be programmed to swap between use of Euclidean xor Manhattan distance as the distance heuristic for its informed goal data.
