# Project : Blackreach-Erebor
### Procedural Content Generation of 3D Environments for Interior Spaces
Steven Eiselen | Version 06/01/22
---

## Introduction / Overview

***Note:** This is currently an inactive research project, as well as a candidate for my since suspended Master's Thesis Project.*

**Blackreach-Erebor** (hereafter BE) encompasses the Procedural Content Generation (hereafter PCG) of interior spaces within highly detailed, realistic, and immersive 3D simulations *(e.g. 'video games' - though I prefer not using that word as these kinds of simulations can be as disjoint from Skyrim as Skyrim is from Pacman)*. Given geometric definitions for any adjacent exterior space(s) in addition to all connections thereof, a contextual definition of what kind of space to generate, and a content database from which to generate the space with: correct methods would produce outputs that both satisfy the input context, 'fit within' (i.e. WRT) the exterior space(s), and 'correctly' connect with exterior access points WRT their data and geometric representations.

**Put more simply:** The goal of BE would be development of methods and tools that would allow the developers of some 3D 'video game' simulation to procedurally generate interiors for everything from houses, to skyscrapers, to dungeons in such a way that the interior spaces ‘fit within’ the exterior structures and terrain, as well as connect to them via entrances and exits. Even if, for example: the interior of a 10 story office tower is in a different ‘scene’ than the exterior within the overworld: the mesh geometry would match; such that if the two parts were brought into one scene, and aligned: they would match up seamlessly. Even down to the windows matching up.

**A greater idea/feature of this work** encompasses the ability to interconnect a new space with other interior and/or exterior spaces at-creation; which supports the powerful concept within **'greater Project : Genesis'** of generating complex composite internal environments. Such environments can encompass the above-ground vertical stacks of floors within a skyscraper, the below-ground labyrinths of chambers and hallways within a dungeon, and the greater composition of both and with adjacent structures: as is the case for modern high-density city centers as much as ancient cities / castle towns; and for modern university campuses as much as ancient temple/citadel complexes. Three more specific descriptions and/or additional examples are:

* The floors of a skyscraper: such that each floor fits inside the exterior tower, has window openings matching thereof, and connects with other floors;
* The basement of a multi-building campus: such that it is arranged ‘neatly’ below the buildings, within the campus bounds; and
* The vast web of halls and chambers composing an ancient Dwarven city within a mountain: such that there are multiple entrance points along the mountainside which correspond geometrically to their pairs encompassing the city; and no parts of the city overlap onto the surface, other structures which happen to exist above or beneath the surface, and especially onto itself.

**Another greater idea/feature of this work** encompasses the likewise (if not corollary) ability to generate these areas both **'offline'** *(i.e. before the simulation is initialized, executed, and 'run')* as well as **'online'** *(i.e. 'on-the-go' or 'at-runtime' as the simulation is being traversed by both human players and NPC characters)*. This yields a VERY interesting means (and reseach question itself) for generating ***some*** of the world as **"on-demand and likely unique 'filler content'"** that is not directly created nor designed by the developer: created only when requested (i.e. via a player of some post-apocalypse RPG who *really* wants to explore every room in all 60 floors of some downtown building); while the ***remainder*** of the world was designed and created ahead of time, thus with the exception of minor things like random loot/object placement and other random events: will otherwise be non-unique shared content.


## Origin Of Name

**'Blackreach'** is a Dwemer (Dwarven) City located beneath the Province of Skyrim within the 'Elder Scrolls' universe. **'Erebor'** is a Dwarven City located beneath the Lonely Mountain from the 'Lord of The Rings' universe. Each had its builders and original inhabitants displaced such that they were both effectively ruins. Their size, scale, and similar outcomes compose perhaps the greatest depictions of the classic 'dungeon' environment known well to any video game and fantasy fiction fan, and this quality is why each compose the names of this project.


## Common Methods Identified Via Precedent Research

**Include:**
* **Convex Hull Generation** and other Computational Geometry methods for identifying the 'build zones', collision areas, etc.
* **Spatial Partitioning** for defining rooms within the 'build zones'

* ***Shape* Grammars** for defining the multi-layer prefabs, as to support variability. That is: the ability to stretch/alter the prefab definition to fit into a defined space; e.g. how the wonka building generator paper supports dynamically modifying building widths and floor heights s.t. the prefabs follow along and fit/correspond therein.

* ***Prefab* Grammars** for *installing* multi-layer prefabs upon the 'build zones'. The word **installing** is very fitting here: as it nicely encompasses my idea of the primitive geometry of the 'build zone' as some hollywood studio kind of basic box-shaped warehouse from which to then assemble and install the various sets for a movie scene.

* **Circle Filling** (e.g. Poisson Disk) and **Square Filling** (e.g. [Blue] Noise) Algorithms (as well as aforementioned methods) to place static and dynamic props.


## Key Quality of Wonka 'Hierarchical Composition Tree'

