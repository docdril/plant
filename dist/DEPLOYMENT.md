# Deployment Instructions

This dist folder is configured for deployment to **Cloudflare Pages**, **Vercel**, and **Netlify**.

## What's Fixed

✅ Relative asset paths (./assets/...)
✅ 404.html for SPA routing fallback
✅ Platform-specific configuration files
✅ Cache headers optimized for production

## Deployment Steps

### For Vercel
1. Delete your current Vercel project or create new one
2. Push this entire dist folder to a new GitHub repo
3. On Vercel:
   - Click "Import Project"
   - Select your GitHub repo
   - **Build & Development Settings:**
     - Framework: "Other"
     - Build Command: Leave empty
     - Output Directory: . (dot)
     - Root Directory: . (dot)
   - Deploy ✅

### For Netlify
1. Push this entire dist folder to a new GitHub repo
2. On Netlify:
   - Click "New site from Git"
   - Select your GitHub repo
   - **Build settings:**
     - Build command: Leave empty
     - Publish directory: . (dot)
     - Function directory: Leave empty
   - Deploy ✅

### For Cloudflare Pages
1. Push this entire dist folder to a new GitHub repo
2. On Cloudflare Pages:
   - Create new project
   - Connect GitHub
   - Select your repo
   - **Build settings:**
     - Build command: Leave empty
     - Build output directory: . (dot)
   - Deploy ✅

## File Structure

```
dist/
├── index.html           - Main app (relative asset paths)
├── 404.html            - SPA routing fallback
├── vercel.json         - Vercel configuration
├── netlify.toml        - Netlify configuration
├── _redirects          - Cloudflare redirects
├── _headers            - Cloudflare cache headers
└── assets/
    ├── index-DzHoiiGk.js
    └── index-B5bh_FfO.css
```

## Important Notes

- **ALWAYS** deploy the entire dist folder as the root of your repository
- Do NOT add this to a subdirectory
- Do NOT merge with the source code
- Keep this folder separate for production deployment
- The 404.html file handles client-side routing for all platforms

## If You Still Get 404 Errors

Try these steps in order:

1. Clear your browser cache (Ctrl+Shift+Delete or Cmd+Shift+Delete)
2. Do a hard refresh (Ctrl+F5 or Cmd+Shift+R)
3. Check that build output directory is set to `.` (dot)
4. Verify build command is empty
5. Make sure all files (including _headers, _redirects, vercel.json, netlify.toml, 404.html) are in the root
6. Wait 2-5 minutes for deployment to propagate

## Testing Locally

To test before deploying:
```bash
cd /Volumes/T9/Coding/testcodes/plant/dist
python3 -m http.server 8000 --directory .
```
Then visit: http://localhost:8000
