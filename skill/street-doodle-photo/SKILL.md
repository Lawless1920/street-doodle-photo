---
name: street-doodle-photo
description: "Transform a user-supplied photograph into an integrated street-doodle artwork in one of two selectable styles: Bold Color uses large high-chroma painted masses, while Dark Narrative uses atmospheric fluorescent line networks, personified subjects, and restrained local color eruptions. Preserve the source's displayed aspect ratio, orientation, framing, scene identity, and recognizable people and objects while allowing coherent full-frame generative editing; add a scene-aware 1–3 word English phrase in wonky multi-outline hatch-filled sign lettering. Use for 街头涂鸦感、大面积彩色涂鸦、暗夜叙事涂鸦、荧光手绘、亚文化照片拼贴、照片 doodle、街头杂志封面, mode comparison, or the user's established personal photo aesthetic."
---

# Street Doodle Photo

Create one authored photo-and-drawing world rather than applying a generic graffiti filter. Let the model edit the complete photograph so lighting, depth, photographed forms, lettering, and doodles can integrate naturally.

## Mode Gate — Run Before Image Generation

Recognize these modes and close equivalents:

- `bold-color` / `Bold Color` / `大色块模式`
- `dark-narrative` / `Dark Narrative` / `暗夜叙事模式`
- `compare-both` / `Compare Both` / `两种都做` / `对比两版`

If the user supplies a photo but does not clearly choose a mode, do not call image generation. Reply in the user's language with this compact selector and wait:

```text
开始创作前，请选择一种模式：

1. Dark Narrative — 暗夜、荧光线网、拟人角色、局部爆裂色；生成 1 张。
2. Bold Color — 大面积红黄青色块、强烈街头海报感；生成 1 张。
3. Compare Both — 同一照片分别生成以上两版；会进行 2 次图片生成，消耗更多图片生成用量。

请回复 1、2 或 3。此时尚未开始生成图片。
```

For a non-Chinese user, translate the selector faithfully. Always make the different output counts and extra usage for option 3 explicit.

When a photo is available, inspect it before showing the selector and append one non-binding recommendation without generating:

- Recommend `Dark Narrative` for low-key or night scenes, cables, rails, machinery, reflections, layered objects, or an atmospheric story.
- Recommend `Bold Color` for bright scenes, open backgrounds, clear subject separation, large negative space, food, playful portraits, or immediate poster impact.
- State the reason in one short sentence and still let the user choose. Do not turn the recommendation into an automatic default.

- Treat the user's reply `1`, `2`, or `3` as choosing the corresponding displayed option.
- If the user explicitly requests `compare-both` before seeing the usage notice, pause once and say that it creates two images and consumes more image-generation usage; proceed only after confirmation.
- If the user selects option 3 after seeing the selector, treat that choice as confirmation and proceed without asking again.
- If the user explicitly requests one mode, generate only that output and do not show the selector.
- If the user asks only for analysis or a recommendation, answer without generating.
- Never silently generate both modes. Dark Narrative is the preferred house style, but it is not an automatic default when the mode is omitted.

## Workflow

1. Resolve the Mode Gate before any image-generation call.
2. Inspect the complete source. Record the displayed width, height, aspect ratio, orientation, framing, subject identity, perspective, quiet zones, and two to four drawing anchors.
3. Read [references/style-system.md](references/style-system.md), then read only the selected mode reference:
   - `bold-color`: [references/bold-color.md](references/bold-color.md)
   - `dark-narrative`: [references/dark-narrative.md](references/dark-narrative.md)
   - `compare-both`: read both and create two clearly separate treatments, never a hybrid compromise.
4. Form one source-specific visual proposition. For `compare-both`, derive two distinct treatments.
5. Distill each proposition into an original 1–3 word English phrase unless the user requests no text.
6. Use full-frame image editing on the supplied photograph. Ask for one finished integrated image, not a transparent overlay, isolated doodle layer, checkerboard, chroma-key canvas, or manual composite.
7. Keep the source file read-only and save every result to a new path. Reject any crop, padding, border, rotation, expansion, or aspect-ratio change.
8. If a final uses a different resolution but the identical displayed aspect ratio, resample the finished integrated image once to the source's displayed pixel dimensions when the user expects original-size delivery. This restores dimensions only; it does not preserve original pixels or native detail.
9. Validate the selected mode, exact phrase, letter construction, scene integration, recognizable identity, important labels, full framing, displayed aspect ratio, and orientation.
10. Apply the Validation and Repair Policy before any additional image-generation call.

## Conflict Priority

When requirements compete, preserve them in this order:

1. complete framing, displayed aspect ratio, orientation, major perspective, and scene identity;
2. recognizable people, faces, eyes, hands, poses, major objects, labels, and logos;
3. the selected mode's dominant visual contract;
4. exact phrase spelling and letter construction;
5. decorative micro-marks.

Simplify or remove a lower-priority invention instead of sacrificing a higher-priority invariant.

## Validation and Repair Policy

