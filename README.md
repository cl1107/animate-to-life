# animate-to-life

A reusable Agent Skill for converting anime / donghua / game-render characters into believable photorealistic live-action cosplay while preserving the source character's identity, costume, pose, composition, props, and scene intent.

The skill explicitly distinguishes **2D anime / donghua** from **3D donghua / CG renders** because they fail in different ways during photorealistic conversion.

## Why split 2D and 3D?

### 2D → live action

2D artwork usually does not fully define real anatomy, depth, garment construction, material behavior, or physically consistent lighting.

The 2D route therefore focuses on **reconstruction**:

- translate stylized facial proportions into plausible human anatomy without losing identity;
- rebuild painted hair as physically believable styled hair;
- infer real garment layers, seams, closures, fabric weight, and prop construction;
- reconstruct scene depth, contact shadows, and photographic lighting;
- preserve pose, camera, composition, and design semantics.

### 3D / CG → live action

3D donghua and game renders already contain stable geometry, perspective, pose, costume structure, and often a strong face identity.

The 3D route therefore focuses on **de-CG conversion**:

- preserve face/body/costume geometry aggressively;
- remove wax/plastic skin and beauty-render artifacts;
- convert CG hair grooming into believable real strands;
- convert shader materials into real fabric, leather, metal, jade, wood, glass, etc.;
- replace render-engine lighting, bloom, and synthetic DOF with photographic optics;
- avoid turning an already-recognizable 3D character into a different generic person.

## Core principles

1. **Character identity before generic beauty.**
2. **Preserve costume semantics, not only colors.**
3. **Preserve pose, camera angle, framing, props, and scene intent unless explicitly asked to change them.**
4. **Use an East Asian live-action casting aesthetic by default for Chinese donghua / guofeng characters, without inventing nationality.**
5. **Avoid generic influencer faces, Westernized facial drift, excessive infantilization, cheap cosplay materials, and plastic CG skin.**
6. **Translate stylization into reality; do not redesign the character merely to make the result prettier.**

## Structure

```text
.
├── SKILL.md
└── references/
    ├── 2d-to-live-action.md
    ├── 3d-to-live-action.md
    ├── character-preservation.md
    └── prompt-output.md
```

### `SKILL.md`

Main router and global rules. It decides whether the source should use the 2D reconstruction route, the 3D de-CG route, or a hybrid route.

### `references/2d-to-live-action.md`

Rules for 2D anime, donghua, manhua/manga, cel-shaded art, painterly illustration, concept art, and similar flattened sources.

### `references/3d-to-live-action.md`

Rules for 3D donghua frames, CG character renders, game cinematics, Unreal/Unity-style renders, and similar volumetric sources.

### `references/character-preservation.md`

Defines the character-lock system for face identity, hairstyle, costume construction, props, pose, expression, camera, and composition.

### `references/prompt-output.md`

Defines prompt ordering, negative constraints, multi-reference handling, short-prompt compression, and model-neutral generation behavior.

## Typical triggers

The skill is intended for requests such as:

- 动漫转真人
- 国漫转真人
- 2D 国漫真人化
- 3D 国漫真人化
- 真人 Cos / 真人 cosplay
- 二次元真人化
- anime to real
- anime to live action
- character to real
- game render to photo
- photorealistic cosplay conversion

## Example workflow

```text
Input reference
    ↓
Classify: 2D / 3D / hybrid
    ↓
Build character lock
    ↓
Preserve face + hair + costume + prop + pose + camera
    ↓
Apply route-specific realism conversion
    ↓
Add photographic skin / hair / materials / lighting / optics
    ↓
Run drift / CG / anatomy / prop-mutation checks
    ↓
Generate or output the final prompt
```

## Chinese donghua / guofeng focus

The default rules are designed to work particularly well with Chinese donghua, xianxia, wuxia, guofeng, and East Asian fantasy characters.

The skill intentionally avoids rules such as assigning a fixed real-world nationality to a fictional character. Instead it preserves the source facial design and uses an appropriate East Asian live-action casting direction unless the user supplies a different face/casting reference.

## Inspiration

This skill was informed by useful ideas from existing agent skills such as `anime-to-life`, Eastern-beauty prompt-direction workflows, and identity-preserving image-generation workflows, while restructuring the process around explicit **2D reconstruction vs 3D de-CG routing** and stronger character-preservation rules.

## Status

Initial version. The next useful extensions are likely to be:

- model-specific adapters for GPT Image, Gemini, Seedream, Midjourney, and Stable Diffusion / ComfyUI;
- example prompt packs for common 2D and 3D donghua cases;
- multi-reference recipes for `character + face + outfit + pose` workflows;
- image-to-video continuation rules after successful live-action conversion.
