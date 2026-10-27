---
title: Empezar
sidebar_label: Empezar
---

# Empezar

Necesitas [Node.js](https://nodejs.org) 20 o posterior.

## En un agente hecho con agent-kit

Instala su extensión desde el marketplace de Falken's Lab, que ejecuta este servidor a una versión fija y añade las skills para usarlo bien:

```bash
my-agent extension marketplace add falkenslab/agent-extensions
my-agent extension add asker-mcp@falkenslab
```

## En Claude Code

```bash
claude mcp add asker-mcp -- npx -y @falkenslab/asker-mcp
```

O, con sus skills, como plugin del mismo marketplace:

```bash
claude plugin marketplace add falkenslab/agent-extensions
claude plugin install asker-mcp@falkenslab
```

## Comprobar que funciona

Pregunta al agente: «¿Qué versión de asker-mcp estás usando?». Llamará a `server_info`.
