# Exim Billing — Deploy Setup

## Files for Auto-Deploy from GitHub to DigitalOcean

| File | Purpose |
|------|---------|
| `Dockerfile` | PHP 8.2 + Apache container |
| `docker-compose.yml` | Runs the PHP app on port 80 |
| `.github/workflows/deploy.yml` | GitHub Actions — auto-deploy on push |

## How to use

1. Copy these 3 files into your project folder
2. `git add . && git commit -m "Add Docker + deploy" && git push`
3. On DigitalOcean VPS, run once:
   ```
   cd /var/www/exim_billing
   docker compose up -d
   ```
4. Set up GitHub Secrets (repo → Settings → Secrets → Actions):
   - `VPS_HOST` = 139.59.99.7
   - `VPS_USER` = root
   - `VPS_SSH_KEY` = (your SSH private key)
5. After that, every `git push` auto-deploys!
