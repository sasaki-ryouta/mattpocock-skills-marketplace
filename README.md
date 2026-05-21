# mattpocock-skills-marketplace

A wrapper marketplace for Claude Code that distributes **every** skill from
[mattpocock/skills](https://github.com/mattpocock/skills).

## Why this exists

`mattpocock/skills` ships as a plugin repository (`.claude-plugin/plugin.json`,
no `marketplace.json`), so it cannot be registered directly with
`/plugin marketplace add`. Its `plugin.json` also registers only a subset of
its skills — the `deprecated/`, `in-progress/`, `misc/`, and `personal/` scopes
are left out.

This marketplace solves both problems:

- It supplies the missing `marketplace.json` manifest.
- Its plugin entry points at
  [sasaki-ryouta/skills](https://github.com/sasaki-ryouta/skills), a fork of the
  upstream repo whose `plugin.json` registers **all skills, every scope**.

## How it stays current

[sasaki-ryouta/skills](https://github.com/sasaki-ryouta/skills) runs an hourly
GitHub Actions workflow (`.github/workflows/sync-upstream.yml`) that mirrors
`skills/` from `mattpocock/skills` and regenerates `plugin.json` from every
`SKILL.md` it finds — so skills added upstream are picked up automatically.
Claude Code pulls the latest fork content on each `/plugin marketplace update`.

## Usage

```
/plugin marketplace add sasaki-ryouta/mattpocock-skills-marketplace
/plugin install mattpocock-skills@mattpocock-skills-marketplace
```
