<div align="center">

<!-- Animated Typing Banner -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=3000&pause=1000&color=2E9EF7&center=true&vCenter=true&multiline=true&repeat=true&width=600&height=100&lines=Design+System+Assistant;5+Agents+%7C+5+Skills;Claude+Code+Plugin" alt="Design System Assistant" />

<br/>

<!-- Badge Row 1: Status Badges -->
[![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge)](https://github.com/pluginagentmarketplace/custom-plugin-design-system/releases)
[![License](https://img.shields.io/badge/License-Custom-yellow?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production-brightgreen?style=for-the-badge)](#)
[![SASMP](https://img.shields.io/badge/SASMP-v1.3.0-blueviolet?style=for-the-badge)](#)

<!-- Badge Row 2: Content Badges -->
[![Agents](https://img.shields.io/badge/Agents-5-orange?style=flat-square&logo=robot)](#-agents)
[![Skills](https://img.shields.io/badge/Skills-5-purple?style=flat-square&logo=lightning)](#-skills)
[![Commands](https://img.shields.io/badge/Commands-4-green?style=flat-square&logo=terminal)](#-commands)

<br/>

<!-- Quick CTA Row -->
[📦 **Install Now**](#-quick-start) · [🤖 **Explore Agents**](#-agents) · [📖 **Documentation**](#-documentation) · [⭐ **Star this repo**](https://github.com/pluginagentmarketplace/custom-plugin-design-system)

---

### What is this?

> **Design System Assistant** is a Claude Code plugin with **5 agents** and **5 skills** for design system development.

</div>

---

## 📑 Table of Contents

<details>
<summary>Click to expand</summary>

- [Quick Start](#-quick-start)
- [Features](#-features)
- [Agents](#-agents)
- [Skills](#-skills)
- [Commands](#-commands)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)

</details>

---

## 🚀 Quick Start

### Prerequisites

- Claude Code CLI v2.0.27+
- Active Claude subscription

### Installation (Choose One)

<details open>
<summary><strong>Option 1: From Marketplace (Recommended)</strong></summary>

```bash
# Step 1️⃣ Add the marketplace
/plugin add marketplace pluginagentmarketplace/custom-plugin-design-system

# Step 2️⃣ Install the plugin
/plugin install custom-plugin-design-system@pluginagentmarketplace-design-system

# Step 3️⃣ Restart Claude Code
# Close and reopen your terminal/IDE
```

</details>

<details>
<summary><strong>Option 2: Local Installation</strong></summary>

```bash
# Clone the repository
git clone https://github.com/pluginagentmarketplace/custom-plugin-design-system.git
cd custom-plugin-design-system

# Load locally
/plugin load .

# Restart Claude Code
```

</details>

### ✅ Verify Installation

After restart, you should see these agents:

```
custom-plugin-design-system:05-plugin-optimizer
custom-plugin-design-system:01-plugin-architect
custom-plugin-design-system:04-plugin-tester
custom-plugin-design-system:03-plugin-designer
custom-plugin-design-system:02-plugin-developer
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤖 **5 Agents** | Specialized AI agents for design system tasks |
| 🛠️ **5 Skills** | Reusable capabilities with Golden Format |
| ⌨️ **4 Commands** | Quick slash commands |
| 🔄 **SASMP v1.3.0** | Full protocol compliance |

---

## 🤖 Agents

### 5 Specialized Agents

| # | Agent | Purpose |
|---|-------|---------|
| 1 | **05-plugin-optimizer** | Expert in plugin optimization, performance tuning, and best  |
| 2 | **01-plugin-architect** | Expert in plugin architecture, folder structure, configurati |
| 3 | **04-plugin-tester** | Expert in plugin testing, quality assurance, and validation. |
| 4 | **03-plugin-designer** | Expert in plugin user experience, interface design, and usab |
| 5 | **02-plugin-developer** | Expert in writing and implementing plugin code. Specializes  |

---

## 🛠️ Skills

### Available Skills

| Skill | Description | Invoke |
|-------|-------------|--------|
| `plugin-testing` | Master plugin testing, quality assurance, and validation. Le | `Skill("custom-plugin-design-system:plugin-testing")` |
| `plugin-optimization` | Master plugin performance optimization, best practices, and  | `Skill("custom-plugin-design-system:plugin-optimization")` |
| `plugin-design` | Master plugin user experience design, command workflows, and | `Skill("custom-plugin-design-system:plugin-design")` |
| `plugin-development` | Master writing plugins including agent implementation, skill | `Skill("custom-plugin-design-system:plugin-development")` |
| `plugin-architecture` | Master plugin folder structure, manifest design, and archite | `Skill("custom-plugin-design-system:plugin-architecture")` |

---

## ⌨️ Commands

| Command | Description |
|---------|-------------|
| `/design-plugin` | plugin - Design Plugin Architecture |
| `/optimize-plugin` | plugin - Optimize & Deploy Plugin |
| `/test-plugin` | plugin - Test & Validate Plugin |
| `/create-plugin` | plugin - Create New Plugin |

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |
| [LICENSE](LICENSE) | License information |

---

## 📁 Project Structure

<details>
<summary>Click to expand</summary>

```
custom-plugin-design-system/
├── 📁 .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── 📁 agents/              # 5 agents
├── 📁 skills/              # 5 skills (Golden Format)
├── 📁 commands/            # 4 commands
├── 📁 hooks/
├── 📄 README.md
├── 📄 CHANGELOG.md
└── 📄 LICENSE
```

</details>

---

## 📅 Metadata

| Field | Value |
|-------|-------|
| **Version** | 1.0.0 |
| **Last Updated** | 2025-12-29 |
| **Status** | Production Ready |
| **SASMP** | v1.3.0 |
| **Agents** | 5 |
| **Skills** | 5 |
| **Commands** | 4 |

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md).

1. Fork the repository
2. Create your feature branch
3. Follow the Golden Format for new skills
4. Submit a pull request

---

## ⚠️ Security

> **Important:** This repository contains third-party code and dependencies.
>
> - ✅ Always review code before using in production
> - ✅ Check dependencies for known vulnerabilities
> - ✅ Follow security best practices
> - ✅ Report security issues privately via [Issues](../../issues)

---

## 📝 License

Copyright © 2025 **Dr. Umit Kacar** & **Muhsin Elcicek**

Custom License - See [LICENSE](LICENSE) for details.

---

## 👥 Contributors

<table>
<tr>
<td align="center">
<strong>Dr. Umit Kacar</strong><br/>
Senior AI Researcher & Engineer
</td>
<td align="center">
<strong>Muhsin Elcicek</strong><br/>
Senior Software Architect
</td>
</tr>
</table>

---

<div align="center">

**Made with ❤️ for the Claude Code Community**

[![GitHub](https://img.shields.io/badge/GitHub-pluginagentmarketplace-black?style=for-the-badge&logo=github)](https://github.com/pluginagentmarketplace)

</div>
