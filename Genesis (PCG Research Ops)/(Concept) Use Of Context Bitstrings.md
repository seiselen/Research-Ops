
# On The Use Of 'Context Bitstrings'

## Overview

Alex Koltz recently *(i.e. Fall 2019 or Spring 2020 semester)* reminded me about the technique of using bitstring hash codes as a knowledge represenation encoding for newly generated (i.e. 'On Init') environments as to effect some degree of persistence (i.e. stays the same post-generation ergo does not *fully* regenerate). I was discussing focusing my Master's Thesis project on bridging the *building interiors* generation layer with the *buildings* layer i.e. **(Building Interiors | {Buildings ∧ CCDB})** as part of the greater multi-layer world generation idea *(05/31/22 note - I'm likely referring to the **'Blackreach-Erebor'** project here). 

The context by which he reintroduced the idea was to allow such interior spaces, once generated, to remain persistent thereafter; as I am also interested in means by which to both support contextual consistency and even enable collaborative discovery and 'as-explored' generation (which would correspondingly realize a world implicitly shared among single players of a particular virtual environment in addition to one explicitly shared as by a MORPG). An immediate extrapolation is to offer persistence such that the static geometry perists unchanged alongside a contextual definition for the interiors' props and NPCs which is subject to modification (e.g. swapping out NPCs and loot items over time as per E.S. Oblivion).

***01/05/2020 Update**: The main if not only purpose of this would be to compress the 'contextual definition' of the generated content; both in terms of its static definition (i.e. "this is a grocery store") and dynamic/unique definition (i.e. "it was looted", "it was overrun with zombies at some point").*

## Example Case

For example of a contextual definition, an encoding could represent the request:
> This interior space represents a floor within a modern hospital building. It is composed of bedrooms, nurse's stations, and other types of rooms consistent for a modern hospital. Generate this space and its props to be consistent with adjacent floors/environment; and consistent with being an emergency triage center that was recently overrun during a zombie apocalypse scenario"

as for the system to 'intelligently' scatter loot and other items throughout the area corresponding to hospital rooms, labs, custodial equipment, etc. while placing zombie NPCs such that most are in the form of zombie nurses, orderlies, doctors, paramedics, patients, and other types that would be expected in a hospital floor. Generating the actual geometry of the rooms is a somewhat more involved item; but TL;DR - it's also techically possible to represent such via bitstrings, but that's out of scope for this document.

## Issues / Challenges / Questions

* Mostly encompasses how such compression and reducibility could be done and to what degree. 
* As aforementioned: the geometry can less easily be encompassed in a bitstring. However, there might be merit in perhaps implementing a **(geometry, context)** data-pair wherein **{geometry}** is unavoidably a mesh generated at-initialization, while **{context}** represents both the 'seed' which constructed the geometry as well as the encoding for how and what could be placed into the environment. So we fully persist the geometric "walls floors ceilings" definition, but contextually persist what gets placed within. And given the polygon costs of even 'game-ready' props, this arrangement actually saves much of the required model storage needed. Furthermore, we could actually persist prop placement … via only keeping a **'Transform,ObjectID'** entry in some data structure associated with the environment!

Thus: The Classic 'Sales Pitch'

> **We will allow you to explore all 60 floors of an office building or however many you have the time and patience to explore, even though the developers only designed the building's exterior *(if even that - but that's a different PCG method!)* We will also guarantee that, once generated, the geometry of the 48th floor of this building will stay the same the next time you visit it, as well as some of the objects placed therein. Correspondingly: we need to procedurally generate the geometry for each floor, and the client (you) must store the geometry created and consequently incur the data costs thereof; but you could choose whether of not the prop items placed within are also saved as *(Transform,ObjectID)* pairs, and we encode the context of what this floor represents in a bitstring versus some larger data representation.***
