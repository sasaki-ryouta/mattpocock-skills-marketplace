# mattpocock-skills-marketplace

A thin wrapper marketplace for Claude Code that tracks
[mattpocock/skills](https://github.com/mattpocock/skills) upstream.

`mattpocock/skills` ships as a plugin repository (`.claude-plugin/plugin.json`,
no `marketplace.json`), so it cannot be registered directly with
`/plugin marketplace add`. This repo supplies the missing marketplace manifest
and points its single plugin entry at the upstream `main` branch via a
`git-subdir` source — Claude Code pulls the latest upstream content on each
marketplace sync.

## Usage

```
/plugin marketplace add sasaki-ryouta/mattpocock-skills-marketplace
/plugin install mattpocock-skills@mattpocock-skills-marketplace
```
