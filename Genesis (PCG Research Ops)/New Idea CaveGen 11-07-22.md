# Project Genesis (Blackreach-Erebor and otherwise)
## New Idea For PCG of Cave[rn] Environments
### Written and Developed by Steven Eiselen, 11/07/22


========================================================================
## QAD Overview

I just read the first 'Wallangong' paper on '3D Cave Gen Via Octrees'. 

Its voxel generation method encompasses, roughly:
  * defining+placing "void spatial primitives" such as spheres and boxes 
    in some finite 3D space as to 'raw-carve' the macro details; then
  * defining a bias-based smoothing function upon those primitives, as 
    to effectively realize a 'blur effect' thereupon; then 
  * generating a 3D perlin noise field throughout the entire space; then
  * realizing a discrete {'VOID' xor 'ROCK'} sampling function for the
    consequent generation of voxels; then
  * {DOWN → UP} construction of (Compressed) Voxel Octree thereof; then
  * Flood-Fill based annihilation thereof, i.e. of small voidous pockets
    and/or 'floating rock chunks'; then'
  * (post-)pro of resultant Octree into final output: i.e. 
    * in their case: to a mesh of resultant voxel-based surface, 
    * in Lague's and ideally my case: to a mesh of Marching Cubes xor
      tetrahedra mapping of the Octree and/or its surface nodes (WLOG)

I want to play with the primitives placement idea; as I think it can be
EXACTLY what I've been looking for WRT creating the plateau/platform and
'ridge-bridge' therebetween effects of my vision of the Dwarven/Eldarin
ruins per Genesis Initiative "Blackreach : Erebor".