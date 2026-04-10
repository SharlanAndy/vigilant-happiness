# Admin Panel — Deploy to GitHub Pages

**Repo:** `SharlanAndy/vigilant-happiness`  
**Live URL:** `https://sharlanandy.github.io/vigilant-happiness/`  
**Backend API:** `https://api.iotareward.com/api`

## Build & Deploy

```bash
# 1. Go to admin project
cd /Users/khoo/Documents/GitHub/project17/apps/admin

# 2. Build for production (requires Node 18+)
PATH=~/.nvm/versions/node/v20.19.5/bin:$PATH \
  VITE_API_URL=https://api.iotareward.com/api \
  npx vite build --base=/vigilant-happiness/

# 3. Copy build output to GitHub Pages repo
cp -r dist/* /Users/khoo/Documents/GitHub/vigilant-happiness/

# 4. Commit and push
cd /Users/khoo/Documents/GitHub/vigilant-happiness
git add -A
git commit -m "Deploy: <describe changes>"
git push origin main
```

## Notes

- Node 14 is default on this machine — must use `PATH=~/.nvm/versions/node/v20.19.5/bin:$PATH` prefix
- `--base=/vigilant-happiness/` is required for GitHub Pages sub-path routing
- `VITE_API_URL` defaults to `/api` (broken on GitHub Pages) — always pass it explicitly
- `404.html` = copy of `index.html` for SPA deep-link refresh support
- GitHub Pages takes ~1 min to propagate after push

## Admin Login

- URL: `https://sharlanandy.github.io/vigilant-happiness/login`
- Demo login: calls `POST /api/auth/admin/demo-login`
- Real login: calls `POST /api/auth/admin/login`
