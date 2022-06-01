# LOA (Level Of Authoring)

## Overview: 

LOA is my attempt to define and speak about the 'guidance' by which PCG generates environments, especially pertaining to human involvement (i.e. 'authoring'). A technique could use one or more of these. The current schema is as follows.

## Sketch-Based

Human provides a rough sketch of what some environment should look like. Roughly speaking: it includes drawing shapes to represent the basic geometry of some feature, and glyphs to describe what the feature represents. For example, splines and spline polygons to indicate terrain alongside the desired feature (e.g. [R] = river, [M] = mountain, [L] = lake); boxes, circles, or some polygon to represent settlements alongside the desired type (e.g. [V] = village, [T] = town, [C] = city); as well as paths to indicate desired connections between settlements. This would be the method most suitable for users who have a clear idea on what they want an environment to look like, both spatially and contextually.

## Description-Based

Basically a 'List' of what the user wants in the environment, with the remaining details left to the generator. For Example: "Generate a mountainous environment with a river going through it, three towns located along the river spaced equidistant from one another, a few mines into the mountain, and a castle. Connect the towns, mines, and castle all with each other and preferably on mostly flat paths that align with the river. Then place random inns, farms, and small villages along the roads but not too close to each other and the other settlements. Lastly, place random bandit camps throughout the environment but nowhere within ½ mile of a settlement". This method would be suitable for users who have an idea for what should be within an environment, but don't have any specification for how the environment should be arranged.

## Similarity-Based

The most ML-suited method. The user does not have an idea for what exactly should be in an environment, but can provide the system with some examples. For example: "Create this particular region to have a giant city and surrounding area in a manner: similar in appearance to Elder Scrolls' Imperial City crossed with London UK, in a desert environment similar to Arizona, and set in the United States in the 1980's".

## FITB-Based (Fill-In-The-Blanks)

Similar to the Similarity-Based method, but generates an environment based largely on whatever surrounding environments have already been generated. Demonstrated with TerrainGAN. Basically: the AI can 'fill in large patches' between manually designed areas which are consistent between such areas. This method was mentioned in another document with a prefix as: **Informed/Intelligent FITB**, likely to imply that AI/ML techniques are utilized thereto.

**FITB Narrative Example:** *We have manually designed the major city, towns, and some other parts of some region, but most of the remaining area remains blank (undefined). Fill the gaps in with a mountain over here, valleys over here, a lake somewhere in here, and otherwise as corresponding with the surrounding area.*