A key quality of Wonka's 'Hierarchical Composition Tree' method in the *'Interactive Visual Editing of Grammars for Procedural Architecture'* paper WRT both BE and PCG in general is that it **supports a multi-layered built-in LOD with the possibility of an expanded variety of uses**; of which include:

* **LOD for rendering purposes** i.e. rendering lower quality versions of models from a distance; and this could be a convenient if not novel way of efficiently culling models from certain layers as well as combining lower-rez models composing multiple layers into a single model (i.e. single model at LOD-3 is low-res version of its LOD-3, 4, and 5 correspondence);
* **LOD for data-size organization and composition of levels** vis-a-vis approaches described by the paper; such that...
  * At-Present: via the SWEET ability to author geometry within certain layers versus worry over the highest rez geometry of layers below *(i.e. represent the art-deco glass and steel facade of a skyscraper as toon-shared quad primitives that can be stretched and modified much more easily when sculpting the building, while auto-generating the subsequent layers nicely)*.
  * In-The-Future: determining the maximal potential towards using this compositional tree to represent an entire level (perhaps as a graph). Could this massively improve rendering, pathfinding, PCG, etc. abilities more than a discrete per-instance definition or other existing 'chunking' methods? Basically: Express an entire dungeon as a 'sea of nodes' similar to how Wonka expresses a skyscraper.


## (11/2019) Notes On Initial BE Algorithm / Details Thereof

**(1) Define 'Externally-Defined Bounds'** as set of Convex Hulls encompassing a uniform offset from the corresponding external geometry. For example: the 'Dungeon in the Mountains' case would receive a mesh corresponding to the mountainous geometry offset by, 50 feet (of rock and WLOG) from which its entrance connects to its exterior counterpart; as well as perhaps a mesh/octree representation of any predefined geometry such as caverns and existing dungeons. The 'Basements in the City' case is analogous; such that the boundaries correspond to the streetscape, existing basements of other buildings (and their connections A/A), subway tunnels and utility corridors, etc.

**(2) Commence initial 'Primitive Geometry Carve-out'** of prospective interior space as another set of convex hulls which effectively corresponds to a 'feasibility region' for where the architecture is 'allowed' to be generated; AKA: **define the 'can-build/generate zones'**. This primitive definition could also be kept for future interior spaces, culling spatial partitioning, etc. as to 'not waste the info'. In any event: via this definition - more refined/detailed candidates can now be generated. Another intermediate process that needs to be discussed is defining geometry for the connections to exterior areas and/or separate interior spaces (A/A to where connections exist and are defined, of course).

* **Side Note:** This could be an application of what I saw in the 'Generative Building Architecture' Wonka-Paper in terms of representing the generated space in a model heirarchy as to support both LOD, and more importantly: easier editing of the space WRT some 'level' thereof. For example: speaking for the room layout of a room before worrying about the installation of prefabs for the walls, floors, etc.

**(3) Commence 'Architectural Generation' of interior space**. This is the *'Big Realization of (Shape) Grammars'* step; and encompasses using 'architectural words, sentences, and songs' in a Shape-Grammar method to install all the prefabs corresponding to all of the interior architecture; e.g. walls, floors, ceilings, doors, stairwells, etc. This was AKA 'swap[ping] the primitive geometric definitions with architectural prefabs', which is also analogous to the Wonka 'Generative Bldg Architecture' paper's high-level methods. Another prospectively novel idea is to incorporate damage modifications into the language, as to support stuff like “produce a partially damaged colonnade” within the generator hierarchy; else some otherwise damage sim to the geometry, as would be necessary for an online, physics-oriented,  and persistent destructible geometry.

**(4) Commence Micro-Architecture Generation and Prop Placement**. An extra step that I'm more convinced should be included in my method: either a different generator (or possibly the same hierarchy) could then generate smaller scale architecture and props (Now THIS is an interesting idea). The former would include loose wires, spiderwebs, pipes, static animated props (e.g. boilers, generators, gearworks, etc.), etc. The latter would include everything from trash bins and chairs to welkynd stones and food.


## (11/2019) Notes On Prospective Novelty Of BE

**The prospective novelty of my emergent approach/methods involves the expansion and composition of known PCG methods** *(naturally, as isn't this much of the frontier of research in Computer Science?)* I would be adapting existing methods 'outwards'; for example: using Wonka's shape grammar/tree methods for generating the exteriors of buildings *(i.e. 'Interactive Visual Editing of Grammars for Procedural Architecture')* towards generating the interiors thereof. I would be adapting existing methods 'inwards' via continuing the 'generative tree' definition towards deeper leaves/layers ergo 'continuing the expressveness of the language'. These improvements would encompass things ranging from procedural damage modifiers (as perhaps deformation maps); to 'micro-element props' such as static lighting fixtures against a wall (and code supporting the light); and/or dynamic props such placing fire hydrants in their geometry-defined boxes within a wall, and/or loose, destructible pipe and wire models connecting geometry-defined I/O wall prefabs *(think DooM 3 labs and/or Skyrim's Dwemer ruins)*.
