# UV Mapping Playground

An interactive, build-it-up-from-primitives way to develop intuition for **UV mapping**,
**PBR texture channels**, and the **lighting formula** — all in the browser, no install.

Six short lessons, each adding exactly one idea. Orbit with the mouse, tweak the controls,
and watch what changes. Every texture is generated **procedurally in-canvas**, so there are
no asset files — just open it.

## The lessons

1. **A single quad & 4 UV coordinates** — UVs are just two numbers per vertex. Drag them and
   watch the texture slide and stretch. The geometry never moves; only the *addresses into the
   texture* change.
2. **Unwrapping, seams & distortion** — see a real mesh flattened into UV space. Spot where the
   flattening has to cheat (a sphere's pinched poles) and where it gets cut (seams).
3. **Beyond RGB: PBR texture channels** — the same UVs sample *five* images at once:
   albedo, normal, roughness, metalness, AO. The bumps are faked entirely by the normal map —
   the mesh is a flat plane.
4. **Stylizing with gradient ramps** — drive a 1-D gradient by UV / Fresnel / height to add form
   and highlight seams. The backbone of toon and stylized shading.
5. **What "sampling" actually means** — hover the surface and watch the same `(u,v)` read one
   value from every map simultaneously. That *is* sampling.
6. **The lighting formula, term by term** — toggle ambient / diffuse / specular / Fresnel and
   watch the final pixel get assembled from `N·L`, `N·H`, and `N·V`.

## The one-sentence mental model

A material is **one lighting formula** fed several inputs; a **texture** is a way to make an
input *vary across the surface* by storing it in an image; **sampling** is reading that image at
a surface point's `(u, v)`; and "more than RGB" means some of those images store *physics*
(directions, roughness, metalness) instead of color — all indexed by the very same `(u, v)`.

## Running locally

It's pure static HTML + [Three.js](https://threejs.org/) loaded from a CDN. Either:

```bash
python -m http.server 8000
# then open http://localhost:8000/
```

or just double-click `index.html`.

## Built with

[Three.js](https://threejs.org/) (r160, via CDN). No build step, no dependencies to install.
