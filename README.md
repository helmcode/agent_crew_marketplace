# AgentCrew Marketplace

Pre-built custom agent images for [AgentCrew](https://agentcrew.sh).

## Repository Structure

```
<agent_type>/<image_name>/
├── Dockerfile
├── README.md
└── VERSION
```

| Directory | Base Image | Image Prefix |
|-----------|-----------|--------------|
| `claude-code/` | `ghcr.io/helmcode/agent_crew_agent:0.3.7` | `agentcrew-cc-` |
| `open-code/` | `ghcr.io/helmcode/agent_crew_opencode_agent:0.3.7` | `agentcrew-oc-` |

### Naming Convention

```
ghcr.io/helmcode/agentcrew-{prefix}-{image_name}:{version}
```

Examples:

| Path | Published Image |
|------|----------------|
| `claude-code/aws/` | `ghcr.io/helmcode/agentcrew-cc-aws:latest` |
| `claude-code/gcp/` | `ghcr.io/helmcode/agentcrew-cc-gcp:latest` |
| `open-code/aws/` | `ghcr.io/helmcode/agentcrew-oc-aws:latest` |

## Available Images

### Claude Code (`cc`)

| Image | Description | Usage |
|-------|-------------|-------|
| [`aws`](claude-code/aws/) | AWS CLI v2 | `ghcr.io/helmcode/agentcrew-cc-aws:latest` |
| [`helmcode-finops`](claude-code/helmcode-finops/) | Helmcode FinOps CLI | `ghcr.io/helmcode/agentcrew-cc-helmcode-finops:latest` |

### OpenCode (`oc`)

| Image | Description | Usage |
|-------|-------------|-------|
| [`aws`](open-code/aws/) | AWS CLI v2 | `ghcr.io/helmcode/agentcrew-oc-aws:latest` |
| [`helmcode-finops`](open-code/helmcode-finops/) | Helmcode FinOps CLI | `ghcr.io/helmcode/agentcrew-oc-helmcode-finops:latest` |

## Usage

Set the **Custom Agent Image** field when creating or editing a team in the AgentCrew UI.

See the [Custom Agent Images](https://agentcrew.sh/docs/configuration#custom-agent-images) documentation.

## Contributing

1. Choose the agent type directory: `claude-code/` or `open-code/`
2. Create a subdirectory with a descriptive name (e.g., `aws`, `gcp`, `playwright`)
3. Add a `Dockerfile` extending the corresponding base image (pin to a specific version):
   - Claude Code → `FROM ghcr.io/helmcode/agent_crew_agent:<version>`
   - OpenCode → `FROM ghcr.io/helmcode/agent_crew_opencode_agent:<version>`
4. Add a `README.md` with base image version, additional tools, and usage
5. Add a `VERSION` file with the image version (e.g., `0.1.0`)
6. Push to `main` — only changed directories are built and published

### CI Pipeline

- **Push to `main`**: detects changed directories and builds only those images
- **Manual trigger**: build all images or a specific one (e.g., `claude-code/aws`)
- All images are built for **linux/amd64** and **linux/arm64**
- Each image is tagged with its `VERSION` and `latest`
