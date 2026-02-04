# Awesome OpenClaw Plugins [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of plugins for [OpenClaw](https://github.com/openclaw/openclaw), the open-source personal AI assistant.

<p align="center">
  <a href="https://docs.openclaw.ai/plugin">Plugin Docs</a> •
  <a href="https://github.com/openclaw/openclaw">GitHub</a> •
  <a href="https://discord.com/invite/clawd">Discord</a>
</p>

---

## Contents

- [Skills vs Plugins: What's the Difference?](#skills-vs-plugins-whats-the-difference)
- [Official Plugins](#official-plugins)
- [Channel Plugins](#channel-plugins)
- [Utility Plugins](#utility-plugins)
- [Observability & DevOps](#observability--devops)
- [Health & Wellness](#health--wellness)
- [Meta & Self-Improvement](#meta--self-improvement)
- [Contributing](#contributing)

---

## Skills vs Plugins: What's the Difference?

OpenClaw has two extension mechanisms: **Skills** and **Plugins**. Understanding when to use each is key to building effective extensions.

### Skills

Skills are **prompt-based instructions** that teach the agent how to use external tools or follow specific workflows.

```
skills/
└── weather/
    └── SKILL.md    # Instructions for the agent
```

**Characteristics:**
- 📝 Markdown files with instructions
- 🧠 Loaded into the agent's context at runtime
- 🔧 Rely on existing tools (exec, browser, etc.)
- 🚀 Easy to create — just write a SKILL.md
- ⚡ No code execution, just prompt engineering

**Best for:**
- Teaching the agent to use CLI tools
- Defining workflows and best practices
- API integration via curl/scripts
- Quick, low-code extensions

### Plugins

Plugins are **TypeScript modules** that run in-process with the OpenClaw gateway, extending its core capabilities.

```
extensions/
└── voice-call/
    ├── index.ts              # Plugin code
    ├── openclaw.plugin.json  # Manifest
    └── package.json
```

**Characteristics:**
- 💻 Full TypeScript/JavaScript code
- ⚙️ Run in the gateway process
- 🔌 Can register new tools, channels, CLI commands, and RPC methods
- 🔐 Access to gateway internals and APIs
- 📦 Distributed via npm or git

**Best for:**
- Adding new messaging channels (Slack, Teams, etc.)
- Custom agent tools with complex logic
- Background services and scheduled tasks
- Gateway UI enhancements
- Anything requiring persistent state or network connections

### The Case for Plugins

While skills are great for quick integrations, **plugins are fundamentally more powerful**:

| Capability | Skills | Plugins |
|------------|--------|---------|
| Add new messaging channels | ❌ | ✅ |
| Register custom agent tools | ❌ | ✅ |
| Add CLI commands | ❌ | ✅ |
| Run background services | ❌ | ✅ |
| Modify gateway behavior | ❌ | ✅ |
| Persistent state management | ❌ | ✅ |
| OAuth flows & auth handlers | ❌ | ✅ |
| WebSocket connections | ❌ | ✅ |
| HTTP endpoint handlers | ❌ | ✅ |
| Ship bundled skills | ❌ | ✅ |

**Bottom line:** Skills tell the agent *how* to do things. Plugins give the agent *new abilities* it couldn't have otherwise.

---

<details open>
<summary><h2 style="display:inline">Official Plugins</h2></summary>

Plugins maintained by the OpenClaw team, available under the `@openclaw/*` scope.

- [voice-call](https://docs.openclaw.ai/plugins/voice-call) - Voice calling via Twilio (or log fallback for dev). `openclaw plugins install @openclaw/voice-call`
- [matrix](https://docs.openclaw.ai/channels/matrix) - Matrix chat protocol channel. `openclaw plugins install @openclaw/matrix`
- [nostr](https://docs.openclaw.ai/channels/nostr) - Nostr decentralized protocol channel. `openclaw plugins install @openclaw/nostr`
- [zalo](https://docs.openclaw.ai/channels/zalo) - Zalo messaging (Vietnam). `openclaw plugins install @openclaw/zalo`
- [zalouser](https://docs.openclaw.ai/plugins/zalouser) - Zalo Personal account integration. `openclaw plugins install @openclaw/zalouser`
- [msteams](https://docs.openclaw.ai/channels/msteams) - Microsoft Teams channel. `openclaw plugins install @openclaw/msteams`

### Bundled Plugins

These ship with OpenClaw and can be enabled via config:

- **memory-core** — Default memory search plugin
- **memory-lancedb** — LanceDB-based long-term memory with auto-recall
- **google-antigravity-auth** — Google OAuth provider
- **google-gemini-cli-auth** — Gemini CLI OAuth provider
- **qwen-portal-auth** — Qwen OAuth provider
- **copilot-proxy** — VS Code Copilot proxy bridge

</details>

---

<details open>
<summary><h2 style="display:inline">Channel Plugins</h2></summary>

Add new messaging platforms to OpenClaw.

- [feishu](https://github.com/m1heng/clawdbot-feishu) - Feishu/Lark (飞书) channel with Stream mode, AI cards, docs/wiki/bitable tools. By [@m1heng](https://github.com/m1heng). `openclaw plugins install @m1heng-clawd/feishu`
- [dingtalk](https://github.com/soimy/openclaw-channel-dingtalk) - DingTalk (钉钉) enterprise bot with Stream mode, AI interactive cards. By [@soimy](https://github.com/soimy). `openclaw plugins install https://github.com/soimy/openclaw-channel-dingtalk.git`

</details>

---

<details open>
<summary><h2 style="display:inline">Utility Plugins</h2></summary>

Enhance the gateway experience with quality-of-life improvements.

- [better-gateway](https://github.com/ThisIsJeron/openclaw-better-gateway) - Enhanced gateway UI with auto-reconnect, connection status indicator, network awareness. By [@ThisIsJeron](https://github.com/ThisIsJeron). `openclaw plugins install @thisisjeron/openclaw-better-gateway`

</details>

---

<details open>
<summary><h2 style="display:inline">Observability & DevOps</h2></summary>

Monitor, debug, and manage your OpenClaw instances.

- [observatory](https://github.com/ThisIsJeron/openclaw-observatory) - Self-hosted observability dashboard — monitor sessions, context windows, costs, and failures across multiple gateways. By [@ThisIsJeron](https://github.com/ThisIsJeron). `openclaw plugins install @thisisjeron/openclaw-observatory`

</details>

---

<details open>
<summary><h2 style="display:inline">Health & Wellness</h2></summary>

Integrate health and fitness data into your agent conversations.

- [ouraclaw](https://github.com/rickybloomfield/OuraClaw) - Oura Ring integration — sleep, readiness, activity, stress data with scheduled summaries. By [@rickybloomfield](https://github.com/rickybloomfield). `openclaw plugins install @rickybloomfield/ouraclaw`

</details>

---

<details open>
<summary><h2 style="display:inline">Meta & Self-Improvement</h2></summary>

Plugins that enhance OpenClaw's ability to learn and grow.

- [foundry](https://github.com/lekt9/openclaw-foundry) - Self-writing meta-extension — observes workflows, learns patterns, writes new extensions and skills. By [@lekt9](https://github.com/lekt9). `openclaw plugins install @getfoundry/foundry-openclaw`

</details>

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on adding plugins to this list.

---

## Related Resources

- [Awesome OpenClaw Skills](https://github.com/VoltAgent/awesome-openclaw-skills) — Curated list of 1700+ OpenClaw skills
- [ClawHub](https://clawhub.com) — Official skill registry
- [Plugin Documentation](https://docs.openclaw.ai/plugin) — Official plugin authoring guide
- [Plugin Agent Tools](https://docs.openclaw.ai/plugins/agent-tools) — How to add agent tools in plugins

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related rights to this work.
