# Character Preservation System

This document defines how to keep the source character recognizable during photorealistic conversion.

The goal is not pixel-level copying. The goal is **semantic identity preservation**: the same character should remain recognizable after the rendering medium changes.

## 1. Character lock card

Before generating, mentally build a compact lock card from the reference image.

### A. Face identity

Record the source impression of:

- apparent adult age category;
- face length and width;
- jaw/chin shape;
- cheekbone softness or prominence;
- eye spacing and tilt impression;
- brow shape and attitude;
- nose delicacy/strength;
- lip shape;
- distinctive marks if present;
- overall temperament: cool, gentle, heroic, aloof, playful, elegant, fierce, melancholic, etc.

Do not reduce identity to "beautiful East Asian woman" or another generic demographic description.

### B. Hair identity

Lock:

- exact color family;
- length;
- main silhouette;
- bangs/fringe;
- parting;
- side locks;
- buns/ponytails/braids;
- ornaments;
- ribbons;
- signature loose strands.

Hair is often one of the strongest character identifiers and should not be casually redesigned.

### C. Costume identity

Lock costume at the **semantic construction** level:

- inner/middle/outer layers;
- neckline and collar;
- sleeve shape;
- waist structure;
- armor vs cloth boundaries;
- skirt/trouser/robe structure;
- exposed-skin boundaries;
- footwear;
- embroidery/pattern placement;
- dominant color blocks;
- signature jewelry/headwear.

Do not preserve only the palette while changing the garment design.

### D. Prop identity

For each major prop, lock:

- object type;
- silhouette;
- size relative to body;
- dominant material/color;
- which hand holds it;
- grip/orientation;
- relation to the body/scene.

A sword must remain the source sword concept. A flute must remain a flute. A fan must remain a fan. Do not allow prop morphing.

### E. Pose and expression

Lock:

- head angle;
- gaze target;
- mouth expression;
- torso direction;
- shoulder line;
- arm placement;
- visible hand action;
- leg stance;
- weight distribution;
- interaction with props or environment.

### F. Camera and composition

Lock:

- camera elevation;
- camera side;
- close-up / medium / full-body scale;
- crop boundaries;
- subject position in frame;
- perspective strength;
- foreground/background ordering;
- dominant negative space.

## 2. Identity hierarchy

When the model cannot preserve everything perfectly, use this order:

1. face identity;
2. hairstyle silhouette and signature hair details;
3. iconic costume silhouette;
4. signature prop/accessory;
5. expression and gaze;
6. pose;
7. camera/composition;
8. secondary ornament detail;
9. minor texture pattern.

## 3. Translate, do not beautify away

Photorealistic conversion inevitably changes stylized geometry. The correct operation is **translation**.

Examples:

- very large anime eyes → realistic eyes retaining the same tilt, gaze, color, and emotional intensity;
- extremely sharp anime chin → naturally narrow/defined human jaw, not a surgically extreme V-line;
- tiny painted nose → delicate but anatomically present nose;
- impossible hair spike → physically styled lock retaining the silhouette;
- painted costume panel → real sewn panel preserving shape/color/motif.

Do not replace unusual source features merely because a generic beauty model would be easier to generate.

## 4. Anti-generic-face rule

The most common failure is producing a technically realistic but unrelated attractive face.

Prevent this by explicitly carrying source-specific face information into the prompt:

- face shape;
- eye/brow relationship;
- nose/lip impression;
- temperament;
- hairstyle framing around the face;
- apparent age;
- makeup restraint.

Avoid prompts dominated by generic phrases such as:

- perfect face;
- flawless beauty;
- supermodel;
- influencer;
- celebrity look;
- doll-like;
- ultra cute;
- baby face;
- sexy face.

These phrases often overpower the source identity.

## 5. East Asian character preservation

For Chinese donghua / guofeng sources where no different casting is specified:

- retain East Asian facial design cues without flattening everyone into one beauty template;
- preserve natural facial variation;
- avoid arbitrary Western facial restructuring;
- avoid excessive nose bridge enlargement, deep eye sockets, oversized lips, or fashion-editorial contouring unless visible in the source;
- avoid excessive face shortening or infantilization;
- prefer refined natural makeup consistent with live-action xianxia/wuxia/costume drama when appropriate.

Do not claim or invent a real-world nationality from the character's appearance.

## 6. Reference-role hierarchy

When several images are provided, each reference should have an explicit role.

Suggested precedence when roles conflict:

1. explicit user instruction;
2. dedicated real-person face reference for facial identity;
3. dedicated character reference for hair/costume/iconic design;
4. dedicated pose/composition reference;
5. dedicated style/lighting/environment reference.

Do not average two different faces unless the user explicitly asks for a blend.

## 7. What may change automatically

The following may change as needed to make the result physically believable:

- tiny anatomical corrections;
- impossible 2D overlaps;
- nonphysical cloth intersections;
- painted highlight placement;
- strand-level hair arrangement;
- microtexture;
- small material imperfections;
- exact bokeh shape;
- invisible garment construction details.

These changes must support realism without altering the character concept.

## 8. What should not change automatically

Do not change without user intent:

- character sex/gender presentation;
- apparent adult vs child category;
- core face identity;
- hair color or main hairstyle;
- eye color;
- iconic costume design;
- exposed-skin boundaries;
- signature weapon/prop;
- pose category;
- camera side/framing;
- major scene identity.

## 9. Iteration diagnosis

If the result is realistic but "doesn't look like the character," fix in this order:

1. restore face shape and temperament;
2. restore eye/brow relationship;
3. restore face-framing hair and bangs;
4. remove generic beauty language;
5. restore costume neckline/headpiece/signature color blocks;
6. restore camera angle and expression.

If the result looks like the character but still feels CG, do **not** change identity. Strengthen material, skin, hair, lighting, lens, and environment realism instead.
