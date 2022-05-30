# Project : Blackreach-Erebor
### Procedural Content Generation of 3D Environments for Interior Spaces
Steven Eiselen | Version 05/29/22

---

## Introduction

### Abstract/Overview



A Steven Eiselen Concept (and Master’s Thesis Proposal) 


“Blackreach-Erebor” (hereafter BE) is a now inactive research and development project focused on the Procedural Content Generation (hereafter PCG) of interior spaces within 3D simulations (e.g. video games). Given geometric definitions for the corresponding exterior space[s] and any connections thereof, a contextual definition of what kind of space to generate, and a content database from which to generate the space with: correct methods would produce outputs that both satisfy the input context, ‘fit within’ the exterior space[s], and connect to exterior access points in terms of both their data and geometric representations.


Put more simply: the goal of BE would be development of methods and tools that would allow the developers of some 3D game to procedurally generate interiors for everything from houses, to skysrapers, to dungeons in such a way that the interior spaces ‘fit within’ the exterior structures and terrain, as well as connect to them via entrances and exits. Even if, for example: the interior of a 10 story office tower is in a different ‘scene’ than the exterior within the overworld: the mesh geometry would match; such that if the two parts were brought into one scene, and aligned: they would match up seamlessly. Even down to the windows matching up.


The ability to interconnect a new space with other interior and/or exterior spaces at-creation further supports the powerful concept of generating complex composite internal environments.


the generation of composite interior scenes, for which there are two main types. Above-ground floors interconnected mostly vertically which compose the interior of a vertically-oriented exterior (i.e. of a skyscraper), and below-ground floors composing the interior of a vertically-oriented exterior


 and interconnected below-grounf


There are three good examples of use-cases which  the goal of these methods which correspond to the two identified major use cases of (1) interconnected above-ground floors which together compose a horizontal structure, and  and below-ground basements


Thus, BE methods could be used to generate environments ranging from:

The floors of a skyscraper: such that each floor fits inside the exterior tower, has window openings matching thereof, and connects with other floors; to
The basement of a multi-building campus: such that it is arranged ‘neatly’ below the buildings, within the campus bounds, and no parts overlap onto the surface; to
A vast ancient ruin (a.k.a. “dungeon”) within a mountain: such that there are several entrance points along the mountainside, and no parts overlap onto the surface.
