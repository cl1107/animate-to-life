---
name: animate-to-life
description: Convert 2D anime/donghua illustrations and 3D donghua/CG/game-render characters into believable photorealistic live-action cosplay while preserving character identity, face design, hairstyle, costume semantics, pose, props, composition, and scene intent. Routes 2D and 3D sources differently, with special support for Chinese donghua, guofeng, xianxia, wuxia, and East Asian character aesthetics. Use for 动漫转真人, 国漫转真人, 二次元真人化, 2D/3D国漫真人化, 真人cos, live-action cosplay, anime-to-real, character-to-real, game-render-to-photo, or photorealistic character conversion.
---

# Animate to Life

Turn a stylized character image into a photograph that looks like a real cosplayer / live-action adaptation of **that specific character**, not a generic attractive person wearing vaguely similar clothes.

The highest-level rule is:

> Preserve character design and visual intent first; replace the rendering medium second.

A successful result should feel as though the original character, costume department, set, pose, and camera setup were recreated physically and photographed in the real world.

## 1. Classify the source before writing or generating

Always identify the source route first.

### Route A — 2D anime / donghua / illustration

Use when the source is hand-drawn, cel-shaded, painterly, manga/manhua, 2D game art, concept art, or clearly flattened stylized artwork.

Read [`references/2d-to-live-action.md`](./references/2d-to-live-action.md).

Core problem: **reconstruction**. The source does not fully define real anatomy, depth, material behavior, garment construction, or optical lighting, so these must be inferred without redesigning the character.

### Route B — 3D donghua / CG / game render

Use when the source is a 3D donghua frame, game cinematic, game character render, Unreal/Unity-style render, or other CG image with already-defined volume and geometry.

Read [`references/3d-to-live-action.md`](./references/3d-to-live-action.md).

Core problem: **de-CG conversion**. Keep the source geometry and character design, but replace synthetic skin, hair, eyes, cloth, lighting, depth of field, and render artifacts with believable photographic equivalents.

### Route C — hybrid / ambiguous

If the image mixes 2D paint-over, 3D render, AI illustration, or heavy post-processing, choose the route based on what defines the character most strongly:

- flattened / invented anatomy and painted forms → start from Route A;
- stable 3D facial volume, body geometry, cloth geometry, and perspective → start from Route B.

Borrow individual rules from the other route only where needed. Do not ask the user to classify it unless the distinction cannot be inferred from the image.

## 2. Build a character lock before changing the medium

Read [`references/character-preservation.md`](./references/character-preservation.md).

Internally identify the following anchors before generation:

1. **Character identity** — facial shape, apparent age category, temperament, distinctive design language.
2. **Hair** — color, length, silhouette, fringe/bangs, parting, ornaments, braids/ponytails, loose strands.
3. **Eyes and brows** — color, shape impression, brow direction, gaze.
4. **Costume semantics** — garment layers, neckline, sleeves, armor/cloth boundaries, embroidery, belts, fasteners, footwear, exposed skin boundaries.
5. **Signature objects** — sword, staff, fan, flute, jewelry, headpiece, ribbons, talismans, etc.
6. **Pose and body language** — torso direction, head angle, limb positions, hand action, weight distribution.
7. **Camera** — viewpoint, lens impression, distance, crop, perspective, framing.
8. **Scene** — location, major background forms, time/weather, atmosphere, key light direction.

Explicit user instructions override every inferred anchor.

## 3. Preservation priority

When trade-offs are necessary, preserve in this order:

1. character identity and recognizable facial design;
2. hairstyle and signature ornaments;
3. costume structure and iconic props;
4. pose, gesture, gaze, and expression;
5. camera angle, crop, and composition;
6. background identity and scene layout;
7. minor decorative detail.

Do **not** sacrifice the first four merely to make the result more conventionally beautiful or fashionable.

## 4. Humanization rules

The output person must look physically real, but should still read immediately as the source character.

- Convert stylized facial geometry into plausible human anatomy while preserving the source face's **shape language**.
- Preserve whether the face feels long/short, narrow/broad, sharp/soft, cool/gentle/heroic, rather than replacing it with a generic model face.
- Use realistic adult human eye proportions. Preserve eye color and the source's emotional impression without literal oversized anime eyes.
- Preserve the hairstyle silhouette while translating it into physically achievable styled hair with real strands, flyaways, gravity, translucency, and scalp-root behavior.
- Treat costume as a real garment or prop build: fabric weight, seams, layering, closures, embroidery, metal, leather, jade, wood, lacquer, and wear must behave like real materials.
- Preserve exposed-skin boundaries and garment coverage unless the user asks for a redesign.
- Use natural skin texture: pores, fine facial hair, subtle tonal variation, believable subsurface scattering, and non-plastic highlights.
- Use photographic eye moisture/catchlights and natural teeth/lips where visible.

