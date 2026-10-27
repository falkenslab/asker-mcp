# Project

**asker-mcp**: [Asker](https://github.com/teuton-software/asker) for AI agents: write a definitions file from a teacher's notes, check it, generate questions in GIFT or Moodle XML, and review them, through MCP.

- **What**: an MCP server over stdio, published on npm as `@falkenslab/asker-mcp`, that an AI app (Claude Code, Codex, an agent built on agent-kit) starts with `npx`. It drives the `asker` command (the `asker-tool` Ruby gem) the person installs apart.
- **For whom**: teachers who build question banks from their own definitions, through miyagi or any MCP client.
- **What an agent does with it**: write an Asker input (HAML: `%map`, `%concept` with `%names`, `%tags`, `%def`, `%table`…) from the teacher's notes, check it (`asker check`), generate questions from it (`asker FILE`: true/false, multiple choice, short answer, matching, ordering), read them back by concept and type, and leave out the bad ones before moodle-teacher imports the file (`import_questions`).
- **How it reaches agents**: as the `asker` extension in [agent-extensions](https://github.com/falkenslab/agent-extensions), which pins its version, declares Ruby and asker-tool as requirements, adds the skills (Asker's input language, generating and reviewing) and the capabilities.
- **Out of scope**: writing questions without Asker (the agent already does, in GIFT), importing them into Moodle (moodle-teacher's), deciding what a course should ask (the agent's craft), and installing Ruby or asker-tool (explained, never installed: ADR-004).
- **Where it stands**: the template, renamed; the work is `.minispec/features/asker-tools.md`.
