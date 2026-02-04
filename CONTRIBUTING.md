# Contributing to Awesome OpenClaw Plugins

Thanks for your interest in contributing! This document provides guidelines for adding plugins to this curated list.

## How to Add a Plugin

1. **Fork this repository**
2. **Add your plugin** to the appropriate category in `README.md`
3. **Follow the format** (see below)
4. **Submit a pull request**

## Entry Format

Each plugin entry should follow this format:

```markdown
- [plugin-name](https://github.com/username/repo) - Brief description of what the plugin does. By [@username](https://github.com/username). `openclaw plugins install <package>`
```

**Example:**
```markdown
- [better-gateway](https://github.com/ThisIsJeron/openclaw-better-gateway) - Enhanced gateway UI with auto-reconnect, connection status indicator, network awareness. By [@ThisIsJeron](https://github.com/ThisIsJeron). `openclaw plugins install @thisisjeron/openclaw-better-gateway`
```

## Plugin Requirements

Your plugin must:

- ✅ Have a valid `openclaw.plugin.json` manifest
- ✅ Be installable via `openclaw plugins install`
- ✅ Include clear documentation (README)
- ✅ Be actively maintained
- ✅ Not duplicate existing functionality without significant improvement

## Categories

Add your plugin to the most appropriate category:

| Category | Description |
|----------|-------------|
| **Official Plugins** | Maintained by OpenClaw team only |
| **Channel Plugins** | Add new messaging platforms |
| **Utility Plugins** | Quality-of-life improvements |
| **Observability & DevOps** | Monitoring, debugging, management |
| **Health & Wellness** | Health/fitness data integrations |
| **Meta & Self-Improvement** | Plugins that enhance OpenClaw itself |

If none of these fit, propose a new category in your PR.

## Creating a New Category

To add a new category:

1. Add it to the **Contents** section
2. Create a new `<details>` block following the existing format:

```markdown
---

<details open>
<summary><h2 style="display:inline">Category Name</h2></summary>

Description of what this category contains.

- [plugin-name](url) - Description. By [@author](url). `install command`

</details>
```

## Quality Guidelines

- **Descriptions** should be concise but informative (1-2 sentences)
- **Links** must be working and point to the correct repository
- **Install commands** should be tested and functional
- **No spam** — plugins must provide genuine value

## Pull Request Process

1. Ensure your entry follows the format above
2. Place entries in alphabetical order within their category
3. Test that all links work
4. One plugin per PR (unless adding multiple related plugins)

## Questions?

- Open an issue for questions about contributing
- Join the [OpenClaw Discord](https://discord.com/invite/clawd) for community support

---

Thank you for helping make OpenClaw's plugin ecosystem better! 🐾
