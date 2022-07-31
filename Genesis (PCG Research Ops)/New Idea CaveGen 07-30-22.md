# Project Genesis (Blackreach-Erebor and otherwise)
## New Idea For PCG of Cave[rn] Environments
### Written and Developed by Steven Eiselen, 07/30/22


## Introduction / Problem Definition

One of the issues I had with previous attempts at the PCG of cave environments is 'controllability' WRT a bunch of things related to the 'Trifold Principle' (namely: Physical Stability and Contextual Consistency), and WRT such for an 'entire composition of an environment'. For Examples:

* **WRT Perlin Noise:** It ironically suffers from its primary benefit, i.e. 'smooth and consistent-enough random noise'. The effects WRT 3D cave environments that I have noticed from my implementations in 2D, alongside those I've seen in 3D via my and especially others' implementations: are that relatively consistent yet individually random chambers are generated; most of which are disjoint from each other. Even if I grant that there may be configurations WRT the parameters of a multi-layer (i.e. octave) Perlin Noise implementation (e.g. lacunarity, persistence, etc.) alongside random offset and scaling values which *could* yield more realistic environments; we're still left with a less-controllable/defineable and infinite environment. Therefore, also ironically: such yields **too** much/random PCG. However, it was while considering the interesting (and satisfyable) individual chambers that Perlin Noise gen'd methods produce which got me to this new idea s.t. it remains a viable PCG method thereunto (more on that later).

* **WRT Cellular Automata:** It encompasses a somewhat similar scenario as with Perlin Noise; except we're tweaking CA episodic rules -vs- Perlin param values, and it is used alongside a random noise (possibly of the Perlin type) method which initializes the terrain state that the CA's then "munch away at" towards smoothing. Indeed, an idea I had for my 3D CA cave smoothing Unity3D project was to swap out the random noise code with a 'zoomed out' config of my 3D perlin generator as to generate a base Perlin Noise state, then use less-intense CAs to smooth it.

* **WRT Simulation/Erosion:** I had just last week come up with this method (unsure if it is novel at the time of writing this, though if I had to guess: likely not). It involves generating caves formed via the erosion of limestone layers via, appropriately and eponymously, simulating such. It would utilize a terrain generation method (e.g. Diamond-Square Algo WLOG) to construct a base "bedrock" layer (defined by a mesh xor heightmap, WLOG). I would then use either a fluid or particle system (else some simpler method WLOG) to "deposit" a layer of limestone upon this base layer to some thickness. Thereafter, I would cover this layer with a non-limestone/organic material type; encompassing things such as silt deposits over long timespans, erosion via nearby taller [bed]rock mountains, volcanic flows and deposits, etc. And even repeat the {limestone, other} deposit cycle a few more iterations (ergo layers). When done, I would run a water erosion simulation over what is ideally a nicely and naturally accurate overlap and exposing of layers between each other; such that the cavities formed by the erosion of some or all of the limestone form as real-to-nature a limestone cavity cave as nature itself can effect.

In all of these cases: I still get much more than I especially need vis-a-vis say a Blackreach-Erebor solution; and the amount that I do get is proportional to the detail that I stand to lose, and especially the control/tuning of the environments. I want the power of "raw low-level" terrain PCG methods for carving out the features of environments, but also the power to effect at least a high-level of direct control over what features such methods generate, how, and where. All this talk of features of a greater environment, and picking/choosing smaller components that I like versus hoping I get lucky with a 'perfect overworld'... Wait a sec: other PCG techniques might offer me a 'middle-of-the-line' 'best-of-both-worlds' solution here!


## 'Feature Graph Cave[rn] PCG Method'

(the usual 'desperately getting 1000 ideas to paper ASAP but am tiring quick' message, but will do what I can and TODO/TBD the rest)

A new method I want to try decomposes the process of generating a cave[rn] environment into two key aspects:
 * **Component Feature Generation** *(of individual 'parts' of the environment via Perlin/CA/other methods)*
 * **Composite Environment Generation** *(of Component Features interconnected with each other)*

The first aspect, **Component Feature Generation**, uses existing PCG methods to construct individual parts of the cave; from which I can define a bunch of abstract but still lower-level methods for various feature types, which encompass a set of modules that can be integrated within a switchboard or even blackboard architecture (see 'NOTE' below for deeper connections with AI/ML). For example: a list of features could include {'column hall', 'dome chamber', 'cone chamber', 'tube hall', 'column atrium', 'passageway' (connecting other features), etc.}; with 'decorations' thereupon which could include {'stalagtites/mites', 'open-to-the-sky', 'water body' ({pool, pond, lake, etc.} depending on adjacent definitions), etc.}. It does NOT worry about the greater environment it is part of nor anything outside of itself sans constraints defined by its counterpart aspect which inform it of how it must be generated WRT all adjacent features including the 'overworld' (i.e. above-ground world).

The second aspect, **Composite Environment Generation**, designs and composes the cave[rn] environment s.t. the features which may compose it are defined for and only known by this aspect via high-level "data node", "feature vector" definitions. IOW: it only sees the components it creates and connects as graphs in a node, not unlike Wonka et.al's "...Grammars for Procedural [Building] Architecture", Stava et.al's "Inverse Procedural Modelling Of Trees", and/or Merrell et.al's "CG Residental Building Layouts". This aspect is what not only designs and connects features, but what provides them with instructions on how to [seamlessly, ideally] connect with any adjacencies. Further, and as if not more exciting: this method supports being human and/or AI/ML driven, as each share and are compatible with the same general architecture. In fact, it works perfectly as a 'true procedural workflow' architecture vis-a-vis the human[s] manually creating some parts of a cave/dungeon/etc., then calling one or more ML model[s] / AI agent[s] to fill in the blanks; not unlike what the 'TerrainGAN' paper discussed.

Now We Can:
 * Generate and regenerate individual features, via one or more PCG methods, as much as we desire and/or until satisfied,
 * Save and Swap defined features, including human-modelled, as much as desired until satisfaction,
 * Constrain features to connect with their adjacent definitions (possibly more difficult WRt human-made models but still),
 * Plot-Out the environment at a higher level and either manually or via PCG craft the per-feature 'fine details' thereby,
 * Utilize AI/ML methods to 'fill in the blanks' WRT the features of an environment which were human-made or modified,
 * etc...