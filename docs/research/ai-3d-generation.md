# AI-generated 3D / CAD for the Viewer

Can we prompt a service and get the E46? For **orbit**, sometimes. For the function bar (opening doors/hood/trunk, cabin, bay), no.

## Text / image → mesh (Meshy, Tripo, Luma Genie, …)

These APIs take a prompt or photos and return a **GLB**: one (or a few) triangle meshes plus a texture. Meshy documents a preview/refine pipeline and a “Smart Topology” mode with “natively separated parts” ([Meshy text-to-3D](https://docs.meshy.ai/api/text-to-3d.md)). Tripo has `generate_parts` and a segmentation product that splits a mesh into named chunks ([Tripo text-to-model](https://developers.tripo3d.ai/en/docs/generation-text-to-model), [segmentation](https://www.tripo3d.ai/features/ai-model-segmentation)). Meshy “Auto Split” is for **3D-print** cuts (watertight chunks on a build plate), not hinged car doors ([Auto Split tutorial](https://www.meshy.ai/tutorials/auto-split-3d-model-into-parts)).

What you get for a car:

- A **statue** that looks like a 3 Series from the outside if the prompt/photos cooperate.
- **Invented** unseen sides (underside, cabin, bay). Image-to-3D is a guess, not a measurement ([Tripo accuracy note](https://www.tripo3d.ai/blog/explore/ai-3d-generator-accuracy-versus-photogrammetry): wheelbase/cabin depth come out estimated).
- Doors that are **painted on**. “Separated parts” means body vs wheels vs maybe a lid chunk — not a door that swings and shows a card, module, and regulator.
- No trunk lamp object. No VIN-accurate SA options.

Our **Region hitboxes** still work on a statue. You cannot open the hood and click the bay.

Meshy’s AUP forbids prompts and references that violate third-party trademarks ([acceptable use](https://www.meshy.ai/acceptable-use-policy); [copyright checklist](https://help.meshy.ai/en/articles/16103168-copyright-checklist-for-meshy-reference-images-and-assets): “recognizable brand products”). “BMW 325i E46” is that. Photos of *your* car as reference are your photos; the output can still look like BMW trade dress.

## Text → CAD (Zoo Zookeeper, other text-to-CAD)

These emit **parametric CAD** (sketches, extrudes, STEP), one part at a time. Zoo’s own write-up: generation without design intent is not useful CAD ([Zookeeper](https://zoo.dev/research/zookeeper)). Assemblies (mates, motion) are still on the roadmap ([Zoo roadmap](https://zoo.dev/roadmap), assemblies called out as upcoming). Independent testers in 2026: a “hinge assembly” prompt returns a **fused sculpture**, not leaves and a pin ([TexoCAD](https://blog.texocad.ai/posts/text-to-cad-assemblies)). Automotive packaging is called out as the same problem at car scale ([TexoCAD automotive](https://blog.texocad.ai/posts/text-to-cad-for-automotive)).

You will not get an E46 body-in-white, opening doors, and an M54 bay from a prompt.

## Photogrammetry / scan (not generative, often confused)

Many overlapping photos of **this** silver car → a dense fused mesh that looks like *your* car. Still no opening doors unless you model them. Interior only if you shoot it. Better likeness, same function gap as AI, more work.

## Compared to the function bar we already set

| Source | Orbit | Open doors/hood/trunk | Cabin + bay | This VIN’s look |
| --- | --- | --- | --- | --- |
| AI mesh (Meshy/Tripo/…) | Yes | No | Hallucinated / empty | Guess + trademark mess |
| AI CAD (Zoo et al.) | A bracket, not a car | No | No | No |
| Photoscan of this car | Yes | No | Only if you scan it | Yes |
| Marketplace sedan GLB | Yes | Yes if the listing says so | Basic, if listed | Generic |
| MediaPool | Official current cars | Unknown | Unknown | Not this E46 |

**Use AI for:** a quick statue if we accept hitboxes-only and skip opening panels. **Do not use AI for:** CAD of the Vehicle, or as a substitute for ETK.
