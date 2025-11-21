# GitHub Actions Workflows

## Docker Build Workflow

This workflow automatically builds and pushes Docker images to Docker Hub.

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

### How It Works

The workflow triggers on:
- **Push to main branch**: Builds and pushes with `latest` and `v0.0.5-beta` tags
- **Manual trigger**: You can run it manually from the Actions tab
- **Daily schedule**: Checks for updates at 2 AM UTC daily
- **Version tags**: If you push a tag like `v1.0.0`, it creates version-specific tags

### Multi-Platform Support

The workflow builds for both:
- `linux/amd64` (Intel/AMD servers)
- `linux/arm64` (ARM servers, Apple Silicon)

### Caching

GitHub Actions caching is enabled to speed up subsequent builds.

