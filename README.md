<div align="center">

<img src="https://raw.githubusercontent.com/falkenslab/asker-mcp/main/docs/static/img/logo.svg" alt="asker-mcp logo" width="112"/>

# asker-mcp

**Your AI agent turns your definitions into a bank of questions with Asker.**<br/>
A definitions file drafted from your notes and checked, questions generated in GIFT or Moodle XML, and reviewed with you before they reach Moodle.

![Node.js 20+](https://img.shields.io/badge/Node.js-20%2B-339933?logo=node.js&logoColor=white)
![MCP server](https://img.shields.io/badge/MCP-server-0b0b0b)
![Status: in development](https://img.shields.io/badge/status-in%20development-d97706)
[![License: MIT](https://img.shields.io/badge/license-MIT-16a34a)](LICENSE)

</div>

asker-mcp is an MCP server for [Asker](https://github.com/teuton-software/asker), which generates many questions (true/false, multiple choice, short answer, matching, ordering) from a file of definitions: a concept's names, its definition and its tables. An AI agent drafts that file from your notes in Asker's language, checks it, runs Asker on it, and goes through the questions with you so the bad ones are left out before the moodle-teacher extension imports the rest into your question bank. The questions come from your own definitions, the same every time. **It's in development and not on npm yet.**

## ✨ Why asker-mcp

- 📝 **Your definitions, your questions.** Every question traces back to a definition you wrote or approved.
- ✅ **Checked first.** An input with a mistake is reported with its line, and nothing is generated.
- 🔎 **Reviewed with you.** The questions by concept and type, and a copy without the ones you leave out.
- 🎓 **Ready for Moodle.** GIFT or Moodle XML, for moodle-teacher's question import.
- 🔁 **Reusable.** Your input files stay yours, to generate again next year.

## 🧰 What's inside (planned)

| Area | For example |
| --- | --- |
| 📝 Inputs | `asker_input_reference`, `check_input` |
| ❓ Questions | `generate_questions`, `read_questions`, `exclude_questions` |
| 🔌 For agents | The `asker` extension in [agent-extensions](https://github.com/falkenslab/agent-extensions), with its skills and capabilities |

## 🛠️ Developing

The plan is in [`.minispec/features/asker-tools.md`](.minispec/features/asker-tools.md) and the main decision in [ADR-005](.minispec/decisions/ADR-005-definitions-are-the-source.md); `CLAUDE.md` lists every command. `npm run build`, `npm test` and `npm run check` before every commit. Releases are published to npm by the owner.

<div align="center">

Made with 💖 by Falken's Lab Team

</div>
