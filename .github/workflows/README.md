# GitHub Actions Workflows

## Automated Docker Build & Upstream Sync

This workflow automatically:
1. **Syncs with upstream** (bnb-chain/reth-bsc) daily
2. **Merges updates** into your fork automatically
3. **Builds Docker images** for both AMD64 and ARM64
4. **Pushes to GitHub Container Registry** (ghcr.io) with version tags

### Setup Instructions

1. **Enable Actions Permissions:**
   - Go to your repository: https://github.com/kw1knode/reth-bsc
   - Click Settings → Actions → General
   - Under "Workflow permissions", select "Read and write permissions"
   - Click "Save"

2. **Enable Package Visibility (Optional):**
   - After the first build, go to your packages: https://github.com/kw1knode?tab=packages
   - Click on the `reth-bsc` package
   - Click "Package settings"
   - Change visibility to "Public" if you want others to pull it

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

### Using the Images

Pull the image from GitHub Container Registry:

```bash
# Latest version
docker pull ghcr.io/kw1knode/reth-bsc:latest

# Specific version
docker pull ghcr.io/kw1knode/reth-bsc:v0.0.5-beta
```

### Caching

GitHub Actions caching is enabled to speed up subsequent builds.

