# AgentCrew Marketplace

Pre-built custom agent images for [AgentCrew](https://github.com/helmcode/agent_crew).

Each directory contains a `Dockerfile` that extends the official AgentCrew agent base images with additional tools and dependencies for specific use cases.

## Usage

Set the **Custom Agent Image** field when creating or editing a team in the AgentCrew UI:

```
ghcr.io/helmcode/agentcrew-<image-name>:latest
```

## Available Images

| Image | Base | Description |
|-------|------|-------------|
| *Coming soon* | | |

## Building Custom Images

See the [Custom Agent Images](https://agentcrew.sh/docs/configuration#custom-agent-images) documentation.

## Contributing

1. Create a new directory with a descriptive name
2. Add a `Dockerfile` extending one of the base images:
   - `ghcr.io/helmcode/agent_crew_agent:latest` (Claude Code)
   - `ghcr.io/helmcode/agent_crew_opencode_agent:latest` (OpenCode)
3. Push to `main` — only the changed directory will be built and published
