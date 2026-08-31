# cc-plugin-marketplace

Claude Code Plugin Marketplace

https://code.claude.com/docs/ja/plugin-marketplaces

```
.claude-plugin/
  marketplace.json
plugins/
  <plugin>/
    .claude-plugin/
      plugin.json
    skills/
      <skill>/SKILL.md
```

plugin.json

```json
{
  "name": "quality-review-plugin",
  "description": "Adds a quality-review skill for quick code reviews",
  "version": "1.0.0"
}
```

marketplace.json

```json
{
  "name": "my-plugins",
  "owner": {
    "name": "Your Name"
  },
  "plugins": [
    {
      "name": "quality-review-plugin",
      "source": "./plugins/quality-review-plugin",
      "description": "Adds a quality-review skill for quick code reviews"
    }
  ]
}
```

## Install plugins

```
/plugin marketplace add ./my-marketplace
/plugin install quality-review-plugin@my-plugins
```

## Run plugin skills

```
/quality-review-plugin:quality-review
```

## plugin

https://github.com/agentplugins/agent-plugins-spec


## Getting Started

```
/plugin marketplace add ./
  ⎿  Successfully added marketplace: szksh-lab-2

/plugin install develop-skill@szksh-lab-2
  ⎿  ✓ Installed develop-skill. Plugin is now active.

/develop-skill:review-skill ../../suzuki-shunsuke/agent-skills/skills/en

I'll review the skills at that path. Let me start by resolving the target and getting the best practices.
```

## Where `/plugin marketplace add` stores marketplace information?

~/.claude/plugins/known_marketplaces.json

```json
{
  "claude-plugins-official": {
    "source": {
      "source": "github",
      "repo": "anthropics/claude-plugins-official"
    },
    "installLocation": "/Users/shunsukesuzuki/.claude/plugins/marketplaces/claude-plugins-official",
    "lastUpdated": "2026-08-30T11:53:21.874Z"
  },
  "szksh-lab-2": {
    "source": {
      "source": "directory",
      "path": "/Users/shunsukesuzuki/repos/src/github.com/szksh-lab-2/cc-plugin-marketplace"
    },
    "installLocation": "/Users/shunsukesuzuki/repos/src/github.com/szksh-lab-2/cc-plugin-marketplace",
    "lastUpdated": "2026-08-31T10:49:21.009Z"
  }
}
```

`/plugin install develop-skill@szksh-lab-2`

.claude/skills/settings.local.json

```json
{
  "enabledPlugins": {
    "develop-skill@szksh-lab-2": true
  }
}
```
