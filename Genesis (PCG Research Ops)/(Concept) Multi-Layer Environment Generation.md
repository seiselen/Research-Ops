# Concept: MLEG (Multi-Layer Environment Generation)

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
  * If a request is made after going through all of the generation steps in which come region containing a landlocked city and surrounding suburbs/towns must now have a giant river running through it, a big lake within it, and be covered/surrounded by a bunch of smaller hills: this will self-evidently require a bunch of edits down the chain - which might in turn lead to upwards edits; and we can see how crazy things might get - and not many other options (naïvely) availavble otherwise besides potentially completely regenerating the lower levels (as is the case with many current/existing methods).

## Answers To Questions

* **One Idea: 'Downwards Generate - Upwards Edit':** Fits with the 'classic-model' of similar muilti-layer PCG methods in that we basically start with generating the terrain, then add roads, then blocks, buildings, etc. When **and only when** a lower-level generation phase requires an upper-level edit (i.e. in the corresponding aforementioned scenarios), then re-edits towards restoring consistency can occur **only up the chain**. The generator may or may not have **right-to-reject)** by which it detects and forbids a lower level edit which might significantly change an upper-level and/or require changes to multiple levels.

* **Another Idea: Guided aka 'Wizard' Editing:** Following from the immediately aforementioned point, there is a system or even an agent within the generator program which 'shepherds' generation down lower levels as to identify and warn if not prevent potentially degenerate actions; and possibly even likewise warn about actions  which might tightly restrict/constrain 'freedom of generation' in lower levels such that the likelihood of an inconsistency therebelow is at or above some error threshold. An example of this is an infrastructure 'shepherd' which identifies the need to expand a 2-lane default road hugging a mountainous terrain into an 8-lane highway due to the mountain containing a large city at its foothill: thus needing terrain editing.

* **'Inter-Layer' Authoring System:** My notes have a kind of alternate wording to the immediately aforementioned idea which I want to retain: *"(such a system) would 'guide' world construction. Why not think of the city generation step(s) as being part of a process in which generation oscillates up and down the layers throughout the authoring process?"*

* **Did Somebody Say Peter Wonka?** Regarding the aforementioned: I am pretty sure that the Wonka Shape Grammars research paper(s) did implement upwards editing with their building generation method as well as possibly their tree generator methods.

## Precedent and Ideas:

* This ideas extends the current work done on composite environment generation, most of which were the city generator papers of which have implemented a 1-3 layer process (but I don't think anyone has gone all the way with a full 5-Layer Generator yet). The definititive method among such precedent that immediately comes to mind is **'Citygen'** as described in George Kelly's MS Thesis *'An Interactive System for Procedural City Generation'*; as well as the methods discussed in his paper with Hugh McCabe *'A Survey of Techniques for Procedural City Generation'*.

* I had another note involving ideas for my own MS Thesis as follows:
  * *Procedural Generation of high-detail 3D environments utilizing ML and a collection of other techniques to define and implement a 'Converged Workflow' which encompasses all stages of the greater process.*
  * *A specific topic could then be an analysis for how to combine all 'macro' and 'micro' components / aspects of procedurally generated environments into a single theoretical and (hopefully) applied model.*