- Inspect the first result before delivery. Do not call a weak output finished merely because generation completed.
- Never make a second image-generation call silently. If correction requires another generation, tell the user it consumes additional image-generation usage and request confirmation unless retries were explicitly authorized in advance.
- Allow at most one targeted correction per output by default. Preserve every successful region and name only the failed requirement in the correction brief.
- For a phrase-only failure, rebuild only the lettering while preserving the composition, people, objects, lighting, and existing doodle ecosystem.
- For an identity, framing, scene, label, or logo failure, restore the named invariant and reduce nearby decoration; do not redesign the complete image.
- For a mode failure, correct only its dominant signal: increase integrated irregular color masses for `Bold Color`, or strengthen the connected fluorescent narrative spine for `Dark Narrative`.
- Do not create a third comparison image or an unrequested alternate. If targeted correction still fails, report the limitation and let the user decide whether to spend another generation.
- Deterministic resampling to the source's displayed pixel dimensions is not a new image generation and needs no extra mode confirmation.

## Creative Integration Contract

- Prioritize a coherent artistic result over pixel identity. Full-frame generative editing may reinterpret color, grain, texture, lighting, and pixels throughout the image.
- Preserve the source's displayed aspect ratio, orientation, camera framing, major perspective, scene, people, pose, expression, objects, and documentary meaning.
- Keep faces, eyes, hands, important labels, logos, and identity-critical features recognizable. Avoid placing dense lettering or major painted forms over them.
- Do not crop, extend, pad, add borders, rotate, replace the background, invent a different location, remove a major subject, or radically redesign clothing or objects unless requested.
- Do not claim that original pixels remain unchanged. Do not use transparent-overlay, alpha-extraction, or green-screen workflows as a default or fallback.
- Preserve the original source file and always deliver a separate output.

## Shared Art Direction

- Keep the photograph immediately recognizable while allowing drawing, light, texture, and local color grading to fuse into one image.
- Attach inventions to real geometry. Let cables become creatures, openings become faces, reflections become portals, shadows release characters, and objects grow expressive anatomy.
- Draw with imperfect marker/chalk energy: uneven pressure, open contours, doubled strokes, loose hatching, small ticks, sparks, zigzags, and visible human wobble.
- Use electric yellow and bright turquoise as the main drawing inks with coral red as controlled punctuation. Use black or white when the selected mode needs contrast.
- Combine scales and preserve at least one deliberate calm zone. Favor playful, odd, streetwise humor over aggression or decorative sticker clutter.

## Adaptive Phrase System

- Invent one scene-specific 1–3 word English phrase per output. Prefer vivid verb–noun combinations, compact imperatives, or suggestive noun phrases.
- Avoid generic filler such as `COOL`, `VIBES`, `WOW`, `AWESOME`, `STREET`, or `DOODLE`.
- Use examples only as calibration: `BITE THE SKY`, `LOUD LUNCH`, `CHASE LIGHT`, or `AFTER HOURS`.
- If the user supplies wording, use it verbatim. If the user requests no text, omit it.
- Put the phrase in the generation prompt as exact quoted text and require exact spelling with no unrelated words.
- Anchor the phrase to photographed geometry and integrate it into the selected mode rather than placing it as a clean caption.

## Letter Construction System

- Treat the phrase as a hand-built sign object, not a font overlay.
- Use chunky outlined show-card letters with a tall, slightly condensed silhouette and visible interior space.
- Use bright turquoise as the main outer contour, one electric-yellow inner contour, and a slightly offset turquoise or coral echo/extrusion contour.
- Keep letter bodies open or pale and fill them with conspicuous coral, yellow, and turquoise vertical or diagonal hatch stripes.
- Vary height, width, tilt, counter shape, spacing, baseline, and top line by hand while preserving exact spelling.
- Prefer lively mixed-case or uneven stacked construction when suitable.
- Add doubled edges, imperfect inlines, short overhangs, and mismatched registration.
- Do not use single-layer solid brush type, smooth script, clean sans serif, varsity lettering, neon tubes, or polished 3D typography.
- If ordinary solid lettering appears, revise with: `Rebuild every letter as turquoise multi-outline dimensional sign lettering with yellow inner contours and coral/yellow/turquoise hatch-filled open interiors.`

## Output Naming

- Single Dark Narrative: `SOURCE-dark-narrative.png`
- Single Bold Color: `SOURCE-bold-color.png`
- Compare Both: return both filenames above and identify each mode clearly.
- If the target filename already exists, append `-v2`, `-v3`, and so on. Never overwrite a prior result.

## Guardrails

- Do not reproduce distinctive characters, exact typography, or the layout of reference artwork. Derive only high-level construction and create source-specific work.
- Do not use spray-can tags, brick-wall clichés, realistic tattoos, glossy 3D, kawaii sticker packs, or clean corporate vector icons unless requested.
- Do not invent brand claims, trademarks, profanity, or unrelated slogans.
- Do not blend the two modes when the user requests a comparison.

## Editing Prompt Pattern

Write one coherent full-frame edit brief per requested mode containing:

1. the source's displayed aspect ratio, orientation, complete framing, scene identity, and important invariants;
2. `integrated full-frame photo edit; preserve the complete composition; no crop, padding, border, rotation, expansion, background replacement, transparent overlay, checkerboard, or chroma key`;
3. the exact selected mode and its reference rules;
4. one source-specific proposition and two to four real drawing anchors;
5. palette roles, scale hierarchy, foreground/background interaction, and a calm-zone plan;
6. the exact 1–3 word phrase, spelling, placement, and multi-outline hatch-filled construction;
7. explicit protection for faces, eyes, hands, important labels, and identity-critical features.

For `compare-both`, write and execute two independent full-frame edit briefs from the same source.
