# GitHub Actions Workflow

Automatically syncs with upstream and builds Docker images.

## Setup

1. Go to https://github.com/kw1knode/reth-bsc/settings/actions
2. Enable "Read and write permissions"
3. Save

## What it does

- Runs daily at 2 AM UTC
- Syncs with bnb-chain/reth-bsc
- Builds AMD64 Docker image
- Pushes to ghcr.io

## Usage

```bash
docker pull ghcr.io/kw1knode/reth-bsc:latest
```
