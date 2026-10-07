# Repository instructions

This repository contains one standalone skill: `sweety-image-art-direction`.

- `skills/sweety-image-art-direction/SKILL.md` is the complete runtime entrypoint. Keep the skill self-contained.
- Preserve explicit-only invocation in the description and `skills/sweety-image-art-direction/agents/openai.yaml` unless the user requests a policy change.
- A packaging or documentation request does not authorize changing art direction rules or generating test images.
- Preserve user-selected style, identity, composition, palette, and exact copy when refining the rules.
- Distinguish prompt checks, file checks, and observed visual quality. Do not claim universal improvement from limited samples.
- Keep Chinese and English repository descriptions consistent. Runtime instructions remain in Chinese unless translation is requested.
- Record releases in `VERSION` and `CHANGELOG.md`; use `vX.Y.Z` tags after committing the corresponding files.
- Keep generated images, private references, credentials, and local audit output out of Git unless explicitly selected for inclusion.

The skill originated in `threerocks/sweety-skills`; this repository is the maintenance source after extraction.
