FROM ghcr.io/helmcode/agent_crew_agent:0.3.7

RUN apt-get update && apt-get install -y --no-install-recommends \
    chromium \
    && rm -rf /var/lib/apt/lists/* \
    && npm install -g agent-browser
