# AgentCrew Marketplace

Pre-built custom agent images for [AgentCrew](https://github.com/helmcode/agent_crew).

## Repository Structure

```
<agent_type>/<image_name>/
├── Dockerfile
└── VERSION
```

| Directory | Base Image | Image Prefix |
|-----------|-----------|--------------|
| `claude_code/` | `ghcr.io/helmcode/agent_crew_agent:latest` | `agentcrew-cc-` |
| `open_code/` | `ghcr.io/helmcode/agent_crew_opencode_agent:latest` | `agentcrew-oc-` |

### Naming Convention

```
ghcr.io/helmcode/agentcrew-{prefix}-{image_name}:{version}
```

Examples:

| Path | Published Image |
|------|----------------|
| `claude_code/aws/` | `ghcr.io/helmcode/agentcrew-cc-aws:latest` |
| `claude_code/gcp/` | `ghcr.io/helmcode/agentcrew-cc-gcp:latest` |
| `open_code/aws/` | `ghcr.io/helmcode/agentcrew-oc-aws:latest` |

## Available Images

### Claude Code (`cc`)

| Image | Description | Usage |
|-------|-------------|-------|
| [`aws`](claude_code/aws/) | AWS CLI v2 | `ghcr.io/helmcode/agentcrew-cc-aws:latest` |

### OpenCode (`oc`)

| Image | Description | Usage |
|-------|-------------|-------|
| [`aws`](open_code/aws/) | AWS CLI v2 | `ghcr.io/helmcode/agentcrew-oc-aws:latest` |

## Usage

Set the **Custom Agent Image** field when creating or editing a team in the AgentCrew UI.

See the [Custom Agent Images](https://agentcrew.sh/docs/configuration#custom-agent-images) documentation.

## Contributing

1. Choose the agent type directory: `claude_code/` or `open_code/`
2. Create a subdirectory with a descriptive name (e.g., `aws`, `gcp`, `playwright`)
3. Add a `Dockerfile` extending the corresponding base image:
   - Claude Code → `FROM ghcr.io/helmcode/agent_crew_agent:latest`
   - OpenCode → `FROM ghcr.io/helmcode/agent_crew_opencode_agent:latest`
4. Add a `VERSION` file with the image version (e.g., `0.1.0`)
5. Push to `main` — only changed directories are built and published

### CI Pipeline

- **Push to `main`**: detects changed directories and builds only those images
- **Manual trigger**: build all images or a specific one (e.g., `claude_code/aws`)
- All images are built for **linux/amd64** and **linux/arm64**
- Each image is tagged with its `VERSION` and `latest`
