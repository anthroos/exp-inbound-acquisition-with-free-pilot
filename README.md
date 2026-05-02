# exp-inbound-acquisition-with-free-pilot

> **What is this?** A 57-day real B2B sales arc — anonymized, cited day by day — that you can install into your Claude Code so it pulls the matching day when you face a similar situation.
>
> **Part of [OpenExp](https://openexp.ai/)** — a runtime that turns real human-AI work into installable experience packs. New here? Read [openexp.ai](https://openexp.ai/) first to understand what packs are and how Claude uses them.

---

## What you get

You install this pack as a Claude Code skill. Then you describe your situation in your own words — for example:

> *"I'm 25 days into a B2B pilot. Counterparty went silent 4 days ago. Should I ping?"*

Your Claude reads this pack's anonymized 57-day trajectory, finds the matching day, and replies with a citation:

> *"From `exp-inbound-acquisition-with-free-pilot`, day +25: counterparty went silent for 6 days after the pilot demo. The author did **not** ping. Instead they sent technical context (architecture diagram) on day +27 — silence broke day +28. On your day, that maps to: don't ping yet, send architecture context by Friday."*

No prediction made up by the model. The day is real, the action is real, the outcome (`closed_won`, day +57) is real. The trajectory is anonymized — counterparty identity is replaced with category tokens (`<counterparty_cto>`, `<regulated_industry>`, etc.). Author identity is public — Ivan Pasichnyk signs the pack.

## Pack facts

| Field | Value |
|-------|-------|
| Author | Ivan Pasichnyk (`ivan-pasichnyk`) |
| Outcome | `closed_won` at `day_+57` |
| Duration | 57 days, 26 ordered steps |
| Category tokens | `<counterparty_cto>`, `<counterparty_pm>`, `<regulated_industry>`, `<e_signing_platform_local>`, `<local_currency>`, `<foreign_corp_entity>`, `<local_jurisdiction>` (13 total) |
| License | MIT |
| Schema | OpenExp pack format v3 (raw — see [Why raw](#why-raw) below) |

## Files

| File | What it is |
|------|------------|
| `meta.yaml` | Facts only — id, outcome label, duration, category tokens, license. No author interpretation. |
| `trajectory.anonymized.yaml` | The timeline, 26 ordered steps from `relative_day: 0` to `relative_day: +57`. |
| `SKILL.md` | Claude entry point — read first when the skill is invoked. |
| `README.md` | This file — human-readable face for catalog browsing. |

## Install

You need two things: the universal **applier skill** (one-time, works for any OpenExp pack) and **this pack** (per-pack).

```bash
# 1. One-time: the universal applier
git clone https://github.com/anthroos/claude-skills.git
ln -s ~/claude-skills/skills/core/openexp-use ~/.claude/skills/openexp-use

# 2. This pack
git clone https://github.com/anthroos/exp-inbound-acquisition-with-free-pilot.git
ln -s "$PWD/exp-inbound-acquisition-with-free-pilot" \
  ~/.claude/skills/openexp:ivan-pasichnyk:inbound-acquisition-with-free-pilot
```

Restart Claude Code. Both auto-discover. Then describe your situation in your own words — the applier finds matching packs and cites the day.

If you've never set up the OpenExp engine itself (Qdrant + hooks), do that first: see the [engine repo](https://github.com/anthroos/openexp).

## Why raw

Earlier OpenExp pack formats shipped a `summary.yaml` with the author's interpretation pre-baked: "this pack applies when X", "the lesson is Y". v3 (this pack's format) drops that. The reader's Claude reads the raw trajectory and derives the match against **your** situation, not the author's frozen reading. Different readers, different contexts, different inferences from the same arc. See `SKILL.md` for the full reading instruction.

## Related

- **[openexp.ai](https://openexp.ai/)** — project home, what OpenExp is, the case for trajectory packs
- **[OpenExp engine](https://github.com/anthroos/openexp)** — the runtime (hooks, MCP server, retrieval) you install once
- **[openexp-use skill](https://github.com/anthroos/claude-skills/tree/main/skills/core/openexp-use)** — the universal applier
- **[Publishing your own pack](https://github.com/anthroos/openexp/blob/main/docs/publishing-a-pack.md)** — author guide

## License

MIT — pack content and metadata. See `meta.yaml` for the in-pack license declaration.
