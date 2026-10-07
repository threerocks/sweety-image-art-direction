# Image Art Direction

[中文](README.md) | English

Turn vague feedback about plastic surfaces, implausible lighting, and distracting detail into specific edits while preserving the chosen style, subject, and composition.

`sweety-image-art-direction` is an explicitly invoked AI skill for visual briefs, prompts, and image review. It covers portraits, real-world scenes, products, posters, infographics, and hand-drawn images. Image generation and editing use the capabilities available in your host tool.

## Try it

Upload an image and ask:

```text
Use $sweety-image-art-direction to edit this image.
Preserve the subject's identity, pose, composition, palette, and style.
Inspect the full image for scattered highlights, strong edges, and fine textures
that distract from the subject. Address that problem in this edit, then check
whether anything I asked to preserve has changed. Generate the edited image.
```

For prompts only, replace the last sentence with: "Return only the editing prompt; do not generate an image."

## What it handles

| Problem | Approach |
| --- | --- |
| Skin, fabric, and glass share the same artificial gloss | Distinguish material responses and check lighting, shadows, reflections, and contact |
| Dense detail obscures the subject | Establish coherent shapes and tonal hierarchy before adding local texture |
| Multiple references mix up identity and style | Assign each reference a specific role: identity, clothing, composition, or style |
| An edit fixes one issue but changes the subject | State the edit target and preservation requirements, then inspect unintended changes |
| An illustration looks like a photo with paper texture | Keep shapes, marks, paint handling, and medium consistent |
| Poster artwork is ready but text is unreliable | Check exact copy and hierarchy, and distinguish layout drafts from final typesetting |

## Install in Codex

Send this to Codex:

```text
Use skill-installer to install https://github.com/threerocks/sweety-image-art-direction.
The skill path is skills/sweety-image-art-direction; its name is sweety-image-art-direction.
Preserve the explicit-only invocation policy in agents/openai.yaml.
If an installation already exists, verify its source and back it up before updating.
```

Invoke `$sweety-image-art-direction` in your next turn after installation. Image-related keywords alone do not activate the skill.

If the ZIP download fails, ask the installer to use Git mode with these arguments:

```text
--repo threerocks/sweety-image-art-direction
--path skills/sweety-image-art-direction
--name sweety-image-art-direction
--method git
```

For manual installation, download the repository and place the entire `skills/sweety-image-art-direction` directory under `${CODEX_HOME:-$HOME/.codex}/skills/`. Keep both `SKILL.md` and `agents/openai.yaml`.

For updates, ask the installer to verify the source and back up the existing installation before reinstalling from this repository. Do not assume the installed directory is a Git checkout.

Other hosts can load [SKILL.md](skills/sweety-image-art-direction/SKILL.md) using their own installation mechanism. Invocation syntax and policy support depend on the host. The instructions are written in Chinese. Without a skill loader, the file can be supplied as conversation instructions.

The skill itself needs no API key, scripts, packages, or other skills. Generating images requires a capable host and may incur its usual charges. A host without image generation can still provide prompts and visual briefs.

## Example requests

```text
Use $sweety-image-art-direction to generate a 3:4 product image.
Show a white ceramic teapot with a wooden handle on a pale wooden table.
Keep the spout, handle, and lid fully in frame. Distinguish ceramic from wood.
Do not add text.
```

```text
Use $sweety-image-art-direction to generate a reading scene.
Reference 1 supplies identity, reference 2 supplies clothing, and reference 3
supplies the gouache style. The person sits by a window holding an open book.
Do not copy the clothing model's face or the style reference's text and composition.
```

```text
Use $sweety-image-art-direction to edit this illustration.
Keep the character proportions, saturated palette, and composition.
Background specks and sharp edges distract from the subject. Resolve them with
coherent painted shapes and directional strokes, without blurring the whole image
or lowering saturation.
```

These are usage examples, not claims about verified outputs. The full input template is in [SKILL.md](skills/sweety-image-art-direction/SKILL.md#可直接复制的专业输入).

## Evaluate the result

Inspect the image at its intended viewing size before checking faces, hands, materials, text, and dimensions. For edits, compare identity, composition, and other preservation requirements against the original.

Darker lighting, softer detail, fewer props, or a different composition do not establish better quality on their own. Installation and file checks do not establish visual quality either. Improvement is not guaranteed; results depend on the model, input, and editing capabilities.

## Origin and migration

Extracted from [sweety-skills](https://github.com/threerocks/sweety-skills) at commit [`5d9ff13`](https://github.com/threerocks/sweety-skills/commit/5d9ff13c809cbf239ab016e0b499a07faa3bc7c0). Standalone version `1.0.0` preserves both runtime files unchanged and starts a separate version history.

Future rule changes belong in this repository. Existing personal installations remain usable; use this repository as their update source. Avoid enabling duplicate copies through both an older `sweety-skills` plugin and a separate installation.

## Files and license

- [SKILL.md](skills/sweety-image-art-direction/SKILL.md): complete instructions and input template.
- [agents/openai.yaml](skills/sweety-image-art-direction/agents/openai.yaml): Codex UI metadata and explicit-only policy.
- [CHANGELOG.md](CHANGELOG.md): version history.
- [LICENSE](LICENSE): MIT, matching the source repository's declared license.

Method attribution remains in `SKILL.md`; following its instructions does not require fetching the source page.
