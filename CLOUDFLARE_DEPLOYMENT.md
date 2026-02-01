# Cloudflare Pages Deployment

This repository is configured to deploy to Cloudflare Pages.

## Automatic Deployment via GitHub Actions

The repository includes a GitHub Actions workflow (`.github/workflows/cloudflare-pages.yml`) that automatically builds and deploys the site to Cloudflare Pages when changes are pushed to the `main` or `master` branch.

### Setup Required

To enable automatic deployment, you need to configure the following secrets in your GitHub repository settings:

1. **CLOUDFLARE_API_TOKEN**: Your Cloudflare API token with Pages write permissions
   - Go to [Cloudflare Dashboard](https://dash.cloudflare.com/profile/api-tokens)
   - Create a token with "Cloudflare Pages: Edit" permissions

2. **CLOUDFLARE_ACCOUNT_ID**: Your Cloudflare account ID
   - Found in your [Cloudflare Dashboard](https://dash.cloudflare.com) URL or account settings

## Manual Deployment via Cloudflare Dashboard

Alternatively, you can deploy directly through the Cloudflare Pages dashboard:

1. Log in to your [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Go to "Pages" in the left sidebar
3. Click "Create a project"
4. Connect to your GitHub repository
5. Configure the build settings:
   - **Build command**: `pip install -r requirements.txt && mkdocs build`
   - **Build output directory**: `site`
   - **Root directory**: `/`
6. Click "Save and Deploy"

## Build Configuration

The site is built using MkDocs with the Material theme. The build process:

1. Installs Python dependencies from `requirements.txt`
2. Runs `mkdocs build` to generate the static site
3. Outputs the built site to the `site` directory

## Environment Variables

No environment variables are required for the build process.

## Python Version

The build uses Python 3.x (latest stable version).

## Node.js Version

The `.node-version` file specifies Node.js 18 for compatibility with Cloudflare Pages.
