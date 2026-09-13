# Prompt Output Rules

This document defines how to turn the analysis into an image-generation instruction without losing the preservation hierarchy.

## 1. Prompt order

Prefer this order because earlier concepts tend to dominate generation:

1. transformation goal;
2. character identity lock;
3. hairstyle and face-framing details;
4. costume and signature props;
5. pose / expression / gaze;
6. camera and composition;
7. route-specific 2D reconstruction or 3D de-CG instructions;
8. scene and lighting;
9. photographic material realism;
10. concise negative constraints.

Do not begin with generic quality words and bury the character identity at the end.

## 2. Universal transformation sentence

A useful default opening is conceptually equivalent to:

> Recreate the supplied character as a real adult human cosplayer / live-action adaptation of the same character, preserving the source identity, hairstyle, costume construction, pose, props, camera angle, framing, and scene layout while replacing illustration/CG rendering with physically believable photography.

Adapt wording to the user's requested age, casting, or realism level.

## 3. 2D route additions

For 2D sources, explicitly instruct the model to:

- translate stylized facial proportions into plausible human anatomy without changing the character identity;
- reconstruct garment seams, layers, closures, fabric weight, and prop construction;
- convert graphic hair shapes into real styled hair while preserving silhouette;
- reconstruct depth, contact shadows, and physically plausible lighting;
- preserve the original composition rather than inventing a portrait setup.

Avoid asking for literal anime facial geometry.

## 4. 3D route additions

For 3D/CG sources, explicitly instruct the model to:

- preserve the existing face and body geometry closely;
- remove plastic/wax skin and synthetic shader behavior;
- replace CG hair grooming with believable strand behavior while keeping the hairstyle;
- replace render materials with real fabric, metal, leather, jade, wood, glass, etc.;
- replace render-engine lighting and DOF with plausible photographic optics;
- keep the original camera and pose.

Do not over-reconstruct a good 3D identity.

## 5. Negative prompt hierarchy

Keep negatives compact and diagnostic.

### Shared negatives

```text
generic influencer face, identity drift, Westernized facial drift when inconsistent with source,
childlike age drift, oversized anime eyes, doll face, wax skin, plastic skin,
cheap cosplay fabric, simplified costume, missing costume layers, prop mutation,
broken hands, extra fingers, fused accessories, distorted anatomy,
changed pose, changed camera angle, changed framing, text, watermark, logo, UI, border
```

### Add for 2D

```text
cel shading, illustration outlines, painted skin texture, flat pasted clothing,
hard plastic wig hair, impossible garment construction
```

### Add for 3D

```text
CG render, 3D render, Unreal Engine look, Unity look, Octane render look,
game cinematic look, glassy eyes, hair-card artifacts, synthetic DOF,
excessive bloom, perfect procedural surfaces
```

Do not dump every possible negative token into every request. Use only what addresses likely failure modes.

## 6. Model-neutral vs model-specific output

If the user does not name a model, write a model-neutral natural-language prompt.

If a model is named:

- preserve the same semantic requirements;
- adapt formatting and verbosity to the model;
- do not silently change composition, age, costume coverage, or casting direction;
- avoid unsupported pseudo-parameters.

For models that respond well to natural-language editing instructions, prefer explicit preservation statements over tag soup.

## 7. Image-editing mode

When a source image is attached and the task is an edit/conversion, describe **what must remain unchanged** as clearly as what must change.

A good edit instruction usually contains:

- `Keep:` identity, hair design, costume, pose, props, framing, scene layout.
- `Change:` rendering medium into live-action photography; material/skin/hair/lighting treatment according to the selected route.
- `Avoid:` the top 5–10 likely drift/failure modes.

Do not tell the model to "redesign" unless the user requests redesign.

## 8. Multi-reference prompt structure

When references have different roles, state the mapping explicitly before the visual prompt.

Example structure:

```text
Reference roles:
- Image 1: character/costume identity
- Image 2: real-person face identity
- Image 3: pose and camera composition

Create one photorealistic live-action image using those roles without blending unrelated attributes.
```

If only one image is supplied, do not invent multiple-reference logic.

## 9. Prompt compression

When the user asks for a short prompt, retain these essentials even when compressing:

1. same character / identity;
2. same hair + costume + prop;
3. same pose + camera + framing;
4. 2D reconstruction or 3D de-CG instruction;
5. real skin/hair/materials/lighting;
6. top negative risks.

Delete decorative adjectives before deleting preservation rules.

## 10. Quality check before sending/executing

Ask internally:

- Could this prompt accidentally produce a random pretty cosplayer?
- Does it make clear what must remain unchanged?
- Is the 2D/3D route visible in the instruction?
- Could "photorealistic" still produce a high-end CG render? If yes, strengthen photographic/material language.
- Are East Asian facial characteristics being preserved where appropriate without asserting a nationality?
- Are there any copied UI, watermark, text, or borders that should be removed?

If any answer exposes a likely failure, revise before generation.
