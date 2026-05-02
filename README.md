# exp-inbound-acquisition-with-free-pilot

> An [OpenExp](https://openexp.ai/) experience pack — a 57-day inbound B2B acquisition trajectory that closed `closed_won`.

**Author:** Ivan Pasichnyk (`ivan-pasichnyk`)
**Outcome label:** `closed_won` at `day_+57`
**Duration:** 57 days · 26 steps
**License:** MIT
**Schema:** OpenExp pack format v3 (raw)

## What is in this repo

Four files. Self-contained, installable into Claude Code via [openexp-use](https://github.com/anthroos/claude-skills/tree/main/skills/core/openexp-use).

| File | What it is |
|------|------------|
| `meta.yaml` | Facts only — id, outcome label, duration, category tokens, license. No author interpretation. |
| `trajectory.anonymized.yaml` | The timeline, 26 ordered steps from `relative_day: 0` to `relative_day: +57`. Counterparty identity replaced with category tokens (`<counterparty_cto>`, `<regulated_industry>`, `<e_signing_platform_local>`, `<local_currency>`, …). Author identity is public — it signs the pack. |
| `SKILL.md` | Claude entry point. Read first when the skill is invoked. |
| `README.md` | This file — human-readable face for catalog browsing. |

Per OpenExp pack format v3, this pack ships **raw** — no `applies_when`, no summary, no author grade reason. Those are interpretations and are deliberately omitted. The reader's Claude reads `trajectory.anonymized.yaml` and derives the situational match on the fly.

## Install

One-time, install the universal `openexp-use` skill so Claude Code knows how to apply any OpenExp pack:

```bash
git clone https://github.com/anthroos/claude-skills.git
ln -s ~/claude-skills/skills/core/openexp-use ~/.claude/skills/openexp-use
```

Then install this pack:

```bash
git clone https://github.com/anthroos/exp-inbound-acquisition-with-free-pilot.git
ln -s "$PWD/exp-inbound-acquisition-with-free-pilot" \
  ~/.claude/skills/openexp:ivan-pasichnyk:inbound-acquisition-with-free-pilot
```

Auto-discovered on next Claude Code session.

## How to use

Describe your situation in your own words. The `openexp-use` skill discovers all installed packs, matches your situation against each pack's trajectory, and replies with a cited `relative_day` from the matching pack — i.e. *"on day +12 of a similar arc the author did X; on your day, that maps to ..."*.

There is no fixed query format — natural language works.

## Related

- [OpenExp engine](https://github.com/anthroos/openexp) — the runtime that hosts and retrieves packs
- [openexp.ai](https://openexp.ai/) — project home, catalog of published packs
- [openexp-use skill](https://github.com/anthroos/claude-skills/tree/main/skills/core/openexp-use) — the universal applier

## License

MIT — pack content and metadata. See `meta.yaml` for the in-pack license declaration.
