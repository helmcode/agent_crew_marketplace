FROM ghcr.io/helmcode/agent_crew_agent:0.3.6

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    unzip \
    && curl -fsSL "https://awscli.amazonaws.com/awscli-exe-linux-$(uname -m).zip" -o /tmp/awscliv2.zip \
    && unzip -q /tmp/awscliv2.zip -d /tmp \
    && /tmp/aws/install \
    && rm -rf /tmp/aws /tmp/awscliv2.zip /var/lib/apt/lists/*