## 5. Chinese donghua / guofeng defaults

For Chinese donghua, guofeng, xianxia, wuxia, historical-fantasy, and similar East Asian designs:

- default to an **East Asian live-action casting aesthetic** unless the source or user indicates otherwise;
- do not invent a nationality or search for one;
- do not Westernize facial structure merely because the image model associates photorealism with Western fashion photography;
- avoid generic influencer / internet-celebrity faces, excessive V-line reshaping, overfilled lips, exaggerated contact-lens eyes, and heavy beauty-filter skin;
- avoid infantilizing a clearly adult character;
- preserve restrained Eastern makeup and styling when appropriate to the source;
- for xianxia/wuxia costumes, favor premium film/TV costume construction over cheap convention-costume fabric.

These are defaults, not identity claims. User-provided casting, ethnicity, face references, or art direction always take precedence.

## 6. Composition lock

Unless the user asks for a new composition:

- keep the same camera side and approximate elevation;
- keep the same crop and subject scale;
- keep the head/body orientation;
- keep the pose and visible hand action;
- keep major props in the same semantic role and approximate location;
- preserve foreground/background ordering;
- preserve the scene's major light direction and atmosphere.

Do not casually turn a full-body scene into a glamour close-up, a side profile into a front portrait, or an action pose into a standing fashion pose.

## 7. Photographic realism target

Aim for **live-action character photography**, not merely a more detailed render.

Prefer language describing:

- real camera optics and physically plausible depth of field;
- natural skin response and lens-resolved texture;
- individual hair strands and believable hair mass;
- real fabric weave, embroidery, metal, leather, wood, jade, glass, water, snow, smoke, rain, etc.;
- coherent key/fill/rim lighting;
- environment reflections and contact shadows;
- cinematic color grading that does not destroy skin realism.

Avoid relying on generic quality tags such as `8k`, `masterpiece`, or `ultra detailed` as a substitute for material and photographic instructions.

## 8. Common failure prevention

Actively prevent:

- generic influencer face / loss of character identity;
- Westernized facial drift on East Asian source characters;
- childlike or overly young facial drift for adult characters;
- oversized anime eyes surviving literally into the real face;
- plastic skin, wax skin, doll skin;
- 3D-render / game-render / Unreal look in the final photograph;
- wig-like solid hair masses or plastic hair strands;
- costume simplification, random redesign, or missing layers;
- cheap satin cosplay texture when the source implies premium fabric;
- prop mutation or jewelry replacing the original prop;
- changed pose/camera merely to obtain a prettier portrait;
- extra fingers, broken hands, fused accessories, distorted anatomy;
- scenery or ornament patterns appearing inside the face/skin;
- excessive particles, bloom, sharpening, or HDR that makes the image artificial;
- text, logos, watermarks, UI, or borders copied from the reference image.

## 9. Multiple references

When multiple images are supplied, determine each image's role rather than blending everything indiscriminately.

Typical roles:

- **character reference** — identity, hairstyle, face, costume;
- **face reference** — human facial identity/casting anchor;
- **outfit reference** — clothing or accessory replacement;
- **pose/composition reference** — body pose and camera framing;
- **scene/style reference** — environment, lighting, photographic treatment.

If the user explicitly says which image controls which attribute, follow that mapping exactly.

If a real-person face reference is provided, preserve that person's identity while applying the fictional character's hair/costume/styling, unless the user asks for a looser interpretation.

## 10. Prompt / execution behavior

Read [`references/prompt-output.md`](./references/prompt-output.md) before producing a final generation prompt.

- If the user asks to **generate or edit an image** and the host has an image-generation/editing tool, execute the image task rather than stopping at a prompt.
- If the user asks for a **prompt**, produce an image-ready prompt organized by preservation anchors and route-specific realism instructions.
- Do not ask unnecessary clarification. Infer sensible defaults from the reference image and the user's existing constraints.
- If the user names a target model, adapt the prompt syntax to that model without changing the visual requirements.

## 11. Final internal check

Before generation, verify:

- source route selected correctly;
- character still recognizable if rendered as a real human;
- face was translated rather than replaced;
- hairstyle silhouette and ornaments are intact;
- costume layers and props retain their semantics;
- pose/camera/composition are locked unless intentionally changed;
- 2D reconstruction or 3D de-CG rules were applied as appropriate;
- final image is expected to read as a photograph, not illustration or CG;
- no irrelevant border, watermark, caption, or UI element is preserved.
