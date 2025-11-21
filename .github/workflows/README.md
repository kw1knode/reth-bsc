# GitHub Actions Workflows

## Automated Docker Build & Upstream Sync

This workflow automatically:
1. **Syncs with upstream** (bnb-chain/reth-bsc) daily
2. **Merges updates** into your fork automatically
3. **Builds Docker images** for both AMD64 and ARM64
4. **Pushes to Docker Hub** with version tags

### Setup Instructions

1. **Create Docker Hub Access Token:**
   - Go to https://hub.docker.com/settings/security
   - Click "New Access Token"
   - Give it a name (e.g., "github-actions")
   - Copy the token (you won't see it again!)

2. **Add Secrets to GitHub:**
   - Go to your repository: https://github.com/kw1knode/reth-bsc
   - Click Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Add two secrets:
     - Name: `DOCKERHUB_USERNAME`, Value: `kw1k`
     - Name: `DOCKERHUB_TOKEN`, Value: (paste the token from step 1)

3. **Enable Actions:**
   - Go to Settings → Actions → General
   - Under "Workflow permissions", select "Read and write permissions"
   - Click "Save"

### How It Works

The workflow triggers on:
- **Daily schedule**: Checks for upstream updates at 2 AM UTC daily
- **Push to main branch**: Builds and pushes immediately
- **Manual trigger**: You can run it manually from the Actions tab
- **Version tags**: If you push a tag like `v1.0.0`, it creates version-specific tags

### Upstream Sync Process

1. Fetches latest changes from `bnb-chain/reth-bsc`
2. Attempts to merge into your `main` branch
3. If successful, pushes to your fork and triggers Docker build
4. If there's a merge conflict, it skips and notifies you

### Multi-Platform Support

The workflow builds for both:
- `linux/amd64` (Intel/AMD servers)
- `linux/arm64` (ARM servers, Apple Silicon)

### Caching

GitHub Actions caching is enabled to speed up subsequent builds.

