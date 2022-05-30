# Project : Blackreach-Erebor
### Procedural Content Generation of 3D Environments for Interior Spaces
Steven Eiselen | Version 05/29/22

---

## Introduction

### Abstract/Overview

***Note:** This is currently an inactive research project, as well as a candidate for my since suspended Master's Thesis Project.*

**Blackreach-Erebor** (hereafter BE) encompasses the Procedural Content Generation (hereafter PCG) of interior spaces within highly detailed, realistic, and immersive 3D simulations *(e.g. 'video games' - though I prefer not using that word as these kinds of simulations can be as disjoint from Skyrim as Skyrim is from Pacman)*. Given geometric definitions for any adjacent exterior space(s) in addition to all connections thereof, a contextual definition of what kind of space to generate, and a content database from which to generate the space with: correct methods would produce outputs that both satisfy the input context, 'fit within' (i.e. WRT) the exterior space(s), and 'correctly' connect with exterior access points WRT their data and geometric representations.


**Put more simply:** The goal of BE would be development of methods and tools that would allow the developers of some 3D 'video game' simulation to procedurally generate interiors for everything from houses, to skyscrapers, to dungeons in such a way that the interior spaces ‘fit within’ the exterior structures and terrain, as well as connect to them via entrances and exits. Even if, for example: the interior of a 10 story office tower is in a different ‘scene’ than the exterior within the overworld: the mesh geometry would match; such that if the two parts were brought into one scene, and aligned: they would match up seamlessly. Even down to the windows matching up.

**A greater idea/feature of this work** encompasses the ability to interconnect a new space with other interior and/or exterior spaces at-creation; which supports the powerful concept within **'greater Project : Genesis'** of generating complex composite internal environments. Such environments can encompass the above-ground vertical stacks of floors within a skyscraper, the below-ground labyrinths of chambers and hallways within a dungeon, and the greater composition of both and with adjacent structures: as is the case for modern high-density city centers as much as ancient cities / castle towns; and for modern university campuses as much as ancient temple/citadel complexes. Three more specific descriptions and/or additional examples are:

* The floors of a skyscraper: such that each floor fits inside the exterior tower, has window openings matching thereof, and connects with other floors;
* The basement of a multi-building campus: such that it is arranged ‘neatly’ below the buildings, within the campus bounds; and
* The vast web of halls and chambers composing an ancient Dwarven city within a mountain: such that there are multiple entrance points along the mountainside which correspond geometrically to their pairs encompassing the city; and no parts of the city overlap onto the surface, other structures which happen to exist above or beneath the surface, and especially onto itself.

**Another greater idea/feature of this work** encompasses the likewise (if not corollary) ability to generate these areas both **'offline'** *(i.e. before the simulation is initialized, executed, and 'run')* as well as **'online'** *(i.e. 'on-the-go' or 'at-runtime' as the simulation is being traversed by both human players and NPC characters)*. This yields a VERY interesting means (and reseach question itself) for generating ***some*** of the world as **"on-demand and likely unique 'filler content'"** that is not directly created nor designed by the developer: created only when requested (i.e. via a player of some post-apocalypse RPG who *really* wants to explore every room in all 60 floors of some downtown building); while the ***remainder*** of the world was designed and created ahead of time, thus with the exception of minor things like random loot/object placement and other random events: will otherwise be non-unique shared content.
