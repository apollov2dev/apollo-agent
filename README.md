# apollo-agent

Releases of the Apollo Platform agent: the service that runs on a club's server and carries out what the platform asks
for (deploying, updating and checking the club's containers). It only makes outbound HTTPS requests to its platform;
nothing on the server has to be reachable from outside.

This repository holds no code, only the [releases](../../releases): for every version the agent for Linux x64 and arm64,
the SHA-256 checksum of each archive, `SHA256SUMS` and the installer `install-agent-linux.sh`.

## Install

On Ubuntu 22.04 / 24.04 or Debian 12 (x64 or arm64), run the command the platform's portal shows when a server is
registered:

```bash
curl -fsSL https://<platform>/api/agent/v1/install.sh | sudo bash -s -- --server https://<platform>
```

The platform hands out the agent version that matches it. The installer installs Docker Engine when it is missing,
downloads that agent, checks it against its checksum, asks for the agent token (hidden prompt) and starts the systemd
service `apollo-agent`. Running it again upgrades the agent and keeps its enrolment.

## Check a download by hand

```bash
sha256sum --check --ignore-missing SHA256SUMS
```
