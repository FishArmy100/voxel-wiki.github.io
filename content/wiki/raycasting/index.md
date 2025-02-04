+++
title = "3D Raycasting"
description = "Traveling through 3D grids in a straight line."
path = "/wiki/raycasting"
[taxonomies]
categories = ["algorithms"]
tags = ["algorithm", "math", "raycasting", "raytracing"]
[extra]
chapters = true
chapter_prev = false
chapter_next = {text = "Raytracing", link = "/wiki/raytracing"}
+++

The [Digital Differential Analyzer](https://en.wikipedia.org/wiki/Digital_differential_analyzer_(graphics_algorithm)) (`DDA`) algorithm,
adapted to 3D, is *exactly* the thing one needs to travel along a line (or a ray) through a grid of voxels.

<!-- more -->

{{ stub_notice() }}
## Implementation:
### Ray Generation
With raycasting, we need to construct a ray for each pixel on the screen, represented by the camera. The following implementation is based on [this library](https://github.com/dps/rust-raytracer/tree/main/raytracer). It should be noted that this is mostly for demonstration pourposes, and its probably not going to be that fast in comparison to other ray generation algorithms.

{{ embed_text(file="ray_building.glsl", lang="glsl") }}

### Casting Rays
Once a ray is generated, it has to be cast into a voxel volume.
The following algorithm is a 3D implementation of the DDA algorithm published in [this paper](http://www.cse.yorku.ca/~amana/research/grid.pdf).

{{ embed_text(file="dda.glsl", lang="glsl") }}

## References

- [Wikipedia](https://en.wikipedia.org/wiki/Digital_differential_analyzer_(graphics_algorithm))
- Paper: [A Fast Voxel Traversal Algorithm for Ray Tracing (1987)](http://www.cse.yorku.ca/~amana/research/grid.pdf)
- [Voxel Rendering Using Discrete Ray Tracing](https://castingrays.blogspot.com/2014/01/voxel-rendering-using-discrete-ray.html)
- [Cast ray to select block in voxel game](https://gamedev.stackexchange.com/a/49423)
- [Lode's Raycasting Tutorial](https://lodev.org/cgtutor/raycasting.html)
- Various Implementations:
  - For [`C`](https://webdocs.cs.ualberta.ca/~graphics/books/GraphicsGems/gemsiv/vox_traverse.c)
  - For [`C++`](https://gist.github.com/garymacindoe/895430c1e53a6e50cb35)
  - For [`GLSL`](https://www.shadertoy.com/view/XddcWn):
    - [Branchless](https://www.shadertoy.com/view/4dX3zl)
    - [Branchless & Textured](https://www.shadertoy.com/view/7dK3D3)
    - [With Sub-Objects](https://www.shadertoy.com/view/7stXzn)
    - [Octree Variant](https://www.shadertoy.com/view/4sVfWw)
