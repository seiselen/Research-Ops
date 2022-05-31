# Key Concept: 'Multi-Layered Environment Generation'

## Blurb/Overview

One of the most interesting and important concept whose methods and implementation cases I've studied and found to merit if not demand further discussion is what I call **'Multi-Layered Environment Generation'**. One of the best way to explain this concept is to describe a general algorithm for what an entire process whose 'layers' author a completely detailed environment could entail, which is done as follows...

## Algorithm

Given **'CCDB' *(Context and Content Database)*** as an input (composed of 3D models, shape grammars, other multimedia assets, and all design / specification assets) which describes and defines some simulation environment: generate a **Physically Stable and Contextually Consistent** output **'world'** of layering order: **({{Terrain → Roads → Blocks → Lots → Buildings} ∧ {Props}} | CCDB)** as generated in the following (primary) sequence:

* **(Terrain | CCDB):** Generate terrain given the input context, including terrain erosion and preparatory steps for 'fitting' contextual content thereupon.
* **(Roads | {Terrain ∧ CCDB}):** From the generated terrain and input context: Generate roads and networks thereof. This could include any type of navigable path from natural trails to railroads and interstate highways.
* **(Blocks | {Roads ∧ CCDB}):** From the generated roads and input context: Generate blocks adjacent to the roads upon which structures could be placed (e.g. s.t. blocks are typically generated at the intersections and edges of roads).
* **(Lots | {Blocks ∧ CCDB}):** Partition the blocks into individual lots e.g. on which buldings could be placed.
* **(Buildings] | {Lots ∧ CCDB}):** Place buildings (and other structures, too) upon the lots. This step could imply an 'upwards edit' s.t. lots are merged to fit larger buildings.

**{Props}** refers to 'prop items' i.e. all kinds of smaller stationary objects e.g. *{trees, plants/flowers, traffic lights, books, bookshelves, coffee cups, coffee machines, small rocks, gemstones, and everything in between}*. Their generation within this greater process is an open question discussed immediately below...

## Questions

* **Inter-Layer Nature Of {Props}:** There are props corresponding to each layer, such as: traffic controls for roads; trees for terrain and lots, furniture within buildings, dumpsters adjacent to buildings, etc. However if we allow changes to be made anywhere within the greater process - these props will likely need to change correspondingly else risk violating contextual consistency or worse! Ergo, as There is a clear interrelationship between edits to a layer and prop validity for all props placed in all layers: how would this work?
* **Inter-Layer Nature Of !{Props}:** Beyond props needing to be correctly populated WRT generating the other layers, it will be the case that the generation of lower-level content becomes inconsistent and even degenerate else otherwise insufficient unless edits can be made upwards; and an analogous situation if vice-versa edits are permitted. For example:
  * It might be necessary to modify the terrain to accomodate a highway or railroad in the lower **{Road}** generation step (which may also require 'cutting down' vegetation props generated in the terrain step (depending on the prop generation method, WLOG);
  * It might be necessary to modify a street layout to make some custom planned and/or spontaneously requested building on that street feasible, which depending on the state of the upper layers might effect a multiple layered edit step from lower to upper layers;
  * If a request is made after going through all of the generation steps in which come region containing a landlocked city and surrounding suburbs/towns must now have a giant river running through it, a big lake within it, and be covered/surrounded by a bunch of smaller hills: this will self-evidently require a bunch of edits down the chain - which might in turn lead to upwards edits; and we can see how crazy things might get.

## Answers To Questions

* **One Idea: 'Downwards Generate - Upwards Edit':** Fits with the 'classic-model' of similar muilti-layer PCG methods in that we basically start with generating the terrain, then add roads, then blocks, buildings, etc. When **and only when** a lower-level generation phase requires an upper-level edit (i.e. in the aforementioned scenarios), 
* 
* 
* The example above discusses the idea of lots being merged in the building generator step in order to increase possible building footprints; and another example across multiple layers is a infrastructure 'shepherd' system which identifies the need to expand a 2-lane road into an 8-lane highway in especially hilly terrain: thus needing terrain editing.

        [a]Actually - this is the answer to these questions. 'Inter-Layer' Authoring systems which 'guide' world construction. Why not think of city generation e.g. as a process in which generation oscillates up and down the layers throughout the authoring process?

        [b]Also - I believe the Wonka Shape Grammars research did implement upwards editing with their building and maybe even tree generators


Precedent and Ideas:

Extends the current work done on composite environment generation, most of which were the city generator papers of which have implemented a 1-3 layer process (but I think nobody has gone all the way with a full 5-Layer Generator yet).

Procedural Generation of high-detail 3D environments utilizing ML and a collection of other techniques to define and implement a 'Converged Workflow' which encompasses all stages of the greater process.
A specific topic could then be an analysis for how to combine all 'macro' and 'micro' components / aspects of procedurally generated environments into a single theoretical and (hopefully) applied model.


