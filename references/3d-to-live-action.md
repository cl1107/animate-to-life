# 3D / CG → Live Action

Use this route for 3D donghua frames, game cinematics, character renders, Unreal/Unity-style images, and other CG sources with already-defined volume, anatomy, cloth geometry, camera perspective, and scene depth.

## Core problem

3D sources already contain much of the spatial information that 2D sources lack. The task is therefore **de-CG conversion**, not structural reinvention.

Preserve the source geometry and design aggressively. Replace synthetic rendering cues with real photographic materials, optics, and lighting.

## 1. Geometry preservation

Unless the user requests a redesign, preserve closely:

- face length/width;
- jaw and chin shape;
- cheekbone placement;
- nose bridge and tip character;
- eye spacing and tilt impression;
- brow shape;
- hairstyle silhouette;
- body proportions;
- costume silhouette and layer boundaries;
- pose and hand placement;
- camera position, focal impression, crop, and perspective.

Do not apply the stronger anatomical reinterpretation used for 2D unless the source itself is extremely stylized.

## 2. Face: remove CG, do not replace identity

3D donghua often already provides a strong identity anchor. Keep it.

Convert the face from render-like to photographic by adding:

- realistic pore scale;
- subtle skin color variation;
- fine facial hair where appropriate;
- natural lip texture;
- soft subsurface scattering;
- believable eyelid thickness;
- tear-line moisture;
- physically plausible catchlights;
- subtle asymmetry and micro-detail.

Reduce or correct only clearly synthetic cues such as:

- perfectly uniform skin;
- overly sharp facial gradients;
- excessive subsurface glow;
- glassy eyes;
- unnaturally clean sclera;
- perfectly symmetric beauty-render features.

Do not reshape the face into a different celebrity/model archetype merely to increase realism.

## 3. Hair: preserve groom, replace render behavior

Keep the source haircut, length, bangs, tied sections, ornaments, and overall groom.

Replace CG cues with:

- mixed strand thickness;
- natural root density;
- individual edge strands;
- flyaways;
- plausible specular variation;
- partial translucency against backlight;
- gravity and soft collision with clothing/skin.

Avoid both extremes:

- solid sculpted hair masses;
- excessively noisy individual strands that destroy the original hairstyle silhouette.

## 4. Eyes

3D eyes often reveal CG origin immediately.

Preserve eye color, shape impression, and gaze while introducing:

- realistic iris texture at photographic scale;
- restrained limbal ring;
- non-uniform sclera;
- wet tear line;
- corneal reflection tied to actual light sources;
- natural eyelashes rather than perfectly repeated geometry.

Avoid luminous game-character eyes unless they are explicitly supernatural in the source. If supernatural, keep the effect localized and allow the glow to illuminate nearby tissue realistically.

## 5. Skin and makeup

Target camera-resolved human skin, not beauty-render perfection.

Prefer:

- restrained makeup matching the character;
- pores visible at close range but not exaggerated;
- natural tonal transitions;
- subtle under-eye and nasolabial structure;
- realistic highlight breakup;
- small asymmetries.

Avoid:

- wax;
- silicone-doll skin;
- aggressive smoothing;
- HDR micro-contrast;
- over-sharpened pores pasted uniformly across the face.

## 6. Costume material conversion

Preserve the 3D costume geometry and design motifs. Replace shader-like materials with physical wardrobe/prop materials.

Examples:

- CG silk → woven silk/satin with restrained directional sheen;
- cloth shader → visible weave, seams, edge thickness, stitching, folds under gravity;
- metallic armor → real metal with micro-scratches, anisotropic reflection where appropriate, contact wear;
- leather → grain, compression, edge finishing, stitch lines;
- jade → subsurface/translucent mineral response;
- lacquered wood → layered gloss with small imperfections;
- gems → physically plausible refraction and setting geometry.

Do not add random dirt or distressing to a pristine celestial/xianxia costume unless the scene calls for it.

## 7. Lighting conversion

Preserve the direction and dramatic purpose of the source lighting, but remove render-engine signatures.

Replace:

- perfectly clean rim lights;
- omnipresent blue/orange edge lighting;
- excessive bloom;
- uniform volumetric fog;
- impossible fill from every direction;
- game-cinematic specular highlights;

with a plausible photographic lighting setup whose sources can be inferred from the scene.

Keep magical/emissive sources if canonical, but ensure their spill, falloff, and reflections obey the scene.

## 8. Camera and optics

A CG image may imitate a camera but still feel virtual. Preserve framing while adding photographic behavior:

- physically plausible depth of field;
- natural lens falloff;
- realistic motion blur only when movement warrants it;
- subtle sensor/lens character rather than artificial sharpening;
- coherent foreground/background focus relationships.

Do not add strong lens distortion, chromatic aberration, film grain, or bokeh simply as realism stickers.

## 9. Environment conversion

Keep the scene identity and composition, but replace procedural/render cues with real-world complexity:

- material imperfections;
- natural variation;
- believable contact shadows;
- environment reflections;
- atmospheric depth;
- physically plausible water/snow/rain/fog;
- set-scale detail.

Do not let environmental realism overpower the character.

## 10. 3D-specific negative risks

Prevent:

- Unreal Engine / Unity / Octane / Blender render look;
- game cinematic appearance;
- plastic or wax skin;
- perfectly symmetric CG face;
- glass eyeballs;
- overly glossy lips;
- hair-card / groom artifacts;
- fabric shader without weave or seam structure;
- excessive bloom and rim light;
- synthetic depth of field;
- floating costume parts;
- perfectly clean procedural surfaces;
- generic face replacement;
- changing a good source pose because the model prefers portrait photography.

## 11. Success criterion

The viewer should feel that the 3D character model was cast as a real person and its costume/set were physically recreated, while the character's existing geometry and identity remain recognizably intact.
